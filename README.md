[![Build Status](https://travis-ci.org/dstar55/100-words-design-patterns-java.svg?branch=master)](https://travis-ci.org/dstar55)
[![Coverage Status](https://coveralls.io/repos/github/dstar55/100-words-design-patterns-java/badge.svg?branch=master)](https://coveralls.io/github/dstar55/100-words-design-patterns-java?branch=master) 
[![GitPitch](https://gitpitch.com/assets/badge.svg)](https://gitpitch.com/dstar55/100-words-design-patterns-java/master?grs=github&t=white)
[![GitHub Stats](https://img.shields.io/badge/github-stats-ff5500.svg)](http://githubstats.com/dstar55/100-words-design-patterns-java)
[![License](http://img.shields.io/:license-mit-blue.svg)](http://gus.mit-license.org/)

# 100 words GoF Design Patterns in Java

## Introduction

Idea: describe GoF Design Patterns on a simple way. 
Each pattern will be described with following structure:
* Story(less than 100 words)
* Implementation in Java

### GoF Design Patterns

#### Creational Patterns
* [Singleton](#Singleton)
* [Prototype](#Prototype)
* [Builder](#Builder)
* [Factory Method](#FactoryMethod)
* [Abstract Factory](#AbstractFactory)

#### Structural Patterns
* [Adapter](#Adapter)
* [Bridge](#Bridge)
* [Composite](#Composite)
* [Decorator](#Decorator)
* [Facade](#Facade)
* [Flyweight](#Flyweight)
* [Proxy](#Proxy)

#### Behavioral Patterns
* [Chain Of Responsibility](#ChainOfResponsibility)
* [Command](#Command)
* [Interpreter](#Interpreter)
* [Iterator](#Iterator)
* [Mediator](#Mediator)
* [Memento](#Memento)
* [Observer](#Observer)
* [State](#State)
* [Strategy](#Strategy)
* [Template Method](#TemplateMethod)
* [Visitor](#Visitor)

##### <a id="Singleton"></a>Singleton
* Motivation

Objects resides inside heap memory and we can instantiate as many objects as there is a physical space in heap memory.
But, in some cases we can have situation that only one instance of an class can be instantiated.

So, imagine that we are developing a progam which is playing audio files.
Inside that program we need to have a class which handles audio output. 
Usaully computer has one audio output, so no more than one sound can be played at a time. 
Therefore a class that handles the computer's audio device should have exactly one instance. 

How we can ensure that only one instance in created, each java class has default public constructor, which can be invoked from any part of the code ?
If we implement in a class, constructor with scope private, then only methods from that class can invoke that constructor, meaning that we can't instantiate that class from other classes.
This is a basis for the Singleton pattern.

Singleton ensures that only one(single) object can be created from the class.

* Story

Singleton ensures that only one(single) object can be created from the class.

Men's 100 meters world record holder is a singleton.
There can be at most one active "Men's 100 meters world record holder" at any given time. 
Regardless of who that person is the title, "Men's 100 meters world record holder" is a global point of access that identifies the fastes person in the world.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/singleton.jpg "Usain Bolt, Men's 100 meters world record holder")  
###### Brick Lane Graffiti Usain Bolt&nbsp;(<a rel='license' href='https://creativecommons.org/licenses/by/2.0/' target='_blank'>CC BY 2.0</a>)&nbsp;by&nbsp;<a xmlns:cc='http://creativecommons.org/ns#' rel='cc:attributionURL' property='cc:attributionName' href='https://www.flickr.com/people/mdpettitt/' target='_blank'>Martin Pettitt</a>

* Implementation


UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/singleton.png "UML Singleton")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to singleton folder:

```
$  cd /src/main/java/com/hundredwordsgof/singleton
```
* Known uses
  * [java.lang.Runtime#getRuntime()](https://docs.oracle.com/javase/8/docs/api/java/lang/Runtime.html#getRuntime--)
  * [java.awt.Desktop#getDesktop()](https://docs.oracle.com/javase/8/docs/api/java/awt/Desktop.html#getDesktop--)
  * [java.lang.System#getSecurityManager()](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html#getSecurityManager--)


##### <a id="Prototype"></a>Prototype
* Motivation

In Singleton pattern we showed how to tackle situation when we should instantiate only one object of the class.
On another side we can have situation that during runtime, we want to copy an object that already exists in a memory, particulary if object is complex. 

So imagine that we are developing software which can work with spreadsheets. 
Spreadsheet consist of the cells, and cell is complex object with lot of attributes like, borders, content, format, color etc. 
Now if we want to split a cell, we can develop a method which will copy each attribute of that object.
This method can became very complex, so we should consider more eleganth solution.

It will be nice if we can copy object with one method, for example cloneMe().

This solution is Prototype pattern.

* Story

Clone itself.

Sheep Dolly is the first mammal to be cloned, so Dolly is a duplicate.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/prototype.jpg "Sheep Dolly")  
###### <a href="https://commons.wikimedia.org/wiki/File:Dolly_the_sheep_2016.JPG">Dolly the sheep 2016</a>, By Geni,<a href="https://creativecommons.org/licenses/by-sa/4.0/legalcode">CC BY-SA 4.0</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/prototype.png "UML Prototype")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to prototype folder:

```
$  cd /src/main/java/com/hundredwordsgof/prototype
```

* Known uses
  * [java.lang.Object#clone()](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#clone--)
  * [java.lang.Cloneable](https://docs.oracle.com/javase/7/docs/api/java/lang/Cloneable.html)


##### <a id="Builder"></a>Builder
* Motivation

Builder, as the name suggests builds complex objects from simple ones step-by-step.

Let’s say, we order child meal at a fast food restaurant. What is it comprised of? Well, a burger, a cold drink, a fries and a toy. 
In fact child meal consist of main item, side item, drink and toy.

Every time a children’s meal is ordered, the service boy will take a burger, a fries, a cold drink and a toy. Now suppose, there are 3 types of burgers available, 
Cheese, Beef and Chicken, 2 types of cold drinks available, Cola and Orange and 2 types of toys available, a car and a doll.

So, the order might be a combination of one of these, but the process how to build child meal, will be the same. One burger, one cold drink, one fries and one toy. All these items are placed in a paper bag and is given to the customer.
The process of the producing child meal is example of the Builder pattern.

Builder pattern, separates the construction of a complex object from its representation so that the same construction process can create different representations.

* Story

This pattern is used by PC shops to contruct PC's.
PC is combination of various parts like CPU, motherboard, memory, storage, power supply, video card, etc.
To build a PC same construction process is used even for each part we have different variation.
Whether a customer picks a classical hard disk or SSD for storage, the construction process is the same. 

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/builder.jpg "The Antec P180, a popular computer case, suitable for use as a silent PC")  
###### The Antec P180, By DonES (Own work) [<a href="http://www.gnu.org/copyleft/fdl.html">GFDL</a> or <a href="http://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA-3.0</a>], <a href="https://commons.wikimedia.org/wiki/File%3ASilent_PC-Antec_P180.JPG">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/builder.png "UML Prototype")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to builder folder:

```
$  cd /src/main/java/com/hundredwordsgof/builder
```

* Known uses
  * [java.lang.StringBuilder.append()](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#append-boolean-)
  * [java.lang.StringBuffer.append()](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html#append-boolean-)
  * [java.lang.Appendable](https://docs.oracle.com/javase/8/docs/api/java/lang/Appendable.html)
  * [javax.swing.GroupLayout.group.addComponent()](https://docs.oracle.com/javase/8/docs/api/javax/swing/GroupLayout.Group.html#addComponent-java.awt.Component-)
  * [java.nio.ByteBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/ByteBuffer.html#put-byte-)
  * [java.nio.CharBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/CharBuffer.html#put-byte-)
  * [java.nio.ShortBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/ShortBuffer.html#put-byte-)
  * [java.nio.IntBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/IntBuffer.html#put-byte-)
  * [java.nio.LongBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/LongBuffer.html#put-byte-)
  * [java.nio.FloatBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/FloatBuffer.html#put-byte-)
  * [java.nio.DoubleBuffer.put()](https://docs.oracle.com/javase/8/docs/api/java/nio/DoubleBuffer.html#put-byte-)
  


##### <a id="FactoryMethod"></a>Factory Method
* Motivation

Imagine that we need to develop a reporting library. 
Two basic abstractions in this library are the classes Engine and Report. 
Both classes are abstract, and clients have extend them in order to realize their application specific implementations. 

The Engine class is responsible for managing Reports and will create them as required.
Report subclasses which Engine should instatiate are application specific and Engine will only knows when a new report should be created, but not what type of Report to create. 
This leads us to situation that our library should instantiate classes, but it only knows about abstract classes, which it cannot instantiate.

So how we can solve this ?

If we encapsulate the knowledge of which Report subclasses to create and move this knowledge outside of the library, then Engine subclass will be able to create Report objects.
This solution is Factory Method pattern.

Factory Method defines an interface for creating objects, but lets subclasses decides which class to instantiate.

* Story

Plasticine is used for children's play. Plasticine is injected into predefined molds. The class of end product(ball, toy, sculpture, cake) is determined by the mold.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/factorymethod.jpg "Cake molds, Han people, metal - Museum of Vietnamese History - Ho Chi Minh City")  
###### Cake molds, Han people, metal - Museum of Vietnamese History - Ho Chi Minh City, By Daderot (Own work) [<a href="http://creativecommons.org/publicdomain/zero/1.0/deed.en">CC0</a>], <a href="https://commons.wikimedia.org/wiki/File%3ACake_molds%2C_Han_people%2C_metal_-_Museum_of_Vietnamese_History_-_Ho_Chi_Minh_City_-_DSC05796.JPG">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/factorymethod.png "UML Factory Method")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to factorymethod folder:

```
$  cd /src/main/java/com/hundredwordsgof/factorymethod
```

* Known uses
  * [java.util.Calendar#getInstance()](https://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html#getInstance--)
  * [java.util.ResourceBundle#getBundle()](https://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html#getBundle-java.lang.String-)
  * [java.nio.charset.Charset#forName()](https://docs.oracle.com/javase/8/docs/api/java/nio/charset/Charset.html#forName-java.lang.String-)
  * [java.net.URLStreamHandlerFactory#createURLStreamHandler(String)](https://docs.oracle.com/javase/8/docs/api/java/net/URLStreamHandlerFactory.html)
  * [java.util.EnumSet#of()](https://docs.oracle.com/javase/8/docs/api/java/util/EnumSet.html#of(E))


##### <a id="AbstractFactory"></a>Abstract Factory
* Motivation


Imagine that we are developing 	framework for a GUI environment, were windows will be drawn on display device and user will 
interact with GUI with a mouse and keyboard. 

First version of the framework will support Window OS, so Factory method is used for creation of the graphical abstractions like, 
Frame, Window, ScrollBar, etc.

In second version framework will be extended to Linux OS.
So, how we will extend our factory method ?

One way would be to introduce factory abstraction where each OS will have dedicated factory for creation of the graphical abstractions.
The proposed solution is example of the Abstract Factory.
 
Abstract Factory is one level higher in abstraction than Factory Method. 
Factory Method abstracts the way objects are created, while Abstract Factory also abstracts the way factories are created 
which in turn abstracts the way objects are created.

Abstract Factory provides an interface for creating families of related objects, without specifying concrete classes.

* Story

This pattern is found in the cards stamping equipment used in the 
manufacture in order to produce playing cards. 
Cards stamping machine is an Abstract Factory which produces a cards. 
The same machine is used to stamp French, Italian or German cards. 

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/abstractfactory.jpg "Poker Cards Back")  
###### Poker Cards Back&nbsp;(<a rel='license' href='https://creativecommons.org/share-your-work/public-domain/cc0/' target='_blank'>CC 0</a>)




* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/abstractfactory.png "UML Abstract Factory")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to abstractfactory folder:

```
$  cd /src/main/java/com/hundredwordsgof/abstractfactory
```

* Known uses
  * [javax.xml.parsers.DocumentBuilderFactory#newInstance()](https://docs.oracle.com/javase/8/docs/api/javax/xml/parsers/DocumentBuilderFactory.html#newInstance--)
  * [javax.xml.transform.TransformerFactory#newInstance()](https://docs.oracle.com/javase/8/docs/api/javax/xml/transform/TransformerFactory.html#newInstance--)
  * [javax.xml.xpath.XPathFactory#newInstance()](https://docs.oracle.com/javase/8/docs/api/javax/xml/xpath/XPathFactory.html#newInstance--)

##### <a id="Adapter"></a>Adapter
* Motivation

Imagine that we need to develop graphical editor which should be able to draw various graphical shapes like line, circle, rectangle and text.
All of our graphical elements are subclass of the base class Shape. So we will have LineShape, CircleShape, RectangeShape and TextShape.

Implementation of the TextShape is not easy. We need to implement lot of complex functionalities like text buffering, text bolding, text coloring, undo, redo, "what you see is what you get", etc.
We have found open source text library which implements pretty much all of the text functionality which we are looking for.

Why not adapt existing text library, so that we can reuse already implemented functionality for our graphical editor.
But, in order to use existing text library, we must adopt interfaces from existing text library towarsd our intefaces.

The process of adaptation of the existing interafces is example of the Adapter pattern.

Adapter, allows us that interface of an existing class can be used from another interface.

* Story

Adapters are often used in daily life, for example eletrical adapter is a device that 
converts attributes of one electrical device or system to those of an otherwise incompatible device or system. 
Some modify power or signal attributes, while others merely adapt the physical form of one electrical connector to another.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/adapter.jpg "Adapter")  
###### <a href="https://commons.wikimedia.org/wiki/User:Lionel_Allorge">Lionel Allorge</a>, <a href="https://commons.wikimedia.org/wiki/File:Adaptateur_de_prise_française_en_prise_suisse_2.jpg">Adaptateur de prise française en prise suisse 2</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0/legalcode">CC BY-SA 3.0</a>

* Implementation

UML: 
Class Adapter

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/classadapter.png "UML Class Adapter")

Object Adapter: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/objectadapter.png "UML Object Adapter")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to adapter folder:

```
$  cd /src/main/java/com/hundredwordsgof/adapter
```

* Known uses
  * [java.util.Arrays#asList()](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#asList-T...-)
  * [java.util.Collections#list()](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#list-java.util.Enumeration-)
  * [java.util.Collections#enumeration()](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#enumeration-java.util.Collection-)
  * [java.io.InputStreamReader(InputStream)](https://docs.oracle.com/javase/8/docs/api/java/io/InputStreamReader.html#InputStreamReader-java.io.InputStream-)
  * [java.io.OutputStreamWriter(OutputStream)](https://docs.oracle.com/javase/8/docs/api/java/io/OutputStreamWriter.html#OutputStreamWriter-java.io.OutputStream-)
  * [javax.xml.bind.annotation.adapters.XmlAdapter#marshal()](https://docs.oracle.com/javase/8/docs/api/javax/xml/bind/annotation/adapters/XmlAdapter.html#marshal-BoundType-)
  * [javax.xml.bind.annotation.adapters.XmlAdapter#unmarshal()](https://docs.oracle.com/javase/8/docs/api/javax/xml/bind/annotation/adapters/XmlAdapter.html#unmarshal-ValueType-)

##### <a id="Bridge"></a>Bridge
* Motivation

Let's imagine that we want to develop audio player on our Windows OS.
We define base class, Audio, which has two subclasses MP3Audio and WavAudio.
First version of the player on Windows is running well, but after some time we want to implement same player on Linux OS.

How we will tackle this situation ?

If we incorporate OS specifics in our hierarchy we will end up with 4 class combinations such as
WindowsMP3Audio, LinuxMP3Audio, WindowsWavAudio and LinuxWavAudio.
Adding more codec types and more operating systems will make hierarchy even bigger. 

Appropriate solution would be that we extract our structure into two separated hierarchies.

Original audio structure classes will remain a same and it will contain a reference to an object of the new hierarchy, the OS hierarchy.
This way we will extract OS specifics into its own class with two child classes, Windows and Linux. 
The Audio class will get a reference field to one of the OS classes. 
Using that reference, it will be able to delegate work to OS objects when needed. 
This reference will serve as a bridge between Audio and OS hierarchies.

Explained solution is example of the Bridge pattern.

So, Bridge pattern decouples an abstraction from its implementation so that the two can vary independently.

* Story

Steering wheel is an example of the Bridge.
The purpose of a steering wheel is to transmit  driver's input to the steered wheels in order to dynamically change direction of the vehicle.
There are different implementations of the steering wheels used in cars, buses, tracks, tractors and formulas.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/bridge.jpg "1924 Stanley 740 Interior")  
###### 1924 Stanley 740 Interior, By Liftarn (Own work) [Public domain], <a href="https://commons.wikimedia.org/wiki/File%3A1924Stanley740-interior.jpg">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/bridge.png "UML Bridge")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to bridge folder:

```
$  cd /src/main/java/com/hundredwordsgof/bridge
```

* Known uses
  * [JDBC-ODBC Bridge](https://docs.oracle.com/javase/7/docs/technotes/guides/jdbc/bridge.html)
  * [AWT](https://docs.oracle.com/javase/8/docs/technotes/guides/awt/), it provides an abstraction layer which maps onto the native OS the windowing support.

##### <a id="Composite"></a>Composite
* Motivation

Imagine that we need to develop graphical framework which should speed up the development of the bussiness applications, where user works with the data using graphical forms.
Graphical form is made up of the basic graphical elements like label, text, input field, button, list etc.

In order to draw something on the screen, every graphical element should implement common interace with **draw** method.
But, some graphical elements in addition to draw interface must act as a container for other graphical elements.
So, for example form is a container for labels, input fields and buttons.

It looks that tree structure can be basis for such a graphical framework, but problem is that we must treat leaf node and internal node on same way.
This problem can be solved using Composite pattern. 

Composite pattern composes objects into tree structures to represent part-whole hierarchies. 
Group of objects is to be treated in the same way as a single instance of an object.

* Story

Lego brick represents Composite pattern. 
A brick is a basic object, but on a same time brick is a container which can hold other bricks in order to construct complex objects.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/composite.jpg "Lego Bricks")  
###### Lego Bricks, By Priwo (photo taken by de:Benutzer:Priwo) [Public domain], <a href="https://commons.wikimedia.org/wiki/File%3ALEGO-01.jpg">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/composite.png "UML Composite")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to composite folder:

```
$  cd /src/main/java/com/hundredwordsgof/composite
```
* Known uses 
  * [java.awt.Container#add(Component)](https://docs.oracle.com/javase/8/docs/api/java/awt/Container.html#add-java.awt.Component-)
  * [javax.faces.component.UIComponent#getChildren()](https://docs.oracle.com/javaee/7/api/javax/faces/component/UIComponent.html#getChildren--)


##### <a id="Decorator"></a>Decorator
* Motivation

Suppose that we are working on a user interface toolkit and we want to be able to add borders and scroll bars to the windows. 
If we are using inheritance, we will extend Window class with new classes like, WindowVerticalScrollBar, WindowHorizontalScrollBar, WindowBorder, etc.

Solution with inheritance is not flexible while we will end up in too many subclasses. Such a hierarchy is hard to maintain, hard to extend and hard to use.

But, if we enclose window in object which can add new features like scroll bar and border dynamically we will have much more flexible solution. 
"Enclosed" object is an decorator.

Decorator pattern, attaches additional responsibilities to an object dynamically.

* Story

The spoilers that are added to a car are examples of the Decorator.
The spoilers do not change the car itself, but adds additional functionality which is to 'spoil' unfavorable air movement across a body of a vehicle in motion, usually described as turbulence or drag.  

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/decorator.jpg "013 Porsche 911 Carrera S (8233337583)")  
######  <a href="https://commons.wikimedia.org/wiki/File:2013_Porsche_911_Carrera_S_(8233337583).jpg">2013 Porsche 911 Carrera S (8233337583)</a>, by <a href="http://www.flickr.com/people/15779944@N00">steve lyon</a> from los angeles, ca, usa,<a href="https://creativecommons.org/licenses/by-sa/2.0/legalcode">CC BY-SA 2.0</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/decorator.png "UML Decorator")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to decorator folder:

```
$  cd /src/main/java/com/hundredwordsgof/decorator
```

* Known uses 
  all subclases of the:
  * [java.io.InputStream](https://docs.oracle.com/javase/7/docs/api/java/io/InputStream.html) 
  * [java.io.OutputStream](https://docs.oracle.com/javase/7/docs/api/java/io/OutputStream.html)
  * [java.io.Reader](https://docs.oracle.com/javase/7/docs/api/java/io/Reader.html)
  * [java.io.Writer](https://docs.oracle.com/javase/7/docs/api/java/io/Writer.html)
  e.g.
  * [java.io.BufferedInputStream(InputStream)](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedInputStream.html)
  * [java.io.DataInputStream(InputStream)](https://docs.oracle.com/javase/7/docs/api/java/io/DataInputStream.html)
  * [java.io.BufferedOutputStream(OutputStream)](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedOutputStream.html)
  * [java.util.zip.ZipOutputStream(OutputStream)](https://docs.oracle.com/javase/7/docs/api/java/util/zip/ZipOutputStream.html)

  * [javax.servlet.http.HttpServletRequestWrapper](https://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletRequestWrapper.html)
  * [javax.servlet.http.HttpServletResponseWrapper](https://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletResponseWrapper.html)

  * [java.util.Collections#checked()](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#checkedCollection-java.util.Collection-java.lang.Class-)
  * [java.util.Collections#synchronized()](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#synchronizedCollection-java.util.Collection-)
  * [java.util.Collections#unmodifiable()](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#unmodifiableCollection-java.util.Collection-)


##### <a id="Facade"></a>Facade
* Motivation

Let's say that we need to develop compiler for brand new programming language.

The process of compiling consist of the steps like scanning, tokenizing, parsing, building abstract syntax tree, code generation etc. 
For each step we need to develop seprate subcomponent. In principle each subcomponent is complex, and the usage of the subcomponents is complex as well.

It does not make sense that the client which want to compile a code is invoking complex subcomponents in order to compile.

Better approach would be to define uniform interface which presents compiler functionality, a Compiler class. 
Compiler class hides "low-level" functionality from the client, so we can say that Compiler class is a facade.

Facade deisgn pattern, hides the complexity of the system and provides an interface to the client from where the client can access the system.

* Story

You want to organize a marriage reception with dinner for 100 people. 
So in order to organize such event, you need to find and decorate a hall where the event will happen, 
then you need to find a music, organize flowers, send invitations and so on and so on.

If this is to much for you than you can find event manager which will organize event for you. 

This is a typical example for Facade. 

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/facade.jpg "Event Management in Pune")  
###### Event Management in Pune, By WeMaxx1248 (Own work) [<a href="http://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>], <a href="https://commons.wikimedia.org/wiki/File%3AEvent_management_in_pune.jpg">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/facade.png "UML Facade")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to facade folder:

```
$  cd /src/main/java/com/hundredwordsgof/facade
```

* Known uses 
  * [javax.faces.context.FacesContext)](https://docs.oracle.com/javaee/7/api/javax/faces/context/FacesContext.html), internally uses [LifeCycle](https://docs.oracle.com/javaee/7/api/javax/faces/lifecycle/Lifecycle.html), [ViewHandler](https://docs.oracle.com/javaee/7/api/javax/faces/application/ViewHandler.html), [NavigationHandler](https://docs.oracle.com/javaee/7/api/javax/faces/application/NavigationHandler.html) etc.
  * [javax.faces.context.ExternalContext](https://docs.oracle.com/javaee/7/api/javax/faces/component/UIComponent.html#getChildren--), internally uses [ServletContext](https://docs.oracle.com/javaee/7/api/javax/servlet/ServletContext.html), [HttpSession](https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpSession.html), [HttpServletRequest](https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html), [HttpServletResponse](https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletResponse.html), etc.
  * [java.lang.Class](https://docs.oracle.com/javase/8/docs/api/java/lang/Class.html), acts as a facade for [Reflection API](https://docs.oracle.com/javase/7/docs/api/java/lang/reflect/package-summary.html)(getConstructors(), getMethods())

##### <a id="Flyweight"></a>Flyweight
* Motivation

Let's imagine that you are teaching youngsters programing. 
You decided to start with simple but exciting example, so during a course graphical editor which can draw a line will be developed.

Base artifact is a class Line with start and end point. Now draw method needs to be implemented and voila our simple graphical editor implemented.
After first usage, we decided that new feature will be implemented, in fact we want that our line has a basic colors.

Line class will be extended with new attribute(Color class) which holds information's about the color and draw method will be extended accordingly.
Now we have new version of our editor, and some users wants to test the edge of the editor, so they draw few thousand lines.
Few thousand lines means that we have few thousand Line objects in memory, but we have few thousand Color objects in a memory as well, even our editor 
is drawing lines only with basic colors.

Can we use memory more efficiently ?
Color objects includes information's that are duplicated.
Why not set up a pool of the basic color objects and share those colors, when Line object need it ?

The properties of the objects that are shared and are reasonably unchanging are moved into flyweight objects. 
For each of the Line objects that use the shared data, only a reference to the appropriate flyweight object is required. 
This will drastically reduce the memory used by each of the Line objects.

Explained solution is example of the Flyweight pattern.
Flyweight patterns removes duplicates and reduces memory by loading only the data necessary to perform action.


* Story

Database normalization is flyweight. 
Normalization, is the process of organizing the columns (attributes) and tables (relations) of a relational database to minimize data redundancy.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/flyweight.jpg "Normal Form Diagram")  
###### Normal Form Diagram, By 04hutts (Own work) [Public domain], <a href="https://commons.wikimedia.org/wiki/File%3ANormalFormDiagram.png">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/flyweight.png "UML Flyweight")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to flyweight folder:

```
$  cd /src/main/java/com/hundredwordsgof/flyweight
```

* Known uses 

  * [java.lang.Integer#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#valueOf-int-)
  * [java.lang.Boolean#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html#valueOf-boolean-)
  * [java.lang.Byte#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#valueOf-byte-)
  * [java.lang.Character#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#valueOf-char-)
  * [java.lang.Short#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#valueOf-short-)
  * [java.lang.Long#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#valueOf-long-)
  * [java.lang.BigDecimal#valueOf(int)](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html#valueOf-long-int-)


##### <a id="Proxy"></a>Proxy
* Motivation

Imagine that we are implementing Viewer which will show Microsoft word document in read only mode.

The Viewer must open and load document quickly, but the problem is that during loading of the document we do not know is there any "heavy" object inside a document. 
Heavy object can be image which is injected in word document on let's say, 10th page of the document.

So, straight solution where we will simply load everything what is inside document can be slow.

Another solution would be that heavy objects are loaded on demand, in our example, image will be loaded when user is on 10th page of the document. 
Meanwhile heavy object will be presented with another lite object which acts as original.

That solution is Proxy.

Proxy pattern, orovides a surrogate or placeholder for another object to control access to it.


* Story

Envoy Extraordinary is a Proxy. 
He is an accredited messenger, agent, or representative who is sent by one government to represent it in dealing with another government.


* Story

Provide a surrogate or placeholder for another object to control access to it.

Envoy Extraordinary is a Proxy. 
He is an accredited messenger, agent, or representative who is sent by one government to represent it in dealing with another government.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/proxy.jpg "The Envoy Extraordinary")  
###### Burmese ambassador, The Envoy Extraordinary and Minister Plenipotentiary, By John Watkins (Kenwoon Mengyee) [Public domain or Public domain], <a href="https://commons.wikimedia.org/wiki/File%3AKinwun_Mingyi.jpg">via Wikimedia Commons</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/proxy.png "UML Proxy")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to proxy folder:

```
$  cd /src/main/java/com/hundredwordsgof/proxy
```

* Known uses
  * [java.lang.reflect.Proxy](https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Proxy.html)
  * [java.rmi.*](https://docs.oracle.com/javase/8/docs/api/java/rmi/package-summary.html)
  * [javax.persistence.PersistenceContext](https://docs.oracle.com/javaee/7/api/javax/persistence/PersistenceContext.html)

  
##### <a id="ChainOfResponsibility"></a>Chain Of Responsibility
* Motivation

Imagine that you just have bought a new wireless router from local Internet Service Provide. You unpack a router from the box, plug the necessary cables and you switch on yours new wireless router. 
But router is not able to establish internet connection. After checking technical manuals and playing with router settings, you gave up and you finally call ISP operator's call center.

The first thing you hear is a machine voice of the auto responder. It suggests dozen of the possible solutions to various problems, but none of these is related to yours. 
After a while, machine connects you to the live operator. After short discussion operator realized that he can not help you either. 
So, he connects you to engineer who finally fixes the problem.

That was example of the Chain of Responsibility.

In essence, we pass an object along a "chain" of potential handlers for that object until one of the handlers tackle the request.

The Chain of Responsibility allows an object to send a command without knowing which object will receive and handle it. 
The request is sent from one object to another making them parts of a chain and each object in this chain can handle the command, pass it on or do both.

* Story

A King and his army is example of the Chain of Responsibility. 
King gives the orders to his army. 
The closest element to react would be the commander, then the officer and then the soldier and those three elements would form a 
Chain of Responsibility.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/chainofresponsibility.jpg "Zulu Soldiers of King Panda’s Army, 1847")  
###### By George French Angas, 1822-1886 (Bibliothèque numérique mondiale), Zulu Soldiers of King Panda’s Army, 1847 [Public domain], <a href="https://commons.wikimedia.org/wiki/File%3AZulu_soldiers_of_the_army_of_King_Umpande_(Panda)%2C_1847.png">via Wikimedia Commons</a>


* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/chainofresponsibility.png "UML Chain Of Responsibility")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to chainofresponsability folder:

```
$  cd /src/main/java/com/hundredwordsgof/chainofresponsibility
```
* Known uses
  * [java.util.logging.Logger#log()](https://docs.oracle.com/javase/8/docs/api/java/util/logging/Logger.html#log-java.util.logging.Level-java.lang.String-)
  * [javax.servlet.Filter#doFilter()](https://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html#doFilter-javax.servlet.ServletRequest-javax.servlet.ServletResponse-javax.servlet.FilterChain-)
  * [java.awt.AWTEventMulticaster](https://docs.oracle.com/javase/7/docs/api/java/awt/AWTEventMulticaster.html)

##### <a id="Command"></a>Command
* Motivation

Imagine that we are developing graphical editor. User can add new text, delete or update existing text.

What to do in a case when user hits wrong action. The user should have posibility return back to the state of the text before wrong action has been executed.

How to implement such behavior ?

One solution would be to hold a list of the text states. If text is big and if we store a lot of states of that big text, we can run out of memory, so this solution is not appropriate for such a scenario.

What if we consider idea, where the current state of text is a result of execution of the sequence of operations. 
These operations can be undone, with the effect that the text reverts to a previous state. Operations that have been undone become redoable, so that later model states can be reached again if necessary.
So, we will no longer invokes operations on text directly, but we will create Command objects that invoke the operations. Each text operation will have appropriate Command object.

This solution is Command pattern. 
Command pattern, issue requests to objects without knowing anything about the operation being requested or the receiver of the request.

* Story

When your car needs service you visit Car Service Center. On reception you explain a problem and you leave a car.
The person at reception encapsulates the problem in to order for Car Technician. The order is queued internaly.
Car Technician will receive a request and fix a problem.

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/command.png "UML Command")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to command folder:

```
$  cd /src/main/java/com/hundredwordsgof/command
```

* Known uses 
  * [java.lang.Runnable](https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html)
  * [javax.swing.Action](https://docs.oracle.com/javase/8/docs/api/javax/swing/Action.html)

##### <a id="Interpreter"></a>Interpreter
* Motivation

* Story

A person who translates orally from one language into another.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/interpreter.jpg "Polish Sign Language - letter C")  
######  Polish Sign Language - letter C, By Tomt87 (Own work) [CC BY-SA 4.0 (http://creativecommons.org/licenses/by-sa/4.0)], via Wikimedia Commons


* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/interpreter.png "UML Command")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to command folder:

```
$  cd /src/main/java/com/hundredwordsgof/interpreter
```
* Known uses 
  * [java.util.Pattern](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html)
  * [java.text.Normalizer](https://docs.oracle.com/javase/8/docs/api/java/text/Normalizer.html)
  * All subclasses of [java.text.Format](https://docs.oracle.com/javase/8/docs/api/java/text/Format.html)
  * All subclasses of [javax.el.ELResolver](https://docs.oracle.com/javaee/7/api/javax/el/ELResolver.html)

  
##### <a id="Iterator"></a>Iterator
* Motivation

In computer science, a data structure is a particular way of organizing and storing data, so that it can be accessed and modified efficiently. 
More precisely, a data structure is a collection of data values, the relationships amongs them, and the functions or operations that can be applied to the data.

There are numerous types of data structures like linked lists, arrays, vectors, maps, etc.
Each collection of the data structure has its own structure and its own way how to access elements of the collection.

In practice it is not convenient to access each type of collections on a different way, 
so it will be nice to have common interface for element-by-element access to a collection, independent of the collection’s shape.

The Iterator pattern lets you do all this. 
The key idea is to take the responsibility for access and traversal out of the aggregate object and put it into an Iterator object that defines a standard traversal protocol.

So, Iterator pattern, provide a way to access the elements of an aggregate object sequentially without exposing its underlying representation.

* Story

Book is a set of written, printed sheets bound together into a volume.
You can browse through the book page by page, or quickly jump to interesting chapter.
Process of browsing is example of Iterator pattern.
* Story

Book is a set of written, printed sheets bound together into a volume.
You can browse through the book page by page, or quickly jump to interesting chapter.
Process of browsing is example of Iterator pattern.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/iterator.jpg "Iterate book page by page")  
###### Open Book by Dave Dugdale, on Flickr&quot;&nbsp;(<a rel='license' href='https://creativecommons.org/licenses/by-sa/2.0/' target='_blank'>CC BY-SA 2.0</a>)&nbsp;by&nbsp; <a xmlns:cc='http://creativecommons.org/ns#' rel='cc:attributionURL' property='cc:attributionName' href='https://www.flickr.com/people/davedugdale/' target='_blank'>Dave Dugdale</a>


* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/iterator.png "UML Iterator")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to iterator folder:

```
$  cd /src/main/java/com/hundredwordsgof/iterator
```
* Known uses 
  * All implementations of [java.util.Iterator](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html)
  * All implementations of [java.util.Enumeration](https://docs.oracle.com/javase/8/docs/api/java/util/Enumeration.html)


##### <a id="Mediator"></a>Mediator
* Motivation


Imagine that we need to develop flight simulator. Our flight simulator will have base artifacts, like airport and aircraft.
Aircraft can take off from the airport, fly in the sky and land to the airport.

Imagine a scenario when one particular aircraft is landing to an airport, how that aircraft will be sure that other aircrafts are not trying to land on same airport at same time ?
It is obvious that our aircraft can't to talk to each aircraft which are in the sky at the moment.

Better approach would be that we introduce a mediator, which is "man in the middle" and aircrafts will talk only to mediator.
The task of ensuring safe operations of the aircrafts falls on air traffic controllers which are mediators. 
They must coordinate the movements of the aircrafts, keep them at safe distances from each other, direct them during takeoff and landing from airports, 
direct them around bad weather and ensure that traffic flows smoothly with minimal delays.

The explained solution is Mediator pattern.
Mediator pattern, defines an object that controls how a set of objects interacts.

* Story

Radio Taxi is an example of the Mediator pattern.
Taxi drivers communicate with the Mediator(Radio Taxi Call Center), rather than with each other. 

When customer needs a taxi, he calls Radio Taxi Call Center. 
All taxis have a GPS unit which tells where the taxi is present right now, also there is a central information system which tells which taxi is available to serve the customer. 
The call center will contact the available taxi nearest to customer’s location and send them to serve the customer.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/mediator.jpg "Call Center Taxis Libres")  
###### Call Center Taxis Libres,By Jquemba (Own work) [Public domain], via Wikimedia Commons 

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/mediator.png "UML Mediator")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to mediator folder:

```
$  cd /src/main/java/com/hundredwordsgof/mediator
```

* Known uses 
  * [java.util.Timer](https://docs.oracle.com/javase/8/docs/api/java/util/Timer.html) (all scheduleXXX() methods)
  * [java.util.concurrent.Executor#execute()](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/Executor.html#execute-java.lang.Runnable-)
  * [java.util.concurrent.ExecutorService](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ExecutorService.html) (the invokeXXX() and submit() methods)
  * [java.util.concurrent.ScheduledExecutorService](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ScheduledExecutorService.html) (all scheduleXXX() methods)
  * [java.lang.reflect.Method#invoke()](https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html#invoke-java.lang.Object-java.lang.Object...-)

##### <a id="Memento"></a>Memento
* Motivation

Modern cars have brakes on all four wheels, operated by a hydraulic system. The brakes may be disc type or drum type.

The front brakes play a greater part in stopping the car than the rear ones, because braking throws the car weight forward on to the front wheels.

Many cars therefore have disc brakes, which are generally more efficient, at the front and drum brakes at the rear.

Imagine a scenario that we need to replace drum brakes at the rear by ourself ? How we will ensure that new drum brake has all necessary pieces at proper pace. One solution can be that we use Memento.

The drums are removed from both sides, exposing both the right and left brakes. Only one side is disassembled and the other serves as a Memento of how the brake parts fit together. Only after the job has been completed on one side, the other side is disassembled. When the second side is disassembled, the first side acts as the Memento.

So, that we an example of the Memento design pattern.
Memento design pattern, helps to restore an object’s state to it previous state.

* Story

Transactions are operations on the database that occur in an atomic, consistent, durable, and isolated fashion. 
A transaction can contain multiple operations on the database, each operation can succeed or fail, however a transaction guarantees that if all operations succeed, 
the transaction would commit and would be final. 
And if any operation fails, then the transaction would fail and all operations would rollback and leave the database as if nothing has happened.

This mechanism of rolling back uses the Memento design pattern. 

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/memento.jpg "States of transaction")  
###### States of transaction 

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/memento.png "UML Memento")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to memento folder:

```
$  cd /src/main/java/com/hundredwordsgof/memento
```

* Known uses 
  * All implementations of [java.io.Serializable](https://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html)
  * All implementations of [javax.faces.component.StateHolder](https://docs.oracle.com/javaee/7/api/javax/faces/component/StateHolder.html)

##### <a id="Observer"></a>Observer
* Motivation

Imagine that we are developing a computer game.

One feature of our game will be awards system. 
Players will earn dozens of different badges for completing specific milestones during game.

When player pass or reach some points in the game, for example jumps over complex fence, 
then we need to catch that part of the code and calculate the award. 

But, how we will implement such a feature ?

One approach would be to find a places in a code where specific milestones are completed and extend those places with a code which 
calculates the awards. This approach is not flexible, not intuitive, makes our code complex and heavy and violets the single responsibility principle.

Another approach would be that we create award events in a code where specific milestones are completed, 
award events are then published as notifications, without caring who receives the notification. 
Awards system is listening to all award events and implements all necessary logic.

This solution is Observer pattern.

Observer pattern define a one-to-many dependency between objects so that when one object changes state, 
all its dependents are notified and updated automatically.

* Story

Keep me updated.

Newsletter subscription demonstrate Observer pattern.
A newsletter is a regularly distributed publication that is generally about one main topic of interest to its subscribers. 
Subscribers can subscribe or unsubscribe to the newsletters.


* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/observer.jpg "Newsletter Banner")  
###### Newsletter Banner by, <a href="https://commons.wikimedia.org/wiki/User:Stevie_Benton_(WMUK)">Stevie Benton</a>, <a href="https://commons.wikimedia.org/wiki/File:Newsletter-banner-v2.jpg">Newsletter-banner-v2</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0/legalcode">CC BY-SA 3.0</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/observer.png "UML Observer")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to observer folder:

```
$  cd /src/main/java/com/hundredwordsgof/observer
```

* Known uses 
  * [java.util.Observer](https://docs.oracle.com/javase/8/docs/api/java/util/Observer.html)
  * [java.util.Observable](https://docs.oracle.com/javase/8/docs/api/java/util/Observable.html)
  * [java.util.EventListener](https://docs.oracle.com/javase/8/docs/api/java/util/EventListener.html)
  * [javax.servlet.http.HttpSessionBindingListener](https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpSessionBindingListener.html)
  * [javax.servlet.http.HttpSessionAttributeListener](https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpSessionAttributeListener.html)
  * [javax.faces.event.PhaseListenerl](https://docs.oracle.com/javaee/7/api/javax/faces/event/PhaseListener.html)
  
##### <a id="State"></a>State
* Motivation

Imagine that we need to implement state machine. We started with few states, and few simple conditions for those states. 
Our initial State machine is implemented using if/else blocks, which are checking current state and perform appropriate behavior.

But over the time, number of states increased. In addition the conditions how to reach certain state became more complex. 
Our if/else based state machine has more and more if/else blocks and it became really hard to maintain, to extent, to debug such a code base.

Is there more elegant way to implement State Machine ?

Another approach would be that for every possible state, separate class where state related behavior over the common interface will be implemented.
The Context class will contain a reference to an state object that represents its current state. 
Instead of performing a behavior on its own, the context will delegate the execution to the state object.
To change the context's state, one would pass another state object to the context.

This solution is example of the State pattern. 

State pattern, allow an object to alter its behavior when its internal state changes.

* Story

Behavior depends on its state.

Pregnancy is time of great physical and emotional change for women. 
Everything from the size of her belly to the speed at which her heart beats will change over the nine months leading up to childbirth. 
Partly the result of hormonal fluctuations and partly the physical strain of carrying extra body weight, pregnant women can expect to buy new bras, 
search for ways to alleviate swollen ankles, gasp for breath after climbing a few stairs, and marvel at how quickly their nails grow.


* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/state.jpg "Human Pregnancy")  
###### <a href="https://commons.wikimedia.org/wiki/File:Pregnant_graffiti.jpg">Pregnant graffiti</a> by, <a href="http://flickr.com/photos/19616008@N00">Petteri Sulonen from Helsinki, Finland</a>, <a href="https://creativecommons.org/licenses/by/2.0/legalcode">CC BY 2.0</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/state.png "UML State")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to state folder:

```
$  cd /src/main/java/com/hundredwordsgof/state
```

* Known uses 
  * [javax.faces.lifecycle.LifeCycle#execute()](https://docs.oracle.com/javaee/7/api/javax/faces/lifecycle/Lifecycle.html#execute-javax.faces.context.FacesContext-)
  
  
##### <a id="Strategy"></a>Strategy
* Motivation

Imagine that we need to implement network load balancer. Load balancer serves as the single point of contact for clients. 
The load balancer distributes incoming traffic across multiple targets, which increases the availability and capability of your application.

The question is how load balancer will distribute the incoming traffic ? 
We can have various algorithms like, round robin, ip-hash, least connected, etc. 
During a time new algorithms can be introduced. So, it is obvious that algorithm for traffic distribution can be implemented on a various ways.

Straight solution would be to implement few algorithms and hide the invocation of the algorithm in if/then or in switch statement.

Is proposed solution flexible enough ?

Another solution would be that we define common interface for our algorithm and then 
we encapsulates the behavior of an algorithm as object which implements common interface.
During runtime we can select which object to use, many different behaviors can be implemented without creating huge if/then or switch statements.

This solution is Strategy pattern. 
Strategy pattern, defines a family of algorithms, encapsulate each one, and make them interchangeable. 
Strategy lets the algorithm vary independently from clients that use it.

* Story

Select an algorithm at runtime.

Payment options in a Shopping Cart is an example of Strategy.
User can choose various payment options like Master Card, Amex or PayPal.
Any of these payment options will pay items in Shopping Cart, and they can be used interchangeably. 
The user must choose the Strategy based on his possibilities, preferences.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/strategy.jpg "Credit Card")  
###### Credit Card&nbsp;(<a rel='license' href='https://creativecommons.org/licenses/by/2.0/' target='_blank'>CC BY 2.0</a>)&nbsp;by&nbsp;<a xmlns:cc='http://creativecommons.org/ns#' rel='cc:attributionURL' property='cc:attributionName' href='https://www.flickr.com/people/mecklenburg/' target='_blank'>ThomasKohler</a>

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/strategy.png "UML Strategy")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to strategy folder:

```
$  cd /src/main/java/com/hundredwordsgof/strategy
```

* Known uses 
  * [java.util.Comparator#compare()](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html#compare-T-T-), executed by among others [Collections#sort()]()
  * [javax.servlet.Filter#doFilter()](https://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html#doFilter-javax.servlet.ServletRequest-javax.servlet.ServletResponse-javax.servlet.FilterChain-)
  
##### <a id="TemplateMethod"></a>TemplateMethod
* Motivation

Imagine that we need to implement application which does various operations on a database. 
We decided to use JDBC, which is standard Java interface for accessing the relational database. 
Using JDBC, for database operation, let's say read operation via select SQL statement, user must execute following steps:

* connect to database   
* execute SQL statement   
* process data which are gathered from database   
* close database connection   
* handle errors if something goes wrong   

If we implement such a database operation few times for a various read operations, 
we will see that we are repeating same steps. 
Also we can see that some steps are always the same, like connect to database, close database connection, handle errors. 
Remaining steps like execute SQL statement, and process data which are gathered from database, are different for every read operation. 
So, let's call steps which are the same invariant and remaining steps are variant.

Now if we implement invariant steps inside abstract base class, 
while the variant steps are either given a default implementation, or no implementation at all. 
The variant steps represent "hooks", or "placeholders", that can, or must, be supplied by the component's client in a concrete derived class.

The explained solution is Template Method design pattern.

Template Method, defines a skeleton of an algorithm in an operation.
Algorithm will have common and specialized part

* Story

Daily routine is example of the Template Method.
Every day workers get up(common part), go to work(common part), do his job(specialized part), go home(common part) and go to sleep(common part).
There are workers with different professions like engineers, teachers, etc.
During work engineer will fix machines while teacher will teach children how to read and write.
At the end of the day they go home, have a dinner and go to sleep.

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/templatemethod.png "UML Template")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to template folder:

```
$  cd /src/main/java/com/hundredwordsgof/templatemethod
```

* Known uses 
  * All non-abstract methods of [java.io.InputStream](https://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html), [java.io.OutputStream](https://docs.oracle.com/javase/8/docs/api/java/io/OutputStream.html), [java.io.Reader](https://docs.oracle.com/javase/8/docs/api/java/io/Reader.html) and [java.io.Writer](https://docs.oracle.com/javase/8/docs/api/java/io/Writer.html).
  * All non-abstract methods of [java.util.AbstractList](https://docs.oracle.com/javase/8/docs/api/java/util/AbstractList.html), [java.util.AbstractSet](https://docs.oracle.com/javase/8/docs/api/java/util/AbstractSet.html) and [java.util.AbstractMap](https://docs.oracle.com/javase/8/docs/api/java/util/AbstractMap.html)


##### <a id="Visitor"></a>Visitor
* Motivation

Imagine that we need to implement a compiler. A compiler is program wich transforms code written in 
one programming language (the source language) into another programming language (the target language).

Compiler functionality is divided into two major blocks: a front-end and a back-end. 
Front-end block is comprised of a sequence of several phases with each stage taking input from its previous stage, 
modifying it and producing its own representation of source program and passing it to the next phase. 
The front-end includes three main stages called lexical, syntax and semantic analysis. 

The first phase takes the source code as a stream of characters and identifies distinct words (tokens) such as variable names, keywords and punctuators.
The second phase determines the validity of syntactic organization of the program and produces Abstract Syntax Tree (AST). 
Semantic analysis checks whether the AST follows the rules of a language (type checking, name resolution, etc.).

AST, which represents the program written in source code, is created during second phase and is used in later a phases of the compiling process 
for a operations like, type-checking, code generation, code optimization, flow analysis, pretty-printing, code instrumentation, etc.

Most of these operations will need to treat nodes that represent assignment statements differently from nodes that represent 
variables or arithmetic expressions. 
Distributing all these operations across the various node classes leads to a system that's hard to understand, maintain and change.

It would be better if each new operation could be added separately, and the node classes were independent of the operations that apply to them. 
If we package related operations in a separate object, called a visitor, and pass it to elements of the AST as it's traversed, 
then when an element of the AST "accepts" the visitor, it sends a request to the visitor that encodes the element's class.

The explained solution is Visitor design pattern.

Visitor allows for one or more operations to be applied to a set of objects at runtime, decoupling the operations from object structure.


* Story

Shopping in supermarket is example of the Visitor pattern. 
You pick a products and put them in shopping cart. When you get to the checkout, the cashier acts as a visitor, taking the 
disparate set of elements, some with prices and others that needs to be weighted, in order to provide you with total.

* Image

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/gh-pages-resources/visitor.jpg "Cashier in Supermarket")  
###### Cashier in Supermarket, CC0 Public Domain

* Implementation

UML: 

![alt text](https://github.com/dstar55/100-words-design-patterns-java/blob/master/src/main/resources/visitor.png "UML Visitor")

Source Code:

Clone repo:
```
$  git clone https://github.com/dstar55/100-words-design-patterns-java.git .
```

Move to visitor folder:

```
$  cd /src/main/java/com/hundredwordsgof/visitor
```

* Known uses 
  * [javax.lang.model.element.AnnotationValue](https://docs.oracle.com/javase/8/docs/api/javax/lang/model/element/AnnotationValue.html) and [AnnotationValueVisitor](https://docs.oracle.com/javase/8/docs/api/javax/lang/model/element/AnnotationValueVisitor.html)
  * [javax.lang.model.element.Element](https://docs.oracle.com/javase/8/docs/api/javax/lang/model/element/Element.html) and [ElementVisitor](https://docs.oracle.com/javase/8/docs/api/javax/lang/model/element/ElementVisitor.html)
  * [javax.lang.model.type.TypeMirror](https://docs.oracle.com/javase/8/docs/api/javax/lang/model/type/TypeMirror.html) and [TypeVisitor](https://docs.oracle.com/javase/8/docs/api/javax/lang/model/type/TypeVisitor.html)
  * [java.nio.file.FileVisitor](https://docs.oracle.com/javase/8/docs/api/java/nio/file/FileVisitor.html) and [SimpleFileVisitor](https://docs.oracle.com/javase/8/docs/api/java/nio/file/SimpleFileVisitor.html)
  * [javax.faces.component.visit.VisitContext](https://docs.oracle.com/javaee/7/api/javax/faces/component/visit/VisitContext.html) and [VisitCallback](https://docs.oracle.com/javaee/7/api/javax/faces/component/visit/VisitCallback.html)

  
