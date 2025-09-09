### Day-1
---
### Python 
- is an Object-Oriented Programming (OOP) language and General Purpose Programming language
- _OOP_ : is a way of writing code where it treat everything as an object that has its own data (properties) and actions (methods).
- _General Purpose Programming language_ : is a language designed to write software for a wide variety of applications, not limited to a specific domain.
- Python uses *interpreter*. (_not compiler_), means 'executes code line by line without converting it into machine code beforehand.'
- Python is _case-sentitive language_
```python
# <varibale_name> <assignemnt-operator> <value>
x = 100
# x= variable_name, = assignment-operator, 100 value
#type() to check the data type of a variable :
type(x)
```
---
#### Comparision Operators in Python :
```
>
<
>=
<=
== (Equals to)
!= (Not Equals to)
```
#### Arthmatic Operators in Python :
```
+
-
*
/
%  (Modulo Operator)
** (Power Operator)
// (Floor Division operator to Round the value). Example : _299//100 = 2_
```
---
#### Comments in Python :
- Single line comment with `#`
- Multi-line comment from `'''`multi-lines`'''`
#### Data-Structure in Python :
- data-structure defines how we are going to work with different data types.
- There are default 5 data-structures in python which `Strings`, `List`, `Tuple`, `Set` and `Dictionary`
- Two Types :
    - 1. *_Ordered Data Structure_* : Strings, List, Tuples
    - 2. *_Un-Ordered Data Structure_* : Set, Dictionary
### 1. *_Ordered Data Structure_* : Strings, List, Tuples
- Ordered means it will have `index` nubmber
---
#### Strings in Python :
- *Strings*- in single-quote 'hi'. Example : s = "viatris is poineer in healthcare." 
- length of a script with function _len(`<string name>`)_
- In string, _indexing_ starts with *zero*. 
- *Slicing in Python* -
    - s[0] => first charater of string
    - s[3] => 4th character of string
    - s[0:7] => "zero to seven" => print all characters from begininng to 7th
    - s[:7] => "util seven" => print all characters from begininng to 7th
    - s[6:] => "after sixth to end" => print all characters from 7th character to end
    - s[::n] => "slice with step-size n" => s[::2] will print every 2nd letter from begining. _Use case : to pick characters at regular intervals._
    - s[::-1] =>  To reverse the string

- *Functions in String* -
    - put "dot" after string-name and call the function. Examples :
        - s.capitalize => To make first-string in Upper-Case
        - s.upper() => To make all-string in Upper-Case
        - s.lower() => To make first-string in Lower-Case
        - *In-Built functions*. Example:  use `__add__` to Concatenate two strings
        - In jupyter notebook has dir(string name) which show all the menthods and inbuilt-functions
        - *Difference in `find()` and `index()`* -
            ```python
            text = "hello world"
            print(text.find("o"))     # 4
            print(text.find("z"))     # -1

            print(text.index("o"))    # 4
            print(text.index("z"))    # ValueError: substring not found
            ```
            - Use `find()` when you're not sure if the substring exists.
            - Use `index()` when the substring must exist (and you want an error if not).
    - Though Strings are *immutable*, but still we can change it by using some functions like _replcae()_ or concatenation with `+`, we can change it.
```python
s = "viatris is poineer in healthcare." 
#print string :
print(s)

#print length of a string :
len(s)

print(f"Length of my string {s} is  {len(s)}")
```
```python
## Slicing in Python :

alphabet = "abcdefghijklmnopqrstuvwxyz"

print(alphabet[0])      # print first character
print(alphabet[3])      # print 4th character
print(alphabet[0:7])    # print first character to 7th character
print(alphabet[3:7])    # print 4th character to 7th character
print(alphabet[:7])     # print first character to 7th character
print(alphabet[6:])     # print 7th character to last character
print(alphabet[3:20:2]) # print 4th character to 20th character with a step of 2 
print(alphabet[::2])    # print all characters with a step of 2
print(alphabet[::-1])   # reverse the string
```
```python
## Functions/Methods in String :
print(dir(alphabet)) # Get a list of all the attributes and methods of an object))
help(alphabet.find) # to know about any function
print(alphabet.capitalize()) # Capitalize first letter of string
print(alphabet.upper()) # Convert string to Uppercase
print(alphabet.lower()) # Convert string to Lowercase
print(alphabet.count("a")) # Count the number of occurrences of a substring in the string
print(alphabet.islower()) # Check if all characters in the string are lowercase
print(alphabet.isupper()) # Check if all characters in the string are uppercase
print(alphabet.replace("a", "A")) # Replace all occurrences of a substring with another substring
print(alphabet.find("f")) # Find the index of the first occurrence of a substring in the string
print(alphabet.index("f")) # Find the index of the first occurrence of a substring in  the string
print(alphabet.__add__("123")) # Concatenate two strings
```
```python
## Some Tricks related to String :

print ('hi' + 'hi')
print ('hi' * 5)

s = "viatris is poaneer in heakthcare." #'poineer' and 'heathcare' spelling is intentionally wrong
print(s)
### Two ways to correct it :

# 1. Using replace() function
s = s.replace("poaneer", "pioneer")
print (s)

# 2. Using slicing and concatenation
s = s[:25]+'l'+s[26:]
print (s)
```
#### List in Python
- List is a collection of object. 
- since it is an ordered data-structure, it will have indexing, starting from zero.  
- object could be non-simillar (hetrogenous) items also like number and string.
- wrappped in square-bracket [] 
- How to check ?
    - type([]) => list
    - type('') => str
- We can have list inside a list
- slicing of list works same as string.
- while `string` is immutable, `list` is *_mutable_*
- `list_name.append('object')` # to append a new object in list.
- `list_name.sort()` or `list_name.sort(reverse=True)` to sort a list.
- `list_name.pop()` # to remove last item from list.
- `list_name.insert(<index number>,<object>)` # to add an item at index-number in the list. 
    - _NOTE_ : `insert()` has `positional arguments`, means `mylist.insert(2,'bengalore')` is `correct` but `mylist.insert('bengalore',2)` is `incorrect`
```python
mylist = [1, 'A', 2, 'B', [3, 'C']]

print(f"mylist looks like => {mylist}")
print(f"mylist first charcater => {mylist[0]}")
print(f"print 1st index of list which is inside in mylist[4][1] => {mylist[4][1]}")

mylist.append('D') # append() function to add a new object at the end of the list
print(f"To append a new object 'D' in mylist => {mylist}")
```
#### Tuples in Python
- Tuples is a collection of object seperated by comma. By convention it will be wrappped in parantheses ().
    - Example : 
        ```
        my_tuples = 1,'abc'
        ```
- since it is an ordered data-structure, it will have indexing, starting from zero.  
- object could be non-simillar (hetrogenous) items, like number and string.
- We can have a tuple or list inside a tuple.
- Difference between tuples and list is tuples are `immutable` like `string`.
- How to check ?
    - type([]) => list
    - type('') => str
    - type(()) => tuple
- `my_tuple[0]` will show first item of an tuple. Note for refering item or set of item, we are using square bracket `[]`. 
- Though `tuples` are *immutable*, but still we can change it by using casting it in list by using `list(my_tuple)` and then again by converting it to tuple by `tuple(my_list)`
- tuples are immutable but can hold mutable objects
```python
t=(1,2,[3,4]); t[2][0]=99; print(t)
(1, 2, [99, 4]) ()
```
- Note : 
- (1) *Type of Copy in Python* :
    - `Shallow-Copy` means did not create a particular storage but only pointing to other variable.
    - `Deep-Copy` means it create a new storage space to store the value.
- (2) *Type of Operations*:
    - `Permanenet operation` means changes the original value.
    - `Adhoc/Temporary operation` means not change the original value. like my_strig.upper() will not change the my_string.
---
### 2. *_Un-Ordered Data Structure_* : Dictionary & Set
- Un-Ordered means it will `not` have `index` nubmber
---
#### Dictionary in Python
- collection of `key-value pairs`
- Empty dictionary `my_dict ={}`
- Example :
    ```python
    my_dic = {'ID':[1,2,3,4,5],
              'Name' : ['Sachin','Sehwag','Kohli','Dravid','Kumble']}
    ```
- To add more key-value pair in dictionary like `my_dic['<new-key>'] = <new values, it could be int, str, list, tuple, another dictionary>`. Note for refering key, we use square bracket `[]`. 
- To remove a specific key-value pair, use `pop('<key>')` method or `del(my_dic['<key>'])`.
- How to check ?
    - type([]) => list
    - type('') => str
    - type(()) => tuple
    - type({}) => dict
- Some Functions/Methods related to Dictionary :
    - `.items()` : to get all key-value pairs in dictionary
    - `.keys()`  : to get all keys in dictionary
    - `.values`  : to get all values in dictionary
    - `.clear()` : to clear all key-value pairs in dictionary
    - `.get('<key-name>')` : to get value of a key in dictionary
    - `.copy()`  : 
    - `.update()`: 
    - `.pop('<key')`:
    - `.popitem()` :
    - `dir(my_dict)` : show all function/methods of a dictionary
```python
my_dict = {'ID':[1,2,3,4,5],
              'Name' : ['Sachin','Sehwag','Kohli','Dravid','Kumble']}
print(f"my_dic looks like => {my_dict}")

my_dict['Country'] = ['India']*5 # to add a new key-value pair in dictionary
print(f"Afer adding a new key-value pair 'Country', my_dict looks like => {my_dict}")

del(my_dict['Name']) # to remove a key-value pair from dictionary
```
```python
print(my_dict.items()) # to get all key-value pairs in dictionary
print(my_dict.keys()) # to get all keys in dictionary
print(my_dict.values()) # to get all values in dictionary
print(my_dict.get('Country')) # to get value of a key in dictionary
print(my_dict.pop('ID')) # to remove a key-value pair from dictionary
print(my_dict.clear()) # to clear all key-value pairs in dictionary
```
#### Set in Python
- Set is a collection of `unique values which are also sorted in numbers`
- empty set with `set()`.
- Sets are mainly used for Comparing items and createing unique items
- Example :
    - `my_set = {1,1,1,2,2,2,3,3,3,5,4,3,4, 'xyz', 'abc'}`
    - it will be stored as => `{1, 2, 3, 4, 5, 'xyz', 'abc'}`
- *Note* : empty set with () but actaul set with {}
- Functions :
    -  Union as `set1|set2`
    - Intersect of `set1&set2`
    - Is a subset => `set1.issubset(set2)`
    - difference in sets => `set1.difference(set2)`
```python
set1 = {1,1,1,2,2,2,3,3,3,5,4,3,4, 'xyz', 'abc'}
print(f"set1 is  : {set1}")

set2 = {4,5,5,6,6,6,7,7, 'xyz', 'xyz', 'pqr'}
print(f"set2 is  : {set2}")

print(f"union of set1 and set2 is  : {set1|set2}")
print(f"intersect of set1 and set2 are  : {set1&set2}")
print(f"difference of set1 and set2 are  : {set1.difference(set2)}")
```
### Iterations in Python

#### (1) `for` loop:
- To iterate through each item.
- it has one : and it follow indentation `\tab`
- `range(n)` or `range(start,stop,step)` will print all the numbers `from 0 to n-1`. to use this in for-loop, use like `for i in rang(10):`
- Example :
```
for i in s:
    print(i)
```
- *Unpacking the tuple* by `for i,j in my_tuple`
```python
for i in s:
    print(i, end="--")  # Default end is '\n' (new line) but we can change it to anything we want.


print("------------------")
my_tuple = ((1,'Delhi'), (2,'Mumbai'), (3,'Bangalore'))
print(f"my_tuple is : {my_tuple}")
print("------------------")
## Prinitng each element of tuple :
for i in my_tuple:
    print(i)
print("------------------")
## Unpacking the tuple elements into individual variables :
for i,j in my_tuple:
    print(f"i = {i} and j = {j}")
```
```python
# Challange : Print key and 3rd value of each key in dictionary :
my_dict = {'ID':[1,2,3,4,5],
           'Name' : ['Sachin','Sehwag','Kohli','Dravid','Kumble'],
           'city' : ['Mumbai','Delhi','Bangalore','Chennai','Kolkata']}

#Solution :
print("--------All keys----------")
for k in my_dict:
    print(k)  #Only key will print
print("-------All items-----------")
for i in my_dict.items():
    print(i)  #Print each item with key and value
print("------All itesms with all keys with 3rd Value------------")
for k,v in my_dict.items():
    print(k ,v[2]) #Print each item with key and 3rd value of each key
print("------------------")
```
#### Conditions in Python:
- `if`, `elif`, `else`
- it has one : and it follow indentation `\tab`
- Example :
```
if (<condition1>):
    statement1
elif (<condition2>):
    statement2
elif (<condition3>):
    statement3
else:
    statement4
```
- `&` as AND
- `||` as OR

- To take input from user, use `input("put your message here")`. 
- Note : input() gives string, so needs to convert into integer using `int(<input-variable-name>)` otherwise it will give `TypeError`

- Three ways to print with variable and message :
    - (1) with `commas`   =>  `print("First variable is ", var1, " and seconds variable is ", var2)`
    - (2) with `.fomart()` => `print("First variable is {} and seconds variable is {}".foramt(var1,var2))`
    - (3) with `f-string`  => `print(f"First variable is {var1} and seconds variable is {var2}")`
```python
## if-elif-else condition in Python :
marks = int(input("Enter your marks : "))

if(marks>85):
    print("A+ Grade")
elif(marks>75):
    print("A Grade")
elif(marks>65):
    print("B Grade")
elif(marks>50):
    print("C Grade")
else:
    print("Fail")
```
```python
# Challenge : ask the user for an input. if it is positive number, check if it is divisible by two or five or both and print accordingly 

user_num = int(input("Enter your number :"))
if (user_num > 0):
    if(user_num % 2 == 0 and user_num % 5 ==0):
        print(f"{user_num} is divisible by both 2 & 5.")
    elif(user_num % 5 == 0):
        print(f"{user_num} is divisible by 5.")
    elif(user_num % 2 == 0):
        print(f"{user_num} is divisible by 2.")
    else:
        print(f"{user_num} is neither divisible by 2 nor 5")
else:
    print(f"{user_num} is a negative number or 0")
```
#### `keywords` in Python
- `pass` : means `do-nothing`
- `break` : the moment condition is true, it will break the logic. (logic moves to end, `breaks out of the loop`)
- `continue` : the moment condition is true, it will not move to next statement but next in loop will start (logic moves to top, `puts the cursor backinto loop`)

#### Short-hand Operator -
- i = i + 1 => short-hand operator will be `i++` or `i+=1`
```python
for i in range(10):
    i+=1
    if (i == 5):
        pass      # print all from 1 to 10
        #break     # print till 4
        #continue  # print all except 5.
    print(f"number is :{i}")
```
#### (2) `while` loop:
- To iterate until condition is True.
- it has one : and it follow indentation `\tab`
- Example :
```
while (<condition>):
    <logic>
    <condition>
```
- NOTE : Be careful about infinite-loop.

- `while True:` is used to run the loop till something `break` the loop.
```python
# while-loop example :
num = 1
while (num < 11):
    print(f"number is {num}")
    num += 1
```
```python
## "while True:" Example :
num = 5
while True:
    guess = int(input("Guess a number between 1 to 5:"))
    if (guess == num):
        print("You guessed right!")
        break
    else:
        print("wrong. Pleae guess again.")
```
```python
#Challenge : create an empty list, in a range of 10 num, square the even number and store it in the list.

even_square =[]
for i in range(10):
    if (i % 2 == 0):
        even_square.append(i**2)
    else:
        pass
print(f"my even_square list is => {even_square}")
```
#### *_List Comprehension_* 
- A concise way to create lists using a single line of code with a loop and optional condition.
- check internet for more deatils like `Lambda Expressions` or `Dictionary Comprehension`
- Example :
```
[<output> <for-loop> <condition>]
```
```python
# List Comprehension
[i*i for i in range(10) if i%2==0]
```
---
