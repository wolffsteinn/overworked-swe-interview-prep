# Sliding Window — the pattern every developer needs to know

## What it is
Sliding window maintains a contiguous subarray using two pointers that expand and contract based on problem constraints. Fixed windows move both pointers together maintaining constant size. Variable windows expand the right pointer to explore and contract the left pointer to satisfy constraints.

## When to reach for it
- Problem asks for contiguous subarray or substring
- You need to find optimal (min/max/best) subarray meeting criteria  
- Constraint involves sum, product, or character frequency within a range
- Brute force would be O(n²) checking all subarrays

## Time and space complexity
| Operation | Complexity |
|-----------|------------|
| Fixed window traversal | O(n) |
| Variable window traversal | O(n) |
| Space | O(1) or O(k) for frequency maps |

## The code

```ts
// Fixed window (size k)
function fixedWindow(nums: number[], k: number): number {
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

// Variable window
function variableWindow(nums: number[], target: number): number {
    let left = 0;
    let sum = 0;
    let minLength = Infinity;
    
    for (let right = 0; right < nums.length; right++) {
        sum += nums[right];
        
        while (sum >= target) {
            minLength = Math.min(minLength, right - left + 1);
            sum -= nums[left];
            left++;
        }
    }
    
    return minLength === Infinity ? 0 : minLength;
}

// Interview version - variable window template
function slidingWindow(arr: any[], isValid: (window: any) => boolean): any {
    let left = 0;
    let result = /* initialize based on problem */;
    
    for (let right = 0; right < arr.length; right++) {
        // Expand window - add arr[right]
        
        while (!isValid(/* current window */)) {
            // Contract window - remove arr[left]
            left++;
        }
        
        // Update result with current valid window
    }
    
    return result;
}
```

## The problems (NeetCode order)
**Best Time to Buy and Sell Stock — LC #121** (Easy)
What the tool does here: Tracks minimum price seen so far while expanding window to find maximum profit.
Key insight: This is a degenerate sliding window where you only care about the minimum left boundary, not maintaining an actual window.

**Longest Substring Without Repeating Characters — LC #3** (Medium)  
What the tool does here: Expands right to include new characters, contracts left when duplicates appear.
Key insight: Use a frequency map to detect duplicates instantly rather than scanning the current window.

**Permutation in String — LC #567** (Medium)
What the tool does here: Fixed window of target length slides across string, comparing character frequencies.
Key insight: Maintain frequency difference counter instead of rebuilding frequency maps for each window position.

## Common mistakes in interviews
- Rebuilding window state from scratch on each iteration instead of incrementally updating
- Using fixed window approach on variable window problems (or vice versa)  
- Forgetting to handle edge cases where valid window might be impossible

## Write it from memory
Close this tab. Open a blank TypeScript file. Write today's core pattern from scratch — no copying, no autocomplete.

Most interview environments are a blank CodeSignal or HackerRank editor with no IntelliSense. The first time that feels jarring should not be during the interview.

Come back and check your implementation against the code section above.

## The one thing to remember
Sliding window turns O(n²) subarray problems into O(n) by maintaining state incrementally instead of recalculating from scratch.