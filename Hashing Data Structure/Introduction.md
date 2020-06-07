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
Insert can insert an item in a deleted slot, but the search doesn’t stop at a deleted slot.<br>
<em><strong>a) Linear Probing:</strong></em> In linear probing, we linearly probe for next slot. For example, typical gap between two probes is 1 as taken in below example also.<br>
let <strong>hash(x)</strong> be the slot index computed using hash function and <strong>S</strong> be the table size<br>
<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2015/08/openAddressing1.png" alt="openAddressing"><strong>Clustering:</strong> The main problem with linear probing is clustering, many consecutive elements form groups and it starts taking time to find a free slot or to search an element<br>
<em><strong>b) Quadratic Probing</strong></em> We look for i2‘th slot in i’th iteration.</p>
<p>let hash(x) be the slot index computed using hash function.<br>
If slot hash(x) % S is full, then we try (hash(x) + 1<em>1) % S<br>
If (hash(x) + 1</em>1) % S is also full, then we try (hash(x) + 2<em>2) % S<br>
If (hash(x) + 2</em>2) % S is also full, then we try (hash(x) + 3<em>3) % S<br>
…<br>
…<br>
<strong>c) Double Hashing</strong> We use another hash function hash2(x) and look for i</em>hash2(x) slot in i’th rotation.</p>
<p>let hash(x) be the slot index computed using hash function.<br>
If slot hash(x) % S is full, then we try (hash(x) + 1<em>hash2(x)) % S<br>
If (hash(x) + 1</em>hash2(x)) % S is also full, then we try (hash(x) + 2<em>hash2(x)) % S<br>
If (hash(x) + 2</em>hash2(x)) % S is also full, then we try (hash(x) + 3*hash2(x)<br>
…<br>
…</p>
<h2 id="double-hashing">Double Hashing</h2>
<p><strong>Double hashing</strong> is a collision resolving technique in <strong>Open Addressed</strong> Hash tables. Double hashing uses the idea of applying a second hash function to key when a collision occurs.</p>
<blockquote>
<p>Double hashing can be done using :<br>
<strong>(hash1(key) + i * hash2(key)) % TABLE_SIZE</strong><br>
First hash function is typically hash1(key) = key % TABLE_SIZE</p>
</blockquote>
<ul>
<li>First hash function is typically hash1(key) = key % TABLE_SIZE</li>
<li>A popular second hash function is : <strong>hash2(key) = PRIME – (key % PRIME)</strong> where PRIME is a prime smaller than the TABLE_SIZE.</li>
</ul>
<p>A good second Hash function is:</p>
<ul>
<li>It must never evaluate to zero</li>
<li>Must make sure that all cells can be probed<br>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/double-hash-function.png" alt=""></li>
</ul>
<h3 id="load-factor-and-rehashing">Load Factor and Rehashing</h3>
<p><strong>How hashing works:</strong><br>
For <strong>insertion</strong> of a key(K) – value(V) pair into a hash map, 2 steps are required:</p>
<ol>
<li>K is converted into a small integer (called its hash code) using a hash function.</li>
<li>The hash code is used to find an index (hashCode % arrSize) and the entire linked list at that index(Separate chaining) is first searched for the presence of the K already.</li>
<li>If found, it’s value is updated and if not, the K-V pair is stored as a new node in the list.</li>
</ol>
<h3 id="complexity-and-load-factor">Complexity and Load Factor</h3>
<ul>
<li>For the <strong>first step</strong>, time taken depends on the K and the hash function.<br>
For example, if the key is a string “abcd”, then it’s hash function may depend on the length of the string. But for very large values of n, the number of entries into the map, length of the keys is almost negligible in comparison to n so hash computation can be considered to take place in constant time, i.e, <strong>O(1)</strong>.</li>
<li>For the <strong>second step</strong>, traversal of the list of K-V pairs present at that index needs to be done. For this, the worst case may be that all the n entries are at the same index. So, time complexity would be <strong>O(n)</strong>. But, enough research has been done to make hash functions uniformly distribute the keys in the array so this almost never happens.</li>
<li>So, <strong>on an average</strong>, if there are n entries and b is the size of the array there would be <strong>n/b</strong> entries on each index. This value n/b is called the <strong>load factor</strong> that represents the load that is there on our map.</li>
<li>This Load Factor needs to be kept low, so that number of entries at one index is less and so is the complexity almost constant, i.e., O(1).</li>
<li></li>
</ul>
<h3 id="rehashing">Rehashing:</h3>
<p><strong>Rehashing means hashing again</strong>. Basically, when the load factor increases to more than its pre-defined value (default value of load factor is 0.75), the complexity increases. So to overcome this, the size of the array is increased (doubled) and all the values are hashed again and stored in the new double sized array to maintain a low load factor and low complexity.<br>
Rehash must be done, increasing the size of the bucketArray so as to reduce the load factor and the time complexity.<br>
Rehashing can be done as follows:</p>
<ul>
<li>For each addition of a new entry to the map, check the load factor.</li>
<li>If it’s greater than its pre-defined value (or default value of 0.75 if not given), then Rehash.</li>
<li>For Rehash, make a new array of double the previous size and make it the new bucketarray.</li>
<li>Then traverse to each element in the old bucketArray and call the insert() for each so as to insert it into the new larger bucket array.</li>
</ul>

