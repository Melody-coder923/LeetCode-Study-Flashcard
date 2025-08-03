## Leetcode 118: Pascal's Triangle

### Concept
Generate **Pascal's Triangle** up to `numRows`. Each number in the triangle is the sum of the two numbers directly above it. The first and last element in each row is always `1`.

### Key Idea
- The first and last element in every row is `1`.
- Every other element in row `r` at index `i` is the sum of the two elements above it:
  \[
  \text{Triangle}[r][i] = \text{Triangle}[r-1][i-1] + \text{Triangle}[r-1][i]
  \]

```
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        res = []
        for row in range(numRows):
            cur = [1] * (row + 1)  # Initialize current row with all 1s
            for col in range(1, row):  # Calculate values for non-boundary elements
                cur[col] = res[row - 1][col - 1] + res[row - 1][col]
            res.append(cur)  # Append current row to result
        return res
```

### Approach
1. **Initialization**: Start with an empty list `res` to store the rows.
2. **Iterate through each row**:
   - For each row, initialize the list with `1`s.
   - For rows greater than `1`, calculate the values between the first and last element using the sum of the two elements directly above it.
3. **Update the result**: Append the current row to `res`.
4. **Return the result**: Once all rows are constructed, return the entire Pascal's Triangle.

### Edge Case Handling
- **numRows = 0** → Return an empty list `[]`.
- **numRows = 1** → Return `[[1]]`.

### Common Examples
- **Example 1**:
  - Input: `numRows = 5`
  - Output:
    ```
    [
      [1],
      [1, 1],
      [1, 2, 1],
      [1, 3, 3, 1],
      [1, 4, 6, 4, 1]
    ]
    ```
  
- **Example 2**:
  - Input: `numRows = 3`
  - Output:
    ```
    [
      [1],
      [1, 1],
      [1, 2, 1]
    ]
    ```

### Time & Space Complexity
- **Time**: O(n^2), where `n` is the number of rows. Each row requires `O(i)` operations for the `i`-th row.
- **Space**: O(n^2), as we need to store the entire Pascal’s Triangle.

### Why This Solution Is Preferred in Interviews
- **Clear and intuitive**: The solution directly follows the properties of Pascal's Triangle.
- **Easy to explain**: The formula for each element is simple and easily understandable.
- **Efficient for small to medium input sizes**: Works well for typical interview constraints.

### Tags
- **Array**
- **Dynamic Programming**
- **Triangle**
