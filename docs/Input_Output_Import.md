## Input :
	input('prompt like Enter a Number, but  it will be a string, hence conert to number using int()')
	
 ### Q1 : How to take Integer as input ?
 **Answer:**
 ```python
my_int = int(input('Enter the Number'))
print("Your Number is :", my_int)
```

 ### Q2 : How to take List elements as input ?
 **Answer:**  3 ways -
 
 (1) Take list elements one by one, and append them to the list.
 ```python
my_list = []
n = int(input("How many elements? "))
for i in range(n):
  element = input(f"Enter element {i+1}: ")
  my_list.append(element)
 print("Your list:", my_list)`
```
(2)  Take all elements in one line and split them
```python
my_list = input("Enter elements separated by space: ").split()
print("Your list:", my_list)
```
 
(3) Using map to and list() function
```python
my_list = list(map(int, input("Enter numbers separated by space: ").split()))
print("Your list:", my_list)
```

---


## Output : 
```python 
print(object(s), sep=’ ‘ ,end = ‘\n’, file = file, flush = flush)
```

| **Parameter** | **Description**                                                       |
| ------------- | --------------------------------------------------------------------- |
| `object(s)`   | The values to print (can be one or multiple).                         |
| `sep`         | String inserted between the objects (default is a space `' '`).       |
| `end`         | String appended after the last object (default is newline `'\n'`).    |
| `file`        | Where to send the output (default is `sys.stdout`, e.g., the screen). |
| `flush`       | If `True`, forcibly flush the output buffer immediately.              |


```python
print("A", "B", "C", sep="-", end=" END\n")
A-B-C END
```
---

## Import :

(1) Syntax to import math and then use pi :
```python
import math as m
print(m.pi)
```
(2) Import only pi from math
```python
from math import pi
print(pi)
```
---
