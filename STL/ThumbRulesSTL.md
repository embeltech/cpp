Thumb rules for using a specific container:


By default, you should use a vector. 
    It has the simplest internal data structure and provides random access. 
    Thus, data access is convenient and flexible, and data processing is often fast enough.

If you insert and/or remove elements often at the beginning and the end of a sequence, 
    you should use a deque. 
    You should also use a deque if it is important that the amount of internal memory used by the container shrinks when elements are removed. 
    Also, because a vector usually uses one block of memory for its elements, a deque might be able to contain more elements because it uses several blocks.

If you insert, remove, and move elements often in the middle of a container, 
    consider using a list. 
    Lists provide special member functions to move elements from one container to another in constant time. 
    Note, however, that because a list provides no random access, you might suffer significant performance penalties on access to elements inside the list if you have only the beginning of the list. 
    Like all node-based containers, a list doesn’t invalidate iterators that refer to elements, as long as those elements are part of the container. 
    Vectors invalidate all their iterators, pointers, and references whenever they exceed their capacity and part of their iterators, pointers, and references on insertions and deletions. 
    Deques invalidate iterators, pointers, and references when they change their size, respectively.
    If you need a container that handles exceptions so that each operation either succeeds or has no effect, you should use either a list (without calling assignment operations and sort() and, 
    if comparing the elements may throw, without calling merge(), remove(), remove_if(), and unique();or an associative/unordered container (without calling the multiple-element insert operations and, 
    if copying/assigning the comparison criterion may throw, without calling swap() or erase()).

If you often need to search for elements according to a certain criterion, 
    use an unordered set or multiset that hashes according to this criterion. 
    However, hash containers have no ordering, so if you need to rely on element order, you should use a set or a multiset that sorts elements according to the search criterion.

To process key/value pairs, use an unordered (multi)map or, if the element order matters, a (multi) map.

If you need an associative array, use an unordered map or, if the element order matters, a map.

If you need a dictionary, use an unordered multimap or, if the element order matters, a multimap
