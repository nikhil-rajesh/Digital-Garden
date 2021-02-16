# Syntax Analysis

## Parsing Techniques

Parsing techniques are divided into two different groups:

* Top-Down Parsing,
* Bottom-Up Parsing

![Image result for bottom up parsers](https://media.geeksforgeeks.org/wp-content/uploads/20190726164056/Capture55555.jpg)

### Top-Down Parsing

In the top-down parsing construction of the parse tree starts at the root and then proceeds towards the leaves.

Two types of Top-down parsing are:

1. **Recursive Descent Parsing**

   This parsing technique recursively parses the input to make a prase tree. It consists of several small functions, one for each nonterminal in the grammar.

2. **Predictive Parsing**

   Predictive parse can predict which production should be used to replace the specific input string. The predictive parser uses look-ahead point, which points towards next input symbols. Backtracking is not an issue with this parsing technique. It is known as LL\(1\) Parser

{% hint style="info" %}
LL Parser is also called Non-recursive Predictive parser
{% endhint %}

### Bottom-Up Parsing

In the bottom up parsing in compiler design, the construction of the parse tree starts with the leave, and then it processes towards its root. It is also called as shift-reduce parsing.

