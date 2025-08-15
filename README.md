# COMP 251 — Assignment 1: Hash Tables, Disjoint Sets, and Keyword Mining

This assignment covers core data structure implementations and problem-solving techniques in Java. It is divided into three main problems:

- **Q1:** Implementing hash tables using chaining and open addressing.
- **Q2:** Building and extending the Disjoint Set (Union–Find) data structure.
- **Q3:** Processing real-world style text data to extract common keywords across users.

---

## Q1 — Hash Tables (Chaining & Open Addressing)

**Description:**  
This problem focuses on building two types of hash table collision resolution strategies:  
1. **Chaining:** Keys that hash to the same index are stored in a linked list (or similar structure) within that bucket.  
2. **Open Addressing (Linear Probing):** All keys are stored in the table array itself. On collision, the algorithm probes subsequent indices based on `(hash + i) mod m` until an empty or deleted slot is found.  

The task involves:
- Implementing multiplicative hashing.
- Handling insertions, deletions (with lazy deletion markers), and collision counting.
- Maintaining correctness across different operations.

**Example:**  
In open addressing, inserting keys 32, 52, and 72 into an empty table might place them at consecutive indices. If key 52 is removed, inserting key 92 should reuse the deleted slot instead of probing further.

---

## Q2 — Disjoint Sets (Union–Find)

**Description:**  
This section implements the Union–Find data structure to manage disjoint sets efficiently. The core operations are:
- **Find:** Determines which set an element belongs to, with path compression for efficiency.
- **Union:** Merges two sets, using union by rank to keep the structure balanced.

In **Part B**, the functionality is extended to include:
- **`move(i, j)`:** Moves element `i` into the set containing `j`, updating all relevant metadata.
- **`sum_elements(j)`:** Returns the sum of all elements in the set containing `j`.

These extensions require careful updates to maintain set integrity and ensure efficient queries.

**Example:**  
Starting with `{0}, {1}, {2}`, after `union(1, 2)` we get `{1, 2}`. Calling `sum_elements(1)` would return the sum of the values in that set (e.g., `1 + 2 = 3`).

---

## Q3 — Real-World Keyword Mining

**Description:**  
Given a sequence of user–message pairs, the goal is to:
1. Track the set of unique words each user has used.
2. Identify words that **every user** has used at least once.
3. Count the total frequency of those common words across all messages.
4. Output them sorted by frequency (descending) and lexicographically for ties.

This problem combines set operations, frequency counting, and sorting.

**Example:**  
If all users have used the word `"chomp"`, and no other word appears in all users’ messages, the output would be just:


---

**Note:**  
This assignment is graded on Ed, which automatically compiles and tests the code using both open and hidden cases. Efficiency is also considered for certain parts, such as Q2A.
