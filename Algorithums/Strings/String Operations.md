---


---

<h1 id="strings---pattern-matching">Strings - Pattern Matching</h1>
<pre><code>**TRIECONSTRUCTION**(_Patterns_)  
_Trie_ ← a graph consisting of a single node _root_  
**for** each string _Pattern_ in _Patterns_  
_currentNode_ ← _root_  
**for** _i_ ← 1 to |_Pattern_|  
**if** there is an outgoing edge from _currentNode_ with label _currentSymbol_  
_currentNode_ ← ending node of this edge  
**else**  
add a new node _newNode_ to _Trie_  
add a new edge from _currentNode_ to _newNode_ with label _currentSymbol_  
_currentNode_ ← _newNode_  
**return** _Trie_
</code></pre>

