### Q :
> Given an integer array arr, count element x such that x + 1 is also in arr.
>
> If there're duplicates in arr, count them seperately.

> ```
> arr = [1,3,2,3,5,0]
> Output: 3
> ```

***

### A:


```python
class Solution:
    def countElements(self, arr: List[int]) -> int:
        test = collections.Counter(arr)
        ans,lastnum = 0,0
        for i,j in sorted(test.items()):
            if lastnum + 1 == i:
                ans += test[lastnum]
            lastnum = i
        return ans
```
