## 1. Brute Force Approach

In the brute force approach, we'll build a new string by appending characters from the original string in reverse order.

### Explanation:
- We start from the last character of the string and keep appending characters to a new string (reversed) until we reach the beginning of the input string.
- This is considered brute force because it creates a new string and involves repeated concatenation.

#### Time Complexity:
- The loop runs for n iterations where n is the length of the string, so the time complexity is O(n).
- Each string concatenation operation takes O(n) time in the worst case because strings are immutable in JavaScript/TypeScript, and every concatenation creates a new string.
- Therefore, the overall time complexity becomes O(n^2) due to the repeated concatenation.

#### Space Complexity:
- We are storing the reversed string in a new variable, so the space complexity is O(n), where n is the length of the input string.



## TypeScript Solution

```ts
function reverseStringBruteForce(input: string): string {
    let reversed = "";
    // perform the calculation
    for(let i=input.length-1; i>=0; i--){
        reversed +=  input[i]
    }
    return reversed;
}

function reverseOptimal(input: string): string{
    let arr = input.split("");
    let left = 0;
    let right = arr.length - 1;

    while(left<right){
        // Swap the characters at the left and right pointers
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
        right--;
    }
    return arr.join("");
}

console.log(reverseStringBruteForce("hello")); // Output: "olleh"
console.log(reverseStringBruteForce("hello world")); //Output: "dlrow olleh"
console.log(reverseStringBruteForce("")); //output: ""

console.log(reverseOptimal("hello")); // Output: "olleh"
console.log(reverseOptimal("hello world")); //Output: "dlrow olleh"
console.log(reverseOptimal("")); //output: ""
```

## Go Solution

```go
// Online Go compiler to run Golang program online
// Print "Try programiz.pro" message

package main
import "fmt"

func reverseStringBruteForce(input string) string {
    reversed := ""
    for i := len(input) - 1; i >= 0; i-- {
        reversed += string(input[i])
    }
    return reversed
}

func reverseOptimal(input string) string {
    runes := []rune(input) // convert string to rune slice
    left, right := 0, len(runes) - 1
    for left<right {
        runes[left], runes[right] = runes[right], runes[left]
        left++
        right--
    }
    return string(runes);
}

func main() {
    fmt.Println(reverseStringBruteForce("hello")) // Output: "olleh"
    fmt.Println(reverseStringBruteForce("")) // Output: "olleh"
    fmt.Println(reverseStringBruteForce("hello world")) // Output: "olleh"
    fmt.Println(reverseStringBruteForce("madam")) // Output: "olleh"
    fmt.Println(reverseOptimal("hello")) // Output: "olleh"
    fmt.Println(reverseOptimal("")) // Output: ""
    fmt.Println(reverseOptimal("hello world")) // Output: "dlrow olleh"
    fmt.Println(reverseOptimal("madam")) // Output: "madam"
}

```

[Youtube Link](https://www.youtube.com/watch?v=aRa0rTWAFQ0)
