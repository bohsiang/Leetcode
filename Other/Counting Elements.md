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

這題是要看陣列中排列組合是否相差1

若是重複的話則以x個數作為答案

而我是先統計所有數值在陣列中的個數

利用`for`迴圈進行計算

若是相差1就加上當前數值的個數避免重複問題

ex.

[1,1,2,2,3,3,3,3] = {1:2,2:2,3:4}

(1,2,3)

2 + 2 =  4

[1,3,2,3,5,0] = {0:1,1:1,2:1,3:2,5:1}

(0,1,2,3)

1 + 1 + 1 = 3

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

- Time complexity : O(n).

- Space complexity : O(n).
