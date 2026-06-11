# Two Pointers — the technique every developer needs to know

## What it is
Two pointers uses two indices that move through an array or string according to specific rules. Instead of nested loops that check every pair (O(n²)), you position pointers strategically and move them based on comparisons or conditions.

## When to reach for it
- Problem asks for pairs, triplets, or subarrays with specific properties
- Input is sorted or you can sort it without breaking the solution
- You need to find something "optimal" — closest sum, longest/shortest subarray
- Brute force would be O(n²) but there's a logical way to eliminate impossible combinations

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Two pointer traversal | O(n) |
| Space (typically) | O(1) |

## The code
```ts
// Verbose version - opposite ends moving inward
function twoPointersInward(arr: number[], target: number): boolean {
    let leftPointer = 0;
    let rightPointer = arr.length - 1;
    
    while (leftPointer < rightPointer) {
        const currentSum = arr[leftPointer] + arr[rightPointer];
        
        if (currentSum === target) {
            return true;
        } else if (currentSum < target) {
            leftPointer++; // Need larger sum
        } else {
            rightPointer--; // Need smaller sum
        }
    }
    
    return false;
}

// Interview version
function twoSum(nums: number[], target: number): boolean {
    let l = 0, r = nums.length - 1;
    
    while (l < r) {
        const sum = nums[l] + nums[r];
        if (sum === target) return true;
        sum < target ? l++ : r--;
    }
    
    return false;
}
```

## The problems (NeetCode order)
**Valid Palindrome — LC #125** (Easy)
What the tool does here: Compare characters from both ends moving inward
Key insight: Skip non-alphanumeric characters by advancing the appropriate pointer without breaking the while loop

**Two Sum II — LC #167** (Medium)
What the tool does here: Find pair that sums to target in sorted array
Key insight: Sorted array means if sum is too small, left must move right; if too large, right must move left

**3Sum — LC #15** (Medium)
What the tool does here: Fix one element, use two pointers on the remaining sorted portion
Key insight: Three pointers total — outer loop fixes first, inner two pointers solve Two Sum II on the rest

**Container With Most Water — LC #11** (Medium)
What the tool does here: Find maximum area between two lines
Key insight: Always move the pointer at the shorter line — moving the taller one can never increase area

## Common mistakes in interviews
- Moving both pointers simultaneously when you should move only one based on a condition
- Forgetting to handle duplicates in 3Sum (skip identical values to avoid duplicate triplets)
- Using two pointers on unsorted data when the algorithm requires sorted input

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Two pointers eliminates the inner loop by using problem constraints to decide which pointer moves.
