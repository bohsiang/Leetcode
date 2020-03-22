### Q :
> Given a non-empty array of integers, return the k most frequent elements.



> ```
> Input: nums = [1,1,1,2,2,3], k = 2
> Output: [1,2]
> ```

***

### A:

這題是要找出陣列中出現最多次的元素，選擇前k個做為輸出

而我的的方法是利用set()的方式將每個在陣列中的數值個數記錄起來

接著依照values進行排序最後輸出前k個key值

而其他利用更快的方式是使用heap找出前k個值概念一樣但複雜度會少上許多


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
