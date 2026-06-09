# Binary Search — the pattern every developer needs to know

## What it is
Binary search eliminates half the search space on each iteration by comparing the target with the middle element of a sorted array. It maintains two pointers that converge until the target is found or the search space is exhausted.

## When to reach for it
- Problem mentions "sorted array" or "sorted order"
- You need to find a target value, insertion point, or boundary condition
- Problem asks for "first occurrence" or "last occurrence" of something
- You see phrases like "find the smallest/largest value that satisfies condition X"

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Search | O(log n) |
| Space | O(1) |

## The code

```ts
// Verbose version - find exact target
function binarySearch(nums: number[], target: number): number {
    let left = 0;
    let right = nums.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1; // target not found
}

// Interview version - find leftmost boundary
function searchLeft(nums: number[], target: number): number {
    let left = 0, right = nums.length;
    while (left < right) {
        const mid = Math.floor((left + right) / 2);
        if (nums[mid] < target) left = mid + 1;
        else right = mid;
    }
    return left;
}
```

## The problems (NeetCode order)
**Binary Search — LC #704** (Easy)
What the tool does here: Standard binary search implementation to find exact target value.
Key insight: Use `left <= right` condition and return -1 when target doesn't exist.

**Search a 2D Matrix — LC #74** (Medium)
What the tool does here: Treats the 2D matrix as a flattened sorted array using index conversion.
Key insight: Convert 1D index back to 2D coordinates with `row = mid // cols, col = mid % cols`.

**Koko Eating Bananas — LC #875** (Medium)
What the tool does here: Binary search on the answer space (eating speed) rather than array indices.
Key insight: The minimum viable speed forms the left boundary of valid speeds.

## Common mistakes in interviews
- Using `(left + right) / 2` instead of `Math.floor((left + right) / 2)` — causes infinite loops with negative numbers
- Confusing boundary conditions between `left <= right` vs `left < right` — know which template you're using
- Off-by-one errors when converting between "find target" and "find boundary" variants

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Binary search is about maintaining invariants: everything to the left fails your condition, everything to the right passes it.