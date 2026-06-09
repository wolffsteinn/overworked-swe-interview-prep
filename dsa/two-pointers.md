# Two Pointers — the pattern every developer needs to know

## What it is
Two pointers uses two indices to traverse data structures, typically arrays or strings, in a coordinated way. Instead of nested loops that create O(n²) time complexity, you move two pointers based on conditions to solve problems in O(n) time.

## When to reach for it
- Problem asks for pairs, triplets, or subarrays with specific properties
- Input is sorted (or you can sort it without breaking the problem)
- You need to find something "optimal" — closest to target, maximum area, longest/shortest sequence
- Brute force would require checking all combinations of two elements

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Traverse with two pointers | O(n) |
| Space usage | O(1) |
| Sorting (if needed first) | O(n log n) |

## The code
```ts
// Verbose version - opposite ends moving inward
function twoPointersOppositeEnds(arr: number[], target: number): number[] {
    let leftPointer = 0;
    let rightPointer = arr.length - 1;
    
    while (leftPointer < rightPointer) {
        const currentSum = arr[leftPointer] + arr[rightPointer];
        
        if (currentSum === target) {
            return [leftPointer, rightPointer];
        } else if (currentSum < target) {
            leftPointer++;
        } else {
            rightPointer--;
        }
    }
    
    return [];
}

// Interview version
function twoSum(arr: number[], target: number): number[] {
    let left = 0, right = arr.length - 1;
    
    while (left < right) {
        const sum = arr[left] + arr[right];
        if (sum === target) return [left, right];
        sum < target ? left++ : right--;
    }
    
    return [];
}

// Same speed pointers
function findCycle(head: ListNode): boolean {
    let slow = head, fast = head;
    
    while (fast?.next) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow === fast) return true;
    }
    
    return false;
}
```

## The problems (NeetCode order)
**Valid Palindrome — LC #125** (Easy)
What the tool does here: Compare characters from both ends moving inward, skipping non-alphanumeric characters.
Key insight: You only need to check half the string — when pointers meet, you've validated the entire palindrome.

**Two Sum II — LC #167** (Medium)
What the tool does here: Leverages the sorted array property to eliminate half the search space with each comparison.
Key insight: If sum is too small, only moving left pointer can increase it; if too large, only moving right pointer can decrease it.

**3Sum — LC #15** (Medium)
What the tool does here: Fixes one number, then uses two pointers on the remaining array to find pairs that sum to the negative of the fixed number.
Key insight: Sort first, then convert the triplet problem into multiple two-pointer subproblems.

**Container With Most Water — LC #11** (Medium)
What the tool does here: Always moves the pointer at the shorter line because keeping it cannot produce a larger area.
Key insight: The area is limited by the shorter line, so the only way to potentially increase area is to try a taller line.

## Common mistakes in interviews
- Moving both pointers simultaneously when you should move only one based on the condition
- Forgetting to handle duplicate values in problems like 3Sum (you need to skip duplicates after finding a valid triplet)
- Using two pointers on unsorted data when the problem requires sorted input for the logic to work

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Two pointers eliminates the nested loop by making smart decisions about which pointer to move based on the problem's constraints.