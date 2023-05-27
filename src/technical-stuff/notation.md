---
order: 100000
icon: pencil
title: Notation
---

The notations commonly used in Machine Learning are of paramount importance. Knowing how to read mathemetical notations can be the difference between understanding a research paper or leaving it utterly confused. This section will attempt at explaining the commonly used notation systems in ML papers.

<!-- - Random variables or random vectors - both abbreviated as `rvs`  - are represented using roman typeface, while their values and realizations are indicated by the corresponding standard font. For instance, the equality x = $x$ indicates that `rv` x takes value $x$.

- Matrices are indicated using uppercase fonts, with roman typeface used for random matrices.

- Vectors will be taken to be in column form.

- $X^T$ and $X^\dag$ are the transpose and the psuedoinverse of matrix X, respectively.

- The distribution of a `rv` x, either probability mass function (pmf) for a discrete `rv` or probability density function  -->

## Basic Arithmetic Notation

- Addition: $1 + 1 = 2$
- Subtraction: $2 - 1 = 1$
- Multiplication: $2 \cdot 2 = 4$
- Division: $2/2=1$

Basic mathematical operations, as listed above, have a sister operation that performs the inverse operation. For example, subtraction is the inverse of addition, and division is the inverse of multiplication.

## Algebra

Algebra largely deals with variables - data of unknown value - usually represented by Roman or Greek letters. 

#### Multiplication Notation

All of the following can represent multiplication:

- $c = a$ x $b$
- $c = a \cdot b$
- $c = a * b$
- $c = ab$
> A lack of notation represents multiplication.

#### Exponents and roots

An exponent represents a number multiplied by itself $n$ times, where $n$ is the exponent.

- $2^3 = 2 * 2 * 2 = 8$

The above is written as `2^3` in plaintext.

Square root is the inverse of an exponent.

- $\sqrt{4} = 2$

This is essentially the expression $2^2 = 4$. A root $\sqrt{}$ with no index is a square root, which can also be written as $\sqrt[2]{}$. In the expression $\sqrt{4}$, we must find a value that, when raised to the power of $2$ (since we're using a *square* root), would give us $4$. This answer is naturally $2$, since $2^2 = 4$.

- $\sqrt[3]{8} = 2$

This represents the expression $2^3 = 8$ in root form.

#### Logarithms and `e`

When we raise 10 to an integer exponent, we call this an order of magnitude:

$10^2 = 10 * 10$ or $100$

Reversing that operation is done by calculating the logarithm of the result 100 **assuming a base of 10.**

$\log{10}(100) = 2$

$2^6 = 64$

$\log{2}(64) = 6$

Another popular logarithm is with the natural Euler's number (`e`) base, a value with infinite precision.

$e = 2.71828...$

Raising Euler's number of a power is called a natural exponential function:

$e^2 = 7.38905...$

Inverse of it:

$\ln(7.38905...) = 2$

#### Greek Letters

Refer to [this wikipedia page](https://en.wikipedia.org/wiki/Greek_letters_used_in_mathematics,_science,_and_engineering) for a full list.

#### Sequence Notation

A sequence can be an array of data or a list of items.

##### Indexing

A key to reading notation for sequences is the notation of indexing elements in the sequence. The notation will specify the beginning and end of the sequence, as as $1$ to $n$, where $n$ will be the extent or length of the sequence.

Items in the sequence are indexed by a variable such as $i$, $j$, and $k$ as a **subscript**. For example, $a_i$ is the $i^{th}$ element of the sequence $a$.

If the sequence is two-dimentional (2D), two indices will be used. For example: $b_{i,j}$ is the $i,j^{th}$ element of the sequence $b$.

##### Sequence Operations

As with most mathematical concepts, operations can be performed on a sequence. Two operations, addition and multiplication, are so common that they have their own shorthand: **the sum** and **the multiplication**.

###### Sequence Summation

The sum over a sequence is denoted as the uppercase Greek letter Sigma $\Sigma$. It's specified with the variable and start of the sequence summation below the sigma symbol (i.e. $i = 1$) and the index of the end of the summation above the sigma (e.g. $n$).

$\huge{\displaystyle\sum_{i=1}^n a_i}$

This is the sum of the sequence $a$ starting at element $1$ to element $n$.

###### Sequence Multiplication

This operation is denoted as the uppercase Greek letter pi $\Pi$. It's specified the same way as the sequence summation with the beginning and end of the operation below and above the letter respectively.

$\huge{\displaystyle\prod_{i=1}^n a_i}$

#### Set Notation

A set is a group of unique items.

##### Set of Numbers
A common set is a set of numbers, such as a term defined as being within the set of integers or real numbers.

Some common sets are:

- Set of all natural numbers: $\N$
- Set of all integers: $\Z$
- Set of all real numbers: $\R$

##### Set Membership

Set membership is denoted by a symbol that looks similar to an uppercase $E$:

$\huge{a \in \R}$

The above notation means that $a$ is defined as being a member of the set $\R$, or the set of real numbers.

There's also set operations; two common ones are:

- Union, or aggregation: $A \cup B$
- Intersection, or overlap: $A \cap B$

Learn more about sets on [Wikipedia](https://en.wikipedia.org/wiki/Set_(mathematics)).

### Other Notation

There's various other notations you may come across. Here's some of the more prominent ones.

It's common to define a method in the abstract and then define it again as a specific implementation with a separate notation. For example, if we're estimating a variable $x$, we may represent it using a notation that *modifies* the $x$; for example:

- x-bar: $\large{\bar{x}}$
- x-prime: $\large{x^{\prime}}$
- x-hat: $\large{\hat{x}}$
- x-tilde: $\large{\tilde{x}}$

The same notation may have a different meaning in a different context, such as use on different objects or sub-fields of mathematics. For example, a common point of confusion is $|x|$, which, depending on the context, can mean:

- $|x|$: The absolute or positive value of $x$.
- $|x|$: The length of vector $x$.
- $|x|$: The cardinality of the set $x$.

### Extended Tips

#### Think about the author

Humans wrote the book or the paper you're reading, so they're prone to errors, omissions, or making things confusing because they might not *fully* understand what they are writing. Relax the constraints of the notation you're reading and think about the *intent* of the author. What are they trying to get across to you?

#### Check Wikipedia
Wikipedia has a list of notations which could help you out. You can try out these two articles:

- [List of mathematical symbols](https://en.wikipedia.org/wiki/List_of_mathematical_symbols)
- [Greek letters used in mathematics, science, and engineering](https://en.wikipedia.org/wiki/Greek_letters_used_in_mathematics,_science,_and_engineering)

#### Sketch in Code

Mathematical operations are functions on data. Map everything you're reading to psuedo-code with variables, for-loops, and more. You could even use a scripting language, along with a small array of contrived data or even an Excel (or LibreOffice Calc!) spreadsheet. 

#### Seek Alternatives

If a paper is too confusing, read explanations or gentler introductions to the topic from another paper, or an online article. 

#### Ask questions

[Quora](https://quora.com) is a great place to ask your questions. The math nerds there will be more than happy to explain things to you, so long as you ask your questions properly. You can also try AI services such as [ChatGPT](https://chat.openai.com) to explain things to you. 



### Summary

In this page, you've discovered the basics of mathematical notation that you may come across when reading the descriptions of techniques in machine learning.

Specifically, you've learned:

- Notation for arithmetic, including variations of multiplication, exponents, roots, and logarithms.
- Notation for sequences and sets, including indexing, summation, and set membership.
- Tips on how to get help if you're struggling with notations.