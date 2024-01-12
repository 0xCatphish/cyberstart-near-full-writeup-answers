#
# Generate a valid xml file at /tmp/vulnerable-countries.xml.
# It should contain a list of country nodes attached to a root node
# that have name attributes, the third node should be Panama.
#

import xml.etree.ElementTree as ET


data = ET.Element('data')
names = ET.SubElement(data, 'name')
item1 = ET.SubElement(names, 'item')
item2 = ET.SubElement(names, 'item')
item3 = ET.SubElement(names, 'item')
item1.set('name','item1')
item2.set('name','item2')
item3.set('name','Panama')

'''

item1.set('name','item1')
item2.set('name','item2')
item1.text = 'item1abc'
item2.text = 'item2abc'
'''


# create a new XML file with the results
mydata = ET.tostring(data)
myfile = open(\"/tmp/vulnerable-countries.xml\", \"w\")
myfile.write(str(mydata))

#
# The aliens seem to be trying to make direct contact, so it's time
# for us to properly listen.
# Write a server that listens on ('localhost', 10000).
# The flag will be sent to that address
# record signal to /tmp/aliensignallog.txt
#
# If you get an address already in use error then try again in a few
# moments.
#
import socket
from time import sleep


def debugMsg(msg):
  # Use this function if you need any debug messages
  with open(\"/tmp/userdebug.log\", \"a\") as myfile:
    myfile.write(msg + \"\\\
\")

serversocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

serversocket.bind(('localhost', 10000))
serversocket.listen(10)

x=open(\"/tmp/aliensignallog.txt\", \"w+\")

while True:
    connection, address = serversocket.accept()
    data = connection.recv(8000).decode()
    if len(data) > 0:
        x.write(data)
        debugMsg(type(data))
    connection.close()
    break

for i in x:
  print(i)


  
connection.close()
print(x)

sleep(5)

#
# Connect to alien server ('localhost', 10000),
# Then send USER followed by aliensignal,
# Then send PASS followed by unlockserver,
# Next SEND followed by moonbase.
# Then send END and if all followed key will provided.
#
# Note: You must receive data back from the server after you send each message
#

import socket

clientsocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
clientsocket.connect(('127.0.0.1', 10000))

def send(string):
\tclientsocket.send(string.encode())
def re():
  data = clientsocket.recv(1024)
  print(str(data))
  
  
send(\"USER\")
re()
send(\"aliensignal\")
re()

send(\"PASS\")
re()
send(\"unlockserver\")
re()

send(\"SEND\")
re()
send(\"moonbase\")
re()

send(\"END\")
re()


#
# Alien Signal API listening on http://127.0.0.1:8082
# Use HTTP GET with x-api-key header to get signal
# We have narrowed down the key to be in the range of 5500 to 5600
# Note: The script can timeout if this occurs try narrowing
# down your search
#
import urllib.request


for i in range(5500,5600+1):
\theader = {'x-api-key': str(i)}
\tcontents = urllib.request.Request(\"http://127.0.0.1:8082\", headers=header)
\tresponse=urllib.request.urlopen(contents).read()
\tprint(response)
  



#
#  Robot Control Map
#
#  +-------------------+
# 9|                   |
# 8|S                  |
# 7|            x x x x|
# 6|            x      |
# 5|            x F    |
# 4|                   |
# 3|                   |
# 2|                   |
# 1|                   |
# 0|                   |
#  +-------------------+
#   0 1 2 3 4 5 6 7 8 9
#
#  S = Start position (0,8) F = Target destination (7,5),
#  x = Ravine, robot will be lost if hits these coords
#
# import robot module and use the robot.left(), robot.right(),
# robot.up() and robot.down() functions
#
import robot

for i in range(4):
\trobot.down()
  
for i in range(7):
  robot.right()
  
robot.up()

#
# Fix the below script to read from each agent file found in /tmp.
# Example agent profile would be /tmp/agent-1.txt
# The contents of each of the agent files makes up the flag
#


import os.path

count = 1
ans=[]

for i in range(100):
  fname = \"/tmp/agent-\" + str(count)+\".txt\"
  if os.path.isfile(fname):
    with open(fname, 'r') as content_file:
      content = content_file.read()
      print(content.rstrip())
      count += 1
      ans.append(content.rstrip())
      
print(\"\".join(ans))

#
# Ok, quick task for you agent - we've received a strange file from
# the first alien communication.
# It's at /tmp/alien-signal.txt, we need you to open and read the file.
#
#
f=open(\"/tmp/alien-signal.txt\")
for i in f:
  print(str(i))

# A regular expression or regex for short is a way of searching text
# for a pattern. Most people look at regex and get scared away, and
# it does look confusing at first. But it's also an incredibly useful
# tool to add to your programming arsenal.

# First you need to import the 're' library:
import re

# In it's most basic form, you can use regex to search for words in
# some text:
pattern = \"flag\"
text = \"The flag is: this is a fake flag: bajhdasdohaudsnasdaasd\"

if re.findall(pattern, text):
    print(\"Found match!\")

# Just telling you if something is there is not that useful though.
# Ideally we want to extract some information out of the text you are
# searching.

pattern = \"flag: (.*)\"
data = re.findall(pattern, text)
print(data[0])

# In this case, we managed to extract the flag from the text provided.
# Let's look more closely at how this happened.

# The key is the pattern: flag: (.*).
# First we're looking for any text that starts with Flag:
# The brackets surround the bit we want to extract. We know the flag
# we want to get comes after flag: so the brackets are after flag:.
# The . inside the brackets means match any character.
# The * means any number of times.
# So put it together and you're extracting any series of characters
# after the word flag: .

# What re.findall returns is an array. That's because it find all
# possible matches, so if there was more than one match, it would
# put them in the other positions in the array.
# For example data[1] for the second match, data[2] for the third
# match and so on...

# Regex is a whole language on it's own, but that is the basics.
# You can find out how to do more things with it at:
# https://regexone.com/

html = \"\"\"
<html>
<head>
    <title>Regex Demo</title>
</head>
<body>
    <div class='firstDiv'>Hello</div>
    <div class='secondDiv'>Hello</div>
</body>
</html>
\"\"\"

# CHALLENGE 1: Write a regex search that extracts all the classes from
#             the divs and saves them into an array.

pattern = \"<div class='(.*)'>Hello</div>\"
data = re.findall(pattern, html)

# CHALLENGE 2: Write a loop that goes through the array from
#              CHALLENGE 1 and prints the contents.
for i in data:
  print(i)

# As you know, computers only think in numbers. That means, when it
# comes to dealing with text, the computer has to have some way of
# converting numbers into letters. This is a form of encoding.

# The most common form of encoding is ASCII. In ASCII, a specific
# number maps to a letter. So for example, the number 65 is a capital
# A.

# Sometimes we need to be able to convert between the number a letter
# represents and the letter itself.

num = 65

# chr allows us to convert a decimal number to it's ASCII value.
char = chr(num)
# ord allows us to convert the ASCII character to it's decimal value.
dec = ord(char)

print(\"Character: \" + char + \", Decimal: \" + str(dec))

# CHALLENGE 1: Write a loop that prints the ASCII characters of all
#              the decimal values between the range 49 and 127
for i in range(49,128):
\tprint(chr(i))

# You aren't limited to using raw sockets to make network connections.
# Python can make HTTP requests quite easily.

# First you'll need to import the necessary urllib modules.
import urllib.request, urllib.error, urllib.parse

# Then you need to open the URL:
response = urllib.request.urlopen(\"http://127.0.0.1:8080\")

# Now you just need to read the contents of the response:
html = response.read()
print(html)

# CHALLENGE 1: Make a connection to: 127.0.0.1:8080/winning and print
#              the response.
response = urllib.request.urlopen(\"http://127.0.0.1:8080/winning\")
h=response.read()
print(h)

from time import sleep

# Sockets are a way of sending data over a network.
# There are two main types of sockets, TCP and UDP.
# Which to use depends on the application you are communicating with.

# You will need to import the socket library first.
import socket

# To make a connection to a TCP server:

# Create a socket. AF_INET means you're connecting to an IPv4 IP
#  Address.
# SOCK_STREAM means you are connecting over TCP and not UDP.
clientsocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# Tell the socket what IP Address and Port number to connect to.
clientsocket.connect(('127.0.0.1', 9987))
# Send some data over the socket.
clientsocket.send('hello'.encode())
# Receive some data back. The 1024 is the max number of bytes of data
# to accept.
data = clientsocket.recv(1024)
print(data)

# You should see \"You said: hello\" printed out. That's because our
# server is setup to respond to whatever you send it by adding
# You said: to the front of it and sending it back.

# To make a TCP Server:

# Create a socket.
serversocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# Bind the socket to listen to a port.
serversocket.bind((\"127.0.0.1\", 9985))
# Tell the socket to start listening.
# The 10 is the maximum number of connections.
serversocket.listen(10)

# Setup an infinite loop so the socket will keep listening for
# incoming connections.
while True:
    # If it gets a new connection, accept it and save the connection
    # and address.
    connection = serversocket.accept()
    # Read 1024 bytes of data from the connection.
    data = connection.recv(1024).decode()
    # Check the length of data. If the length is more than 0 then
    # that means something was sent, so print it out.
    if len(data) > 0:
        print(\"Received: \" + data)

    # Close the connection.
    connection.close()
    # We don't need to keep listening any more so break out of the
    # infinite loop
    break

# Close the socket.
serversocket.close()

sleep(0.05)

# CHALLENGE 1: Write a TCP Client that will connect to 127.0.0.1 on
#              port 9990.
#              Your client must send \"Knock, knock\" to the server.
#              Then get the response, and print it out.


# Working with files is a common task for a programming language
# Python makes it easy. Let's look at an example:

myfile = open(\"/tmp/newfile.txt\", \"w\")

# Open a file called newfile.txt in /tmp. If no file exists it will be
# created.
# The \"w\" is the mode, in this case \"w\" is for write. You could use \"r\"
# for read.
# There are various other modes we will cover them briefly later.

myfile.write(\"Here is my message.\
\")
myfile.write(\"Here is my second message.\")

# Write \"Here is my message\
\" to the file you opened. \
 is a
# newline character.
# You need to add a \
 every time you want to add a new line,
# otherwise everything will be on one line.

myfile.close()

# Since we opened the file, we need to close it when we're done with it.

# There are many different modes for opening a file in Python.
# Here are just a few useful ones:
# w - Allows you to write to a file only. If the file exists, it will
# be overwritten.
# r - Allows you to read the file only.
# r+ - Allows you to read and write to the file.
# w+ - Allows you to read and write to the file, but if the file
# already exists it will overwrite it.
# a - Allows you to append to the file
# (write to the end of an existing file)
# a+ - Allows you to append to the file, and read from the file.

myfile = open(\"/tmp/newfile.txt\", \"r\")
filecontents = myfile.read()
print(filecontents)
myfile.close()

# Here we are reading the file we created previously.

# You can also use the 'with' syntax. It's better.
# Here is an example of reading a file line by line instead of all
# at once.

with open(\"/tmp/newfile.txt\", \"r\") as myfile:
    for line in myfile:
        print(line)

# The major benefit of using 'with' is that it handles closing the
# file for you.
# We used a for loop to read the file line by line.

# CHALLENGE 1: Write a for loop that will create a file called
#              /tmp/cars.txt. There should be 50 lines of text in the
#              file. The first line should be \"There are 0 cars\"
#              and 1 car should be added every line. Until
#              the last line which should read \"There are 49 cars\"
myfile = open(\"/tmp/cars.txt\", \"w\")

for i in range(50):
\tmyfile.write(\"There are {} cars\
\".format(i))

# CHALLENGE 2: Open the file at /tmp/cars.txt and read the contents.
#              Print the contents to the screen.
myfile = open(\"/tmp/cars.txt\", \"r\")
filecontents = myfile.read()
print(filecontents)
myfile.close()
myfile.close()

# In programming, there are many situations where we have to repeat a
# task over and over until a condition is met. We use loops for this.

# The first type of loop we will look at, is a while loop.
# Like the name suggests, a while loop will keep repeating while a
# condition is true.

count = 0
while count < 10:
    print(\"The count is: \" + str(count))
    count = count + 1

# In our example, the condition is that count should always be
# less than 10.
# When count is more than 10, the loop will stop executing.
# Our example will print \"The count is 0\" then \"The count is 1\" and
# so on until \"The count is 9\"

hungryPeople = 8
pizza = 10

while hungryPeople > 0:
    pizza -= 1
    hungryPeople -= 1
    print(\"Someone ate a pizza.\")
print(\"There are no more hungry people\")

# In this second example we are using pizza -= 1 instead of
# pizza = pizza - 1.
# It's the same thing, it's just a short way of writing it.
# You can use the same shortcut for addition.
# For example pizza += 1 is the same as pizza = pizza + 1
# You will see when the loop exits that
# \"There are no more hungry people\" will print.
# That is because hungryPeople > 0 is no longer true so the
# code moves on to line 24.

# It's very important that you make sure the condition where a loop
# exits will always be met. If it doesn't get met, you will have an
# infinite loop. If you have an infinite loop, the program will never
# stop running unless you force it to quit.

# The other type of loop is a for loop. For loops are particularly
# useful for going through arrays. Let's look at an example:

myarray = [\"Strong\", \"Coffee\", \"Is\", \"The\", \"Best\"]

for x in myarray:
    print(x)

# This is the most basic form of a for loop. Here, each time the loop
# executes, x will be the next value in the array. The loop will exit
# on it's own when there are no more array values.

# So for example, the first time the loop runs, x will be \"Strong\",
# the second time x will be \"Coffee\" and so on...

# We can also do ranges in for loops.
# This will print 0 through to 49.
for x in range(0, 50):
    print(x)

# CHALLENGE 1: Create an empty array called numbers.
numbers=[]
# CHALLENGE 2: Write a while loop that will add 100 numbers to the
#              array, starting from the number 100 and incrementing by
#              2 each time. For example, start from 100, then the next
#              number added will be 102, then 104 and so on.
i=100
while len(numbers)<100:
  numbers.append(i)
  i=i+2
# CHALLENGE 3: Write a for loop that will look through your numbers
#              array and print out each value in the array.
for x in numbers:
    print(x)

# An array is just a collection of data.
# Let's look at an example:

myarray = [\"Hello\", \"World!\", 28, 22.5]
print(myarray) # This prints all the values in the array.
# This prints the first value in the array (We start counting from 0)
print(myarray[0])
print(myarray[1]) # This prints the second value in the array.
print(myarray[2]) # This prints the third value in the array.
print(myarray[3]) # This prints the fourth value in the array.

# We can see we can access positions in the array using square
# brackets [].You can also add to an array...

myarray.append(\"morestuff\")
print(myarray) # We can see \"morestuff\" got added to the end
# of the array.

# We can also change the values in a specific position of the array:

myarray[3] = \"changed\"
print(myarray) # We can see the fourth value in the array was
#changed to \"changed\".

# We can also remove from the array:

myarray.pop(3) # This removes the fourth item from the array
print(myarray)

# Similar to arrays are dicts or dictionaries.
# With arrays, you can only reference positions in the array using
# numbers.
# With a dict, you associate one value with another, a key-value pair.
# The colon ':' differentiates the key from the value.
# In the example below, name is a key. Bob is the value associated with name.

mydict = {\"name\": \"Bob\", \"age\": 23, \"height\": 180}

# In this example, name is the key and Bob is the value. If you
# want to find out the name you can just do:

print(mydict[\"name\"])

# To get the age:

print(mydict[\"age\"])


# CHALLENGE 1: Create an array with the following values in it in
#             order:
#             42, 1337, \"Coffee\", \"Anonymous\" then print the array.
a=[42, 1337, \"Coffee\", \"Anonymous\"]
print(a)
# CHALLENGE 2: Add two more values to the end of the array you created
#              in CHALLENGE 1: \"Blue\", \"Sky\" then print the array.
a.append(\"Blue\")
a.append(\"Sky\")
print(a)
# CHALLENGE 3: Print the fourth value in the array you created in
#              CHALLENGE 1.
print(a[3])
# CHALLENGE 4: Create a dict that includes the following values in
#              order: \"Subject\": \"Hacking\", \"Grade\": \"A\".
dict = {\"Subject\": \"Hacking\", \"Grade\": \"A\"}
# CHALLENGE 5: Print the grade value in the dictionary you created in
#              CHALLENGE 4.
print(dict[\"Grade\"])

# A function is just a bit of code that is taken out of the main
# program so it can be used over and over again.

# You've already been using functions. print() is a function.
# The print function takes in what you want to print as a parameter.
# Then it runs code that prints that to your screen.

# We're going to learn how to write our own functions.
# First we need to define a function with def:

def myfunction():
    print(\"This is my first function...\")

# On it's own, this program doesn't do anything. We have to call the
# function first.

myfunction()

# Now this program should print \"This is my first function...\"

def myfunction(name):
    print(\"Hello \" + name + \".\")

# We've changed the function to take a parameter this time.
# Let's see how that works...

myfunction(\"Bob\")

# Now this program will print \"Hello Bob.\"

def myfunction(name):
    formatted = \"Hello \" + name + \".\"
    return formatted

# Now we've changed the function again. This time it doesn't print,
# it saves a string into the variable formatted. Then it returns the
# variable.By returning something, that just means you can save
# the output into a variable,

result = myfunction(\"Bob\")

# Here we are returning \"Hello Bob.\" and saving it into the variable
# 'result'. Let's check:

print(result)

# We can also take in multiple parameters:

def myfunction(name, age):
    return \"I am \" + name + \" and I am \" + str(age) + \" years old.\"

# Now the function takes in a name and an age and returns the result.

result = myfunction(\"Bob\", 26)

print(result)

# CHALLENGE 1: Write a function that takes in two integers and
#              multiplies them together then returns the result.
def fu(x,y):
  return(x*y)
# CHALLENGE 2: Run the function from CHALLENGE 1, passing in the
#              integers 99 and 52 and print the result.
print(fu(99,52))
# CHALLENGE 3: Write a function that takes two integers and prints
#              the string \"I am 5 ft 6 inches tall\",
#              replacing the 5 and the 6 with the values passed into
#              the function.
def ff(x,y):
  return(\"I am {} ft {} inches tall\".format(x,y))
# CHALLENGE 4: Run the function from CHALLENGE 3, passing in 6 and 2
#              as the parameters.
print(ff(6,2))

# You can't really understand conditionals without understanding logic.
# Computers are binary, they think in 1s and 0s. Or put another way,
# True or False.
# If a 1 is a True, then a 0 is a False.

# Logic is Maths. So it's not surprising that calculating logic looks
# a lot like solving Maths problems.
# True AND False = True
# It looks very similar to:
# 1 + 3 = 4

# There are several logical operators which you should know:
# and - Logical AND. Both sides of the equation have to be True for it
# to be True. If not it's False.
# or - Logical OR. If either side of the equation is True then it's
# True. If not it's False.
# not - Logical NOT. Turns a True result into False and a False into
# a True.

print(True and True) # This prints 'True'
print(True and False) # This prints 'False'
print(False and True) # This prints 'False'
print(False and False) # This prints 'False'

# This prints 'False', because the not reverses it.
print(not(True and True))
# This prints 'True', because the not reverses it.
print(not(False and False))
# Did you notice how every time we open a bracket '(' we have to close it ')'?
# This is called bracket matching. If you leave open brackets that
# never get closed, you will start seeing errors.

# You can also see how this works in conditionals. Let's use our
# example from the previous challenge.

fun = 2
hacking = 6

if hacking > fun:
    print(\"more hacking\")

# hacking > fun is the key here. What does hacking > fun come out to?
print(hacking > fun) # This prints 'True'.

# So actually what is happening here is we're saying if something
# is true, then do...
# What happens if we negate it with not?

print(not(hacking > fun)) # This prints 'False'

# So if we used that in a conditional?

if not(hacking > fun):
    print(\"This isn't going to run...\")

# How about checking for two things in one if statement?

pizza = 4

if (hacking > fun) and (pizza > fun):
    print(\"more hacking and more pizza...\")

# Here, hacking > fun is True. pizza > fun is also True.
# True and True = True, so the if statement is True.

if (hacking < fun) or (pizza > fun):
    print(\"at least there's pizza.\")

# Here hacking < fun = False. pizza > fun is True.
# So it ends up being: False or True, which equals True.

# CHALLENGE 1: Print the result of true or true.
print(True or True)
# CHALLENGE 2: Print the result of true or false.
print(True or False)
# CHALLENGE 3: Print the result of false or true.
print(False or True)
# CHALLENGE 4: Print the result of false or false.
print(False or False)
# CHALLENGE 5: Use not to negate the result of true OR false and
# print the result.
print(not True or False)

# Programs aren't always static.
# Sometimes a program has to behave differently based on the
# information it gets. We can control the flow of a program
# using conditionals.

fun = 3
hacking = 5

if fun < hacking:
    print(\"Not enough fun!\")

# Here we have an if statement.
# It says: if the value of fun is less than the value of hacking...
#          then print \"Not enough fun!\"

# Did you notice that there is a tab before print in our example?
# This is called a code block.
# The ':' after hacking means the start of the code block.
# And the tab at the start of every line after that means that code
# belongs to that block.

if fun < hacking:
    print(\"This code belongs to the if statement...\")
    print(\"That's because there is a tab at the beginning.\")
print(\"This code does not belong to the if statement.\")
print(\"It will run no matter if the statement is true or not.\")

# Let's prove it...

hacking = 2
fun = 10

if fun < hacking:
    print(\"Fun is not less than hacking, so this line will never print.\")
print(\"But this line does not belong to the if statement.\")
print(\"So it will print no matter what.\")

# Here are the conditional operators you should know.
# You might recognise them from Maths class.

# < - Less than
# > - Greater than
# <= - Less than or equal to
# >= - Greater than or equal to
# == - Equals To

fun = 5
hacking = 5

if fun == hacking:
    print(\"The value of fun is equal to the value of hacking...\")

# That's not all! We can also chain if statements together.

if fun < hacking:
    print(\"The value of fun is less than the value of hacking...\")
elif fun > hacking:
    print(\"The value of hacking is greater than the value of fun...\")
else:
    print(\"The value of hacking and the value of fun are equal...\")

# In the above example we can see first we check if fun is less than
# hacking.
# If it is then it runs the code in the block that belongs to it.
# If it isn't, then we go on to the next if statement.
# The next statement checks if fun is greater than hacking.
# If it is then it runs the code in the block that belongs to it.
# If it isn't then it moves on to the last statement.
# The last statement is an 'else'. That just means if it didn't match
# any of the other
# if statements, then run the code in the block that belongs to it.
# In this case, if it isn't greater than or less than then it must be
# equal to, it's the only thing left.
# You can have multiple 'elif's also.

people = 5
capacity = 50

# CHALLENGE 1: Check if the number of people is lower than the capacity.
#              If it is, print \"success\"
#              If the number of people is higher than the capacity,
#              print \"too full\"
#              If the number of people is equal to the capacity,
#              print \"maximum people\"
def check():
  if people < capacity:
    print(\"success\")
  if people > capacity:
    print('too full')
  if people == capacity:
    print(\"maximum people\")
check()

# CHALLENGE 2: Set the value of the people variable to 500.
#              Then run the same check from CHALLENGE 1 again.
people = 500
check()

# CHALLENGE 3; Set the value of the people variable to 50.
#              Then run the same check from CHALLENGE 1 again.
people=50
check()



# You've already seen how we can use strings.

# We can concatenate strings (add them up) like so:

firstString = \"Hello, \"
secondString = \"World!\"

print(firstString + secondString)

# But we can go further. We can use a format string.
# Look at this example:

count = \"first\"

print(\"Hello for the %s time.\" % (count))

# The %s is a format string specifier for a String.
# It tells Python that there is a string that needs to replace the %s.
# The string that replaces the %s comes after the %.

# There are other format string specifiers.
# Some of the ones you might need are:
# %s is for strings.
# %d is for integers. Think d is for digits.
# %f is for floats.

integer = 10

print(\"There are %d crates.\" % (integer))

floatpoint = 2.22

print(\"There are %f humans who understand code.\" % (floatpoint))

# You can also use multiple format string specifiers at once.

print(\"String: %s, Num: %d, Float: %f.\" % (count, integer, floatpoint))

# CHALLENGE 1: Save the integer 5 in the variable ch1_1, and
#              the string \"robots\" in the variable ch1_2
#              Use a format string to print the following sentence:
#              There are 5 robots in the room

ch1_1=5
ch1_2=\"robots\"

print(\"There are {} {} in the room\".format(ch1_1,ch1_2))



# You can do maths in programming too...

addition = 5 + 5
print(addition) # This will print 10.

multiplication = 5 * 5
print(multiplication) # This will print 25.

division = 5 / 5
print(division) # This will print 1.

# You can also do maths without saving the result in a variable.

print(100 - 42)

# Here are some mathematical operators you should know about:
# Addition [+], as in 5 + 5 = 10
# Subtraction [-], as in 10 - 2 = 8
# Multiplication [*], as in 5 * 5 = 25
# Division [/], as in 10 / 2 = 5
# Power Of [**] as in 2 ** 3 = 8

# CHALLENGE 1: Multiply 80 by 512 and save it to a variable called ch1.
ch1=80*512
# CHALLENGE 2: Add 1024 to 768 and save it to a variable called ch2.
ch2=1024+768
# CHALLENGE 3: Do 40 minus 100 and save it to a variable called ch3.
ch3=40-100
# CHALLENGE 4: Divide 33 by 6 and save it to a variable called ch4.
ch4=33/6
# CHALLENGE 5: Do 2 to the power of 6 and save it to a variable called ch5.
ch5=2**6
# CHALLENGE 6: Save 0.33 to a variable called ch6_1, and save 5 to a
#              variable called ch6_2. Multiply ch6_1 with ch6_2 and save
#              the result to a variable called ch6.
ch6_1=0.33
ch6_2=5
ch6=ch6_1*ch6_2
# CHALLENGE 7: Print out the following variables in order:
#              ch1, ch2, ch3, ch4, ch5, ch6
print(ch1) 
print(ch2)
print(ch3)
print(ch4)
print(ch5)
print(ch6)

# Now that you know the different data types, let's look at how to
# convert between them.

# To convert an integer to a string:
anInt = 4
aString = str(anInt)

# To convert a string to an integer:
aString = \"20\"
anInt = int(aString)

# To convert a string to a float:
aString = \"3.333\"
aFloat = float(aString)

# Here's an example...
carInfo = \"Number of Doors: \"
carDoors = \"4\"

# Now we can print the number of car doors with:

print(carInfo + carDoors)

# You can see that this prints out:
# Number of Doors: 4

# This works because both carInfo and carDoors are strings.
# Notice the quotation marks.

carDoors = 4

# Now carDoors is not a string anymore, it's an integer. (No quotation
# marks)
# If you tried to do:
# print(carInfo + carDoors)
# Then you would see an error:
# TypeError: cannot concatenate 'str' and 'int' objects.
# Try it for yourself.

carDoors = 2

# CHALLENGE 1: Convert carDoors to a string using type conversion.
# Save it in a new variable: carDoorsString
carDoorsString=str(carDoors)
# CHALLENGE 2: Print out the number of doors in the car
# using print(carInfo + carDoorsString)
print(carInfo + carDoorsString)


# A variable is just a box with a label on it that can hold something.

# What you put in the box is up to you, but no matter what is inside,
# you can refer to whatever is there by the label on the box.

stuff = \"hello\"
print(stuff)

stuff = \"world!\"
print(stuff)

# See? The contents of the variable 'stuff' changed, but we can still
# refer to whatever is there by the label on the box.

# In programming, there are different 'types' of information.
# Learn the ones below.
# String - A string is text. Strings usually have to be wrapped
# in quotation marks.
# Integer - An integer is a whole number. Integers shouldn't have
# quotation marks.
# Float - A float is a number with a decimal point. Floats shouldn't
# have quotation marks.
# Boolean - A boolean value can either be True or False. Boolean
# values shouldn't have quotes.

# Python automatically changes the type of data a variable can hold
# depending on what you try to put into it.
# Sometimes it won't be able to do it automatically, and you'll have
# to convert it yourself.

# CHALLENGE 1: First create a variable called aString and assign it
aString=\"Testing\"
# the following text: Testing
# Remember the format to assign data to a variable
# is: variableName = \"SomeValue\"

# CHALLENGE 2: Next create a variable called anInt and assign it the
# following number: 899
# Remember, you don't need quotes for numbers!
anInt=899
# CHALLENGE 3: Next create a variable called aFloat and assign it the
# following number: 12.55
aFloat=12.55
# CHALLENGE 4: Next create a variable called aBool and assign it the
# value False.
aBool=False
# CHALLENGE 5: Print the variables out in order of the challenge
# number. i.e Challenge 1 first, then Challenge 2, and so on.

print(aString)
print(anInt)
print(aFloat)
print(aBool)



# This is a code comment
# Anything with a '#' before it is considered a comment and ignored.
# You can use these for writing notes about what your code is doing.
# This is so you can understand it more easily if you
# come back to it after some time.

# In Python, you can output text to the screen using the print function.
# The function is print(\"text\")

print(\"text\")

# You can also print numbers out. With numbers, you don't have to
# put them in quotation marks.

print(42)

# CHALLENGE 1: First print out the text: Hello, World)
print('Hello, World')
# CHALLENGE 2: Next print out the numbers: 1337
print('1337')