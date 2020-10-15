# Binary Search Template

## Description
* Find any position of a target number in a sorted array. Return -1 if target does not exist.

## Example

```
Input: nums = [1,2,2,4,5,5], target = 2
Output: 1 or 2
```

```
Input: nums = [1,2,2,4,5,5], target = 6
Output: -1
```

## Solutions
```
public  int findPosition(int[] nums, int target) {
		if(nums==null||nums.length==0) {
			return -1;
		}
		int start = 0;
		int end = nums.length-1;
		// A:  start =  end;
		// B:  start <= end;
		// C: start+1< end; 
		
		while(start + 1< end) {
			// int mid  = (start+end)/2 if start = 2^31 -1 out of int scope
			int mid = start  + (end - start)/2;
			if(nums[mid] == target) {
				return mid;
			}
			if(mid < target) {
				start = mid;//
				// start = mid + 1;
			}else {
				end = mid;
				// end = mid - 1;
			}
		}
		
		if(nums[start] == target) {
			return start;
		}
		if (nums[end] == target) {
			return end;
		}
		return -1;
	}
```


## Descrption

```
Find the last position of a target number in a sorted array. Return -1 if target does not exist.
```
## Example
Give an array [1, 2, 2, 4, 5, 5]

* For target = 2, return 2.
* For target = 5, return 5.
* For target = 6, return -1.

## Solutions


# Take away
* Binary search is not looking for answer, is shorting the list range.
Give an array [1, 2, 2, 4, 5, 
Give an array [1, 2, 2, 4, 5, 5] 
