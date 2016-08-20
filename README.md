# TIL
A minimal repo for my #TIL stuffs related to programming, technology and anything.

## August 19, 2016
1. In vim, `ctrl-i` or `ctrl-o` jumps to previously/next visited locations.  

2. In vim, pressing `gx` over the line with url opens the url in browser.

-------------------
-------------------

## August 20, 2016
1. Python has `namedtuple` where you can create tuple with attributes.  

```python
from collections import namedtuple

# first argument    : the name of the tuple
# second argument   : comma separated attributes quoted in a single string 
Person = namedtuple("Person", "name, bio")
me = Person("paradox", "I know nothing")
```

The value of the tuple can be accessed using the attributes as:

```python
print(me.name)
```

> namedtuple is elegant, easy and fast if you don't want to create a custom class just to store attributes/values

-------------------
-------------------
