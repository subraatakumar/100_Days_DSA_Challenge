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
