---
layout: post
title:  "[Java] Passing null to a destructive method"
date:   2016-05-28 12:46:55 -0400
categories: jekyll update
---

I plan to implement a destructively catenation function in Java like public static void dcatenate(IntList A, IntList B), which is used to append list B to A, and the original A should be modified. For example,

```java
IntList A = new IntList(1,2,3); // A: 1->2->3
IntList B = new IntList(4,5,6); // B: 4->5->6
dcatenate(A, B) // A: 1->2->3->4->5->6
```

However, what if A=null?

```java
IntList A = null;
IntList B = new IntList(4,5,6); // B: 4->5->6
dcatenate(A, B) // A: 4->5->6 (is it possible?)
```

Since the function parameter is passed by value, I cannot locate the original A in the function when I pass null to the parameter. Moreover, modifying the parameter A will never change the original A because they are stored in different addresses although they are both null. Is my understanding correct? If so, how can I solve this problem? Is it possible to pass the address of original A to the parameter just like C/C++?

