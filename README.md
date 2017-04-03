# extra9
Simple C++ program illustrating hashing functions

## Saurabh School
### Hashing in Data Structures
* [YouTube link](https://www.youtube.com/user/saurabhschool/playlists)

* __Good Hash Functions__
  * Good hash functions have the following properties:
    * Easy to compute
    * Even distribution
    * Less collision
* __How to Handle Collisions__
    * Different ways to avoid collisions but the three common collision resolution strategies are linear probing, quadratic probing, and double hashing
        1. Separate Chaining (Open Hashing)
            * The idea is to keep a list of all elements that hash to the same value
                * The array elements are pointers to the first nodes of the lists
                * A new item is inserted to the front of the list (push_front)
            * Advantages:
                * Better space utilization for large items
                * Simple collision handling
                    * Only need to search a linked list
                * Overflow
                    * We can store more items than the hash table size
                * Deletion is quick and easy
                    * Deletion from a linked list
            * Disadvantages:
                * It is no longer a simple data structure
                    * An array of lists
                * Have to use extra memory that is greater than the hash table size
        2. Linear Probing (Open Addressing)
            * In an open addressing hashing system, all of the data go inside of the table
                * Thus, a bigger table is needed
                    * Generally the load factor should be below 0.5
                * If a collision occurs, alternative cells are tried until an empty cell is found
            * Formal definition:
                * Cells h<sub>0</sub>(x), h<sub>1</sub>(x), h<sub>2</sub>(x), ... are tried in succession where h<sub>i</sub>(x) = (hash(x) + f(i)) mod TableSize, with f(0) = 0
            * In linear probing, collisions are resolved by sequentially scanning an array (with wraparound) until an empty cell is found.
                * i.e. f is a linear function of i, typically f(i) = i
            * Find and Delete
                * The find algorithm follows the same probe sequence as the insert algorithm
            * Advantages:
                * As long as the table is big enough, a free cell can always be found, but the time to do so can get quite large
                * Even worse, if the table is relatively empty, blocks of occupied cells start forming
                    * This effect is known as *primary clustering*
        3. Quadratic Probing (Closed Hashing)
            * If collisions occurs, alternate cells are tried until h<sub>i</sub>(x) = (hash(x) + f(i)) mod HSize, with f(0) = 0
            * i.e. f is a quadtratic function of i, typically f(i) = i<sup>2</sup>
            