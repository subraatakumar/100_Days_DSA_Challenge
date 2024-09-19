## Problem: Valid Anagram

Given two strings s and t, determine if t is an anagram of s. An anagram is a word or phrase formed by rearranging the letters of another, typically using all the original letters exactly once.

### Brute-force Approach:

In the brute-force method, the most straightforward approach would be to:

- Sort both strings s and t.
- Compare if the sorted versions of both strings are the same.

#### Explanation:

- Sorting ensures that all characters in both strings are arranged in the same order, so if they are anagrams, the sorted versions will be equal.
- Time complexity of sorting two strings is O(n log n) where n is the length of the strings.

#### Brute-force Code: TypeScript

```typescript
function isAnagramBruteForce(s: string, t: string): boolean {
    // If lengths are different, they can't be anagrams
    if (s.length !== t.length) return false;
    
    // Sort both strings and compare them
    return s.split('').sort().join('') === t.split('').sort().join('');
}

// Test
console.log(isAnagramBruteForce("hello","elhlo")) // true 
console.log(isAnagramBruteForce("Hello","Hai")) // false
console.log(isAnagramBruteForce("Rat", "Cat")) // false
```

#### Explanation:

- s.split('') splits the string into an array of characters.
- .sort() sorts the array.
- .join('') joins the sorted characters back into a string.
- Finally, we compare the sorted versions of s and t.

#### Brute-force Code: Go

```go
package main

import (
	"fmt"
	"sort"
	"strings"
)

// Helper function to sort a string
func sortString(s string) string {
	slice := strings.Split(s, "")
	sort.Strings(slice)
	return strings.Join(slice, "")
}

func isAnagramBruteForce(s, t string) bool {
	// If lengths are different, they can't be anagrams
	if len(s) != len(t) {
		return false
	}
	// Sort both strings and compare
	return sortString(s) == sortString(t)
}

func main() {
  fmt.Println(isAnagramBruteForce("hello","elhlo"))
  fmt.Println(isAnagramBruteForce("hello","hai"))
  fmt.Println(isAnagramBruteForce("rat","cat"))
}
```

#### Explanation:

- strings.Split(s, "") splits the string into an array of characters.
- sort.Strings(slice) sorts the array of characters.
- strings.Join(slice, "") joins the sorted characters back into a string.

## Optimal Approach:

The optimal approach leverages counting character frequencies rather than sorting the entire string. This has a time complexity of O(n).

#### Optimal Approach Explanation:

- First, check if the lengths of the strings are equal. If not, return false.
- Use a frequency map (or array) to count the occurrences of each character in string s.
- For each character in string t, decrement the corresponding count in the frequency map.
- If any character count goes negative, it means t contains extra characters, so they are not anagrams.
- If all counts are zero after processing both strings, then the strings are anagrams.

#### Optimal Code: TypeScript

```typescript
function isAnagramOptimal(s: string, t: string): boolean {
    if (s.length !== t.length) return false;
    
    const charCount: { [key: string]: number } = {};
    
    // Count characters in string 's'
    for (let char of s) {
        charCount[char] = (charCount[char] || 0) + 1;
    }
    
    // Decrease the count for characters in string 't'
    for (let char of t) {
        if (!charCount[char]) {
            return false;
        }
        charCount[char] -= 1;
    }
    
    return true;
}

// Test
console.log(isAnagramOptimal("hello","elhlo")) // true 
console.log(isAnagramOptimal("Hello","Hai")) // false
console.log(isAnagramOptimal("Rat", "Cat")) // false
```

#### Explanation:

- charCount is an object that tracks the frequency of characters in s.
- We increment counts when iterating through s and decrement counts for each character in t.
- If any character count goes below zero, the strings are not anagrams.

#### Optimal Code: Go

```go
package main

import "fmt"

func isAnagramOptimal(s, t string) bool {
	if len(s) != len(t) {
		return false
	}
	
	charCount := make(map[rune]int)
	
	// Count characters in string 's'
	for _, char := range s {
		charCount[char]++
	}
	
	// Decrease the count for characters in string 't'
	for _, char := range t {
		if charCount[char] == 0 {
			return false
		}
		charCount[char]--
	}
	
	return true
}

func main() {
  fmt.Println(isAnagramOptimal("hello","elhlo"))
  fmt.Println(isAnagramOptimal("hello","hai"))
  fmt.Println(isAnagramOptimal("rat","cat"))
}
```

#### Explanation:

- A map charCount tracks the frequency of characters.
- We increment counts while iterating through s and decrement counts for each character in t.
- If any count drops below zero, it means t has extra characters, so the strings are not anagrams.

#### Time and Space Complexity:

- Brute-force approach: O(n log n) for sorting, where n is the length of the string.
- Optimal approach: O(n) time complexity for counting characters and constant space O(1) for the map (since there are a limited number of characters).
