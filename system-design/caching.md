# Week 1 Quiz — test your pattern recognition

## The problems

**Contains Duplicate — LC #217** (Easy)
Pattern to use: Basic hashset lookup
Approach: Iterate through array, check if current element exists in set. If yes, return true. If no, add to set and continue.

**Valid Anagram — LC #242** (Easy) 
Pattern to use: Frequency counting with hashmap
Approach: Count character frequencies in both strings using hashmaps. Compare the two frequency maps for equality.

**Valid Palindrome — LC #125** (Easy)
Pattern to use: Two pointers from opposite ends
Approach: Left pointer at start, right pointer at end. Move inward while characters match (ignoring non-alphanumeric). If pointers meet without mismatch, it's a palindrome.

**Best Time to Buy and Sell Stock — LC #121** (Easy)
Pattern to use: Sliding window (variable size, expanding right boundary)
Approach: Track minimum price seen so far as left boundary. For each day, calculate profit if selling today. Update maximum profit and minimum price as you go.

## What you should have recognized

Each problem telegraphs its pattern through specific structural clues:

- **Duplicate detection** → Think hashset for O(1) lookups
- **Character counting/anagram** → Think frequency hashmap
- **Palindrome verification** → Think two pointers moving inward
- **Optimization over subarray** → Think sliding window

## If you missed the patterns

Go back to Monday-Thursday posts. The tool recognition is more important than solving individual problems. In a real interview, you have 20-25 minutes per problem. Pattern recognition in the first 2-3 minutes determines everything else.

## Write it from memory

Close this tab. Pick one of the four problems above. Write out:
1. The pattern you would use
2. The high-level approach in 2-3 sentences
3. The time/space complexity

No code needed. Just the approach. This is what you do in the first few minutes of any coding interview before touching the keyboard.