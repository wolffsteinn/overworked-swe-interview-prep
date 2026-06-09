# Two Pointers — the pattern every developer needs to know

## What it is
Two pointers is a technique where you maintain two indices that move through an array or string according to specific rules. The pointers can start at opposite ends and move toward each other, or start together and move apart, or move at different speeds.

## When to reach for it
- Problem mentions "pair", "triplet", "subarray", or "substring" 
- You need to find elements that satisfy a relationship (sum, difference, comparison)
- Input is sorted or you can sort it without breaking the problem
- You're looking for something optimal in a contiguous sequence

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Traversal with two pointers | O(n) |
| Space usage | O(1) |

## The code

```ts
// Verbose version - opposite ends moving inward
function twoPointersOppositeEnds<T>(arr: T[]): void {
    let leftPointer = 0;
    let rightPointer = arr.length - 1;
    
    while (leftPointer < rightPointer) {
        // Process current pair
        const leftValue = arr[leftPointer];
        const rightValue = arr[rightPointer];
        
        // Move pointers based on your condition
        if (someCondition(leftValue, rightValue)) {
            leftPointer++;
        } else {
            rightPointer--;
        }
    }
}

// Interview version
function twoPointers<T>(arr: T[]): void {
    let l = 0, r = arr.length - 1;
    while (l < r) {
        if (condition(arr[l], arr[r])) l++;
        else r--;
    }
}

// Same speed pointers (sliding window variant)
function sameSpeedPointers<T>(arr: T[]): void {
    let left = 0;
    for (let right = 0; right < arr.length; right++) {
        // Expand window with right pointer
        
        while (windowInvalid()) {
            // Shrink window with left pointer
            left++;
        }
        
        // Process valid window
    }
}
```

## The problems (NeetCode order)
**Valid Palindrome — LC #125** (Easy)
What the tool does here: Compare characters from start and end moving inward
Key insight: Skip non-alphanumeric characters without breaking the pointer movement pattern

**Two Sum II - Input Array Is Sorted — LC #167** (Medium)  
What the tool does here: Use sorted property to eliminate half the search space each move
Key insight: If sum is too small move left pointer right, if too large move right pointer left

**3Sum — LC #15** (Medium)
What the tool does here: Fix one number, use two pointers on the remaining array
Key insight: Sort first, then skip duplicates at all three positions to avoid duplicate triplets

## Common mistakes in interviews
- Moving both pointers simultaneously when you should move only one based on the condition
- Forgetting to handle edge cases when pointers meet or cross over
- Not skipping duplicates in problems that require unique results, leading to duplicate answers

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Two pointers eliminates nested loops by using the problem's structure to decide which pointer to move.