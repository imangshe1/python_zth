![](/images/p14-3.png)
# Function
The smallest granularity of reusable code
```python
# syntax
def functionname( args ):
    "function_docstring"
    function_suite
    return [expression]
```
```python
# example
def foo(x, y, z):
    return x + y + z
```
# Module
A collection of functions and source code in a single ***.py*** file.  
[modules](https://docs.python.org/3/tutorial/modules.html#modules)  
 ### fibo.py
![](/images/p14-1.png)
## Reusing a module
A module can be either imported by another module or run directly by the interactive interpreter.
```python
# greet.py module

def print_greeting():
    print('have a nice day')

print_greeting()
```
#### Importing a module
```python
# my_module.py module

import greet

greet.print_greeting()
```

> Executing ***my_moudle.py*** will print 'have a nice day' twice. **Why?**

#### Running a module from interactive interpreter
```cmd
$ python greet.py
have a nice day
```
#### Distinguish between import and running as a script
module's [\_\_name\_\_ ](https://docs.python.org/3/library/__main__.html) global variable is set to ***"\_\_main\_\_"*** if running as script, otherwise it is the module name.
```python
# greet.py module - fixed!

def print_greeting():
    print('have a nice day')

if __name__=="__main__":
    print_greeting()
```
## Recommended scriptable module layout

 - add ***main()*** function which runs script logic
 - ***if \_\_name\_\_ == \_\_main\_\_*** should call ***main()***  
 
Introducing the ***main()*** function allows the module to be run as a script also within other program (thats import the module and invokes ***main()*** ). In addition, it tends to remove clutter from the if ***\_\_name\_\_ == \_\_main\_\_*** block

```python
# main.py module

def some_func(args):
    ...

def parse_args():
    ...

def main():
    args = parse_args()
    some_func(args)

if __name__ == "__main__":
    main()
```
## The import statement
[import](https://docs.python.org/3/reference/simple_stmts.html#import)
#### module import
```python
import fibo

fibo.fib(5)
fibo.fib2(5)
```
#### specific module symbols import
```python
from fibo import fib, fib2

fib(5)
fib2(5)
```
#### specific module symbols import with aliasing
```python
from fibo import fib as fibonacci

fibonacci(5)
```
#### all module symbols import (except those beginning with `_`)

> **Bad practice** (use only in interactive sessions!): 
> - introduces an unknown set of names into the interpreter, possibly hiding some things you have already defined.
> - causes poorly readable code.

```python
from fibo import *

fib(5)
fib2(5)
```
### Module search path
When a module named  `spam`  is imported, the interpreter first searches for a built-in module with that name. If not found, it then searches for a file named  `spam.py`  in a list of directories given by the variable  [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path").  [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path")  is initialized from these locations:

 -   The directory containing the input script (or the current directory when no file is specified).
 -   [`PYTHONPATH`](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH)  (a list of directory names, with the same syntax as the shell variable  `PATH`).
 -   The installation-dependent default.
# Package
A collection of modules (sub-modules) and other packages (sub-packages).
![](/images/p14-2.png)
## `__init__.py`
Marks a directory as package.
In most cases, `__init__.py` can just be an empty file, but it can also execute initialization code for the package or set the `__all__` variable.
### Importing * from a package

> **Bad practice, don't do it!**

`from sound.effects import *` doesn't goes out to the filesystem and imports all submodules.
 - could take a long time
-  importing sub-modules might have unwanted side-effects (executing all submodules code).

In order to explicitly define which modules to import on package * import use the `__all__` variable in `__init__.py`
```python
# __init__.py

__all__ = ["echo", "surround", "reverse"]
``` 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzU4OTM4MDI2LC0yNDA2NzQxODYsNDcwMT
g5NTMwLDE0NTcwOTYyMSwyNjc5NzE2MTgsMTA5NjU1MTY1OSw2
NTY2ODM3NywtMjAzMzMxNzE0NCwxNDQ0NDc3NTY3LDEwMTI5OD
M1OTZdfQ==
-->
