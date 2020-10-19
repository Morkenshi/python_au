# Math

+ [Reverse Integer](#reverse-integer)
+ [Palindrome Number](#palindrome-number)
+ [Fizz Buzz](#fizz-buzz)
+ [Base 7](#base-7)
+ [Fibonacci Number](#fibonacci-number)
+ [Largest Perimeter Triangle](#largest-perimeter-triangle)
+ [Sqrt(x)](#sqrt(x)

## Reverse Integer

https://leetcode.com/problems/reverse-integer/

```python
class Solution:
    def reverse(self, x: int) -> int:

        if x == 0:
            return 0
        if x > 0:
            ans = int(str(abs(x))[::-1])
        else:
            ans = -int(str(abs(x))[::-1])
        if ans >= -2 ** 31 and ans <= 2 ** 31 - 1:
            return ans
        else:
            return 0
```



## Palindrome Number

https://leetcode.com/problems/palindrome-number/

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        str_x = str(x)
        if str_x == str_x[::-1] and x >= 0:
            return True
        else:
            return False
```



## Fizz Buzz

https://leetcode.com/problems/fizz-buzz/

```python
class Solution(object):
    def fizzBuzz(self, n):

        res = ['']*n
        for i in range(2,n,3):
            res[i]+='Fizz'
        for i in range(4,n,5):
            res[i]+='Buzz'
        for i in range(0, n):
            if not res[i]:
                res[i]+=str(i+1)
        return res  
```



## Base 7

https://leetcode.com/problems/base-7/

```python
class Solution:
    def convertToBase7(self, num: int) -> str:
        if num<0 :
            sign = '-'
        else :
            sign = ''
        num=abs(num)
        result = []
        while num:
            result.append(str(num % 7))
            num //= 7
        result.append(sign)
        return ''.join(reversed(result))
```



## Fibonacci Number

https://leetcode.com/problems/fibonacci-number/

```python
class Solution:
    def fib(self, N: int) -> int:
        if N <= 1:
            return N
        fib0 = 1
        fib1 = 1
        for _ in range(2,N):
            fib3 = fib0 + fib1
            fib0 = fib1
            fib1 = fib3
        
        return fib1
```



## Largest Perimeter Triangle

https://leetcode.com/problems/largest-perimeter-triangle/

```python
class Solution:
    def largestPerimeter(self, A: List[int]) -> int:
        A.sort(reverse=True)
        n = len(A)
        for i in range(n-2):
            if A[i] < A[i+1] + A[i+2]:
                return  A[i] + A[i+1] + A[i+2]
        return 0
```



## Sqrt(x)

https://leetcode.com/problems/sqrtx/

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        n = 0
        while n*n <= x :
            n = n+1
        return n-1
```