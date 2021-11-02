# Python notes

## classes
classes are defined with the keyword class. e.g.: 

class example():

## initialisation
every class needs a top method __init__(). This is the intiliastion method which runs when a class is created. As below the init method prints a message to the console when the class is created.

class example(object):
	def __init__(self):
		print(' class created ')


## inheritance
sub classes can inherit from an other class using: super().__init__()

## Methods
Methods are defined underneath each class e.g.


## importing modules

### from . import XXXX
when used in an #import . means import from current directory. ex:
 from . import views [[DJANGO]]

 will import views from the current directory
 
 
 ### from scipy.optimize import *
 when used in an #import * means import everything from current module. ex:
 
 from scipy.optimise import *
 
 means import every function and class from scipy.optimise.