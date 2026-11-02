## 01. Sort by Decreasing Frequency

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sorting-elements-of-an-array-by-frequency-1587115621/1)

### Problem Description

**Task:** Given an array of integers arr[], sort the array according to frequency of elements, i.e. elements that have higher frequency comes first. If the frequencies of two elements are the same, the smaller number comes first.Examples :Input: arr[] = [5, 5, 4, 6, 4]

#### Examples

##### Example 1

- **Output:**
```text
[4, 4, 5, 5, 6]
```
- **Explanation:** The highest frequency here is 2. Both 5 and 4 have that frequency. Now since the frequencies are the same the smaller element comes first. So 4 4 comes first then comes 5 5. Finally comes 6. The output is 4 4 5 5 6.

##### Example 2

- **Input:**
```text
arr[] = [9, 9, 9, 2, 5]
```
- **Output:**
```text
[9, 9, 9, 2, 5]
```
- **Explanation:** The highest frequency here is 3. Element 9 has the highest frequency So 9 9 9 comes first. Now both 2 and 5 have the same frequency. So we print smaller elements first. The output is 9 9 9 2 5.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-11-02 11:53:18
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
    public ArrayList<Integer> sortByFreq(int arr[]) {
        Map<Integer, Integer> freqMap = new HashMap<>();
        for (int num : arr) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }

        ArrayList<Integer> list = new ArrayList<>();
        for (int num : arr) {
            list.add(num);
        }

        list.sort((a, b) -> {
            int freqA = freqMap.get(a);
            int freqB = freqMap.get(b);

            if (freqA != freqB) {
                return Integer.compare(freqB, freqA);
            }

            return Integer.compare(a, b);
        });

        return list;
    }
}
```

*Generated on: 02/11/2026, 11:53:37*