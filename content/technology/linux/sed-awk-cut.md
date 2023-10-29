---
title:  "Text processing using awk sed and cut"
date:   2022-02-18 04:04:21 +0530
categories: awk sed cut
slug: "text-processing-using-awk-sed-and-cut"
draft: false
---

## awk

```
openstack image list > images.txt
+----------------+--------------+-----------+
| ID             | Name         | Status    |
+----------------+--------------+-----------+
| 9789-4b3f-95b8 | windows-2012 | active    |
| 27a3-46c2-b821 | windows-2016 | active    |
| f45a-4c89-a69f | windows-2019 | active    |
| 012f-4751-822a | windows-2019 | active    |
| 68c8-4d4b-a5b5 | windows-2022 | active    |
+----------------+--------------+-----------+
```

### extract only windows-2016 image id
```
# on a bash or zsh shell
ID=`awk '$4=="windows-2016" {print $2}' images.txt`
echo $ID
27a3-46c2-b821

# on a fish shell
set ID $(awk '$4=="windows-2016" {print $2}' images.txt)
echo $ID
27a3-46c2-b821

```

### using a variable
```
# on a bash or zsh shell
IMAGE_NAME="windows-2022"
ID=`awk -v image_name=$IMAGE_NAME '$4==image_name {print $2}' images.txt`
echo $ID
68c8-4d4b-a5b5

# on a fish shell
set IMAGE_NAME 'windows-2022'
set ID $(awk -v image_name=$IMAGE_NAME '$4==image_name {print $2}' ~/tmp/images.txt)
echo $ID
68c8-4d4b-a5b5
```

### find a process (middleman) and kill it 
```
kill -9 $(ps -ef | grep middleman | awk '$8=="/usr/local/var/rbenv/versions/2.3.0/bin/middleman" {print $2}')
# find another process and kill it

```

## cut

### list status column
```
while read line
do [ -z "$line" ] && continue ;
echo $line|rev|cut -f5 -d' '|rev
done < images.txt
```

### read all image names
```
while read line
do [ -z "$line" ] && continue ;
echo $line|cut -f4 -d' '
done < images.txt
```

### get lines count
```
cat -n images.txt | tail -n 1 | cut -f1
```

### print the number of fields/columns in each line of the file

```
awk '{print NF}' images.txt
```

### more presentable
```
awk '{print NR "----" NF}' images.txt
# 1----1
# 2----7
# 3----1
# 4----7
# 5----7
# 6----7
# 7----7
# 8----7
# 9----1
```

### column count for each line
```
while read line
do [ -z "$line" ] && continue ;
# echo $line
COUNT=`echo $line|awk '{print NF}'`
echo $COUNT
# echo $line|rev|cut -f5 -d' '|rev
done < images.txt
```

### print column 2 if column text is not `ID`
```
awk '{ if ($2!="ID") {print "Image", $2, "\n"} }' images.txt
```
# awk with conditions 
```
awk '{ 
id=$2;
first_line="+----------------+--------------+-----------+";
if($1!=first_line);
{ print "ID", $2, "NAME", $4, "STATUS", $6, "\n"};
}' images.txt
```

### use a file with awk
```
cat << EOF > image.awk
{ 
id=$2;
name=$4;
status=$6;
first_line="+----------------+--------------+-----------+";
if ( id!="ID" );
{ print "ID", $2, "NAME", $4, "STATUS", $6, "\n"};
}
EOF

awk -f image.awk images.txt
```

### using a file for input another file for command.

#### create a text file called kids.txt
```
cat << EOF >kids.txt
FEMIDA    8   Female      Berlin
FARZANA   3   Female      Chennai
YUSRA     6   Female      Howrah
AFIRA     10  Female      Thanjavur
FAZILA    4   Female      Thanjavur
WAFIQAH   13  Female      Madurai
FAZIL     10  Male        Santhamanikam
FAIZAL    8   Male        Santhamanikam
FEMINA    4   Female      Santhamanikam
EOF
```

#### create an awk command file called language.awk
```
cat << EOF >language.awk
{
name=$1;
if ( name=="FEMIDA" ) language="German";
else if (name=="FARZANA") language="English";
else if (name=="YUSRA") language="German";
else if (name=="AFIRA") language="English";
else if (name=="FAZILA") language="English";
else if (name=="WAFIQAH") language="English";
else if (name=="FAZIL") language="English";
else if (name=="FAIZAL") language="English";
else language="None";

if(language!="None") print "The favorite language of ", name, "is ", language;
else print "No person found";
}
EOF
```

#### run it
```
awk -f language.awk kids.txt
```

### prints last column/field in each line
```
awk 'NF>1{print $NF}' kids.txt
```

### prints total number of rows/lines in the file
```
awk 'END {print NR}' kids.txt
```

### similar commands to acheive the same thing
```
wc -l < kids.txt
sed -n '$=' kids.txt

brew install gawk
```

### get first field of a file
```
gawk -F: '{ print $1 }' kids.txt
```

### create a file called marks.txt
```
cat << EOF >marks.txt
Tamil       95
English     100
Mathematics 100
Science     98
Social      98
EOF
```

### prints the entire line if text found
```
grep '^Tamil' marks.txt

gawk '{ sum += $2 }; END { print "You scored ", sum, "out of 500 marks"}' marks.txt
```

### output
```
You scored  491 out of 500 marks
```



## Text manipulation with cut

### -f3- prints column 3 onwards including columnn 3
```
echo "ABC DEF MNO PQR ZSA" | cut -d ' ' -f3-
# it shows from columns 3 onwards including 3 
MNO PQR ZSA
```

### -f3 prints column 3 only
```
echo "ABC DEF MNO PQR ZSA" | cut -d ' ' -f3
# output 
MNO

```

### use awk to extract
```
_input=kids.txt
while IFS= read -r line
do
  awk '{print substr($0, index($0,$4))}' <<< "$line"
done < "${_input}"
```

### use cut to extract 
```
echo "ONE TWO THREE FOUR FIVE" |  cut -d ' ' -f3-
THREE FOUR FIVE

```

## sed

### replace just the text
```
sed -ie 's/Tamil/German/g' marks.txt
```

### replace the entire line
```
sed -ie 's/.*German.*/Tamil  90/g' marks.txt
```

### search something and write if not found
```
grep -q '^English' marks.txt && sed -ie 's/^English.*/English 95/' marks.txt 
grep -q '^English' marks.txt && sed -ie 's/^English.*/English 100/' marks.txt || echo 'English   95' >> marks.txt
```

### @ as a separator; find Social and replaces the line with 'SocialScience   98'
```
sed -ie 's@^Social.*@SocialScience   98@g' marks.txt
```

### finds Arabic in the file marks.txt, if not found writes it
```
grep -q "Arabic" marks.txt || echo "Arabic  99" >> marks.txt
```
