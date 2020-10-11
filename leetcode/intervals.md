# Intervals

+ [Non-overlapping intervals](#non-overlapping-intervals)
+ [Merge intervals](#merge-intervals)
+ [Insert interval](#insert-interval)

## Non-overlapping Intervals

https://leetcode.com/problems/non-overlapping-intervals/

```python
class Solution:
    def find(self,l1,l2):
        if l2[0]<=l1[0]<l2[1] or l2[0]<l1[1]<=l2[1] or l1[0]<=l2[0]<l1[1] or l1[0]<l2[1]<=l1[1]:
            return 1
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        num = 0
        if len(intervals)<=1:
            return num
        temp = intervals[-1]
        intervals.sort(key = lambda x: x[1])
        k = 1
        while True:
            if self.find(intervals[k-1],intervals[k]) == 1:
                
                num+=1
                del intervals[k]
                k-=1
            k+=1
            if k==len(intervals):
               break 
        return num
```



## Merge Intervals

https://leetcode.com/problems/merge-intervals/

```python
class Solution:
    def find(self,l1,l2):
        if l1[0]<=l2[0]<=l1[1] or l1[0]<=l2[1]<=l1[1] or l2[0]<=l1[0]<=l2[1] or l2[0]<=l1[1]<=l2[1]:
            return True
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        list = []
        k = 1
        if len(intervals)==1 or len(intervals)==0:
            return intervals
        intervals.sort(key = lambda x: x[0])
        while True:
            
            if self.find(intervals[k-1],intervals[k]):
                temp = [min(intervals[k-1][0],intervals[k][0]),max(intervals[k-1][1],intervals[k][1])]
                del intervals[k-1]
                del intervals[k-1]
                
            
                intervals.insert(k-1,temp)
                k-=1
            k+=1
            if k>=len(intervals):
                break
            
        return intervals
```



##Insert Interval

https://leetcode.com/problems/insert-interval/

```python
class Solution:
    def find(self,l1,l2):
        if l1[0]<=l2[0]<=l1[1] or l1[0]<=l2[1]<=l1[1] or l2[0]<=l1[0]<=l2[1] or l2[0]<=l1[1]<=l2[1]:
            return True
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        intervals.append(newInterval)
        k = 1
        if len(intervals)==1 or len(intervals)==0:
            return intervals
        intervals.sort(key = lambda x: x[0])
        while True:
            
            if self.find(intervals[k-1],intervals[k]):
                print(1)
                temp = [min(intervals[k-1][0],intervals[k][0]),max(intervals[k-1][1],intervals[k][1])]
                del intervals[k-1]
                del intervals[k-1]
                
            
                intervals.insert(k-1,temp)
                k-=1
            k+=1
            if k>=len(intervals):
                break
            
        return intervals
```

