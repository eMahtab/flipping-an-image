# Flipping an image

Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

```
Example 1:

Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]

Example 2:

Input: [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
Output: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
Explanation: First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]].
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]

Notes:
1 <= A.length = A[0].length <= 20
0 <= A[i][j] <= 1
```

### Implementation 

```java
public int[][] flipAndInvertImage(int[][] A) {
        if(A == null)
            return A;
        for(int i = 0; i < A.length; i++){
            int start = 0;
            int end = A[0].length - 1;
            while(start < end){
                int temp = A[i][start];
                A[i][start] = A[i][end] ^ 1;
                A[i][end] = temp ^ 1;
                start++;
                end--;
            }
            
            if(start == end){
               A[i][start] = A[i][start] ^ 1 ;
            }   
        }
    return A;
}
```

Above implementation have runtime complexity of O(r * c) and space complexity of O(1), where r is the number of rows in the input matrix and c is the number of columns in the input matrix.

```
Runtime Complexity = O(r * c)
Space Complexity   = O(1)
```
