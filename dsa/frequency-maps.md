# Two Pointers — the pattern every developer needs to know

## What it is
Two pointers uses two indices to traverse data structures, typically arrays or strings, from different positions or directions. The pointers move based on conditions you define, eliminating the need for nested loops in many scenarios.

## When to reach for it
- Problem asks for pairs, triplets, or subarrays with specific properties
- Input is sorted or you can sort it without breaking the solution
- You need to find something in O(n) time that brute force would solve in O(n²)
- Keywords: "two sum," "closest to target," "remove duplicates," "palindrome"

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Traverse with two pointers | O(n) |
| Sort then two pointers | O(n log n) |
| Space | O(1) |

## The code

```ts
// Verbose version - opposite ends moving inward
function twoPointersOpposite<T>(arr: T[], condition: (left: T, right: T) => number): boolean {
    let leftPointer = 0;
    let rightPointer = arr.length - 1;
    
    while (leftPointer < rightPointer) {
        const result = condition(arr[leftPointer], arr[rightPointer]);
        
        if (result === 0) {
            return true; // Found what we're looking for
        } else if (result < 0) {
            leftPointer++; // Need larger left value
        } else {
            rightPointer--; // Need smaller right value
        }
    }
    
    return false;
}

// Interview version - same direction
function twoPointersSame<T>(arr: T[], isValid: (slow: number, fast: number) => boolean): number {
    let slow = 0;
    for (let fast = 0; fast < arr.length; fast++) {
        if (isValid(slow, fast)) {
            slow++;
        }
    }
    return slow;
}
```

## The problems (NeetCode order)
**Valid Palindrome — LC #125** (Easy)
What the tool does here: Compare characters from both ends moving inward
Key insight: Skip non-alphanumeric characters by advancing the appropriate pointer

**Two Sum II - Input Array Is Sorted — LC #167** (Medium)
What the tool does here: Find pair that sums to target using sorted property
Key insight: If sum is too small, move left pointer right; if too large, move right pointer left

**3Sum — LC #15** (Medium)
What the tool does here: Fix one number, use two pointers on remaining sorted array
Key insight: Sort first, then skip duplicates to avoid duplicate triplets

## Common mistakes in interviews
- Moving both pointers simultaneously when you should move only one based on the condition
- Forgetting to handle duplicates in problems that require unique results
- Not considering edge cases where pointers meet or cross over

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Two pointers eliminates nested loops by using the input's structure to decide which pointer to move.