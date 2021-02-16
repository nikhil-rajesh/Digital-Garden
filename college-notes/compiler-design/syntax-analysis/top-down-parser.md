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

{% hint style="info" %}
**Grammar**  
E → i E'  
E' → + i E' \| ε
{% endhint %}

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

{% hint style="info" %}
**Grammar**  
S → cAd   
A → a
{% endhint %}

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

{% hint style="info" %}
**Grammar**  
S → cAd   
A → a
{% endhint %}

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

