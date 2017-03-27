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

## August 22, 2016
1. **VIM**: Append text to the end of multiple selected lines:

- Goto **Visual Block** mode using `ctrl-v`
- Jump to end of line using standard `$` symbol
- Press **A**. Then type in your text
- `Esc`
- The same text will be appended to each of the selected lines

-------------------
-------------------

## August 28, 2016
1. **VIM** : Use `*` to search the word under the cursor

-------------------
-------------------

## October 16, 2016
1. **Python** : python dictionaries and lists can be recursive  
    i.e. they can contain themselves:

```python
x = {}
x['x'] = x
print(x)

# output :  {'x': {...}}
```

Same can be for lists too.
> I don't see any practical use case for this though

-------------------
-------------------


## December 14, 2016

1. **VIM** : user `g` followed by `Ctrl-g` in **Visual Mode**  to get the information about selected lines.


------------
-----------

## January 12, 2017

1. **GIT** : use `git reset --hard HEAD~1` to remove unpushed local commit

------------
-----------

## March 27, 2017

### 1. Builder Design Patterns
- use builder design pattern when the constructor is very much populated by arguments.
- it becomes tedious for creating new instances of a class if constructor is accepting so much arguments.

#### example

**constructor over population**

```java
pulic class Burger {
    private int size;

    private boolean cheese = false;
    private boolean tomato = false;
    private boolean lettuce = false;
    private boolean pepperoni = false;

    public Burger(int size, boolean cheese, boolean tomato, boolean lettuce, boolean pepperoni) {
        this.size = size;
        this.cheese = cheese;
        this.tomato = tomato;
        this.lettuce = lettuce;
        this.pepperoni = pepperoni;
    }
}

Burger burger = new Burger(14, true, true false, false);
```

As it can be seen, as the number of items to be added to the burger grows, we have to increase the number of arguments in the constructor
too.  
This is a very bad design practice because it becomes difficult to remember the order of arguments as well as what type of arguments
are there in the arguments.

**builder pattern**

```java
class Burger {
    private size;

    private boolean cheese = false;
    private boolean pepperoni = false;
    private boolean lettuce = false;
    private boolean tomato = false;

    public Burger(BurgerBuilder builder) {
        this.size = builder.size();
        this.cheese = builder.cheese();
        this.pepperoni = builder.pepperoni();
        this.lettuce = builder.lettuce();
        this.tomato = builder.tomato();
    }
}

class BurgerBuilder {
    public size;

    public cheese = false;
    public pepperoni = false;
    public lettuce = false;
    public tomato = false;

    public BurgerBuilder(int size) {
        this.size = size;
    }

    public BurgerBuilder addPepperoni() {
        this.pepperoni = true;
        return this;
    }

    public BurgerBuilder addLettuce() {
        this.lettuce = true;
        return this;
    }

    public BurgerBuilder addCheese() {
        this.cheese = true;
        return this;
    }

    public BurgerBuilder addTomato() {
        this.tomato = true;
        return this;
    }

    public Burger build() {
        return new Burger(this);
    }
}


Burger burger = (new BurgerBuilder(14))
                    .addPepperoni()
                    .addLettuce()
                    .addTomato()
                    .build();

```

In the `BurgerBuilder` class, all the `add` method returns the builder type so that we can form the chain for subsequent addition.  
Finally, `build` method returns the Burger which is what we want.
