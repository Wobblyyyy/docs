# Binary
So... you're interested in binary, huh? Well, you've come to the right place.
If you're a fan of half-baked sarcasm, computational theory, entirely useless
information, and maybe cute cats, you've come to the right place - I have all
of those, except for the cute cats. But I do have the sarcasm and the
computational theory. You may be wondering - who am I? Well, I'm none other
than Colin Robertson himself. What are my credentials? I built a 16 bit
computer in Minecraft. Also, I'm a nerd. 

## A foreword
I tend to be rather verbose, so there's a lot of text here. There's a handy
little table of contents provided so you can quickly jump to the sections
of the document you actually care about, and I'd suggest you use that. If
you want to read more about this document, then you can read more about this
document. Otherwise, you can skip the boring parts.

## Description
I'm sure you've seen, at least once in your life, a terminal with hundreds
of 0's and 1's scrolling by, and some hooded figure typing on a keyboard.
This, obviously, is absolutely nothing like how real programming or computers
work. Like, at all. It's not even close. So I'm here to give you a taste
of the real stuff that's going on. This information has taken hundreds of years
of humanity's brightest minds to compile. 

Binary isn't code. It's even more low-level than code. (Low-level is a
potentially confusing term to non-programmers - it means it's more challenging
to understand. You have more flexibiliy (you have more control over how you
control the computer) with binary, but it's... nearly impossible for any
human being to understand.) If you're interested in code, I'd suggest you
pick up a language like Java or JavaScript (or, if you're feeling frisky,
maybe even try C or C++) instead of continuining this tutorial. But if you
want to learn about binary... well, keep on going! I guess... good luck...

## A shameless self-promo
This guide is being published in preparation for a game I'm developing and
will be releasing soon. The game is based on binary and binary logic gates.
This isn't a "fun" or "intense" game like Counter-Strike or Call of Duty.
This is basically an even nerdier version of chess. The idea here is that you
can, using just 1's and 0's build your own computer, or calculator, entirely
from scratch. The premise of the game is a large two-dimensional grid. Each
space on the grid (a "node") can have nothing, a wire, a kind of logic gate,
or some kind of input. If you create the right logic gates in the right order,
you can build a fully functioning... whatever. Because of the sandbox-like
design of the game, what you do is entirely open for you to decide. This has
one unfortunate consequence - if you don't know what you're doing, the game
will be... very boring. 

If you thought tutorials for games were boring, you've seen nothing yet.
Waiting 5 minutes to complete a tutorial before you can play with your friends?
Oh well, that's fine. But having to read an entire document and spend hours
researching number systems, binary math, and logic gates? That's almost as bad
as being forced to listen to Nickleback for more than 45 seconds. 

### More information about my shameless self-promo
Because you obviously want that. By the way, you can totally just skip this
section if you're not interested - I won't be offended.

#### What's it called?
The game is currently unnamed, but for internal development purposes, the game
is called "Daisy". This is absolutely subject to change in the near future,
but all of the code will refer to the game as "Daisy".

#### How's the code being developed?
It took quite a while to determine what language I'd use to write the game.
My top contenders were:
- C++: it's fast, it's well-supported, and there's quite a few game engines
  written in C++.
- JavaScript: it can run on anything with a web browser and it's very easy
  to create a minimum viable product.
- Java: executable JAR files can run on just about any computer built in the
  past decade. Also, modern JVMs are well-optimized, meaniing performance
  shouldn't be too bad.
The most important considerations I had to take into account were portability
and performance. Portability because I use Linux for development and Windows
for gaming, so I'd like to be able to play the game on both. Performance so
it's actually possible to built a working computer. C++ would be the choice
here if performance was the sole consideration, but I'm choosing Java because
it's a better structured language.

As for the game engine I'm using - I originally considered not using a game
engine and custom-coding the rendering myself, but I decided against this
because it would take a long time to do and it wouldn't be very well done.
So, I'm using libGDX - a Java game engine - for the game. The game is 2d and
fairly simple graphically, and libGDX seems to be fairly performant... so,
let's hope everything goes well.

#### Can I contribute? 
Absolutely! I'm pretty big on open-source, so this entire project is going
to be available on GitHub. I will not be accepting any contributions until
I get a stable release out - I have a very specific structure for the code
that I'd like to implement (it's based loosely on shapez.io, but in Java)
and adding more contributors at this stage just makes it harder to stick
to one very specific style. But after I'm done with making the core game,
I'd love to get some help with it! Performance optimizations and graphics
will be the two biggest categories. 

## Just so you're not dissapointed
This is NOT a step-by-step guide on building your own Intel Core i7 from
scratch. This isn't even a tutorial or a guide at all - it's simply a 
compilation of information on binary mathematics, structured so that, if you
read the document in a linear manner and understand all of the concepts
perfectly, you'll know how to build your own computer. I hate to sound like
an elitist, but this shit is hard. You're going to need to carry your own
weight here. You can shoot me a text if you're confused and need help, and
I'll do my best, but I'm not going to hold your hand as you try and figure
out the fundamentals of computational theory. I wrote my first line of code
when I was 7. 11 years later, I'm 18 now, and I still barely understand very
low-level computational theory. It's taken dozens of iterations of Minecraft
computers to get here. 

## One more helpful tip
To really learn and understand, you should try to follow along with the
tutorial here. Look up "logic gate game" and find a game that allows you
to simulate logic gates - before finishing a section, you should be able
to build and explain any of the logic gates that are being used. I believe
"NandGame" is a solid game here, but I could be wrong. Once again, I'm not
going to hold your hand and slow-walk you through this entire process. I'll
give some high-level information, and your job is to interpret the rest.
You're a smart cookie, come on, you got this. Bill Gates will be proud.
(Not really.)

Also, you should find a decimal to binary converter - it will come in
handy at one point or another.

## Legal information
This document, and all of the information contained in it, is provided to
you under the GNU General Public License v3, colliqually the "GPLv3." This
means that you're allowed to copy and redistrubte all of the information
contained in this doucment, so long as you include the following copyright
information.

```
Copyright (c) 2021, Colin Robertson

This file is licensed under the GNU General Public License v3. Redistrubtion
of this file (and any associated files) is permissible, unless applicable law
holds otherwise, so long as this copyright information, and a copy of the
GNU General Public License v3, is included. 

If you did not receive a copy of the license with this file, you may acquire
one online.
```

If you don't understand what any of that means, and if you don't plan on
copy-pasting this information, you can ignore all of this. If you're slightly
interested in what that means, it's an open-source license. I released this
guide with the intention of providing a document that anybody can copy and
change and redistribute, so long as the same open-source license is provided.
This means anyone who improves this doucment has to share their contributions,
so the entire world can see whatever changes and improvements they've made.
I'm not a filthy capitalist!

Ready now? Let's go.

# Number systems
If you've passed 1st grade, there's a pretty good chance you know what numbers
are. Aat the very least, you know what decimal numbers are. A decimal number
could take any of the following forms:
- `10`
- `5.5`
- `0.3`
- `1`

## Low-level functioning of a number system
Every number you've ever seen is made up of digits. Each of these digits has
a unique value, and these values can be compared to one another. For example,
the number 9 is greater than the number 8. There's no reasoning behind this -
we just decided, arbitrarily, that writing a 9 on a paper has a higher numeric
value than writing a number 8.

Let's redefine what a number is really quick: a number is a combination of
digits. The number 10 is a combination of the numbers 1 and 0. The number
22 is a combination of the number 2, twice. The number 44.3 is a floating
point number (you can Google this if you're curious, it would take way too
long to explain what that means) made up of the digits 4, 4, and 3. 

The only important thing you need to take away from this section is the
following. *A number is a combination of digits. A digit is an individual
value. Digits are arbitrary.*

## Decimal numbers
The key here is that the decimal number system you're likely accustomed to is
what's known as "base 10." If you've ever noticed, there are a grand total
of 10 digits - there's 0, 1, 2, 3, 4, 5, 6, 7, 8, and 9. Every number greater
than these digits is comprised of variable combinations of those digits. This
is where the term "base 10" comes from - there's 10 states a digit can be in.
After reading 9, in order to increment the number any further, you need to
restart to a multiple of 10, which is, remember, the base.

## Hexadecimal numbers
These aren't exactly relevant to binary mathematics and especially not 
decimal mathematics, but it's important to have a fundamental understanding 
of how the hexadecimal number system works. Remember how the decimal number
system is base 10? The hexadecimal number system is base 16, meaning more
values can be stored in a smaller amount of digits. 

Here's a quick heads-up: if you're in a bit of a time crunch, you can skip
this section of the document and jump right to the binary numbers section.
I would encourage you not to, because it provides a bit of useful background
for various number systems, but it's up to you.

### Arbitrary digits
Remember how I said digits are arbitrary? They're literally just random
squiggly lines we associate with a value. I could say that the letter F
was a digit. Let's define F. For the sake of simplicity, I'll only be
working with integers here.
- F is greater than 15.
- F is less than 17.
So, using some deductive reasoning here, we can determine that F is
equivalent to the decimal number 16. F isn't just a random letter I'm making
up - it's an actual digit used in the hexadecimal system.

### Hexadecimal notation
This isn't at all relevant to the core concepts being discussed here, but it's
incredibly important, as you'll see this at some point down the line. Hex
numbers are prefixed by a `0x`. If you see a number prefixed by a `0x`, you
know it's a hexadecimal number. Examples:
- `0x000`
- `0xfff`
- `0x11f`

### Digits in the hexadecimal number system
Remember how there's a grand total of 10 digits in the decimal number
system, and how there's a grand total of 16 digits in the hex number system?
We don't have Arabic numerals to represent all 16 of these digits, so the
people who originally came up with the hexadecimal number system had to get
a little bit creative. Here's what they came up with. This is a handy-dandy
little table correlating hex digits to their decimal equivalents.
```
HEX DIGIT | DECIMAL DIGIT
0         | 0
1         | 1
2         | 2
3         | 3
4         | 4
5         | 5
6         | 6
7         | 7
8         | 8
9         | 9
a         | 10
b         | 11
c         | 12
d         | 13
e         | 14
f         | 15
```
As you can see, there are more digits in the hex number system than there
are in the decimal number system, meaning we have to start combining digits
to represent hexadecimal values. 

### Translating between decimal and hexadecimal
I'll explain a more efficient way to determine the hexadecimal equivalent
of a decimal number later on, but for now, here's a relatively simple trick.
Count up. There you go. That's the trick. Start counting at 0, and start
counting up. Keep track of the decimal number you've counted up to, and
translate that into a hex number. After you reach 15 - AFTER you reach 15,
when you're on 16, you need to restart your hex number.

You know how when you're using the decimal number system, after reaching 9,
you go to 10? Likewise, in the hexadecimal number system, after reaching f,
you go to f0. And then f1. And then f2, and so on and so forth. I'm sure
you get the general idea.

## Binary numbers
Okay, here's where it gets interesting. Well, to be entirely honest, it isn't
very interesting, but if you're a complete nerd like me, it is. If you read
the section on hexadecimal numbers, binary numbers will be a piece of cake.
If you didn't, it might be a bit more difficult to pick up on what's going
on here, but I'll try and go slowly.

### Binary notation
Firstly, I'd like to describe the basic way in which binary numbers are
notated. If you read the section on hex, you know that hex numbers are
prefixed with a `0x` when being described in code. Binary numbers aren't
done the same way - they're just a combination of 0's and 1's. This is because
most programming languages (namely C and its subsets, including, but not
limited to, C++ and C#) don't have native support for binary literals like
they do for hex literals. This isn't important. I'll stop rambling.

### Binary digits
As you could probably guess, binary digits are... quite simple. Let's
take a quick look at some descriptions of number systems.
```
DECIMAL      | base 10 (10 total digits, 0-9)
HEXADECIMAL  | base 16 (16 total digits, 0-f)
BINARY       | base 02 (02 total digits, 0-1)
```
Binary digits can only exist in two states. Firstly, 0. Secondly, 1. That's
it. I'll provide a handy translation table, but it probably won't be
all that helpful.
```
BINARY | DECIMAL
0      | 0
1      | 1
```
Rather, it would probably be more helpful to provide a reversed table.
```
DECIMAL | BINARY | HEXADECIMAL
0       | 0000   | 0
1       | 0001   | 1
2       | 0010   | 2
3       | 0011   | 3
4       | 0100   | 4
5       | 0101   | 5
6       | 0110   | 6
7       | 0111   | 7
8       | 1000   | 8
9       | 1001   | 9
10      | 1010   | a
11      | 1011   | b
12      | 1100   | c
13      | 1101   | d
14      | 1110   | e
15      | 1111   | f
```
If you notice, each binary number is a combination of four digits. In the 
computing world, these are known as "bits." Decimal and hexadecimal numbers
have digits, binary numbers have bits. All of those numbers are 4 bit numbers.
If you've ever heard the term 64 bit, this is where that comes from - your
computer processes numbers in 64 bit forms. The maximum decimal value a four
bit binary number can store is 16. The maximum hexadecimal value a four bit
binary number can store is f. As you learn more about binary, you'll start to
get a deeper understanding of what this all means. 

### Converting decimal to binary
This is probably going to sound a little bit complicated, but here's the
process. 
1. Divide the number by 2.
2. Get the integer quotient for the next iteration.
3. Get the remainder for the binary digit.
4. Repeat the steps until the quotient is equal to 0.
Here's yet another table - I'm sure you're going to grow to love tables as
much as I do. Here, we'll be converting the decimal number 13 into a binary
number.
```
DIV BY 2 | QUOTIENT | REMAINDER | BIT #
13/2     | 6        | 1         | 0
6/2      | 3        | 0         | 1
3/2      | 1 (1.5)  | 1         | 2
1/2      | 0        | 1         | 3
```
To explain what "bit number" means, here's - you guessed it - another
table.
```
ABCD = 1010
A = 1 | (bit number 0)
B = 0 | (bit number 1)
C = 1 | (bit number 2)
D = 0 | (bit number 3)
```
If you've ever written any code, you probably know that arrays start at 0.
Likewise, so do binary numbers. The very first number you see in a binary
number (in our ABCD case, the A bit) is known as the 0th bit. The second
number is the first bit. The third is the second, and the fourth is the
third bit. This might sound a little bit confusing right now, but you'll
start to get the hang of it if you stick around for long enough.

# Binary logic
This is the interesting part of the document. Well, it's more interesting
than number systems, but less interesting than what's to come. But it's
really important you understand binary logic before delving any further
into the world of binary computing. Now that we've gone over binary numbers,
we have a solid foundation to start working with binary logic. If you are,
at any point, confused, you have a couple of options.
1. Re-read.
2. Re-read the binary numbers section.
3. Google it.
4. Google a lot of stuff, actually.

## What's a logic gate?
Glad you asked! A logic gate is the very foundation of binary logic. (In the
world of computer science, this is a part of autonoma theory - it's known
as "combinational logic," and it's a subset of finite-state machines.) There
are a few logic gates that do a few different things. The physical
implementation of these logic gates is largely irrelevant to the concepts
behind the logic gates, but that physical implementation is very important
in the world of electronics. Good thing we're not in the world of eletronics.

Formally, a logic gate is defined as follows:
> A logic gate is an idealized model of computation or physical eletronic
> device implementing a boolean function, a logical operation performed on
> one or more binary inputs that produces a single binary output.

All of that is 100% true, but it might be a little confusing if you're not
already familiar with what a logic gate is. So, let's break it down a bit.

> A logic gate is an idealized model of computation or physical
> eletronic device...
This basically means it's a conceptual model, and not something physical, like
a rock. You know what a rock is, and you know it exists. A logic gate, however,
is only as real as something like math is. It's not physically here, but we
know it exists. Does that make sense? 

> ... implementing a boolean function...
A boolean is something that can be in one of two conditions - true or false.
If you've been paying attention, a binary bit can be in one of two conditions
as well - 0 or 1. Let's do some matching!
```
BOOLEAN STATE | BINARY STATE
false         | 0
true          | 1
```
By the way, "boolean" can sometimes be notated as "bool." This is common
in low-level programming languages: C and C++, for example. C# has some
syntatic sugar that allows the primitive "bool" and the object "Boolean" to
be used interchangably, and Java opts to use "boolean." Anyways.

> ... a logical operation performed on one or more binary inputs that
> produces a single binary output.
Alright, we're almost done with the breakdown! Let's go! A logical operation
is an operation that, given the same inputs, always produces the same outputs.
For example, if you're working in the decimal number system and you add the
numbers 2 and 3, you'll get 5 - every single time. Decimal addition is a
logical operation, meaning there's a formal definition for how the operation
works, and it will always produce the same outputs, given the same inputs.

Great, so now we know WHAT a logic gate is. I know you're just DYING to know
all about logic gates, but hold on - there's still one more important
concept I'd like to cover.

## Truth tables
A truth table is a fundamental concept of logical operations. It's another
type of table - I know, you love tables just as much as I do, I know...
Anyways. A truth table can be described as following:

> A table with a variable number of columns, equal to the number of inputs
> (n) plus one, or more simply n+1. Each row describes the result of an
> operation when all n columns are used. The last column of the row
> describes the output for the row's input columns.

Here's a visual example, because that sounds really confusing.
```
Number of inputs: 2
Number of outputs: 1

INPUT COL 1 | INPUT COL 2 | OUTPUT COL

Input columns:
INPUT COL 1
INPUT COL 2

Output columns:
OUTPUT COL
```
See! Not so bad after all. In this example, n is equal to 2. As always, 
there is only a single output. Here's a more concrete example that might
make a little bit more sense.
```
DECIMAL ADDITION TRUTH TABLE

NUM 1 | NUM 2 | RESULT 
0     | 0     | 0
0     | 1     | 1
0     | 2     | 2
0     | 3     | 3
0     | 4     | 4
0     | 5     | 5
0     | 6     | 6
0     | 7     | 7
0     | 8     | 8
0     | 9     | 9
1     | 1     | 2
1     | 2     | 3
1     | 3     | 4
... continued
```
For the sake of time, I'm not going to continue with the table - I'm
sure you're starting to get the point. Importantly, we know the following.
For the operation (DECIMAL ADDITION), given two inputs (NUM 1 and NUM 2),
we can determine a single output (RESULT) according to a set of logical
rules that we follow.

## All about logic gates!
Yay! We're finally here. There are quite a few logic gates. I'm going to
name & describe each of them here, and will then go more in-depth on how
the logic gate actually functions.
```
NAME  | ALIAS 
OR    | or
AND   | and
XOR   | exclusive or
NOT   | NOT (this is a special case!)
NOR   | inverse or
NAND  | inverse and
XNOR  | exclusive inverse or
```
For each logic gate, I'll do my best to describe how the logic gate
functions, and will provide a truth table for the logic gate.

### Logic gate: OR
The OR logic gate is one of the most commonly used logic gates, and for
good reason. In short, if either of the two inputs are true, the output
will also be true.
```
INPUT 1 | INPUT 2 | OUTPUT
false   | false   | false
true    | false   | true
false   | true    | true
true    | true    | true
```

### Logic gate: AND
The AND logic gate is the MOST common logic gate. This will return true
only if both of the inputs are true.
```
INPUT 1 | INPUT 2 | OUTPUT
false   | false   | false
true    | false   | false 
false   | true    | false
true    | true    | true
```

### Logic gate: XOR
The XOR logic gate (also known as "exclusive OR") is another frequently
used logic gate, particularly useful in ripple-carry adding machines. If
either of the inputs are true, the output will be true, UNLESS both of the
inputs are true. In other words, the XOR gate will output true if exactly
one of the inputs are true - 0 and 2 true inputs means a false output.
```
INPUT 1 | INPUT 2 | OUTPUT
false   | false   | false
true    | false   | true
false   | true    | true
true    | true    | false
```

### Logic gate: NOT, NOR, NAND, and XNOR
The NOT logic gate is really simple. It's a special case for one reason -
it only has one input. Without further ado, here's the truth table.
```
INPUT | OUTPUT
true  | false
false | true
```
As you can see, it literally just inverts whatever input it's given. Now that
we know what a NOT logic gate is, let's talk about the remaining gates.
- NOR is the logical compliment to OR.
- NAND is the logical compliment to AND.
- XNOR is the logical compliment to XOR.
A logical complement is a fancy word for saying "opposite of." Here's yet
another table to break it down even further.
```
NOR  | OR + NOT
NAND | AND + NOT
XNOR | XOR + NOT
```
To put it really simply, NOR, NAND, and XNOR do exactly the same as their
counterparts, except the output is reversed. For example:
```
XOR GATE
INPUT 1 | INPUT 2 | OUTPUT
false   | false   | false
true    | false   | true
false   | true    | true
true    | true    | false

XNOR GATE
INPUT 1 | INPUT 2 | OUTPUT
false   | false   | true 
true    | false   | false 
false   | true    | false 
true    | true    | true
```

## Logic gates, in combination
A logic gate on its own isn't anything special. Your computer has millions -
billions, even, of these tiny little logic gates engrained in its processor.
By the way - if you're even a little bit confused about logic gates, you
should go do some research - they're really important.

Another important concept here is this: binary numbers and decimal numbers
are exactly the same, just stored in a different form. 1101 has the same exact 
value as 13, they're just expressed in a different form. Because combinations
of logic gates can get incredibly advanced - like I said, your computer is
just a combination of logic gates - they're going to get a big section.

# Getting started with combined logic gates
There's a LOT of stuff you can do with logic gates. We're going to start with
the most simple thing you can do - addition. Please keep a couple of things
in mind here - binary and decimal numbers are the same. If you need to convert
between the two, you can just Google the conversion. 

## Binary addition
There's a couple of ways to perform binary addition. We're going to focus on
the most simple way, known as "ripple-carry addition." Please note that this
method is NOT used in real-life, as it can be very slow. However, it's very
useful in explaining the concepts at play here.

### Half adder
Formally defined as follows:
> A half adder is a combinational logic circuit which is designed by
> connecting one XOR gate and one AND gate. The half adder circuit has
> two inputs: A, and B, which add two input digits and generates two outputs:
> a carry, and a sum.

Notice that the half-adder DOES NOT produce a single output, meaning it isn't
a logic gate - it's a combinational logic gate. Now, to describe what
all of that stuff actually means.
```
A INPUT
One of two binary bits (either true/false) that's provided as an input.

B INPUT
One of two binary bits (either true/false) that's provided as an input.

SUM OUTPUT
The sum of the two provided binary bits. 

CARRY OUTPUT
If the sum of the two binary bits can't be expressed with one number, the
carry output will store the other output.
```
We need to cover another very important concept breifly - how does binary
addition even work? Well, I'll tell you how it works, and I'll use decimal
numbers to make it even easier.

First, recall that the binary state 0 is equal to the decimal number 0, and
the binary state 1 is equal to the decimal number 1. So, if you add two
numbers in the decimal number system... what happens?
```
NUM 1 | NUM 2 | SUM
0     | 0     | 0
1     | 0     | 1
1     | 1     | 2
```
That's great, but a half adder accepts BINARY inputs, not decimal inputs.
Let's add another column to our table.
```
NUM 1 | NUM 2 | DECIMAL | BINARY
0     | 0     | 0       | 0
1     | 0     | 1       | 1
1     | 1     | 2       | 10
```
Ahh! Look! Binary bits only have TWO states, meaning the number 2 cannot
be expressed with only a single binary bit. So we need two outputs,
because, in theory, we can have a number that requires two outputs to
be properly displayed.

Here we get to the fun part - a half adder truth table!
```
IN 1 | IN 2 | SUM   | CARRY OUTPUT
0    | 0    | 0     | 0
1    | 0    | 1     | 0
0    | 1    | 1     | 0
1    | 1    | 0     | 1
```
A half adder on its own isn't anything very special - you can't do much with
a single half adder. That's why we need another type of combinational logic
circut - a full adder.

#### Well... how the hell does a half adder work?
Glad you asked. It's pretty simple, actually - there's two logic gates - a
XOR gate, and an AND gate. These two gates correspond to two outputs. First,
there's the SUM output - this is the XOR gate. Next, there's the CARRY output.
This one is the AND gate. It really is that simple.

Just to jog your memory:
- A XOR gate outputs TRUE if exactly ONE of the inputs are TRUE. If both of
  the inputs, or if none of the inputs, are true, the gate outputs FALSE.
- An AND gate outputs TRUE only if BOTH of the inputs are TRUE. If either of
  the inputs, or if both of the inputs, are false, the gate outputs FALSE.

### Full adder
The most simple definition of a full adder is the combination of two half
adders. A more complex definition is as follows:
> A full adder adds three one-bit binary numbers, two operands and a carry
> bit. The adder outputs two numbers, a sum and a carry bit. The term is
> contrasted with a half adder, which adds two binary digits.

That's right - there's THREE inputs. Three is an ugly number, but don't worry.
You only have to worry about TWO of the inputs - the third input (the carry
bit) is handled by other full adders that are linked up with this one.
Because you already understand the idea behind a half adder, we'll skip
right to the truth table. Because there's three inputs, we need five columns
instead of the four needed for a half adder.
```
CARRY IN | IN 1 | IN 2 | SUM OUT | CARRY OUT |
0        | 0    | 0    | 0       | 0         | *
0        | 1    | 0    | 1       | 0         | *
0        | 0    | 1    | 1       | 0         | *
0        | 1    | 1    | 0       | 1         | *
1        | 0    | 0    | 1       | 0         | 
1        | 1    | 0    | 0       | 1         | 
1        | 0    | 1    | 0       | 1         | 
1        | 1    | 1    | 1       | 1         | 
```
The rows marked with an asterik are exactly the same as the truth table from
a half adder - if the carry in value is 0, it functions identically. If
the carry in value ISN'T the same, however, things start to change. Let's
go back to more decimal addition, but this time, we're going to use three
numbers. Also, for the sake of time, I'll include the binary representations
here - there won't be another table for that.
```
IN 1 | IN 2 | IN 3 | DECIMAL | BINARY |
0    | 0    | 0    | 0       | 00     | no input
1    | 0    | 0    | 1       | 01     | carry in is on
0    | 1    | 0    | 1       | 01     | one of the inputs is on
0    | 0    | 1    | 1       | 01     | one of the inputs is on
1    | 1    | 0    | 2       | 10     | one of the inputs + the carry in is on
1    | 0    | 1    | 2       | 10     | one of the inputs + the carry in is on
0    | 1    | 1    | 2       | 10     | both of the inputs are on
1    | 1    | 1    | 3       | 11     | both inputs and the carry in are all on
```
You're probably wondering - literally why would anybody ever care about a
full adder? A calculator can do so much more than that. That's true, but a
calculator needs an adder to add. 

A full adder adds two numbers together. This is pretty important to know.
Unfortunately, binary numbers only have two states - on and off, meaning a 
single full adder can, at the most, add two 1's, resulting in an output of 2.
With the carry input, a full adder can output a value of `11`, or three.

### Ripple carry addition
Ripple carry addition is the most simple form of binary addition. Please note
that it's not used in real-world computers anymore, because it's relatively
slow and requires each bit to be calculated sequentially. I'm using ripple
carry addition here because it's easy to understand and I'm assuming you're
not going to build the next Intel Core i7, so speed isn't that much of a
priority. I could be wrong, but oh well.

Ripple carry addition can best be explained as a chain of full adders. The
carry output from one adder is the carry input for the next adder. You continue
repeating this pattern. If you have four full adders, you have a 4 bit ripple
carry adder. If you have eight full adders, you have an 8 bit ripple carry
adder - I'm sure you get the point.

Another concept that many people find confusing is how the bits are layed out.
Here's a simple diagram. Hopefully simple.
```
IN 1A -> OUT 1
IN 1B ->

IN 2A -> OUT 2
IN 2B ->

IN 3A -> OUT 3
IN 3B ->

IN 4A -> OUT 4
IN 4B ->
```
Notice how there's a total of eight inputs - an A and B input for each of
the adders. This adding machine can add two four bit numbers. A four bit
number has a minimum value of 0000 and a maximum value of 1111 (0 and 15
in decimal, respectively).

Let's say you want to add the following two numbers:
- `0101` (decimal equivalent: 4) ("number 1")
- `0111` (decimal equivalent: 7) ("number 2")
In total, there are EIGHT digits - four digits in number 1, and four digits
in number 2. If you notice, our adding machine accepts 8 inputs. Let's call
number 1 "number A" and number 2 "number B". The four digits of number 1
would be inserted into:
- in 1 a
- in 2 a
- in 3 a
- in 4 a
... and the four digits of number 2 would be inserted into:
- in 1 b
- in 2 b
- in 3 b
- in 4 b
Make sense? Hopefully. If you don't get what's going on, you should really
go look up a better diagram - it's kind of hard to express this concept
effectively simply through text. And of course, a 4 bit adder has 4 bits of
output. These 4 bits of output will account for every combination of inputs
EXCEPT for `1111` and `1111`, as the sum (`10000`) is five bits, and... well,
we don't have five bits. In this case, the last carry output in our adder
would be turned on, and every other output bit would be turned off.

Real-life adding machines aren't four bits - I'm assuming the device you're
viewing this on has a 64 bit CPU, meaning it has a 64 bit ALU (the part of the
CPU that handles all of the math) and thus a 64 bit adder. A 4 bit adder can
handle decimal numbers as 2^4. A 64 bit adder? 2^64. In case you couldn't
tell, that's a pretty big number.

#### A (very bad) diagram
It's pretty hard to create a good diagram using only a bunch of text, but
that sure won't stop me from trying.
```
FULL ADDER

cin ->|=|
in1 ->|*|-> sum
in2 ->|=|-> cout

cin = carry input
in1 = input 1
in2 = input 2
sum = sum output
cout = carry output

CHAINED FULL ADDER

cin ->|=|
in1 ->|*|-> sum
in2 ->|=|-------v
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-> cout
```
As you can see, in the case of the chained full adder, the second adder's
carry input is the first adder's carry output. You repeat this many, many
times and you can get an adder of whatever size you'd like! Let's make 
an 8 bit adder for fun.
```
      |=|
in1 ->|*|-> sum
in2 ->|=|-------v  (adder 1)
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-------v  (adder 2)
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-------v  (adder 3)
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-------v  (adder 4)
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-------v  (adder 5)
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-------v  (adder 6)
v---------------|
----->|=|
in1 ->|*|-> sum 
in2 ->|=|-------v  (adder 7)
v---------------|
----->|=|
in1 ->|*|-> sum
in2 ->|=|-----------> carry output  (adder 8)
```
As you can (probably, hopefully) see the first adder's carry input... isn't
there. This is because it's not needed - there's no adder that comes before
it, so we don't need to have any carry input. This carry input will be useful
for subtraction, but that's a topic for later.

## Storing information with bytes
So. You've figured out how an adder works - you can add two numbers. But...
then what? What do you do with the numbers? One of the most important features
of a modern computer is its ability to store and remember information. That's
why you don't have to enter your password every time you log into the same
website, or why you can save a file locally and load it back later. There's
two ways information can be stored on a computer:
- Using magic
- Using bytes
Magic, although rather cool, isn't very practical here, so we'll look at the
other method - bytes. 

You've heard of the term "bit" now - it's a single on/off or true/false or
0/1 piece of information. But what's a byte? A byte is a combination of 8
bits - that's any combination of 0's and 1's that requires 8 bits to express.

### Byte diagram
Here's (another) lovely diagram.
```
0 1 2 3 4 5 6 7 (bit addresses, starting at 0)
A B C D E F G G (bit labels, starting with A)
```
Note that bit labels aren't actually a real thing used in the real world,
I'm just using them for the sake of simplicity. 

### What can you put in a byte?
A lot of stuff. You can store pictures of cats, text messages from a loved
one, pictures of a loved one (god I miss her) or even your homework! But
obviously, a picture isn't just a number. And a text messsage isn't a number
either, so how are both of those stored? There's a lot of high-level stuff
going on here to convert an image into a sequence of 0's and 1's, and it would
take me... quite a long time to explain all of that. So, for the sake of saving
time (and my sanity) we'll go over a simpler topic - how numbers are stored
in binary.

So, we know that the maximum value of a sequence of binary numbers is equal
to 2 to the power of how many bits there are minus one. Examples:
```
1 bit  : 2^1 = 2, 2-1 = 1
2 bits : 2^2 = 4, 4-3 = 3
3 bits : 2^3 = 8, 8-1 = 7
4 bits : 2^4 = 16, 16-1 = 15
...
8 bits (1 byte) : 2^8 = 256, 256-1 = 255
```
So a byte can store any value between 0 and 255. In total, that's 256 unique
combinations of bits that represent a decimal number. (0 is considered to be
a state - the highest value a byte can represent is 255)

### What else can you put in a byte?
Like I said earlier, just about anything. You just have to figure out a way
to encode and decode whatever you want to save into 1's and 0's. Numbers are
pretty easy to do - positive integers, at least. Signed integers and floating
point numbers are a topic of their own. If you're interested in learning
about floating point numbers, look up "IEEE 754." I will warn you now - it's
a lot of information to absorb. Anyways. You can encode text into binary too -
how do you think you're reading this document right now? There are a couple
of different standards for encoding text into binary, but the most simple (and
one of the most common) is UTF-8, which has a grand total of 256 characters.
Why 256 characters? Because UTF-8 uses 8 bits, and 8 bits can store up to
256 unique values.

The specific implementation and translation of letters into numbers isn't
exactly relevant to the theory behind storing information, but in short,
every character is assigned a unique character code. These character codes
are all made up, but here's an example.
```
H = 1
E = 2
L = 3
O = 4
W = 5
R = 6
D = 7
  = 8 (that's a space)
, = 9 (that's a comma)

"HELLO, WORLD" could be expressed as follows:
1 2 3 3 4 9 8 5 4 6 3 7
```
There's a reason all of those letters are uppercase - uppercase and lowercase
letters have different character codes. I won't delve further into the topic,
but if you're interested in unicode, you can look up "unicode" and do some
independent research.

## Alright - we know what bytes are, but how do you store them?
Good thing you asked. Physically, there's a couple of different ways to store
information. I'm not very good with electronics, so I'm going to skip that
part. Conceptually, however, there's one very simple concept. Or two, actually.
But you get the point.
- RAM (Random Access Memory)
- Storage
Let's start with RAM, because it's the simpler of the two.

### Random Access Memory
Alright. So let's pretend we have a magical device used for storing
information. This device has two features:
- We can write information to the device, and it will remember the state.
- We can read information from the device, and it'll output whatever the last
  state you wrote to it was.
This is how RAM works in real life. Your computer likely has several billion
bytes of RAM, whereas the conceptual computers we're talking about here will
likely have around 64-128 bytes. Yes, bytes - not kilobytes, but bytes.

Each byte of RAM has an address. Modern computers handle RAM differently than
we will here, but modern computers have many more resources available and are
much more efficient. In our case, each byte of RAM has a 2-byte address.
There's 256 possible combinations for a single byte, meaning if we were to use
a single byte address, we could have up to 256 bytes of RAM. We're going to
use a 2-byte address system, so we can have to 65,536 bytes of RAM. There is
absolutely no chance we'll ever use that much, but there's no harm in having
support for it. The idea here is as follows:
- Each byte of ram has a 2-byte address.
- The first of the two bytes is the "X" position of the RAM.
- The second of the two bytes is the "Y" position of the RAM.
X and Y values can both range from 0-255, respectively. 

Just as a note: we'll use hexadecimal to represent RAM addresses. This is an
incredibly common process with real computers. If you've ever read an error
message, you may have seen something like:
```
Segmentation fault at 0xbbbbbbbb
```
That's a memory address. Remember how I said two hexadecimal digits can
represent a whole byte? Yeah. That's true. Take a look:
```
BINARY    | DECIMAL | HEXADECIMAL
0000 0000 | 0       | 0
1111 1111 | 255     | ff
```
Great! So now we know how RAM can be addressed. But what's next? Of course,
we need a way to read and write to the RAM. Later on, we'll learn about
"opcodes" and instruction sets, but for now we'll stick to the basics.

#### Writing a byte to RAM
Okay. So. We have a magical machine that accepts three inputs:
- A X coordinate.
- A Y coordinate.
- A byte of information to store.
If we feed the machine the following input:
```
X: 0x00
Y: 0x00
Input: 0000 0000
```
It will store the input (0000 0000) at the address (0x00, 0x00). We could
do something similiar, look:
```
X: 0xff
Y: 0xff
Input: 1111 0000
```
That will store the input (1111 0000) at the address (0xff, 0xff). We can use
any X and Y values between (inclusive) 0x00 and 0xff, and our input can be
any byte value between (inclusive) 00000000 and 11111111. The information
gets stored, and now it can be accessed.

#### Reading from RAM
So. We stored the information. But how can we read it? We'll need another
magical machine, and this machine will accept two inputs and provide a
single output.
- A X coordinate input.
- A Y coordinate input.
- A one-byte output.

Let's give our machine the following inputs and see what it has to say.
```
X: 0xff
Y: 0xff
```
Hey! Look! That's the same address that we just wrote some information to!
Let's see what output we get.
```
1111 0000
```
Woah! Look at that! That's the information we just wrote! Let's try another.
```
X: 0xfa
Y: 0xb3
```
That's an address we haven't seen before. So... what's the output?
```
0000 0000
```
Yep. A completely empty byte. That's because the default state of RAM is
0000 0000 - if there's no information written, that's the information that's
being stored.

### RAM in application
Alright. Say we have an 8-bit adding machine. There's a couple of operations
our adding machine supports. Take a look:
- Adding two 8-bit numbers together.
- Saving up to three unique 8-bit numbers.
- You can "remember" one of the saved 8-bit numbers and use that number as an
  input (one of the numbers that's being added).
You may be wondering - how exactly do you do that? I'll tell you how you do
it. It's not all that hard, to be honest.

For the sake of simplicity, we're going to assume we still have a magical RAM
device that can store and remember 256^2 bytes of information. Later on,
we'll learn how to actually implement something like this, but just for the
purpose of demonstration, let's pretend it exists, and it works.

If we know that we have three pieces of information that we want to store, and
we won't ever have to use any more pieces of information, we can use static
memory addresses to remember these. This doesn't work as soon as we need to
dynamically assign memory addresses, but it will do for now. So, let's assign
these memory addresses as follows.
```
N1: 0x00 0x00
N2: 0x00 0x01
N3: 0x00 0x02
```
Also, for the sake of simplicity, we can express these numbers in a more
compact form:
```
N1: 0x0000
N2: 0x0001
N3: 0x0002
```
Remember that one hexadecimal digit represents one binary word (4 binary bits)
and thus, two hexadecimal digits represents a binary byte. By extension, four
hexadecimal digits represents two bytes, so we still have a two byte address.

Let's say our imaginary user has a couple of inputs. 
- They can enter up to 2 8-bit binary numbers.
- The sum will automatically be calculated after the number has been entered.
- There's a button you can press to save to memory address 1 (0x0000).
- There's two more buttons to save to 0x0001 and 0x0002.
- There's a total of 6 buttons to read information from memory.
- There's 2 buttons for address 0x0000 - one of the buttons will read that
  value and insert it as the user's first number, and the other of the buttons
  will read that value and insert it as the user's second number.
- Addresses 0x0001 and 0x0002 also have two buttons each. 
So, in theory, we can save up to three binary numbers and add them to
eachother. This is great! Right? Yeah. We're at the level of a rudimentary
calculator you can purchase on Amazon for about a dollar. But that's alright -
remember, we're just getting started, and this is a topic humans have been
studying for decades now. 

### Going further - re-using RAM
So. We have our three bytes of memory, right? Each of these bytes can store
a value from 0 to 255 (0x00 to 0xff). In theory, we can add an infinite number
of numbers now, here's the process:
- Add two numbers.
- Save the result of the two numbers.
- Use one of those results as an input.
- Enter another number.
- Add the two numbers (one from memory, one from input).
- Save the two numbers and repeat.
Makes sense? Now, I say an infinite amount of numbers because, in theory, you
can add an infinite number of 0x00's without exceeding the maximum possible
8-bit value (1111 1111). In practice, we can only add a limited amount of
numbers, and the sum of all of these numbers must be equal to or less than
the decimal number 255.

What happens if we try and go above 255?
```
NUMBER 1: 1111 1111 (0xff)
NUMBER 2: 0000 0001 (0x01)
```
Remember how our ripple carry adder works? If we add a 1 to that number,
it'll cause all of the digits to have a carry output, meaning our sum output
is simply 0000 0000. We do, however, get a 9-bit number: 256 (0x100). This
is because our carry output is active - all of the numbers carried, causing
an overflow of some sorts - our adding machine can't support numbers as large
as that. 

Let's assume we're not planning on going above 255. We're good, right?
Of course. Theoreticlly, we would be able to construct a machine that can
automatically add numbers for us. For example, let's say we have a list of
numbers we want to add together. 
```
0000 0000 A
0000 1000 B
0000 1100 C
0010 0000 D
0011 1001 E
0100 0000 F
```
Each of the binary numbers has a letter assigned to it so we can reference
them more easily. Normally, the process we'd have to go through is:
- Add A to B, resulting in S1. (sum 1)
- Save S1 to memory.
- Recall S1 from memory, and add S1 to C, resulting in S2.
- Save and recall S2, then add it to D, resulting in S3.
- Save/recall S3, add it to E, resulting in S4.
- Save/recall S4, add it to F, resulting in S5, which is our final output.
You could also use multiple adding machines to optimize the runtime of our
calculation. If we have three adding machines, we can add up to 6 8-bit
numbers at once, outputting 3 8-bit numbers, which is better than 2 and 1.
- On adder 1, add A and B, resulting in AB.
- On adder 2, add C and D, resulting in CD.
- On adder 3, add E and F, resulting in EF.
- Save adder 3's output (EF) to memory.
- On adder 3, add AB and CD, resulting in ABCD.
- Recall EF from memory, and add it to ABCD, resulting in ABCDEF. This
  is our sum - we've finished the calculation.

This probably sounds really boring, but I promise it's about to get super
important.

# Designing our first CPU
It's not gonna be the next i7, or the next Ryzen 9, or the next... well, it's
not gonna be much at all, but we're about to design our very first 8-bit
processor. Note that this is just a conceptual overview of the processor -
this doesn't actually explain to implement the processor. In order to create
a CPU, however, we're going to need to know about all of the parts of a CPU.
- ALU (Arithmetic Logic Unit): this component is responsible for performing
  mathematical and logical operations. For example, the adder we just 
  conceptualized would fit into this category. 
- Instruction register and instruction pointer: these two parts of the CPU
  work in tandem to manage the current state of the processor. This pointer
  is generally an integer representing a value (often between 0x0000 and
  0xffff) that "points" to a specific byte of memory. 
- Processor clock: a rather boring part of the CPU, but it's pretty vital
  to the workings of a modern computer. The CPU clock tells the rest of the
  computer when to update and when to perform certain operations.
- RAM access system: of course, we need to be able to store information in the
  random access memory we were using earlier. There has to be some way for
  the CPU to do this.
- CPU registers: basically RAM on crack, CPU registers are the lowest-level
  memory available. These are only used by the CPU when performing an
  operation. For example, let's say you're adding several numbers, and you
  need to keep track of the numbers. Instead of storing the numbers in RAM,
  which can have (comparatively) long read/write times, we'd store that
  information in a CPU register, which is immediately available to the CPU.
Alright, so now that we've gotten that out of the way. What's next? How do we
actually design a processor? Here's a list of specifications we want the CPU
to have. These are entirely arbitrary and I'm just making them up right now.
- 8-bit. Working with 8 bits means the numbers are relatively managable, but
  it does provide some pretty severe limitations to functionality. 16-bit is
  practically the bare minimum to create a user-operable computer. 
- A register with a maximum of 256 bytes of memory. In practice, we probably
  won't ever use this much register space. But to keep things simple, we're
  going to declare the minimum addressable size as a byte. This means that,
  in order to point to a place in the register, the register's address will
  be exactly one byte - no more, no less.
- A RAM read and write system with two-byte addresses. Yes, that's a lot of
  addresses - over 65,000 in fact - but there's no harm in having more than 
  we need, right?
- Our ALU will also be 8-bit. Once again, this is severely limiting and
  cripples the system from a usability standpoint. You'll be able to understand
  your system, but that's because you built the whole thing from scratch.
  Anybody without a solid understanding of computer science will be completely
  and utterly lost trying to use your system for anything more advanced than
  adding two numbers together.
Now that we've worked all of that out, let's get on to the fun part. It's not
actually very fun, but... it's fun for me! Almost...

## Opcodes - the language of your CPU
The term "opcode" comes from a combination of the words "operation" and
"code." Basically, it's an operation that your CPU can perform. What's an
operation, you may ask? Well, your CPU could copy one byte of memory from
one location to another. Or your CPU could add two numbers. Or your CPU
could do a backflip - except I'm just kidding about that last one, as most
computers are, unfortunately, inanimate. Unlucky!

Because we have an 8-bit processor (and also because we don't need any more)
we're going to use 8-bit (or 1 byte) opcodes. If you've been following along
closely, you know that 1 byte can store 256 unique values. That means there
are 256 unique opcodes, and that means there are 256 unique operations our
computer will be able to perform for us.

We haven't finished our CPU's ALU yet - we still need to add things like
multiplication, division, subtraction, and number comparison. Not only that,
but we don't have floating point numbers yet - something we'll have to add
later down the line. We'll keep things simple for now.

### What defines an opcode?
Whatever you want to define an opcode, to be honest. There are certain
standards that real-world computers use, but it doesn't exactly matter what
your opcodes are, so long as your computer works.

### Picking some generic opcodes
Once again - we have not finished our CPU yet. There are still missing parts
to it, so this won't be a complete list of opcodes. Some abbreviations will
be used to comply with 80-character line limits, so I hope you understand.

These opcodes will be notated in hexadecimal for brevity and clarity. Our
computer will process them in binary form, but hexadecimal makes it a bit
easier to understand and read. 

And as a final note before we get to the opcodes, this is not code. Or at
least code as we know it. At some point down the line, we'll be able to make
an assembly language and write code in actual text instead of just 1's and
0's, but for now, we have to stick to machine language.
```
OPCODE | OPERATION
0x00   | NOP (no operation, do nothing)
0x01   | Write a byte to a specific register (address, byte)
0x02   | Write a byte to memory (address, byte)
0x03   | Push a byte to the stack (byte)
0x04   | Push a byte from the register to the stack (register address)
0x05   | Pop a byte from the stack to a register (register addr)
0x06   | 
0x07   | 
0x08   |
0x09   |
0x0a   | Jump to a specific instruction (instruction address (1 byte))
0x0b   | Copy a byte from a register to memory (register addr, memory addr)
0x0c   | Copy a byte from memory to a register (memory addr, register addr)
0x0d   | Copy a byte from a register to a register (reg 1 addr, reg 2 addr)
0x0e   | Copy a byte from memory to memory (memory 1 addr, memory 2 addr)
0x0f   | Add two bytes together. This opcode functions by getting the value
       | of the byte at the provided register address, getting the value on
	   | top of the stack, adding those two values together, and pushing the
	   | sum onto the stack (register addr)
```
If you've ever written code in an assembly language, you'll recognize some
of those instructions - MOV, for example. If you haven't, you won't, but that
doesn't really matter.

If you've ever written code in a high-level language, such as C, Java, C#,
Python, or JavaScript, you'll notice something weird. There are no variables.
And there's no way to read data. Why is that? How do you do anything if you
can't even read the data you're storing? 

Fear not! We don't need to read data. Actually, reading data makes operating
the CPU significantly more complicated. We only ever WRITE data here. Read
operations are performed, but not by us - the CPU handles those for us.

### The VGA buffer
Here's another new concept - the VGA buffer. This was introduced by IBM
as part of the VGA standard for their computers. Basically, it maps part of
memory to the screen. IBM mapped 0xb8000 to text on the screen - any info
you stored at that address and onwards, would be displayed on the screen as
text on an 80 char wide and 25 char high terminal screen. Have you ever
turned your computer on and gotten some scary-looking black and white text?
That's probably making use of the VGA buffer. It's the simplest way to
output information.

### Our own VGA buffer
We don't have access to memory address 0xb8000. In decimal, that's
address number 753,664. Even with a two-byte addressing system, we only have
65,536 address spaces available. So, we can't use the VGA standard, and,
instead, we'll have to come up with our own. Let's figure out where to map it
in memory, shall we? 

Remember, we have 256 bytes of memory available, total. Assuming each character
occupies one byte (in our case, they will) that means you can display a max
of 256 characters, but that means we don't have any memory available. Because
we're still operating at such a low level, that's alright - we can store any
runtime variables in our 256-bit register. But just for the sake of having
some memory left over, we'll reserve 128 bytes of memory for our own usage,
and we'll use 128 bytes of memory for the VGA buffer.

Memory addresses begin at zero - the first addressable piece of memory is
addressed as 0x00. Once again, the maximum addressable piece of memory is 0xff.
```
HEX  | DECIMAL
0x00 | 0
0xff | 255
```
What's right in between those two addresses? In decimal, that's 127. In 
hexadecimal, that's 0x8f. So that's where we're going to map our "VGA buffer."

You may have noticed that the VGA buffer is 80x25. Assuming each of the
characters on the screen takes up exactly 1 byte, that's 2,000 bytes dedicated
just to text. IBM's VGA buffer goes further - they have support for multiple
colors, meaning it uses even more than 2,000 bytes. That can be done later,
but for now, we're only going to have 128 bytes available for our text buffer
purposes. We clearly can't do 80x25, so let's do... how about we do 32x4?
It's certainly not as useful as 80x25, but it's something, and something is
much better than nothing.

### Writing to our own VGA buffer (and our character codes)
So. How do we write to our VGA buffer? Well, the obvious answer is to execute
an operation like this:
```
0x02 0x8f 0x11

BREAKDOWN:
0x02 | The instruction/opcode we want to execute (write a byte to memory)
0x8f | The address we'd like to write to (this is our VGA buffer)
0x11 | The value we'd like to write (who knows what this is)
```
Why am I saying "who knows what this is?" Because, really, who knows what
that is. Not me. Not you. Not anybody, actually. And that's because we haven't
defined any character codes yet, so we're going to have to do that. There
are already existing standards, such as UTF-8, but there's no purpose in
implementing such a standard when we'll only make use of a fraction of it.
So let's create our own character codes. Remember, we have 256 total available
character codes.
```
CODE | VALUE            | DECIMAL
0x00 | ' ' (whitespace) | 0
0x01 | 'a'              | 1
0x02 | 'b'              | 2
0x03 | 'c'              | 3
0x04 | 'd'              | 4
0x05 | 'e'              | 5
0x06 | 'f'              | 6
0x07 | 'g'              | 7
0x08 | 'h'              | 8
0x09 | 'i'              | 9
0x0a | 'j'              | 10
0x0b | 'k'              | 11
0x0c | 'l'              | 12
0x0d | 'm'              | 13
0x0e | 'n'              | 14
0x0f | 'o'              | 15
0x10 | 'p'              | 16
0x11 | 'q'              | 17
0x12 | 'r'              | 18
0x13 | 's'              | 19
0x14 | 't'              | 20
0x15 | 'u'              | 21
0x16 | 'v'              | 22
0x17 | 'w'              | 23
0x18 | 'x'              | 24
0x19 | 'y'              | 25
0x1a | 'z'              | 26
```
Alright! So we've got all twenty-six lowercase letters and a way to add
whitespace. That's great! Obviously, we're missing A LOT of characters -
uppercase characters, numbers, symbols, etc. But for now, these 26 letters
should be enough to write SOMETHING.

### Displaying some text
How do you display text, you may ask? Well, we can display a character by
providing an address in the buffer and a byte value to store there. So
logically, we can display text by doing that several times for several
characters. Here's the general idea. I'll explain later.
```
0x02 0x8f 0x08 | 'h'
0x02 0x90 0x05 | 'e'
0x02 0x91 0x0c | 'l'
0x02 0x92 0x0c | 'l'
0x02 0x93 0x0f | 'o'
0x02 0x94 0x00 | ' '
0x02 0x95 0x17 | 'w'
0x02 0x96 0x0f | 'o'
0x02 0x97 0x12 | 'r'
0x02 0x98 0x0c | 'l'
0x02 0x99 0x04 | 'd'
```

#### Disclaimer on displaying text
Your processor needs to have a way to actually display the text! This process
is NOT included in this guide, because this guide is only designed to cover
the conceptual model behind computing, not the specific implemenetation of
such a model. In other words - everything I'm saying here IS true, but only
if you make a display capable of receiving inputs and displaying characters
like we're doing here. 

#### How did we just display any text?
Look at all of the hexadecimal values we used to display the string "hello
world". That's quite a few, no? Here's the break-down.
```
Every line has THREE components:
INSTRUCTION | OPERAND 1 | OPERAND 2

In the case of the letter 'h', these components have the following values:
INSTRUCTION - 0x02
OPERAND 1   - 0x8f
OPERAND 2   - 0x08

0x02 refers to the WRITE TO MEMORY opcode our processor has.
OPERAND 1 (0x0f) refers to the memory address we'd like to write to.
OPERAND 2 (0x08) refers to the byte value we'd like to write.
```
Because we're using memory mapping, we just need to write these values to
memory in order for them to be displayed. Magic, right?

## Instruction processing
So, we have the math part of our CPU down. But how can we actually get the CPU
to do what we want it to? Every CPU has to be able to read instructions and
execute those instructions. In practice, this can be rather challenging to
implement, but because we're working in the land of imagination, we can make
this very simple.

There's a great long array of instructions. Just for fun, let's look
at some Java code that displays what I mean.
```java
public class Instructions {
	public static final int[] instructions = new int[255];
}
```
There's 255 addresses of instructions. But remember - opcodes aren't all one
byte instructions, some of them can require two, or even three, bytes. For
example, in order to display the letter 'h', we need three bytes:
- 0x02 (the opcode itself)
- 0x8f (the address to write to)
- 0x08 (the value to write)
So, our array would look something like this:
```java
public class Instructions {
	public static final int[] instructions = new int[]{
		0x02,
		0x8f,
		0x08,
		0x00,
		0x00,
		// .. 
		// about 250 more 0x00's
	};
}
```
If we wanted to display two letters, we'd use up a total of 6 instruction
spaces. The amount of instructions required to print a single letter is
equal to the amount of letters to print times 3 - so, as you can see, this
can get pretty big pretty quick, especially given we can only store 255
instructions.

### Instruction pointers
Every instruction in the array has a unique index (a decimal value from 0
to 255). Likewise, every instruction in our CPU has a unique index - a decimal
value from 0-255, or, in CPU-friendly terms, a single byte of information. 
We could use opcode 0x0a to jump to a specific instruction: for example;
```
0x0a 0x00
```
... would jump to the first instruction. This is how loops are implemented -
you keep jumping to a specific instruction until a condition is satisfied.

### Physical implementation
I know I'm largely ignoring the physical implementation of these concepts, but
I feel it may be important to say something about this here. The simplest way
to implement this is to have an index in your CPU that keeps track of the
instruction it should process. This index gets incremented every time you 
process an instruction and move on to a new instruction. Your CPU requests
the information stored at the index it's processing, processes the request,
and then continues. If you want to jump to a specific index, you can set
the CPU's index, and the next instruction it processes will be the one you
just set it to.

### Using instruction pointers to spam "hello world"
It's pretty simple, actually. In some assembler, this would
look something like:
```
MOV ...
MOV ...
MOV ...
MOV ...
MOV ...
MOV ...
MOV ...
MOV ...
MOV ...
MOV ...
JMP ...
```
In machine code, it would look like this.
```
0x02 0x8f 0x08 | 'h'                    - instruction 0x00
0x02 0x90 0x05 | 'e'                    - instruction 0x01
0x02 0x91 0x0c | 'l'                    - instruction 0x02
0x02 0x92 0x0c | 'l'                    - instruction 0x03
0x02 0x93 0x0f | 'o'                    - instruction 0x04
0x02 0x94 0x00 | ' '                    - instruction 0x05
0x02 0x95 0x17 | 'w'                    - instruction 0x06
0x02 0x96 0x0f | 'o'                    - instruction 0x07
0x02 0x97 0x12 | 'r'                    - instruction 0x08
0x02 0x98 0x0c | 'l'                    - instruction 0x09
0x02 0x99 0x04 | 'd'                    - instruction 0x0a
0x0a 0x00      | jump to instruction 0  - instruction 0x0b
```
Note that almost ALL of the code here is just copy-pasted from the printing 
section - we just added one instruction at the end - `0x0a 0x00`, which jumps
to the first instruction, (instruction 0x00), which prints the letter H.
`0x0a 0x00` jumps to `0x02 0x8f 0x08`, and the loop goes on. And on. But...
it's not doing anything?

### Static addressing
You can use a static address if you know what you want to put where - for
example, `0x02 0x8f 0x08` uses a static memory address `0x8f` because we
already KNOW where we want to put the information. But once you get anywhere
above very low-level computing, you need to be able to dynamically reference
memory instead of having to do so statically. This is where compilers and
compiler theory come in handy - a compiler is able to take some human 
readable text and turn it into machine code. When you do the following:
```
int c = 255;
```
... in C, what you're doing could be described as...
- Allocating a memory address for `c`.
- When the compiler passes over this, it'll generate a memory address for c.
  Any time your compiler passes over this again, it'll replace `c` with the
  automatically generated memory address.
So when you do something like:
```
if (c == 0) {
	// ...
}
```
You're checking the memory address the compiler said `c` is at and seeing
if it equals 0. Pretty neat, right? 

#### Compiler theory
I hate to break it to you, but that's way down the line. Unless you're building
a machine that conforms to certain specifications and standards in the world
of computing, you'll need to build your own compiler in a process called
"bootstrapping." In other words, you have to write a compiler in machine code
in order to compile your code for the very first time. 
- The C compiler is written in C. But how was it compiled for the first time?
- A compiler for C was written in machine code. This compiler was used to
  compile C's actual compiler (written in C), which, once compiled, could
  compile more C files in the future.
Yep. That sounds like hell. And don't worry, it is. Even the smallest of
compilers can be several kilobytes in size. But don't worry! We're not there
yet. We still have barely covered addition. 

#### Optimizing compilers
Ooh! Another fun topic. Optimizing compilers transform code written in a human
readable form (C, for example) into FAST and EFFICIENT code written in 1's and
0's. Because there's some translation going on - C to 1's and 0's - there are
bound to be SOME inaccuracies. Not inaccuracies, but... inefficiences. The
C compiler can't be configured to create optimal code for every single 
project, but it can try. Modern compilers will use information they can 
deterermine by analyzing the source code to create efficient assembler code.
