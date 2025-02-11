# LEETCODE-Strings-1910--III-
---

### **How it works**
1. **The `check` method**:
   - Takes a stack (`st`), the substring `part`, and its length `n`.
   - Creates a temporary copy of the stack (`tst`).
   - Verifies if the top `n` characters of the stack match `part` in reverse order.
   - If they match, it returns `true`; otherwise, it returns `false`.

2. **The `removeOccurrences` method**:
   - Initializes an empty stack (`st`).
   - Iterates through the input string `s`, pushing each character onto the stack.
   - After each push, it checks if the top `n` characters of the stack match the substring `part` by invoking the `check` method.
   - If they match, it pops `n` characters from the stack to effectively remove that occurrence of `part`.

3. **Result construction**:
   - Once all characters of `s` are processed, the stack contains the remaining characters of `s` (with all occurrences of `part` removed).
   - The characters in the stack are popped and appended to a `StringBuilder` to construct the final string in reverse order.
   - The result is reversed before returning, as the stack stores the characters in reverse order.

---

### **Dry Run Example**
#### Input:
```java
s = "daabcbaabcbc"
part = "abc"
```

#### Step-by-Step Execution:
1. **Initialization**:
   - `n = 3` (length of `part`).
   - `m = 12` (length of `s`).
   - `st` starts empty.

2. **Iterate through `s`**:
   - Push each character onto the stack (`st`).
   - Check if the top `n` characters match `part`:
     - `st = [d, a, a]` → No match.
     - `st = [d, a, a, b, c]` → Match! Remove `abc`.
       - `st = [d, a]`.
     - Continue until all characters in `s` are processed.

3. **Final Stack**:
   - After processing `s`, the stack will contain `[d, a, b, c]`.

4. **Construct Result**:
   - Build the result string from the stack: `"dabcbc"`.

#### Output:
```java
"dab"
```

---

### **Complexity Analysis**
1. **Time Complexity**:
   - Let `m` be the length of `s` and `n` the length of `part`.
   - Each character in `s` is pushed and popped from the stack once.
   - Checking the top `n` characters of the stack has an overhead of \(O(n)\).
   - Worst-case time complexity: \(O(m \cdot n)\).

2. **Space Complexity**:
   - The stack can hold up to \(O(m)\) characters in the worst case.
   - Space complexity: \(O(m)\).

---
