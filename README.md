Python Attribute List
=====================

Add/set attributes to python lists.

A google search for "add attributes to python lists" yields no good stackoverflow answer,
hence the need for this.

Useful for machine learning stuff where you need labeled feature vectors. 

This technique can be easily adapted for other built-ins (e.g. int).

The Problem
-----------

```Python
a = [1, 2, 4, 8]
a.x = "Hey!" # AttributeError: 'list' object has no attribute 'x'
```

The Solution
------------

```Python
class L(list):
 
    def __new__(self, *args, **kwargs):
        return super(L, self).__new__(self, args, kwargs)
 
    def __init__(self, *args, **kwargs):
        if len(args) == 1 and hasattr(args[0], '__iter__'):
            list.__init__(self, args[0])
        else:
            list.__init__(self, args)
        self.__dict__.update(kwargs)

    def __call__(self, **kwargs):
        self.__dict__.update(kwargs)
        return self

a = L(1, 2, 4, 8)
a.x = "Hey!"
print a       # [1, 2, 4, 8]
print a.x     # "Hey!"
print len(a)  # 4

# You can also do these:
a = L( 1, 2, 4, 8 , x="Hey!" )                 # [1, 2, 4, 8]
a = L( 1, 2, 4, 8 )( x="Hey!" )                # [1, 2, 4, 8]
a = L( [1, 2, 4, 8] , x="Hey!" )               # [1, 2, 4, 8]
a = L( {1, 2, 4, 8} , x="Hey!" )               # [1, 2, 4, 8]
a = L( [2 ** b for b in range(4)] , x="Hey!" ) # [1, 2, 4, 8]
a = L( (2 ** b for b in range(4)) , x="Hey!" ) # [1, 2, 4, 8]
a = L( 2 ** b for b in range(4) )( x="Hey!" )  # [1, 2, 4, 8]
a = L( 2 )                                     # [2]
```

Tags
----

add or set attributes properties methods to list reopen class inheritance OOP subclass list elegant solution dictionary set monkey-patch short concise fast efficient easy simple compatible
