# Binary Search
Binary search is a search algorithm that finds the position of a target value within a sorted array or list. It compares 
the target value to the middle element of the search range, then, based on the comparison, narrows the search to the 
upper or lower half of the current search range.

Two versions of binary search has been implemented in this repository - BinarySearch and BinarySearchTemplated.

## BinarySearch
![binary search img](../../../../../docs/assets/images/BinarySearch.png)
Image Source: GeeksforGeeks

BinarySearch is a more straightforward and intuitive version of the binary search algorithm. In this approach, after the
mid-value is calculated, the high and low pointers are adjusted by just one unit. From the above example, after mid 
points to index 4 in the first search, the low pointer moves to index 5 (+1) when narrowing the search. Similarly, when 
mid points to index 7 in the second search, the high pointer shifts to index 6 (-1) when narrowing the search. This
prevents any possibility of infinite loops.

## BinarySearchTemplated

BinarySearchTemplated removes the condition that checks if the current mid-value is equal to the target (which helps to
end the search the moment the target is found). The template adds a "condition" method which will be modified based on
the requirements of the implementation.

The narrowing of the search space differs from BinarySearch - only one of the high or low pointers will be adjusted by
one unit.

This template will work for most binary search problems and will only require the following changes:
- Search space (high and low)
- Condition method
- Returned value (low or low - 1)

### Search Space (Requires change)
Simply modify the initialisation of the high and low pointer according to the search space.

### Condition (Requires change)
We assume that when the condition returns true, the current value "passes" and when the condition returns false, the 
current value "fails".

In this template, we want to find the first "pass" in the array.

INSERT IMAGE OF FIRST PASS

### Returned Value (Requires change)
In the implementation of BinarySearchTemplated, return low was used to find the first "pass".

EXPLANATION TBC, STILL THINKING HOW TO PHRASE IT.

### Search Space Adjustment
What should be the search space adjustment? (Why only low = mid + 1)

Due to the nature of floor division in Java's \ operator, the searched mid-index will always be smaller than the high
pointer of the previous search range. On the other hand, low = mid + 1, ensures that the searched mid-index is always
larger than the low pointer of the previous search range. This ensures that the search range is narrowed in every loop
and prevents the possibility of infinite loops.

INSERT IMAGE HERE TO EXPLAIN

As we close in towards the target value, the final low = mid + 1 narrows the search range from low. TBC ON EXPLANATION

Credits: [Powerful Ultimate Binary Search Template](https://leetcode.com/discuss/general-discussion/786126/python-powerful-ultimate-binary-search-template-solved-many-problems)

## Complexity Analysis
**Time**:
- Worst case: O(log n)
- Average case: O(log n)
- Best case: 
  - BinarySearch O(1)
  - BinarySearchTemplated O(log n)

BinarySearch:
In the worst case, the target is either in the first index or does not exist in the array at all.
In the best case, the target is the middle (odd number of element) or the first middle element (even number of elements)
if floor division is used to determine the middle.

BinaryTemplated:
In all cases, O(log n) iterations will be required as there is no condition to exit the loop prematurely.

**Space**: O(1) since no new data structures are used and searching is only done within the array given
