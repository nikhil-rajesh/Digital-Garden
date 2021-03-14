# Syntax Directed Translation

Converting parse trees using the actions associated with production rules and the attributes associated with grammar symbols.

Two types of attributes

* **Synthesized Attributes** are such attributes that depend only on the attribute values of children nodes.
* **Inherited Attributes** are such attributes that depend on parent and/or siblings attributes.
  * eg: int x,y,z; // int will be the sibling of idlist

