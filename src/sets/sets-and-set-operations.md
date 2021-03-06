<title>Sets and Set Operations – IMT DeCal</title>

# Sets and Set Operations

_by Suraj Rampure_<br>
_Last modified: March 21, 2019_

---

<br>

<!--

Jump to:
* [Sets](#sets)
	* [Cardinality](#cardinality)
* [Subsets](#subsets)
* [Set Operations](#set_operations)
	* [Union](#union)
	* [Intersection](#intersection)
		* [Disjoint Sets](#disjoint)
	* [Difference](#difference)
	* [Cartesian Product](#cartesian)
* [Complements and Universes](#complement)
* [De Morgan's Laws](#demorgan)

<br>

-->

In this note, we will look at the formal definition of a set, a subset, and identify various operations that act on multiple sets. We also introduce the idea of the universal set and a complement. One notable omission is any discussion on the size of a set; this idea will be studied further when we discuss combinatorics. 


<a name='sets'>

> ### Definition: **Set** </a>
> In mathematics, a **set** is a well-defined collection of objects. 
> By well-defined, we mean that for any object $$x$$, we can easily determine whether or not $$x$$ is an element (also referred to as a "member") of the set. Formally, if $$S$$ is a set, we write $$x \in S$$ to state that $$x$$ is in the set $$S$$, and $$x \not \in S$$ to state the opposite. 


We define sets in one of two ways:
- By listing out all of the elements in the set, e.g. $$A_1 = \\{1, 3.14, -15, \pi + e\\}$$, $$A_2 = \\{..., -3, -2, -1, 0, 1, 2, ...\\}$$ or $$A_3 = \\{ \text{Lebron, Jordan, Kobe} \\}$$
- By stating a property that determines the set, e.g. $$A_4 = \\{x : x + 3 \\: \text{is prime} \\}$$ or $$A_5 = \\{t : t^2 - 5t + 6 = 0 \\}$$

Some remarks:
- The symbols $$:$$ and $$\big|$$ both translate to "such that", and precede the condition for inclusion into a set. You will see both used throughout this text. 
- It should be noted that sets can either have finitely many elements, as in $$A_1$$, $$A_3$$ and $$A_5$$, or infinitely many elements, as in $$A_2$$ and $$A_4$$ above. This is a concept we will explore further later in the chapter.
- Stating a property (or properties) that defines a set is known as "set-builder notation."

<br><br>

Before looking at any set operations, we need to define the most basic property of a set there is – the **cardinality**.

<a name='cardinality'>


> ### Definition: **Cardinality** </a>
> The **cardinality** $|S|$ of a finite set $|S|$ is the number of elements in $S$.

For example, we say can say set $$A = \\{1, 2, 9, 12, -3\\}$$ has cardinality $$|A| = 5$$. The same is true for set $$B = \\{1, 1, 2, 2, 2, 2, 12, -3, -3, 9 \\}$$, because when dealing with sets, we only care about unique elements, and don't care about order. 

Notice, our definition was specific to finite sets. It doesn't make much sense to talk about the number of elements in an infinite set, such as the real numbers. However, cardinality is still very well defined in such cases – this is something we will study in Section 1.3.

<br>

<a name='subsets'>

## Subsets

</a>

---

> ### Definition: **Subset**
> Given some set $$A$$, another set $$B$$ is a **subset** of $$A$$ if and only if every element in $$B$$ is also an element of $$A$$. Symbolically, we represent this relationship as $$B \subset A$$ (just like with $$\geq, >, \leq, <$$ signs, the $$\subset$$ sign opens towards the larger set), and its opposite (i.e. $$B$$ is not a subset of $$A$$) as $$B \not \subset A$$. Equivalently, we can say $$A$$ is a **superset** of $$B$$.


For example, if $$A = \\{1, 5, 7, 9, 12\\}$$ and $$B = \\{7, 12\\}$$, we can say $$B \subset A$$, but also that $$\\{5, 6\\} \not \subset A$$.

What if two sets $$A$$ and $$B$$ are subsets of one another – what can we infer about $$A$$ and $$B$$? This would have to mean every element in $$A$$ is in $$B$$, and every element in $$B$$ is in $$A$$. It turns out that this is the exact condition for set equality. Formally, we can say two sets $$A$$ and $$B$$ are **equal** if and only if both $$A \subset B$$ and $$B \subset A$$; in this case we could also write $$A = B$$. 

All sets are subsets of themselves. We say set $$B$$ is a **proper subset** of $$A$$ when $$B \subset A$$ and $$A \neq B$$.

<br>

<a name='set_operations'>

## Set Operations
---

</a>

We will now look at four operations that act on multiple sets – union, intersection, difference and product. Note that these operations are all **closed**, meaning that the results are all also sets (as opposed to being elements of sets, or numbers, or anything else). 

<a name='union'>

### Union
---

</a>

The **union** of two sets $$A, B$$ is the set of everything contained by either $$A$$ or $$B$$. Formally:

<div align=center>

$$\boxed{A \cup B = \\{x : x \in A \\: \text{or} \\: x \in B \\}}$$

</div>

For example, if $$A = \\{1, 5, 7\\}$$ and $$B = \\{2, 3, 7, 8\\}$$, $$A \cup B = \\{1, 2, 3, 5, 7, 8\\}$$. Note that even though there was a 7 in both sets, the 7 is not repeated within the set. It is also worth noting that finite sets need not necessarily be ordered; we could equivalently write $$A = \\{5, 7, 1\\}$$ and $$A \cup B = \\{8, 5, 1, 3, 2, 7 \\}$$. 

For any set $$A$$:
- $$A \cup A = A$$ (Justification: $$\\{x : x \in A \\: \text{or} \\: x \in A\\} = \\{x : x \in A \\}$$)
- $$A \cup \emptyset = A$$ (Justification: $$\\{x : x \in A \\: \text{or} \\: x \in \emptyset\\} = \\{x : x \in A \\}$$)

<a name = 'intersection'>

### Intersection
---

</a>

The **intersection** of two sets $$A, B$$ is the set of everything contained in both $$A$$ and $$B$$. Formally:

<div align=center>

$$\boxed{A \cap B = \\{x : x \in A \\: \text{and} \\: x \in B \\}}$$

</div>


Using the same examples as before, $$A \cap B = \\{7 \\}$$.

For any set $$A$$:
- $$A \cap A = A$$ (Justification: $$A \cap A = \\{x : x \in A \\: \text{and} \\: x \in A \\} = \\{x : x \in A\\}$$)
- $$A \cap \emptyset = \emptyset$$ (Justification: $$A \cap \emptyset = \\{x : x \in A \\: \text{and} \\: x \in \emptyset \\} = \\{x : x \in \emptyset\\}$$)

In the event that the intersection of two sets is the empty set, we have the following definition:

<a name='disjoint'>

> ### Definition: **Disjoint** </a>
> Two sets $$A$$ and $$B$$ are **disjoint** if they have no elements in common, i.e. if $$A \cap B = \emptyset$$.

For example, the set of all even numbers and the set of all odd numbers is disjoint. However, the set of all non-negative numbers (numbers greater than or equal to zero) and the set of all non-positive numbers (numbers less than or equal to zero) are not disjoint, as their overlap has at least one element – in this case, the number 0.

One question we are now equipped to answer is, what is the cardinality of $|A \cup B|$, in relation to $|A|, |B|$, and $|A \cap B|$? While we'll cover this along with Set Theory in the course at UC Berkeley, we will look at this problem more closely in Chapter 3 in the textbook. (If you're curious, you can look at a homework walkthrough **[video](https://youtu.be/_bIum7LkZmk?t=203)** that covers the derivation.)

<a name='difference'>

### Difference
---

</a>

The **difference** of two sets $$A, B$$ is the set of everything contained in $$A$$ but not contained in $$B$$. Formally:

<div align=center>

$$\boxed{A - B = \\{x : x \in A, x \not \in B \\}}$$

</div>


With our example, $$A - B = \\{1, 5\\}$$. Notice that the difference operation is the first set operation that we've studied in which the other matters. $$A \cup B = B \cup A$$ and $$A \cap B = B \cap A$$, but $$A - B \neq B - A$$ – unlike the union and intersection, the difference operation is not **symmetric**. 

Note: Sometimes the difference is written $$A \backslash B$$. 


<a name='cartesian'>

### Cartesian Product
---

</a>

The **Cartesian product** of two sets $$A, B$$ is the set of all possible combinations of one element in $$A$$ and one element in $$B$$. Quite literally:

<div align=center>

$$\boxed{A \times B = \\{(x, y) : x \in A, y \in B  \\}}$$

</div>


Let's use a smaller example – let $$A = \\{1, 2, 3\\}$$ and $$B = \\{x, y, z\\}$$. Then, we have

<div align=center>

$$A \times B = \\{(1, x), (1, y), (1, z), (2, x), (2, y), (2, z), (3, x), (3, y), (3, z) \\}$$

</div>

Notice that the Cartesian product is also not symmetric – if we instead looked at $$B \times A$$, each of the ordered pairs in the set above would be flipped.

<br>

While we only defined the above set operations on two sets, since the result of any of these operations is also a set, we can combine these operations in any way we want. For example, $$A \cup B \cup C$$ can be thought of as $$(A \cup B) \cup C$$, or $$A \cup (B \cup C)$$. We can't assign parentheses as arbitrarily when we combine operations, though: $$(A \cap B) \cup C \neq A \cap (B \cup C)$$ in general.

Note on vector spaces: Algebraic vector spaces are actually defined by a Cartesian product, of the real numbers. The symbol $$\mathbb{R}^n$$ refers to the Cartesian product of the set of real numbers (which we have yet to define) with itself $$n$$ times, i.e. the set of all real-valued vectors with $$n$$ elements.

<br>

<a name='complement'>

## Complements and Universes
---

</a>

Often when dealing with sets, we work relative to some _universal_ set, which contains all relevant objects. For example, when choosing three students from a class of thirty, the set of all students in the class refers to the universe, and any particular subset of three students we choose can denote our set of interest. Using a numerical example, if we let the universe be $$\mathbb{U} = \\{1, 2, 3, 4, 5, 6, 7, 8, 9, 10\\}$$, any set $$A$$ we deal with will be a subset of $$\mathbb{U}$$.

Suppose $$A = \\{1, 2, 4, 8\\}$$. Sometimes, we want to consider the set of elements that are **not** in $$A$$ – this is known as the **complement** of $$A$$. Without a universe, this is impossible to quantify, but with a universe this is straightforward. 

> ### Definition: **Complement**
> Given some set $$A$$, the complement of $$A$$ is defined as 
$$A^c = \\{x : x \not \in A, x \in \mathbb{U} \\}$$


In our case, the complement of $$A$$ (denoted $$A'$$, $$A^{c}$$ or $$\bar{A}$$) is $$A^c = \\{3, 5, 6, 7, 9, 10\\}$$.


<br>


<a name='demorgan'>

## De Morgan's Laws
---

</a>


We can actually combine the idea of the complement of a set with the union and intersection operations, by **De Morgan's Laws**, as follows:

<div align=center>

$$\boxed{\begin{align*} (A \cup B)^c &= A^c \cap B^c \\\ (A \cap B)^c &= A^c \cup B^c \end{align*}}$$

</div>


De Morgan's Laws allow us to convert from a union to an intersection, and vice versa. We will actually prove De Morgan's Laws when we we talk about Propositional Logic.

Let's work out an example as a sanity check. Suppose again that $$\mathbb{U} = \\{1, 2, 3, 4, 5, 6, 7, 8, 9, 10\\}$$, $$A = \\{1, 2, 4, 8\\}$$ and $$B = \\{3, 4\\}$$. Then:

<div align=center>

$$\begin{align*} (A \cup B)^c &= \\{1, 2, 3, 4, 8 \\}^c \\\ &= \\{5, 6, 7, 9\\} \\\ &= \\{3, 5, 6, 7, 9\\} \cap \\{1, 2, 5, 6, 7, 8, 9, 10\\} \\\ &= A^c \cap B^c \end{align*}$$

</div>

You should work out the second case on your own, and verify that it works.

<br>

