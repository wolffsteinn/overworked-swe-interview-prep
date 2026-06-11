# Sliding Window — the pattern every developer needs to know

## What it is
A technique that maintains a window of elements in an array or string, expanding and contracting the window boundaries based on problem constraints. You track window state (usually with two pointers) and update it incrementally instead of recalculating from scratch.

## When to reach for it
• Problem asks for "substring", "subarray", or "contiguous elements"
• You need to find optimal window meeting some condition (longest, shortest, exact match)
• Constraint involves sum, count, or frequency within a range
• Brute force would involve nested loops checking all possible ranges

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Fixed window traversal | O(n) |
| Variable window traversal | O(n) |
| Space for window state | O(1) or O(k) where k is constraint size |

## The code

```ts
// Fixed window - verbose
function fixedWindowMax(nums: number[], k: number): number {
    let windowSum = 0;
    
    // Initialize first window
    for (let i = 0; i < k; i++) {
        windowSum += nums[i];
    }
    
    let maxSum = windowSum;
    
    // Slide window
    for (let i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];
        maxSum = Math.max(maxSum, windowSum);
    }
    
    return maxSum;
}

// Fixed window - interview version
function fixedWindow(nums: number[], k: number): number {
    let sum = nums.slice(0, k).reduce((a, b) => a + b, 0);
    let max = sum;
    
    for (let i = k; i < nums.length; i++) {
        sum += nums[i] - nums[i - k];
        max = Math.max(max, sum);
    }
    
    return max;
}

// Variable window - verbose
function variableWindowLongest(s: string): number {
    const charSet = new Set<string>();
    let left = 0;
    let maxLength = 0;
    
    for (let right = 0; right < s.length; right++) {
        // Expand window
        while (charSet.has(s[right])) {
            charSet.delete(s[left]);
            left++;
        }
        
        charSet.add(s[right]);
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}

// Variable window - interview version
function variableWindow(s: string): number {
    const seen = new Set();
    let left = 0, max = 0;
    
    for (let right = 0; right < s.length; right++) {
        while (seen.has(s[right])) {
            seen.delete(s[left++]);
        }
        seen.add(s[right]);
        max = Math.max(max, right - left + 1);
    }
    
    return max;
}
```

## The problems (NeetCode order)
**Best Time to Buy and Sell Stock — LC #121** (Easy)
What the tool does here: Single pass tracking minimum price seen so far and maximum profit possible
Key insight: You only need the minimum element to the left of current position, not a traditional window

**Longest Substring Without Repeating Characters — LC #3** (Medium)
What the tool does here: Expand window until duplicate found, then contract from left until duplicate removed
Key insight: Use a set to track characters in current window for O(1) duplicate detection

**Permutation in String — LC #567** (Medium)
What the tool does here: Fixed window of target length sliding across string, comparing character frequencies
Key insight: Frequency map comparison can be optimized to a single counter tracking matches

## Common mistakes in interviews
• Recalculating window state from scratch instead of incrementally updating (loses the O(n) guarantee)
• Using nested loops when the inner loop is actually the window contraction (think "while" not "for" for the left pointer)
• Forgetting to handle edge cases where window size exceeds array length

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Two pointers create a window that expands and contracts — you update window state incrementally, never recalculate.