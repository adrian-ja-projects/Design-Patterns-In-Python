# Composite Design Pattern

## Overview

The **Composite** design pattern is a structural pattern useful for hierarchal management.

The Composite design pattern, 

* allows you to represent individual entities(leaves) and groups of leaves at the same.
* is a structural design pattern that lets you compose objects into a changeable tree structure.
* is great if you need the option of swapping hierarchal relationships around. 
* allows you to add/remove components to the hierarchy.
* provides flexibility of structure

Examples of using the Composite Design Pattern can be seen in a filesystem directory structure where you can swap the hierarchy of files and folders, and also in a drawing program where you can group, un-group, transform objects and change multiple objects at the same time.

## Terminology

* **Component Interface**: The interface that all leaves and composites should implement.
* **Leaf**: A single object that can exist inside or outside of a composite.
* **Composite**: A collections of leaves and/or other composites.

## Composite UML Diagram

![Composite Pattern UML Diagram](/img/composite_concept.svg)

## Source Code

In this concept code, two leaves are created, `LEAF_A` and `LEAF_B`, and two composites are created, `COMPOSITE_1` and `COMPOSITE_2` .

`LEAF_A` is attached to `COMPOSITE_1` .

Then I change my mind and attach `LEAF_A` to `COMPOSITE_2` .

I then attach `COMPOSITE_1` to `COMPOSITE_2` .

`LEAF_B` is not attached to composites.

## Output

``` bash
python ./composite/composite_concept.py

LEAF_A          id:2050574298848
LEAF_B          id:2050574298656
COMPOSITE_1     id:2050574298272
COMPOSITE_2     id:2050574298128

<Leaf>          id:2050574298656        Parent: None
<Composite>     id:2050574298128        Parent: None    Components:2
<Leaf>          id:2050574298848        Parent: 2050574298128
<Composite>     id:2050574298272        Parent: 2050574298128   Components:0
```

## Composite Example Use Case

Demonstration of a simple in memory hierarchal file system.

A root object is created which is a composite.

Several files (leaves) are created and added to the root folder.

More folders (composites) are created, and more files are added, and then the hierarchy is reordered.

## Composite Example UML Diagram

![Composite Pattern Use Case UML Diagram](/img/composite_example.svg)

## Output

``` bash
python ./composite/client.py
<DIR>  root             id:2028913323984        Components: 4
..<FILE> abc.txt        id:2028913323888        Parent: 2028913323984
..<FILE> 123.txt        id:2028913323792        Parent: 2028913323984
..<DIR>  folder_a       id:2028913432848        Components: 1
....<FILE> xyz.txt      id:2028913433088        Parent: 2028913432848
..<DIR>  folder_b       id:2028913433184        Components: 1
....<FILE> 456.txt      id:2028913434432        Parent: 2028913433184

<DIR>  root             id:2028913323984        Components: 3
..<FILE> abc.txt        id:2028913323888        Parent: 2028913323984
..<FILE> 123.txt        id:2028913323792        Parent: 2028913323984
..<DIR>  folder_b       id:2028913433184        Components: 2
....<FILE> 456.txt      id:2028913434432        Parent: 2028913433184
....<DIR>  folder_a     id:2028913432848        Components: 1
......<FILE> xyz.txt    id:2028913433088        Parent: 2028913432848
```

## New Coding Concepts

### Conditional Expressions (Ternary Operators).

In [/composite/composite_concept.py](/composite/composite_concept.py), there are two conditional expressions. 

Conditional expressions an alternate form of `if/else` statement.

``` python
id(self.reference_to_parent) if self.reference_to_parent is not None else None
```

If the `self.reference_to_parent` is not `None`, it will return the memory address (id) of `self.reference_to_parent`, otherwise it returns `None`.

This conditional expression follows the format

``` python
value_if_true if condition else value_if_false
```

eg, 

``` python
SUN = "bright"
SUN_IS_BRIGHT = True if SUN == "bright" else False
print(SUN_IS_BRIGHT)
```

or

``` python
ICE_IS_COLD = True
ICE_TEMPERATURE = "cold" if ICE_IS_COLD == True else "hot"
print(ICE_TEMPERATURE)
```

or

``` python
CURRENT_VALUE = 99
DANGER = 100
ALERTING = True if CURRENT_VALUE >= DANGER else False
print(ALERTING)
```

Visit [https://docs.python.org/3/reference/expressions.html#conditional-expressions](https://docs.python.org/3/reference/expressions.html#conditional-expressions) for more examples of conditional expressions.

## Summary

* The Composite design pattern allows you to structure components in a manageable hierarchal order.
* It provides flexibility of structure since you can add/remove and reorder components.
* File explorer on windows is a very good example of the composite design pattern in use.
* Any system where you need to offer at runtime the ability to group, un-group, modify multiple objects at the same time, would benefit from the composite design pattern structure. Programs that allow you to draw shapes and graphics will often also use this structure as well.