### Q :
> Given a non-empty array of integers, return the k most frequent elements.



> ```
> Input: nums = [1,1,1,2,2,3], k = 2
> Output: [1,2]
> ```

***

### A:


```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        d = {}
        for i in set(nums):
            d[i] = nums.count(i)
        return [i[0] for i in sorted(d.items(),key = lambda d:d[1],reverse = True)[:k]]
        
        ### other method
        s = collections.Counter(nums)
        return heapq.nlargest(k,s.keys(),key=s.get)
```
