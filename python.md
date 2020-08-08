# One, concise overview

## 1. Coding

* If there are no special circumstances, the file will use UTF-8 encoding
* If there are no special circumstances, the file header must be added with the `#-*-coding:utf-8-*-` logo

## 2. Code format

### 2.1, indentation

* Use 4 spaces for indentation

### 2.2, line width

Each line of code should not exceed 80 characters as far as possible (in special cases it can slightly exceed 80, but the longest cannot exceed 120)

reason:

* This is helpful when viewing side-by-side diffs
* Convenient to view the code under the console
* Too long may be defective in design

### 2.3, quotation marks

Simply put, natural language uses double quotation marks, and machine labels use single quotation marks. Therefore, most of the __ code __ should use __ single quotation marks.

 * ***Natural language*** **Use double quotes** `"..."` 
 For example, error messages; in many cases it is still unicode, use `u"Hello World"`
 * ***Machine ID*** **Use single quotes** `'...'`
 For example, the key in dict
 * ***Regular expression*** **Use native double quotes ** `r"..."`
 * ***Docstring*** **Use three double quotes ** `"""......"""`

### 2.4, blank line

* There are two blank lines between module-level functions and class definitions;
* A blank line between class member functions;

```python
class A:

 def __init__(self):
 pass

 def hello(self):
 pass


def main():
 pass 
```

* You can use multiple blank lines to separate multiple sets of related functions
* Blank lines can be used to separate logically related codes in functions


## 3. Import statement

* The import statement should be written in separate lines

```python
# Correct writing
import os
import sys

# Not recommended
import sys,os

# Correct writing
from subprocess import Popen, PIPE
```
* The import statement should use __absolute__ import

```python
# Correct writing
from foo.bar import Bar

# Not recommended
from ..bar import Bar
```

* The import statement should be placed at the head of the file, after the module description and docstring, and before the global variables;
* Import statements should be arranged in order, separated by a blank line between each group

```python
import os
import sys

import msgpack
import zmq

import foo
```

* When importing class definitions of other modules, you can use relative import

```python
from myclass import MyClass
```

* If a naming conflict occurs, you can use the namespace

```python
import bar
import foo.bar

bar.Bar()
foo.bar.Bar()
```

## 4、Space

* Leave a space on each side of the binary operator `[=,-,+=,==,>,in,is not, and]`:

```python
# Correct writing
i = i + 1
submitted += 1
x = x * 2-1
hypot2 = x * x + y * y
c = (a + b) * (a-b)

# Not recommended
i=i+1
submitted +=1
x = x*2-1
hypot2 = x*x + y*y
c = (a+b) * (ab)
```

* In the parameter list of the function, there must be a space after `,`

```python
# Correct writing
def complex(real, imag):
 pass

# Not recommended
def complex(real,imag):
 pass
```

* In the parameter list of the function, do not add spaces on both sides of the default equal sign

```python
# Correct writing
def complex(real, imag=0.0):
 pass

# Not recommended
def complex(real, imag = 0.0):
 pass
```

* After the left parenthesis, do not add extra spaces before the right parenthesis

```python
# Correct writing
spam(ham[1], {eggs: 2})

# Not recommended
spam( ham[1], {eggs: 2})
```

* No extra spaces before the opening parenthesis of the dictionary object

```python
# Correct writing
dict['key'] = list[index]

# Not recommended
dict ['key'] = list [index]
```

* Do not use extra spaces to align assignment statements

```python
# Correct writing
x = 1
y = 2
long_variable = 3

# Not recommended
x = 1
y = 2
long_variable = 3
```

## 5. Line break

Python supports line breaks in parentheses. There are two situations at this time.

1) The second line is indented to the beginning of the bracket

```python
foo = long_function_name(var_one, var_two,
 var_three, var_four)
```

2) The second line is indented 4 spaces, which is suitable for the situation where the opening parenthesis just wraps

```python
def long_function_name(
 var_one, var_two, var_three,
 var_four):
 print(var_one)
```

Use the backslash `\` to wrap the line, the binary operator `+` `.`, etc. should appear at the end of the line; long strings can also be wrapped in this way

```python
session.query(MyTable).\
 filter_by(id=1).\
 one()

print'Hello,'\
 '%s %s!' %\
 ('Harry','Potter')
```

Compound statements are prohibited, that is, multiple statements in one line:

```python
# Correct writing
do_first()
do_second()
do_third()

# Not recommended
do_first();do_second();do_third();
```

`if/for/while` must wrap:

```python
# Correct writing
if foo =='blah':
 do_blah_thing()

# Not recommended
if foo =='blah': do_blash_thing()
```

## 6, docstring
The two most basic points in the docstring specification:

1. All public modules, functions, classes, and methods should be written in docstrings. Private methods are not necessarily required, but a block comment should be provided after def.
2. The ending """ of the docstring should be on its own line, unless the docstring has only one line.

```python
"""Return a foobar
Optional plotz says to frobnicate the bizbaz first.
"""

"""Oneline docstring"""
```
