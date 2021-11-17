
# 1. overview
## fundamentals
object oriented is a programming paradigm

main advantage of object oriented is code reusability

an object can contain other objects

## what is a class
a class has 3 components:
* #name (type) - what is it?
* #attributes (properties) - what describes it?
* #behaviour (operations) - what can it do?

## what is an object? 
an object is a instance of a class

objects are thought of as nouns. Can you put the word THE infront of it?

each object has its own state (attributes / properties)

## 4 key concepts when creating class

* #abstration - focus on essential qualities rather than one specific example
* #polymorphism - having many forms. allows a single action to be performed in multiple ways.
	* #staticpolymorphism uses method #overloading
	* #dynamicpolymorphism uses method #overriding.
		* Overriding -> allowing a subclass to replace the implementation of a method from the superclass
* #inheritance - base a new object or class on an existing one. Inherit the existing attributes and methods. Great form of code reuse. Person is the #superclass (parent class) to customer and employee #subclass (child class / derived class). inheritance can be #singleinheritance or #multipleinheritance if the language allows inheritance from multiple classes.
* #encapsulation - containing elements in an object to protect them from unwanted changes. An object should not make anything available unless it is absolutely neccesary by another part of the application to work. #blackboxing

## analysis, design and programming

* #analysis - what do we need to do?
* #design - how we are going to do it?
* #programming - 

#5step process
1. gather requirements
2. describe the application
3. identify the main objects
4. describe the interactions
5. create a #classdiagram

## unified modelling language #uml
#link uml tools https://en.wikipedia.org/wiki/List_of_Unified_Modeling_Language_tools

1...*  - means 1 or more objects

+ and - are added infront of variables nad methods to denote #public + and #private -

#staticvariable nad #staticmethods are denoted with an underline.

name string: = "jane"  is how to write #variables in UML

#abstractclass name is denoted in  itallics

The arrows for inheritance, interfaces, aggregation and compostion should always point to the super class.

#inheritance  is shown between classes with an unfilled arrow. 


#interface are denoted as a class box but with a interface tag in doulbe less than / greater than symbols above the class name. interface arrows are dashed and unfilled

#aggregation is denoted with an unfiled diamond symbol between boxes.

#composition is denoted with an filedin diamond symbol between boxes.

# 2. requirements
What does it need to do?
What is the problem we are trying to solve?

## type of requirements

define a minimum viable product #mvp

* #functionalrequirements - what must it do? quantifiable and specific not detailed into implementation. The system must...

* #non-functionalrequirements - how should it do it? The system should....
	* legal
	* performance
	* support
	* security	- either functional or non-functional


## #FURPS+
The purpose of FURPS+ is to prompt you to think of key requirement areas. it is ok to have not applicable or to come back to these areas.
* F - functionality. Capability, reusability, security
* U - usability. human factor, aesthictis, consistancy, documentation
* R - reliability. availability, failure rate and duration, predictability. How much system downtime is acceptable?
* P- performance. speed, efficiency, resource, consumption, scalability
* S - suportability. testability, extensibility, serviceability, configurability.

plus model adds 4 more categories:
* Design. addresses constraints on how software must be built, relational database etc.
* Implementation. Does it have to be written in a certain language? Standards or methodology that must be followed?
* Interface. Is there an external system that must be interfaced with?
* Physcial.  Actual physcial requirements of the hardware the system will be deployed on.

# use cases and user stories

no single way to write use case. Written in everyday language. But in general there are three steps:

* Title  - what is the goal? short phase with adjective
* #primaryactor - who desires it? any external entity who acts on the sytem.
* Success scenario - how is it accomplished? This can be written in a simple step by step with extensions incase anything goes wrong in the traditional step. 

#example 
**Title** - heat meal
**#primaryactor** - astronaut
**success scenario** - Astronaut inserts meal package. system identifies type of meal. system heats package for length of time required for meal type. system notifies astronaut that meal is ready via space page. astronaut removes package from system.

## identifying actors

as well as people any potential systems should be included

#primaryactor is the entity which initiates it.

## identifying the scenario
focus on typical situation use active voice. i.e. astronaut inserts meal choice. very broad not detailed. Do not include user interface info such as user pressess start button. Focus on **intention**

## diagramming use cases

shows relationship between actors and their different use cases.

#primaryactor  on left hand side

#secondaryactor on right hand side

box should be drawn to show system boundary

use cases should be individual and circled within system boundary box

lines should show interaction between users and use cases 

![alt text](https://www.researchgate.net/profile/Omar-Tariq-4/publication/341945176/figure/fig4/AS:899129471401984@1591380579284/USE-CASE-DIAGRAM-USER-LOGIN-MANAGEMENT.jpg)

## user stories

#userstory are shorter and simpler than a #usecase
1 or 2 sentances. 

as a...
i want...
so that...

# 3. domain modelling
## identifying obects
create #conceptualmodel to represent important objects and relationship between them

1. pick up all **nouns** from use cases.
2. review all nouns and see if there are duplicates
**if in doubt keep it!**

## identify class relatonships

draw lines between all objects for any relationships add short note to each line to describe relationship.

#example spaceship fires missile. The word fires is added between object spaceship and missile

## identifying class responsibilities
1. look at use cases and identify **verbs**

object should be responsible for their own behaviours. 

This is not where an action originates but what is responsible for performing them

a common mistake is to put too many on one object. This can be called a #godobject. 

think... what object needs to know... what object performs this task...

## crc / crh cards
usefull tool to start seeing links

they contain:
* class name
* Responsibility
* collaboration / helper

cards can then be laid out and moved around

![alt text](http://agilemodeling.com/images/models/crcCardLayout.jpg)


# class diagrams
## creating class diagram

### attributes
attributes should have

name, type and potential default value (if required):

-callSign: String = "Excelsior"  #private
-shieldActive: Boolean

### behaviours
should be get/set named. Should have parenthesis to show inputs and also return type.


* minus denotes private to the class. not directly accessible to other objects
* positive denotes it is public

+getShieldStrength(): Integer  #public 
+reduceShield(Integer)
-setPosition(Coordinate)


## converting class diagram to code

code should be laid out in a similar way to the class diagram cards.

* define your class
* define your instance variables
* define your methods 

class Spaceship(): [[python]]
	def __init__(self):
		instance variables
		self.callSign = ""
		self._sheildStrenght = 100   note: Underscore added to treat it as private (note to programmer only)
	
methods
def fireMissile(self):
	return "Pew!"
def reduceShield(self, amount):
    self.shieldStrength -= amount
	
	
## instantiation
to create a new object:

jave, c# and c++ use the keyword new  [[chash]] [[java]]

java / c# Spaceship myShip = new Spaceship()

c++ Spaceship *myShip = new Spaceship()

#python myShip = Spaceship()  [[python]]

### constructor
#constructors are special methods called when the class is created and often are a method with the same name as the class. This is differnet in #python where teh constructor is the __init__() method.

#constructors can be #overloaded within a class for example one with default params and the other passes a string to the params. In python this is simpler and doesnt require multiple constructor calls.

### destructor
#destructors are a method that gets called when the object is destroyed

languages that use #garbagecollection use a finaliser instead of a destructor.

## static attributes and methods

#staticvariable is a variable that is shared accross all objects in a class. Think game difficulty on npc's.
This is also called  a shared or a class variable.

It can be thought of as a #globalvariable across all the NPCs but not hte whole programme.

This is more #efficient than updating the difficulty of every NPC every time the player changes difficulty. 

[[java]] #java uses keyword static. public static float toughness;

[[python]] #python does not do this.  a static variable is a variable called within a class but outside of a method.
class spaceship():
	# class variable
	toughness = 0.8
	def __init__():
		etc...

### accessing static variables 
to access the static variable the class name must be used not the instance variable name. I.e. not ship1.toughness() but spaceship.toughness()


# 4. Inheritance and composition
## identifying inheritance
**DONT GO LOOKING FOR INHERITANCE IT WILL TEND TO SHOW ITSELF**
#inheritance desribes an "is a" relationship between two objects

a starfighter is a spaceship
a cargoshuttle is a spaceship
therefore a spaceship #superclass should be used and starfighter and cargoshuttle should inherit from them.

This shows inheritance

## using inheritance
#java -> public class CargoShuttle extends Spaceship{...
#chash -> public class CargoShuttle: Spaceship {...
#python -> class CargoShuttle(Spaceship):...

### calling a method in the super class

#java -> super.setShield()
#chash -> base.setSheild()
#python -> super().setShield()

## abstract and concrete classes
### abstract class
* an #abstractclass exists for other classes to inherit.
* cannot be instantiated
* contains at least one abstract method


### concrete / final class
* a concrete or final class has to be instantiated
* cannot be extended (has no children)
* this avoids redundant coding in child classes

## interfaces

* an #interface is a list of methods for a class to implement. It doesnt contain any actual behaviour
* interfaces represent a capability
	
## aggregation
	
#aggregation is a "has a" or a "uses a" relationship. collection of objects
	
A fleet has a spaceship is aggregation

If the fleet is destroyed the spaceship will still exist

## composition

* #composition is a more specific form of #aggregation.
* composition implies ownership.

composition: a spaceship owns a engine

If the spaceship is destroyed the engine is destroyed.

# software development

## object oriented programming support for different languages
python and c++ allows #multipleinheritance  

#chash and #java only allow single inheritance

## general development principles

#solid principle:
* S - single responsibiltiy principle
	* A class should have only a single responsibility - no #godclass!
* O - open/closed principle
* L - Liskov substitution principle
* I - interface segregation principle
* D - dependency inversion principle

#dry principle:
* D - dont
* R - repeat
* Y - yourself

#yagni principle:
don't abstract too much and waste time!
* Y - you
* A - aren't
* G - gonna
* N - need 
* I - it

## software testing
when designing make sure you implement  automated unit and systems tests.

## design patterns
one should use a #designpattern when possible because it will result in a code that is more easily #extensible and #maintainable

### #creationalpatterns
focus on abstatiation of objects and provide clever ways to have more flexibility on how objects are created.
* #factorymethodpattern - uses factory method to deal with creting objects
* #abstractfactory -
* #builder -
* #prototype -
* #singleton -

### #structuralpatterns 
describe how classes are actually designed, how inheritance, composition and aggregation can be used to provide extra functionaity 
* #adapter
* #bridge
* #composite
* #decorator
* #facade
* #flyweight
* #proxy

### #behaviouralpatterns
are specifically concerned with communication between objects when the programme is running
* #chainofresponsibility
* #command
* #interpreter
* #iterator
* #mediator
* #mementopattern - provides the ability to restore an object to its previous state
* #observer
* #state 
* #strategy
* #templatemethod
* #visitor