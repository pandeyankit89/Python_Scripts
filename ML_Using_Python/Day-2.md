#### Day-2
---
#### Types of Copies in Python :
- There are 2 types of Copies :
- (1) *_Shalow-Copy_* :
    - Python `don't allocate any storage` but just create a pointer. Example -
```python
list2 = list1
```

- (2) *_Deep-Copy_* :
    - Python `allocates seperate storage` 
```python
list2 = list1[:]
# or
list2 = list1.copy()
```
---
#### Functions in Python:
- Function is created when we want to use a repeated logic.
- To create a function in Python, we use `def`. Expample -
```python
def functionName(arguments):
    pass
```
- function with no argument - `def myfun()`
- function with `default value` - `def myfun(x=10)`, so if we call the function myfunc() with no argument, it will use x = 10.
- `return` can be used only inside a function. it will return the value when function gets a call.
- for `Docstrings`, which gives some information about function, `use 3-single-quotes '''` to give this information. Example -
```python
def myfunction_with_docstring():
    '''This function is about ....'''
    pass
myfunction_with_docstring()
```
```python
# Square function:
def square(num):
    '''This function will print the square on a number.'''
    print(f"square function is printing : {num**2}")

x= square(3)
print(f"value of x is : {x} because print does not return any value. Hence use retun inside function.")

def cube(num):
    '''This function will print as well as return the cube on a number.'''
    print(f"cube function is printing : {num**3}")
    return num**3

x= cube(3)
print(f"value of x is : {x} because this time function returns a value.")

#square function is printing : 9
#value of x is : None because print does not return any value. Hence use retun inside function.
#cube function is printing : 27
#value of x is : 27 because this time function returns a value
```
---
#### In-built Functions :
- `__len__`-> return this length of a list
```python
list1.__len()__
#or
list1.len()
```

- `__dir__` -> return the list of inbuilt functions.
```python
list1.__dir__
#or
dir(list1)
```
```python# Challenge : Create a function which takes 2 arguments and return the max :
def maximum(x,y):
    '''This function will return the max among two integer arguments'''
    if(x > y):
        return x
    else:
        return y

print(f"max number is : {maximum(2,3)}")
```
#### Useful important functions in Python:
-  Functional Program Constructs ?
- `iterable object` means collection which we can traverse for each object. like a `list`
- `list(map(<function_name>,<iterable_object>))` accepts 2 arguments and run the function for each value of iterable object. inside `list(map..)` to make output in a list.
- in last `[None..]` is coming ??
- `list(filter(<function-name>,<iterable_object>))`
    - filter function return the value of `iterable-object` only for those items where function is retruning `True`. 
    - _Note:_ function must return `True/False`. 
    - inside `list(filter..)` to make output in a list.

- `lambda` function is a `anonymous function` which we `want to use once`.
    - used inside `map` function
    - Example -
```python
list1 = [1,4,7]
list2 = [2,3,6]
result = list(map(lambda x,y: x if x<y else y, list1, list2))
print(result)   # [1,3,6]
```
- `reduce` function `repeatedly combines elements of an iterable-object into one value` using a given function.
    - `from functools import reduce` -> first import `reduce` from `functools` 
    - It takes:
        - A function (with 2 arguments),
        - An iterable (like list/tuple),
        - (Optional) an initial value. (_Example 3_)
    - It then reduces the iterable to a single value by applying the function again and again.
```python
from functools import reduce
list2 = [1,2]
result = reduce(lambda x,y: x if x<y else y, list2)
print(result)   # 1
```

```text
+-----------+--------------------------------+----------------+
| Function  | Purpose                        | Output Example |
+-----------+--------------------------------+----------------+
| map       | Apply function to all elements | [2,4,6,8,10]   |
| filter    | Keep elements that match cond. | [2,4]          |
| reduce    | Combine all into one value     | 15             |
+-----------+--------------------------------+----------------+

```
---
```python
# map :
list1 = [1,2,3,4,]
list(map(square,list1))

#square function is printing : 1
#square function is printing : 4
#square function is printing : 9
#square function is printing : 16
```
```python
## filter -
def issquare(x):
    return x%2==0

list(filter(issquare,list1))

#[2, 4]
```
```python
## lambda -
list1 = [1,4,7]
list2 = [2,3,6]
result = list(map(lambda x,y: x if x<y else y, list1, list2))
print(result)

#[1, 3, 6]
```
```python
## reduce -
#Example 1:
from functools import reduce
list2 = [4,2,4,1]
result = reduce(lambda x,y: x if x<y else y, list2)
print(result)

#Example 2:
from functools import reduce
nums = [1, 2, 3, 4]
result = reduce(lambda x, y: x + y, nums)
print(result)   # 10

#Example 3 (with Initial-Value):
nums = [1, 2, 3]
result = reduce(lambda x, y: x + y, nums, 10)
print(result)   # 16
```
---
- *_Explore more on below functools_* -
    - `lambda`
    - `map`
    - `reduce`
    - `zip`
    - `generator(yield)`
    - `iterator`
    - `decorator`
- check topics
    - list comprehensions
        - when to use `list-comprehensions` and when to use `map`
    - orbitrary args
    - prime numbers
    - recursive function
    - File handling
    - Exception handling with `try:-except:-finaly:`
        ```python
            except ZeroDivisionError as zd:
                print(zd.args)
            except ValueError as ve:
                print(ve.args)
        ```
    - Object-Oriented-Programming (OOP) concepts
---
#### *_Scope of Varibales_* :
- scope is decided by *_LEGB scope rule (Local, Enclosing, Global, Built-in)_*
```text
+-----------+-----------------------------------------------+----------------------------------+
| Scope     | Meaning                                       | Example in Python                |
+-----------+-----------------------------------------------+----------------------------------+
| Local     | Names inside current function                 | variable in def foo()            |
| Enclosing | Names in outer function (nested functions)    | variable in def outer()->inner() |
| Global    | Names defined at top-level of a module/script | global_var outside any def       |
| Built-in  | Names pre-defined by Python                   | len(), sum(), range()            |
+-----------+-----------------------------------------------+----------------------------------+
```
```python
# scope
x = 20
y = 30
def scope_var():
    global x
    print(f"value of x & y within the function, when x is declared as global while y is not. values are :  x = {x} and y = {y}")
    x =15
    print(f"value of x & y within the function are :  x = {x} and y = {y}")

scope_var()
print(f"value of x & y outside the function are : x = {x} and y = {y}")

#value of x & y within the function, when x is declared as global while y is not. values are :  x = 20 and y = 30
#value of x & y within the function are :  x = 15 and y = 30
#value of x & y outside the function are : x = 15 and y = 30
```
---
#### Exceptions in Python :

```text
+-----------------------+--------------------------------------------+-----------------------------+
| Exception Type        | When it Occurs                             | Example                     |
+-----------------------+--------------------------------------------+-----------------------------+
| SyntaxError           | Wrong Python syntax                        | if True print("hi")         |
| IndentationError      | Wrong indentation                          |   print("hi")               |
| NameError             | Variable not defined                       | print(x)                    |
| TypeError             | Wrong type of operation                    | "2" + 2                     |
| ValueError            | Right type, wrong value                    | int("abc")                  |
| IndexError            | Index out of range                         | [1,2][5]                    |
| KeyError              | Missing dictionary key                     | {"a":1}["b"]                |
| AttributeError        | Invalid attribute access                   | (3).append(4)               |
| ZeroDivisionError     | Division by zero                           | 5/0                         |
| ImportError           | Import module not found                    | import non_existing_module  |
| ModuleNotFoundError   | Specific import error for modules          | import xyz123               |
| FileNotFoundError     | File operation on missing file             | open("abc.txt")             |
| IOError / OSError     | Input/output related errors                | open("/restricted/path")    |
| RuntimeError          | Generic runtime error                      | raise RuntimeError("oops")  |
| MemoryError           | Out of memory                              | big_list * 100000000        |
| StopIteration         | End of iteration in loops/generators       | next(iter([]))              |
| OverflowError         | Number too large (math operations)         | math.exp(1000)              |
| AssertionError        | assert statement fails                     | assert 2==3                 |
+-----------------------+--------------------------------------------+-----------------------------+

```
---
```python
#try-except:

num=15
try:
    inp = int(input("enter a number : "))
except ValueError as ve:
    print(ve.args)
try:
    v = num/inp
    print(v)
except ZeroDivisionError as zd:
    print(zd.args)

#('division by zero',)
```
### Packages & modules:

- Python is a general-purpose programiming. It has many packages and modules for wide-range of  areas. This is the reason for its popularity.
- Modules for different areas of work are -
    - _Networking/Socket_ --> socket, raspberry, ordinov, IoT
    - _Data Science_ --> Numpy, Pandas, Scipy,sklearn, Tensorflow(keras), Pytorch
    - _Testing_ --> Unit test, Selenium, Debugger, tinker
    - _Parallel processing_ --> multi threading, pooling
    - _Robotics_ 
    - _Automation_
    - _Web-Application development_ --> Django (intagram), Flask

- *Question : What is an Virtual Environment ?*
    - It a project specific virtual collection of packages and modules.
    - `conda env list` --> it will list all conda environments
    - `conda create -n <env-name> python==3.10` --> To create a new environemnt with python 3.10. then `conda activate <env-name>`
    - in VS-Code --> `clt + Shif + P` for `Show and Run Commands` -> select `Python : Create Environment` -> then `activate vnev` -> to comeout of this environment, run `deactivate`
- *_Module_* is a single Python file (.py) that contains code (functions, classes, variables)
    - call in script as `import <module-name>`, after that i can use functions which are mentioned inside module.
    - to check the functions of a module, we can use command `dir(<module-name>)`
    - we can give it an alias name with `as` like `import pandas as pd`
- *_Package_* is a collection of modules grouped in a folder with an `__init__.py` file. Example : `functools`
    - call in script as `from <package-name>`
    ```python
        import reduce from functools
    ```
    - some modules are inbuilt in python, hence no need to call their package-name. like -
    ```python
        import math
    ```
- Order is  `(from) Package -> (import) Module -> (.) Function`

- check more on :
    - `__name__` : means name of the file, If this module is called from back to directory, do this, if called from other place do-this
    - `__main__` :
    ```python
    if __name__ == __main__:
 
    ```
- `library` = `package`
---
### NumPy (Numerical Python) module:

```python
list1 = [1,2,3,4,5,6]
list2 = [4,5,6,7,8,9]

list1 + list2 #will concatenate, instead of adding each them as matrix (based on rows and columns numbers)
#[1,2,3,4,5,6,4,5,6,7,8,9]
```
- NumPy module solution to above problem. It provides `N-dimentional arrays`
- Numpy `Array` is also an `Ordered Data-Structure`
- `<array-name>.shape` : to get the size of array. Output is a `tuple`
- `<array-name>.reshape (row, col)` : convert 1-D array to N-D array 

```python
#pip3 install numpy
import numpy as np

np.array(list1) + np.array(list2)
#array([5,7,9])
```

- Methods to access data of an array -
- `arr[row_index , column_index]`
- If 2D → first part = rows, second part = columns
- _Notes_: 
    - `:` → "take everything"
    - `::` → "take everything _with step_"
    - `arr[::, ::]` → same as `arr[:, :]` (all rows & all cols).
    - `arr[::2, :]` → every 2nd row, all columns.
    - `arr[:, ::2]` → every 2nd column, all rows.
    - `arr[1:, 1:]` → from row 1 onward & col 1 onward.
```python
list1 = [1,2,3,4,5,6]
list2 = [4,5,6,7,8,9]

print (list1 + list2) #will concatenate, instead of adding each them as matrix (based on rows and columns numbers)
#[1, 2, 3, 4, 5, 6, 4, 5, 6, 7, 8, 9]

#pip3 install numpy
import numpy as np
array1 = np.array(list1) + np.array(list2)
print(array1)
#[ 5  7  9 11 13 15]


#shape of an array
print(f"shape of this array is : {array1.shape}")
#shape of this array is : (6,)

#reshape an array
array2 = array1.reshape(2,3)
print(array2)
#[[ 5  7  9]
# [11 13 15]]

print(f"shape of this array is : {array1.reshape(2,3).shape}")
#shape of this array is : (2, 3)

array2[::,::] #All rows and All columns

array2[:,:] #All rows and All columns

array2[:,2] # All rows, 2nd column

array2[1,:] # First-Index row, All column

array2[1,[1,2]] # First-Index row, first and second indexed columns

array3 = np.array([10,20,50,23,12,19,11,88,30,100,55,82]).reshape(4,3)
print(array3)

#[[ 10  20  50]
# [ 23  12  19]
# [ 11  88  30]
# [100  55  82]]

array3[::2] # step-seize 2, means all row from begining(0) and + 2, means 0 and 2nd

array3[1::2] # start-point is 1st row, step-seize 2, means all row from begining(1) and + 2, means 1 and 3rd(index)

array3[0::3,0::2]
#or
array3[[0,3],::2]
```
#### NumPy Functions

- `<array>.cumsum()`
- `<array>.arrange(n)`
- `<array>.max()`
- `<array>.argmax()`
- `<array>.min()`
- `<array>.mean()`
- `<array>.std()`
- `<array>.flatten()`

- Explore more on -
    - np.ones(10)
    - np.zeros(10)
---
#### `random` module :
- `import numpy.random as r`
- `r.rand(2,5)` => Generates random floats in range [0,1) (uniform distribution).
- `r.randint(1,5,2)` => Generates random integers between given low and high. 3rd cahracher (here 2) means number of outputs in return.
- `r.randn(2,12)` => Generates random floats from a standard normal distribution (mean=0, std=1).

```python
import numpy.random as r

print(r.randint(2,15,2))  #[ 2 11]
```
```python
#pip install seaborn
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')

sns.distplot(r.randn(12,24))
```
---

```

