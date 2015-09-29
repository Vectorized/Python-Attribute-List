Python Attribute List
=====================

Add/set attributes to python lists.

A google search for "add attributes to python lists" yields no good stackoverflow answer,
hence the need for this.

Useful for machine learning stuff where you need labeled feature vectors. 

This technique can be easily adapted for other built-ins (e.g. int).

The Problem
-----------

    a = [1, 2, 4, 8]
    a.x = "Hey!" # AttributeError: 'list' object has no attribute 'x'

The Solution
------------

    a = L(1, 2, 4, 8)
    a.x = "Hey!"
    print a       # [1, 2, 4, 8]
    print len(a)  # 4

    You can also do these:
    a = L( 1, 2, 4, 8 , x="Hey!" )                 # [1, 2, 4, 8]
    a = L( [1, 2, 4, 8] , x="Hey!" )               # [1, 2, 4, 8]
    a = L( {1, 2, 4, 8} , x="Hey!" )               # [1, 2, 4, 8]
    a = L( (2 ** b for b in range(4)) , x="Hey!" ) # [1, 2, 4, 8]
    a = L( [2 ** b for b in range(4)] , x="Hey!" ) # [1, 2, 4, 8]
    a = L( 2 )                                     # [2]

Tags
----

add or set attributes properties methods to list reopen class inheritance OOP subclass list elegant solution dictionary set monkey-patch short concise fast efficient easy simple compatible
