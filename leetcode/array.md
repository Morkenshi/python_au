+ [ Max Consecutive Ones](#Max-Consecutive-Ones)
+ [ Flipping an Image](#Flipping-an-Image)
+ [ Transpose Matrix](#Transpose-Matrix)
+ [ Move Zeroes](#Move-Zeroes)
+ [ Squares of a Sorted Array](#Squares-of-a-Sorted-Array)
+ [ Reshape the Matrix](#Reshape-the-Matrix)
+ [ Image Smoother](#Image-Smoother)
+ [ Intersection of Two Linked Lists](#Intersection-of-Two-Linked-Lists)
+ [ Sort List](#Sort-List)

##  Max Consecutive Ones
https://leetcode.com/problems/max-consecutive-ones/
```python
class Solution(object):
    def findMaxConsecutiveOnes(self, nums):
        currentMax,resultMax = 0,0
        for num in nums:
            if num == 1 :
                currentMax += 1
                if currentMax > resultMax:
                    resultMax = currentMax
            else:
                currentMax = 0
        return resultMax
```
##  Flipping an Image
https://leetcode.com/problems/flipping-an-image/
```python
class Solution(object):
    def flipAndInvertImage(self, A):
        for row in A:
            row.reverse()
            for element in range(0 , len(A)):
                if row[element] == 1:
                    row[element] = 0
                else:
                    row[element] = 1
        return A
```
##  Transpose Matrix
https://leetcode.com/problems/transpose-matrix/
```python
class Solution(object):
    def transpose(self, A):
        rows, collums = len(A[0]), len(A)
        Onerow, result = [], []
        for i in range(rows):
            for j in range(collums):
                Onerow.append(A[j][i])
            result.append(Onerow)
            Onerow = []
        return result
```
##  Move Zeroes
https://leetcode.com/problems/move-zeroes/
```python
class Solution(object):
    def moveZeroes(self, nums):
        for num in nums:
            if  num == 0:
                nums.remove(num)
                nums.append(num)
        return nums
```
##  Squares of a Sorted Array
https://leetcode.com/problems/squares-of-a-sorted-array/
```python
class Solution(object):
    def sortedSquares(self, A):
         return(sorted([x*x for x in A]))
```
##  Reshape the Matrix
https://leetcode.com/problems/reshape-the-matrix/
```python
class Solution(object):
    def matrixReshape(self, nums, r, c):
        mem_sum = sum(nums, [])
        if (len(mem_sum) != (r*c)):
            return nums
        res = [[0]*c for i in range(r)]
        for i in range(0,len(mem_sum)):
            res[i//c][i%c] = mem_sum[i]
        return res
```
##  Image Smoother
https://leetcode.com/problems/image-smoother/
```python
class Solution:
    def imageSmoother(self, M):
        m = len(M)
        n = len(M[0])
        sums = [[0] * n for _ in range(m)]
        for r in range(m):
            for c in range(n):
                sums[r][c] = sum(M[r][max(0, c-1):c+2])
        for r in range(m):
            for c in range(n):
                total = sums[r][c]
                sum_count = 3 if c != 0 and c != n - 1 else min(n, 2)
                total_count = sum_count
                if r != 0:
                    total += sums[r-1][c]
                    total_count += sum_count
                if r != m - 1:
                    total += sums[r+1][c]
                    total_count += sum_count

                M[r][c] = int(floor(total / total_count))
        return M
```