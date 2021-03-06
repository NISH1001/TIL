# TIL (Today I learned)
A minimal repo for my #TIL stuffs related to programming, technology and anything.

--------------
--------------

## July 29, 2017

### 1. Base64 Encoding == padding
`Base64` encoded strings have == at the end when the number of encoded bytes is not divisible by 3

--------------
--------------

## July 25, 2017

### Lookarounds In Regex
Lookarounds in regex are awesome non-capturing group. It is used to match pattern but not included in the matching list.  

### 1. Lookahead Positive
Find expression **A** that is followed by expression **B**:  
```bash
A(?=B)
```

### 2. Lookahead Negative 
Find expression **A** that is followed not by expression **B**:  
```bash
A(?!B)
```
### 3. Lookbehind Positive 
Find expression **A** that is preceded by expression **B**:  
```bash
(?<=B)A
```
### 4. Lookbehind Negative 
Find expression **A** that is not preceded by expression **B**:  
```bash
(?<!B)A
```

--------------
--------------

## May 12, 2017

### 1. enable VI mode in gnome-terminal
Open the terminal and run the command:
```bash
set -o vi
```


### 2. Enable VI mode in terminal automatically when terminal starts
Open `bashrc` file that is located in home directory i.e. in `~/.bashrc` and put the above command at the end.

--------------
--------------

## May 08, 2017

### 1. join lines in vim
The lines can be joined using the normal mode command.

```bash
:<start>,<end>j
```

Where,  
**start** : starting line number
**end** : ending line number  
**j** : implies join command

#### Example
```bash
1) Hello there!  
2) I am Nishan.  
3) I am Paradox.  
4) I am nishparadox.  
```

Join line number (2) and (3), the following command is used:  

```bash
:2,3j
```
It results into:

```bash
1) Hello there!  
2) I am Nishan.I am Paradox.  
3) I am nishparadox.  
```

------------
-----------

## April 28, 2017

### 1. spell correction in vim

#### Turn On Spell checking
Just hit the vim command:

```bash
:set spell
```

Once set, it will ask for you confirmation to download the word models. Just hit **yes**.

Once set and downloaded, any incorrect words will be highlighted as you type.

#### List Available Correct Words
Put the cursor over a misspelled word and just hit the following command:

```bash
z=
```

------------
-----------

## April 17, 2017

### 1. Enforce the singleton property with a private constructor or an enum type
A single-element enum type is the best way to implement a singleton.

```java
public enum MySingleton{
    INSTANCE;
}
```

By default, it has implicit constructor. So, it can be written as:
```java
public enum MySingleton{
    INSTANCE;
    private MySingleton(){
        System.out.println("Inside MySingleton constructor");
    }
}
```

So, whenever the enum instance is created here, the same object is reused.

> Since Singleton Pattern is about having a private constructor and calling some method to control the instantiations (like some getInstance), in Enums we already have an implicit private constructor.


------------
-----------

## April 10, 2017

### 1. Get auido file directly from youtube-dl
```bash
youtube-dl -g https://www.youtube.com/watch?v=-qfCrYwdqCA
```

The output consists of two url. The first url consists of isolated video. The second consists of isolated audio.  
So, open the audio link and just download the audio file.

------------
-----------

## March 27, 2017

### 1. Builder Design Patterns
- use builder design pattern when the constructor is very much populated by arguments.
- it becomes tedious for creating new instances of a class if constructor is accepting so much arguments.

#### example

**constructor over population**

```java
public class Burger {
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
public class Burger {
    private size;

    private boolean cheese = false;
    private boolean pepperoni = false;
    private boolean lettuce = false;
    private boolean tomato = false;

    public Burger(BurgerBuilder builder) {
        this.size = builder.size;
        this.cheese = builder.cheese;
        this.pepperoni = builder.pepperoni;
        this.lettuce = builder.lettuce;
        this.tomato = builder.tomato;
    }
}

public class BurgerBuilder {
    public size;

    public boolean cheese = false;
    public boolean pepperoni = false;
    public boolean lettuce = false;
    public boolean tomato = false;

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

------------
-----------

## April 09, 2017

### 1. Partial Function
Partial function from **X** to **Y** is that function in which elements of subset of **X** maps to unique elements of **Y**.  
That is:
**Xs** = subset of X  
Then, partial function from **X** to **Y** is a function from **Xs** to **Y**.  

If **Xs** = **X**, it is a *total function*.

#### example
```python
X = [1, 2, 3]
Y = [a, b, c, d]
Xs = [2, 3]
```

![partial function](http://i.imgur.com/R0Lh7rS.jpg)

------------
-----------

## January 12, 2017

1. **GIT** : use `git reset --hard HEAD~1` to remove unpushed local commit

------------
-----------

## December 14, 2016

1. **VIM** : user `g` followed by `Ctrl-g` in **Visual Mode**  to get the information about selected lines.

------------
-----------

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

## August 28, 2016
1. **VIM** : Use `*` to search the word under the cursor

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

## August 19, 2016
1. In vim, `ctrl-i` or `ctrl-o` jumps to previously/next visited locations.  

2. In vim, pressing `gx` over the line with url opens the url in browser.

-------------------
-------------------
