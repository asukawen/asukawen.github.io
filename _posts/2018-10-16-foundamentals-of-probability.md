---
layout: post
title: "Foundamentals of Probability"
date: 2018-10-15
---
#####Conditional Probability:
- Given B is ture, probability of A is true: P(A|B)
- Chain Rule:
  P(A, B): Both A and B are true.
  - P(A, B) = P(A|B) * P(B)
  - P(A, B, C) = P(A| B, C) * P(B| C) * P(C)
#####Bayes' theorem:
 >$P( B|A) = \frac{P(B) P(A|B)}{P(A)}$

P(B): prior probobility.  
We use it to test the probability firstly. Whether this method is better or worse depends.
>$P( B|A_1, A_2) = \frac{P(B|A_1) P(A_2|B,  A_1)P(A_1)}{P(A_1, A_2)}$

*(add $A_1$ to the end)*
P(B| $A_1$): prior probability

#####Naive Bayes Classifier:
- Question: how to calculate P(C|F1, F2, ..., Fn)?
- Example: **Fraud User Detection**
Prior information: Real User C0 = 77%; Fake User C1 = 23%
Features:
F1: Number of blogs -> s, m, l
F2: Number of friends -> s, m, l
F3: Real Avator or Not
  - Lemma:
    >P(C| F1, F2, ..., Fn) = P(F1|C) * P(F2|C) * ... P(Fn|C) * P(C)/Z

    P(C| F1, F2, ..., Fn) 
= P(F1, F2, ..., Fn|C)\*P(C)/P(F1, F2, ..., Fn)
= P(F1, F2, ..., Fn|C)*P(C)/Z
Because F1-Fn are all independent:
P(F1, F2, ..., Fn|C) = P(F1|C) * P(F2|C) * ... P(Fn|C)
  - Complete Fraud User Detection:
P(C0| F1 = S, F2 = M, F3 = R)
= P(C0) \*P(F1 = S| C0) \*P(F2 = M| C0) \*P(F3 = R| C0)/Z
= 0.0623 / Z
- **Conclusion: to calculate P(C|F1, F2, ..., Fn), we first calculate P(F1, F2, ...,Fn, C) to get the prior probability.**