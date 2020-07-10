---


---

<h1 id="searching-algorithums">Searching Algorithums</h1>
<h2 id="linear-search">Linear Search</h2>
<p>A simple approach is to do <strong>linear search</strong>, i.e</p>
<ul>
<li>Start from the leftmost element of arr[] and one by one compare x with each element of arr[]</li>
<li>If x matches with an element, return the index.</li>
<li>If x doesn’t match with any of elements, return -1.<br>
<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/Linear-Search.png" alt="" title="Click to enlarge">The time complexity of above algorithm is <strong>O(n).</strong></li>
</ul>
<h2 id="binary-search">Binary Search</h2>
<p>We basically ignore half of the elements just after one comparison.</p>
<ol>
<li>Compare x with the middle element.</li>
<li>If x matches with middle element, we return the mid index.</li>
<li>Else If x is greater than the mid element, then x can only lie in right half subarray after the mid element. So we recur for right half.</li>
<li>Else (x is smaller) recur for the left half.<br>
<img src="https://www.geeksforgeeks.org/wp-content/uploads/Binary-Search.png" alt="https://www.geeksforgeeks.org/wp-content/uploads/Binary-Search.png">The array is sorted and reduce the time complexity to O(Log n).</li>
</ol>
<h2 id="jump-search">Jump Search</h2>
<p>Suppose we have an array arr[] of size n and block (to be jumped) size m. Then we search at the indexes arr[0], arr[m], arr[2m]……arr[km] and so on. Once we find the interval (arr[km] &lt; x &lt; arr[(k+1)m]), we perform a linear search operation from the index km to find the element x.<br>
Time Complexity : O(√n)<br>
Auxiliary Space : O(1)</p>
<p><strong>Important points:</strong></p>
<ul>
<li>Works only sorted arrays.</li>
<li>The optimal size of a block to be jumped is (√ n). This makes the time complexity of Jump Search O(√ n).</li>
<li>The time complexity of Jump Search is between Linear Search ( ( O(n) ) and Binary Search ( O (Log n) ).</li>
<li>Binary Search is better than Jump Search, but Jump search has an advantage that we traverse back only once (Binary Search may require up to O(Log n) jumps, consider a situation where the element to be searched is the smallest element or smaller than the smallest). So in a system where binary search is costly, we use Jump Search.</li>
</ul>
<h2 id="exponential-search">Exponential Search</h2>
<p>Exponential search involves two steps:</p>
<ol>
<li>Find range where element is present</li>
<li>Do Binary Search in above found range.</li>
</ol>
<p>The idea is to start with subarray size 1, compare its last element with x, then try size 2, then 4 and so on until last element of a subarray is not greater.<br>
Once we find an index i (after repeated doubling of i), we know that the element must be present between i/2 and i<br>
<strong>Time Complexity :</strong> O(Log n)</p>
<blockquote>
<p>mid1 = l + (r-l)/3<br>
mid2 = r – (r-l)/3</p>
</blockquote>
<h2 id="why-is-binary-search-preferred-over-ternary-search">Why is Binary Search preferred over Ternary Search?</h2>
<p><strong>Ternary search</strong> is a divide and conquer algorithm that can be used to find an element in an array . It is similar to binary search where we divide the array into two parts but in this algorithm.</p>
<p><strong>Steps to perform Ternary Search:</strong></p>
<ol>
<li>First, we compare the key with the element at mid1. If found equal, we return mid1.</li>
<li>If not, then we compare the key with the element at mid2. If found equal, we return mid2.</li>
<li>If not, then we check whether the key is less than the element at mid1. If yes, then recur to the first part.</li>
<li>If not, then we check whether the key is greater than the element at mid2. If yes, then recur to the third part.</li>
<li>If not, then we recur to the second (middle) part.</li>
</ol>
<p><img src="https://media.geeksforgeeks.org/wp-content/uploads/ternaryS-3.png" alt="" title="Click to enlarge"><br>
<strong>Time Complexity:</strong> <img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-e7d599398d519e7f30b7cee550e75619_l3.svg" alt="O(\log _{3} n)" title="Click to enlarge">, where n is the size of the array.’</p>
<p>Since the value of (2 / Log23) is more than one, Ternary Search does more comparisons than Binary Search in worst case.</p>

