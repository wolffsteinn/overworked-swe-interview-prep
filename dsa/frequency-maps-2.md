# Two Pointers — the pattern every developer needs to know

## What it is
Two pointers is a technique where you maintain two indices that move through a data structure according to specific rules. The pointers can start at opposite ends and move toward each other, or both start at the beginning and move at different speeds.

## When to reach for it
- Problem mentions "sorted array" or "sorted list"
- You need to find a pair/triplet that satisfies some condition
- Problem asks about palindromes or string reversal
- You see words like "two sum," "target sum," or "closest to target"
- Input has some ordering property you can exploit

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Traverse with two pointers | O(n) |
| Space usage | O(1) |

## The code

```ts
// Verbose version - opposite ends moving inward
function twoPointersOpposite(arr: number[]): boolean {
    let leftPointer = 0;
    let rightPointer = arr.length - 1;
    
    while (leftPointer < rightPointer) {
        // Process current pair
        const leftValue = arr[leftPointer];
        const rightValue = arr[rightPointer];
        
        // Move pointers based on condition
        if (someCondition(leftValue, rightValue)) {
            leftPointer++;
            rightPointer--;
        } else if (needToMoveLeft) {
            leftPointer++;
        } else {
            rightPointer--;
        }
    }
    
    return false; // or whatever result
}

// Interview version - opposite ends
function twoPointers(arr: number[]): boolean {
    let l = 0, r = arr.length - 1;
    while (l < r) {
        if (condition) return true;
        if (needLeft) l++;
        else r--;
    }
    return false;
}

// Verbose version - slow and fast pointers
function slowFastPointers(arr: number[]): number {
    let slowPointer = 0;
    let fastPointer = 0;
    
    while (fastPointer < arr.length) {
        if (shouldMoveSlow(arr[fastPointer])) {
            arr[slowPointer] = arr[fastPointer];
            slowPointer++;
        }
        fastPointer++;
    }
    
    return slowPointer;
}

// Interview version - slow and fast
function slowFast(arr: number[]): number {
    let slow = 0;
    for (let fast = 0; fast < arr.length; fast++) {
        if (condition) arr[slow++] = arr[fast];
    }
    return slow;
}
```

## The problems (NeetCode order)
**Valid Palindrome — LC #125** (Easy)
What the tool does here: Compare characters from both ends moving inward until pointers meet.
Key insight: Skip non-alphanumeric characters by advancing the appropriate pointer without comparing.

**Two Sum II - Input Array Is Sorted — LC #167** (Medium)
What the tool does here: Use the sorted property to eliminate half the search space with each comparison.
Key insight: If sum is too small, left pointer must move right; if too large, right pointer must move left.

**3Sum — LC #15** (Medium)
What the tool does here: Fix one element, then use two pointers on the remaining subarray to find the pair.
Key insight: Sort first, then skip duplicates to avoid duplicate triplets in the result.

## Common mistakes in interviews
- Forgetting to handle the case where pointers meet (off-by-one in while condition)
- Not skipping duplicates in problems that require unique results like 3Sum
- Moving both pointers simultaneously when you should move only one based on the comparison result

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Two pointers eliminates the need for nested loops when you can make progress by moving indices based on comparisons.