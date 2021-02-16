# Top-Down Parser

## Recursive Descent Parsing

Start from the Start symbol. Expand Recursively until input string is matched.

{% hint style="info" %}
For RDP, the grammar should not have left recursion.
{% endhint %}

```objectivec
// Before removing Left Recursion
E → E + T | T
T → T * F | F
F → ( E ) | id

// After removing Left Recursion
E  → T E’
E’ → + T E’ | ε
T  → F T’
T’ → * F T’ | ε
F  → ( E )  | id
```

#### Example Code

> **Grammar**  
> E → i E'  
> E' → + i E' \| ε

```c
int main() { 
    // E is a start symbol. 
    E(); 

    // if lookahead = $, it represents the end of the string 
    // Here l is lookahead. 
    if (l == '$') 
        printf("Parsing Successful"); 
} 

// Definition of E, as per the given production 
E() { 
    if (l == 'i') { 
        match('i'); 
        E'(); 
    } 
} 

// Definition of E' as per the given production 
E'() { 
    if (l == '+') { 
        match('+'); 
        match('i'); 
        E'(); 
    }
} 

// Match function 
match(char t) { 
    if (l == t) { 
        l = getchar(); 
    } else
        printf("Error"); 
}
```

### Back-Tracking

For RDP, if one production fails, it is back-tracked and another rule is applied until the input string matches. If all productions fail, Syntax Error is thrown.

**Input String:**  
cad$  
**Grammar:**  
S → c A d  
A → a b \| a

First "cab" is tried, then back-tracked try "cad".

## Predictive Parsing

{% hint style="info" %}
This parsing will only work if, for all productions with same L.H.S start with a different character.
{% endhint %}

### Recursive Predictive Parsing

It is recursive descent parsing without back-tracking. To achieve this we are using a lookahead.  
When expanding the non-terminal, pass the next character in input. Expand the non-terminal starting with that character. If not present, Syntax Error.

> **Grammar**  
> S → cAd  
> A → a

```c
S() {
    lookahead = next_token();
    switch(lookahead) {
        case 'c':
            match('c');
            A();
            match('d');
            break;
        default:
            error();
    }
}

A() {
     switch(lookahead) {
         case 'a':
             match('a');
             break;
         default:
             error();
     }
}

match(token) {
    if lookahead == token:
        lookahead = next_token();
    else:
        error(); 
}
```

### Non-Recursive Predictive Parsing - LL\(1\)

Recursion is avoided by using a parsing table and a stack.

{% hint style="info" %}
[Detailed algorithm for creating parsing table.](https://www.csd.uwo.ca/~mmorenom/CS447/Lectures/Syntax.html/node13.html)
{% endhint %}

#### Example

> **Grammar**  
> S → cAd  
> A → a

```c
// TERM - Array of terminals
// input - Input buffer
// X - top of stack
// M - Parsing table (2D array)
// output - takes parent and children array to create parse tree

main() {
    push($, S) // Push the intial contents of stack
    input_pointer = 0;
    while(1) {
        X = pop();
        token = input[input_pointer];
        if X in TERM or X == $ :
            if X == token:
                input_pointer++;
            else if X == $:
                break;
            else:
                error();
        else :
            production = M[X, token];
            // Push everything in production in reverse
            for i in reverse(production):
                push(i);
            output(X, production);
    }
    print("Parsing Successful");
}

error() {
    print("Syntax Error");
    exit();
}
```

#### Construction of Parsing Table

```c
// M - Parsing Table

for each production A→α 
    for each terminal 'a' in First(α)
        M[A, a] = A→α
    if ε in First(α)
        for each terminal 'b' in Follow(A)
            M[A, b] = A→α
    for each terminal 'a'
        if M[A, a] == undefined
            M[A,a] = error
```

#### Computing of First\(X\)

> If α is any string of grammar symbols, then First\(α\) is the set of terminals that is the start symbols in string derived from α. If α →ε, ε is also in First\(α\).

```c
if X is a terminal
    First(X) = X
else 
    if X→ε is a production
        add ε to First(X) 
    else
        First(X) = undefined
if X→Y1 Y2 ... Yk is a production
    for i in 1...k
        First(X) = First(Yi) U First(X)
        if ε not in First(Yi) 
            break
```

#### Computing of Follow\(X\)

> For a non-terminal A, Follow\(A\) is the set of terminal 'a' that can appear immediately to the right of A in some sentence.
>
> If A is the rightmost symbol in some sentential form, then $ is in Follow\(A\)

```c
if S is the Start Symbol and $ is the right end marker:
    add $ to Follow(S)
if A → α B β
    add First(β) to Follow(B)
if ( A → α B ) or ( A → α B β where First(β) contains ε )
    add Follow(A) to Follow(B)
```



