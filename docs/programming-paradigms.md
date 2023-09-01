# Programming Pardigms
A [programming paradigm](https://en.wikipedia.org/wiki/Comparison_of_programming_paradigms) is a style or method of programming characterised by the main features or constructs used.

This page describes and compares the paradigms available in Dyalog. It is not an academic or authoratative classification of paradigms.

## Array-oriented
This is one ingredient in the secret sauce of APL.

In the most trivial sense, basic APL operations can be compared to [SQL](https://www.w3schools.com/sql/sql_intro.asp) statements.

```APL
      names _ ages     ⍝ A list of names stacked on top of a list of corresponding ages
┌─────┬───┬───────┬─────┬─────┐
│Alice│Bob│Charlie│David│Ellie│
├─────┼───┼───────┼─────┼─────┤
│22   │5  │26     │30   │12   │
└─────┴───┴───────┴─────┴─────┘

      names⌿⍨ages>15   ⍝ Select names where age is greater than 15
┌─────┬───────┬─────┐
│Alice│Charlie│David│
└─────┴───────┴─────┘
```

How does this work? Operations work on whole arrays in a consistent manner, so we can compare two numbers as easily as many:

```APL
      22 > 15     ⍝ 1 for yes, 0 for no
1
      ages > 15   ⍝ This is a list of Booleans
1 0 1 1 0
```

The function [replicate](http://help.dyalog.com/latest/#Language/Primitive%20Functions/Replicate.htm) (`⍺/⍵`), when used with Booleans (1s and 0s), is called *compress*. Here we are using [compress-first]() (`⍺⌿⍵`) to be more consistent with [leading axis theory]().

```APL
      1 0 1 1 0 ⌿ 'ABCDE'
ACD
```

Dyalog allows you to mix and match styles of programming to fit your use case.

## Procedural
Traditional APL code often has this flavour. This is probably most relatable to people who have a traditional computer science background, and learned a language like **C** or **Python**.

In procedural programming, you decompose a problem into the smallest steps that you know how to express to the computer, and then you tell the computer *do this* then *do this* then *do this other thing*.

It is easily compared to a cooking recipe: *add flour*, *add water*, *mix together to make a dough*, *fry the dumplings*.

Say that we have a list of `salaries`, with corresponding `groups` of employees which are labelled `ABCD...`. We want to increase the salaries for all employees in group 'C' by 
15%.

We could break this down as a sequence of steps as follows:

1. Begin with first group
1. Compare group with `'C'`. If the group is equal to `C`:
	1. If group is equal to `C`, replace the corresponding salary with that salary multiplied by `1.15`
1. If we have processed all groups, return the list of salaries.
1. Otherwise, repeat from **2** with the next group.

This can be translated using control structures:

```APL
    ∇  salaries←group RaiseBy percent
[1]    :For s :In ⍳≢salaries
[2]        :If groups[s]≡'C'
[3]            salaries[s]×←1.15
[4]        :EndIf
[5]    :EndFor
    ∇
```

Because we can processing arrays of data at a time, we can express this algorithm as a single step and translate it directly into a single line of code:

1. Replace salaries where group is equal to `'C'` with corresponding salaries multiplied by `1.15`.

```APL
    ∇  group RaiseBy percent
[1]    salaries[⍸groups=group]×←1+percent÷100
    ∇
```

## Object-oriented
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [Namespaces in Dyalog APL](https://www.youtube.com/watch?v=eBEwBSO5mBA)

In this model, all of the key entities are *objects*. These are not physical objects like a table or a book, but they are conceptually like objects.

You can define a *class* of object, like a **dog** or a **bird**.

You can then define some *properties* and *methods* for objects of that class, like dogs have legs and birds have wings. Dogs go woof while birds go **tweet**.

You can then define classes which use others as a base. So you can define 

|Class|Instance|Property|Method|
|---|---|---|---|
|Dog|Golden Retriever|Legs|Woof|
|Dog|Cocker Spaniel|Legs|Woof|
|Bird|Parakeet|Wings|Tweet|
|Bird|Sparrow|Wings|Tweet|

See our guide on [Object Oriented Programming for APL Programmers](http://docs.dyalog.com/latest/Object%20Oriented%20Programming%20for%20APL%20Programmers.pdf). Or if you haven't the time, [Object Oriented Programming for Impatient APL Programmers](http://docs.dyalog.com/latest/Object%20Oriented%20Programming%20for%20Impatient%20APL%20Programmers.pdf).

## Functional
In APL terminology, a **function** is a thing with `3=⎕NC` [nameclass 3](http://help.dyalog.com/latest/#Language/System%20Functions/nc.htm).

<a href="https://dyalog.tv/Dyalog11/?v=bQlH49krwbk">What is Functional Programming? John Scholes and Roger Hui at the Dyalog '11 User Meeting<a>

In contrast to our procedural examplel [above](#procedural), pure functional programming would insist that our functions have no side effects.

```APL
 Raise←{
⍝ ⍺: (groups)(salaries)
⍝ ⍵: (groups to raise)(percentage)
⍝ ←: salaries of groups raised by percentage
     (g s)←⍺
     (r p)←⍵
     (1+p÷100)×@(⍸g∊r)⊢s
 }
```

Often times, the array-oriented approach and the functional approach yield similar encodings of the same solution. One key difference between functional programming and array-oriented programming is that while functional programming focuses on the composition of pure functions.

This contrast is exemplified by two ways to write code which takes the first four words in a text vector.

In a functional approach, we define functions which perform each step of 

1. Split character vector into a [nested vector of character vectors]().
2. Take the first four words
3. Join our list of four words into a single, non-nested character vector.

```APL
      SplitWords ← ' '∘(≠⊆⊢)
      Take4 ← 4∘↑
      Join ← 1∘↓⍤∊' '∘,¨
      Join Take4 SplitWords 'here are four words and here are five more'
here are four words
```

In the [traditional APL](/language/modern-apl) approach, the main focus is on the transformation of data from one stage to the next.

```APL
      text ← 'here are four words and here are five more'
      ' ' = text
0 0 0 0 1 0 0 0 1 0 0 0 0 1 0 0 0 0 0 1 0 0 0 1 0 0 0 0 1 0 0 0 1 0 0 0 0 1 0 0 0 0
      +\' ' = text
0 0 0 0 1 1 1 1 2 2 2 2 2 3 3 3 3 3 3 4 4 4 4 5 5 5 5 5 6 6 6 6 7 7 7 7 7 8 8 8 8 8
      4>+\' ' = text
1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
      text⌿⍨4>+\' ' = text
here are four words
```

The advantage in the functional case is that the functions we create should be useful for solving other problems as well. The advantage in the array-oriented case is that not only are we making the best use of the core primitive functions and operators, but we are use [flat arrays]() .

- Using flat arrays
- Using the core primitives
- From step to step, each transformation can be used for a different purpose.