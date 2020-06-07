---


---

<h1 id="hashing--introduction">Hashing | Introduction</h1>
<p><strong>Hashing</strong> is the solution that can be used in almost all such situations and performs extremely well compared to data structures like Array, Linked List, Balanced BST in practice. With hashing we get O(1) search time on average (under reasonable assumptions) and O(n) in worst case.</p>
<p><strong>Hash Function:</strong> A function that converts a number to a small practical integer value. The mapped integer value is used as an index in hash table.<br>
A good hash function should have following properties</p>
<ol>
<li>Efficiently computable.</li>
<li>Should uniformly distribute the keys .</li>
</ol>
<p><strong>Hash Table:</strong>  An array that stores pointers to records corresponding to a given phone number. An entry in hash table is NIL if no existing number has hash function value equal to the index for the entry.</p>
<p><strong>Collision Handling</strong>: Since a hash function gets us a small number for a big key, there is possibility that two keys result in same<br>
value. The situation where a newly inserted key maps to an already<br>
occupied slot in hash table is called collision and must be handled<br>
using some collision handling technique. Following are the ways to<br>
handle collisions:</p>
<ul>
<li>**Chaining:**The idea is to make each cell of hash table point to a linked list of records that have same hash function value. Chaining is simple, but requires additional memory outside the table.</li>
<li><strong>Open Addressing:</strong> In open addressing, all elements are stored in the hash table itself. Each table entry contains either a record or NIL. When searching for an element, we one by one examine table slots until the desired element is found or it is clear that the element is not in the table.</li>
</ul>
<h2 id="index-mapping-or-trivial-hashing-with-negatives-allowed">Index Mapping (or Trivial Hashing) with negatives allowed</h2>
<p><strong>How to handle negative numbers?</strong><br>
On a limited range array contains both positive and non-positive numbers, i.e., elements are in the range from -MAX to +MAX. Our task is to search if some number is present in the array or not in O(1) time.<br>
Since range is limited, we can use index mapping  (or trivial hashing). We use values as the index in a big array. Therefore we can search and insert elements in O(1) time.</p>
<p>The idea is to use a 2D array of size hash[MAX+1][2]</p>
<p><em>Algorithm:</em></p>
<p>Assign all the values of the hash matrix as 0.<br>
Traverse the given array:<br>
If the element <em>ele</em> is non negative assign<br>
hash[<em>ele</em>][0] as 1.<br>
Else take the absolute value of <em>ele</em> and<br>
assign hash[<em>ele</em>][1] as 1.</p>
<h2 id="separate-chaining">Separate Chaining:</h2>
<p><strong>What are the chances of collisions with large table?</strong><br>
Collisions are very likely even if we have big table to store keys. An important observation is Birthday Paradox. With only 23 persons, the probability that two people have the same birthday is 50%.<br>
<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2015/07/hashChaining1.png" alt="hashChaining"><br>
<strong>Advantages:</strong></p>
<ol>
<li>Simple to implement.</li>
<li>Hash table never fills up, we can always add more elements to the chain.</li>
<li>Less sensitive to the hash function or load factors.</li>
<li>It is mostly used when it is unknown how many and how frequently keys may be inserted or deleted.</li>
</ol>
<p><strong>Disadvantages:</strong></p>
<ol>
<li>Cache performance of chaining is not good as keys are stored using a linked list. Open addressing provides better cache performance as everything is stored in the same table.</li>
<li>Wastage of Space (Some Parts of hash table are never used)</li>
<li>If the chain becomes long, then search time can become O(n) in the worst case.</li>
<li>Uses extra space for links.</li>
</ol>
<h2 id="open-addressing">Open Addressing</h2>
<p>In Open Addressing, all elements are stored in the hash table itself. So at any point, size of the table must be greater than or equal to the total number of keys (Note that we can increase table size by copying old data if needed).<br>
Insert(k): Keep probing until an empty slot is found. Once an empty slot is found, insert k.<br>
Search(k): Keep probing until slot’s key doesn’t become equal to k or an empty slot is reached.<br>
Delete(k): <em><strong>Delete operation is interesting</strong></em>. If we simply delete a key, then search may fail. So slots of deleted keys are marked specially as “deleted”.<br>
Insert can insert an item in a deleted slot, but the search doesn’t stop at a deleted slot.</p>

