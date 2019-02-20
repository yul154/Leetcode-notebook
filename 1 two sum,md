# two pointers
```
def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        nums=enumerate(nums)
        nums=sorted(nums, key=lambda x:x[1])
        left,right=0,len(nums)-1
        while left!=right:
            if nums[left][1]+nums[right][1]==target:
                return (nums[left][0],nums[right][0])
            elif nums[left][1]+nums[right][1]<target:
                left+=1
            else:
                right-=1
```

# Dictionay with one pass
```
def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        maping={}
        for i,num in enumerate(nums):
            if target-num in maping:
                return [maping[target-num],i]
            maping[num]=i
```

# Dictionary with two pass
```
def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        maping={}
        length=len(nums)
        for i in range(length):
            maping[nums[i]]=i
        for i1 in range(length):
            k=target-nums[i1]
            if k in maping and maping[k]!=i1:
                return [i1,maping[k]]
```

# low memory
```
def twoSum(self, nums, target):
        for index1, a_num in enumerate(nums):
            for index2, b_num in enumerate(nums[(index1+1):]):
                if a_num+b_num == target: return [index1, index1+index2+1]
```
