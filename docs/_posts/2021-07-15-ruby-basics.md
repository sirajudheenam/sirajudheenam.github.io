---
layout: post
title:  "Ruby Crash Course"
date:   2021-07-15 20:24:41 +0530
author: Sirajudheen Mohamed Ali
image: images/how_it_works.png
comments: false
hide: false
categories: ruby
---

```ruby

# Find out if you have ruby installed.

print "Ruby is Object Oriented Programming Language"

x = 1
puts x + 2
first_variable = x + 2
articles_written = 100
puts articles_written
puts first_variable
puts 1234.class
x = 1234 * 1234 * 1234 * 1234 * 12345678
puts x
puts x.class

puts -200.abs
puts 200.next
puts 123456.8967.class
x = 10.0
y = 12.4
z = x + y
puts z

puts 12345.789.round
puts 12345.789.ceil
puts 1234.34.to_i
greeting = "Hello"
target = "World"
puts greeting + ' ' + target

puts 'I\'m escaped'
puts "I said, \"I'm escaped.\""
puts "Difference between Single Quote and Double Quote"
puts "\ta\tb\nc\nd"
puts "Difference between Single Quote and Double Quote"
puts '\ta\tb\nc\nd'
puts
# Both Single Quote and Double Quotes produces same result.
puts "I wanted to say #{greeting} #{target}"

puts 'I wanted to say #{greeting} #{target}'

puts "Hello".reverse
puts "hello".capitalize
puts "Hello".downcase
puts "Hello".upcase
puts "Hello".length
puts "Hello".reverse.capitalize.downcase.upcase

#Array - Collection of Objects
puts "ARRAY"
data_set = []
data_set = ["a","b","c"]
puts data_set[0]
data_set[0]="d"
data_set << "e"
puts data_set
data_set
data_set.class
data_set =[]
puts data_set.class
data_set = nil
puts data_set.class
#
array = [1,2,3,4,5]
array2 = [1,"2",3.0, ["a","b"],"dog"]
puts array

# Difference
puts array.inspect
puts array2
puts array2.inspect
puts array2.to_s
puts array2.join
puts array2.join(", ")
x = "1,2,3,4,5"
y = x.split(',')
puts y.reverse
puts y.inspect
array3 = [3, 5, 7, 4, 6, 9, 8, 3]
puts array3.sort
puts "Unsorted array 3"

# Just to display the Unique values only
puts array3.uniq  
# Modify the array and Display the Unique values
puts array3.uniq!
puts array3.inspect

# Delete the digit at array position 2
puts array3.delete_at(2) 

# Displays after deletion 
puts array3 
array3 << 14
array3.push(0)

# Displays after inserting
puts array3  
puts array3.inspect

# Pops the last one out
puts array3.pop

puts array3.shift
puts array3.unshift(3)
puts array3
puts new_array = array + array3
puts new_array.inspect
puts array - [2]

# Hashes
puts "HASHES - Key / Value Pair"
puts person = ["Kevin","Skoglund","male","blue","blonde"]
puts person = {'first_name' =>"Femida Hasina", 'last_name'=>'Sirajudheen'}
puts person.inspect
puts person['last_name']
puts person['first_name']
mixed = {[1,2]=>"Array", 1=>"Number One", "String"=>"Some String"}

puts "Mixed Array"
puts mixed[[1,2]]
puts mixed.keys
puts mixed.values
puts mixed.length
puts mixed.size
puts mixed.to_a.inspect #Coverts Hash into an array
puts person['birth_date'] ='01/01/2014'
puts person
puts person.inspect

puts "SYMBOLS - Syntax :symbol_name"
puts :sample #Symbol called sample
puts :sample.object_id
puts child = {:first_name =>"Femida Hasina", :last_name => 'Sirajudheen'}
puts child[:first_name]
puts "*******************************"
puts "BOOLEANS"
puts "Comparison & Logical Operators {== / < > <= >= ! != && ||}"

# Comparision Operators
x = 1
puts x==1
puts true.class
puts false.class
puts !x; 
puts x-1
puts x==0
puts x>=5
puts 1 <= 4 && 5 <= 100
puts 1 <= 4 && 5 <= 100 && 100 >=500
puts 1 <= 4 || 5 <= 100 || 100 >=500
puts 16 <= 4 || 5 <= 100 || 100 >=500
puts 16 <= 4 || 500 <= 100 || 100 >=500
puts x.nil?
puts y.nil?
puts 2.between?(1,4)
puts [].empty?
puts [1,2,3].empty?
puts [1,2,3].include?(2)
puts [1,3,3].include?(2)

puts x={'a' =>1, 'b'=>2 }.has_key?('a')
puts x={'a' =>1, 'b'=>2 }.has_key?(:a)
puts x={'a' =>1, 'b'=>2 }.has_value?(1)
puts x={'a' =>1, 'b'=>2 }.has_value?(4)

# Ranges
puts "Ranges 1....10"
puts "Inclusive Ranges 1 2 3 4 5 6 7 8 9 10 (includes 10)"
puts x = 1..10
puts (1..10).class
puts x.begin
puts x.end
puts x.first
puts x.last

puts "Exclusive Ranges - 1 2 3 4 5 6 7 8 9 (Not 10)"
puts y = 1...10
puts (1..10).class
puts y.begin
puts y.end
puts y.first
puts y.last
puts x.include?(10) # Should return true
puts y.include?(10) # Should return false
puts "Exclusive Ranges - It still returns 10 as the last number"

# Expanded 
z = [*x] 
puts z

alpha ='a'..'m'
puts alpha.include?('g')
puts alpha.include?('m')
alpha ='a'...'m'
puts alpha.include?('g')
puts alpha.include?('m')

# Expand alpha
puts [*alpha]
puts [*alpha].inspect
puts "*****************************"
puts "CONSTANTS"
puts "Constants starts with Upper case "
TEST = 10
puts TEST
TEST = 11
puts TEST # You will get a warning
puts "*****************************"
puts "CONTROL STRUCTURES"
puts "if ... elsif (YES ELSIF) .... else .. end "
name ="Mary"

if name == "Sam"
	put "Sam"
elsif name == "Mary"
	puts "Mary"
else
	puts "Not Sam or Mary; You confused me"
end

first_name = "Femida"
puts "Femida is the first name" if first_name == "Femida"
puts "Hasina is the first name" if first_name == "Hasina"
puts "unless..... "
puts "case <test_value>... when <value> when boolean else .. end"
puts ("Ternary operator")
puts ("boolean > code 1:code 2")
puts x==1 ? "one" : x
x = 1
y = 2
x = z || y
puts x
unless x
  x = 10
end
d||=10
puts d

puts "LOOPS - "
puts " loop do 
		.....
		end"
puts "loop do
	break .. Quit immediately
	next ..
	redo .. 
	retry .. Start completely again"
	e = 0
	loop do
		e+=2
		break if e >= 20
		puts e
	end
puts "This code will skip printing 6 since we ask it to do next"
	loop do 
		 e += 2
		break if e >=20
		next if e==6
		puts e
	end

puts " while boolean
	....
	end"
puts ""
x=0
while x<=20
	puts x
	x=x+2
	end
x=0
puts x+=2 while x<100
y = 2400
puts y/=2 until y <=1

puts "ITERATORS - LOOP TYPE"
puts "5.times do 
	puts \"Hello \"
end"
5.times do 
puts "Hello" 
end
puts " {} = do .. end"
1.upto(5) {puts "5 times"}
5.downto(1) {puts "Hello"}
(1..5).each {puts "Hello"}

1.upto(5) do |i|
	puts"Hello " + i.to_s
end
fruits = ['banana','apple','pear']
fruits.each do |fruit|
	puts fruit.capitalize
end
for fruit in fruits
	puts fruit.capitalize
end
puts "Integer/floats: times upto downto step"
puts "Range each, step"
puts "String: each, each_line, each_byte"
puts "Array: each, each_index, each_with_index"
puts "Hash each, each_key,each_value, each_pair"
puts "*****************************************"
puts "CODE BLOCKS "
puts 5.times {puts "One"}
1.upto(5) {|i| puts "Hello : " + i.to_s}
array = [1,2,3,4,5]
x=1
array.each {|num| puts num * 20 + x} # num is Block variable it is not accessible outside the block
# puts num # Will return an error
num =1
array.each {|num| puts num * 30 + x} #now it will use the local variable on older version
puts num # Displays local variable
puts "Common methods that use blocks"
puts " find
		merge
		collect
		sort
		inject
		"
puts "FIND
	find /detect
	find_all/select
	any?
	all?
	delete_if
	"
puts (1..10).find {|i| i==5}
puts (1..10).find {|i| i % 3 ==0}
puts (1..10).detect {|i| i % 3 ==0}
puts (1..10).find_all {|i| i % 3 ==0 }
puts (1..10).select {|i| (1..10).include?(i*3)}
puts (1..10).any? {|i| i % 3 ==0 } #returns a boolean
puts (1..10).all? {|i| i % 3 ==0 } #returns a boolean
puts [*1..10].delete_if {|i| i % 3 == 0}

puts "MERGE - Use with only HASH"
h1 = {"a" => 111, "b"=> 222}
h2 = {"b" => 333, "c" => 444}
puts "default merge - overwrites the old one"
puts h1.merge(h2) # now b = 333
puts h2.merge(h1) # now b=222
puts h1.merge(h2) {|key,old,new| new}
puts h1.merge(h2) {|key,old,new| old}
puts h1.merge(h2) {|key,old,new| old < new ? new : old}
puts h1.merge(h2) {|key,old,new| new < old ? new : old}
puts "Using if method"
puts h1.merge(h2) do |key, old, new|
	if old < new
		old
	else 
		new
	end
end
# ! gives the merge permanent merge!
puts "collect or map has similar meaning here"
puts "number of items in = number of items out"
puts " It always returns an array"
puts " It work well with ARRAY / HASH / RANGE but returns only array"
array = [1,2,3,4,5,6,7,8,9]
puts array.collect {|i| i+1}
puts array.collect {|j| j*30}
puts ['apple','banana','mango'].map {|fruit| fruit.capitalize}
puts ['apple','banana','mango'].map {|fruit| fruit.capitalize if fruit == 'banana'}
v = ['apple','banana','mango'].map do |fruit| 
	if fruit == 'banana'
		fruit.capitalize
	else 
		fruit
	end
end
puts v
puts v.inspect
puts v.reverse.inspect
puts (1..20).collect {|num| num*20}
hash = {"a"=>111, "b"=>222, "c"=>333}
puts hash.map {|k,v| k}
puts hash.map {|k,v| v}
puts hash.map {|k,v| v*20}
new_array = hash.map {|k,v| "#{k}: #{v*20}"} 
puts new_array.inspect
new_array = ['apple','banana','mango'].map {|fruit| fruit.capitalize}
puts new_array
puts new_array.inspect
puts new_array.class
puts "*******************************************************"
puts "SORT - which makes use of code block {}"
puts "Comparision Operator <=> "
puts " Returns 1 - Less than ; 0 - Equal; 1 - Greater than"
puts " -1 - Less than - MOVES LEFT; 0 - Equal - STAYS; 1 - >  - MOVES RIGHT"
array =[4,2,5,3,1,6,9,3]
puts array.sort {|v1,v2| v1 <=> v2} # Returns -1 if v1 < v2, returns 0 if v1=v2, returns 1 if v1 > v2
puts array.sort #behaves the same way as above code
puts array.sort {|v1,v2| v2 <=> v1}
puts array.sort.reverse #behaves the same way as above code
array =['banana','apple','orange', 'pear','mango']
puts array.sort!
puts array.sort {|fruit1,fruit2| fruit1.length <=> fruit2.length } # sorts by string length
puts array.sort_by {|fruit| fruit.length}
puts array.sort_by {|fruit| fruit.length}.inspect
puts array.sort_by {|fruit| fruit.length}.inspect.class
puts array.sort_by {|fruit| fruit.reverse}
puts "hash sort converts the hash in to an array before it sorts"
hash = {"a"=>444, "c"=>222, "d"=>111, "b"=>666}
puts hash.to_a
puts hash.to_a.inspect
puts hash.sort
puts "IT IS SORTING BASED ON THE ITEM INDEX"
puts hash.sort { |item1, item2| item1[0] <=> item2[0]  }.inspect
puts hash.sort { |item1, item2| item2[0] <=> item1[0]  }.inspect
#puts hash.to_a
#puts hash.to_a.inspect
puts "********************************************************"
puts "inject === ACCUMULATE"
puts "========================================================"
puts "Syntax array.inject {|memo,n| memo + n}"
puts "========================================================="
array = [*1..10]
puts array.inspect
puts array.inject {|memo,n| memo + n}
# This snippet is gonna give you an error
##  puts array.inject {|memo,n| memo + n if n != 3}
sum = array.inject {|memo,n| puts memo + n; memo}
puts sum.inspect
# Here memo's initial value is 100
sum = array.inject(100) {|memo,n| memo + n}
puts sum
array = [4,5,6,7,8,9]
puts array.inspect
puts array.inject {|memo,n| memo + n} #memo takes the first value in array by default
puts "inject(initial_value)"
puts array.inject(100) {|memo,n| memo + n}
puts "If nothing given, it takes the first value in the array[0]:  #{array[0]}"
array = [0,4,5,6,7,8,9]
puts array.inject {|memo,n| memo + 20} #memo takes the first value in array by default
array = [0,4,5,6,7,8,9]
puts array.inject {|memo,n| memo * 20} #memo takes the first value in array by default
# inject with an String Array
fruits = ['apple','banana','mango', 'pineapple']
longest_word = fruits.inject do |memo, fruit|
	if memo.length > fruit.length
		memo # If memo's length is longest then keep return memo
	else
		fruit
	end
end
puts "The longest word in the array #{fruits.inspect} is: #{longest_word}"
puts "Another example: "
menu = ["Home","History","Products","Services","Contact Us"]
# memo = 10 + "Home".length+....+"ContactUs".length
menu.inject(10) {|memo,item| memo + item.length}
puts "*****************************************************"
puts "*****************************************************"
puts " METHODS / FUNCTIONS "
def welcome
	puts "This is first method - by Sam"
end
welcome



# ******************************************************
# Array default values
def welcome(name="World")
	puts "Hello #{name} !"
end
def add(n1=0, n2=0)
	puts n1 + n2
end

def longest_word(words=[])
	longest_word = words.inject do |memo, word|
		memo.length > word.length ? memo : word
	end
	puts longest_word
end

def overfive(value)
	puts value > 5 ? 'Over 5' : 'Not Over 5'
end
welcome("Mary")
welcome
add(2,2)
add(3)
longest_word
fruits =  ['apple','pear','banana','plum']
longest_word(fruits)


# ******************************************************
# Retun Value
def welcome(name="Femida")
	puts "Hello #{name}"
	1 + 1 # this is the return value

end
returned_value = welcome
puts "Returned Value #{returned_value}"

def welcome(name="Femida")
	puts "Hello #{name}"
return 3 + 3 # this is the return value explicit reference
end
# To return early in the code block
# return does not have to be at the end 
# return can be more than one
def overfive?(value=nil)
	return "Exactly 5 !" if value.to_i == 5
	if value.to_i > 5
		return "Over 5"
	else
			return "Under 5"
	end
end

return_value1 = overfive?(5)
puts return_value1
return_value2 = overfive?(6)
puts return_value2
return_value3 = overfive?(4)
puts return_value3

# Return is Singular  -- Only one value
# If you wanna return multiple values then put them in an array

def add_and_subtract(n1=0,n2=0)
	add = n1 + n2
	sub = n1 - n2
	return add , sub # equals to return [add,sub]

end
result = add_and_subtract(12,6)
puts "addition #{result[0]}"
puts "subtraction #{result[1]}"

# Assigning double values if the return value is an array
add, sub = add_and_subtract(40,20)
# [add, sub]= add_and_subtract(40,20) // Similar
puts add
puts sub

# **************************************************
# Operators are also methods
# 8+2  8.+(2) #these two are same
# 8-2  8.-(2) #these two are same
# 8*2  8.*(2) #these two are same
# 8/2  8./(2) #these two are same
# 8**2 8.**(2) #these two are same

# Syntactic Sugar

# array << 4 	array.<<(4)
# array[2]		array.[](2)
# array[2]='x'	array.[]=(2,'x')
# Name your methods also this way
# "hello".5  
puts 8+2
puts 8.+(2)
puts 8 - 2
puts 8.-(2)
puts 8*2
puts 8.*(2)
puts 8/2
puts 8./(2)
puts 8**2
puts 8./(2)

array1 = [1,2,3]
puts array1.inspect
array2 = [1,2,3]
puts array2.inspect

array1 << 4
puts array1.inspect
array2.<<(4)
puts array2.inspect

array[2]
puts array.inspect
array.[](2)
puts array.inspect

array[2] = 'x'
puts array.inspect
array.[]=(2,'x')
puts array.inspect

puts("This is an example Ruby Program")
print("Hello This is from print statement\n")
puts("Enter your name: ")
name = gets
puts "Your name is : " + name
number1 = "10\n"
number2 = "20\n"
result = Integer(number1) + Integer(number2)
print("The result of " + number1.chomp + "\splus\s" + number2.chomp + "\sis\s :", result , "\n")


# Classes 
# # **************************************************
# CLASS
class SomeName #CamelCase It has to start with Upper Case

end
class Animal
	def make_noise
		# "Moo !!"


	end
end

animal1 = Animal.new # Instance: An object created from Class
puts animal1.make_noise

animal2 = Animal.new # Instance: An object created from Class
puts animal2.make_noise

# **************************************************
# Attributes:
# Instance Attributes: @variable -- 
# These variables are not accessible outside these methods
class Animal
	def set_noise(noise)
		@noise = noise # noice is local variable
	end
	def make_noise
		@noise
	end
end

animal1 = Animal.new # Instance: An object created from Class
animal1.set_noise("Moo ! ")
puts animal1.make_noise

animal2 = Animal.new # Instance: An object created from Class
animal2.set_noise("Quack")
puts animal2.make_noise
# **************************************************
# Reader / Writer methods (set / get methods in Java)
class Animal
	def noise=(noise)
		@noise = noise # noise is local variable
	end
	def noise
		@noise
	end
end

animal1 = Animal.new # Instance: An object created from Class
animal1.noise = "Moo ! " # Setter Method in Ruby
puts animal1.noise # Getter method in Ruby

animal2 = Animal.new # Instance: An object created from Class
animal2.noise = "Quack" # Setter Method in Ruby
puts animal2.noise # Getter method in Ruby
# **************************************************
# Attribute Methods - for set/get - Shortcut	
# often called as -- attr_* method
# attr_reader
# attr_writer
# attr_accessor # Both methods
# ******************************
# attr_reader:name
# def name
#	@name
# end
# ====================
# attr_writer:name
# def name=(value)
# @name = value
# end
# ====================
# attr_accessor:name
# def name
#	@name
# end
# def name=(value)
# @name = value
# end
# =====================
class Vehicle
	attr_accessor :name # It creates getter and setter method for 
	attr_writer :color # It creates setter method for color
	attr_reader :wheels, :gears # It creates only getter method

	def self.all_vehicles
		['van','lorry','taxi']
	end
	def setup_parts 
		@gears = 5
		@wheels = 4
	end

	def initialize(name, gears=5, color="Yellow") # like a constructor - Runs everytime  object got created when an instance is created
		@gears = 5
		@wheels = 4
		puts 
	end
	def color # explicit getter for color as it has only writer
		"The Color is #{@color} " 
	end

end

vehicle1 = Vehicle.new("Van",5,4)
# vehicle1.setup_parts
vehicle1.name 	= "Audi"
vehicle1.color 	= "BLUE"
puts Vehicle.all_vehicles.inspect
puts vehicle1.name
puts vehicle1.color #It should give me an error cos no getter is defined yet
puts vehicle1.gears
puts vehicle1.wheels

# **************************************************
# INITIALIZE METHOD == Constructor
# just call it "initialize"
# Pass the arguments via Class.new(args) to pass it to initialize
# **************************************************
# Class Methods
#	def self.method_name	
#	end


# **************************************************
# INHERITANCE - Only one class can be a super class
# Overriding - 
# 

#----------------------
# Files & INPUT OUTPUT
# __FILE__
# File.expand_path(__FILE__)
# File.dirname(__FILE__)
#  File.join('','Users','Sam','cloudmon')
puts "The file name is : #{__FILE__}"
dir_path = File.dirname(__FILE__)
puts "The File Path is (short) : #{dir_path}"
dir_path = File.expand_path(__FILE__)
puts "The File Path is (long) : #{dir_path}"

```