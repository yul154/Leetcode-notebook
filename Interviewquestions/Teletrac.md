# Question

Fold array N times

# Example
```
// write a method that folds an array N times
//  [1, 20, 300], 1 => [301, 20]
//  [1, 20, 300, 4000], 1 => [4001, 320]
// [1,4000]=> 
//  [1, 20, 300, 4000, 50000], 2 => [50001, 4020, 300] => [50301, 4020]

// two pointers, l = 0, r = nums.length()-1;
// while (l!=r)
// sum (l+r)=> nums[l];
// l+=1;
// r-1;
```


# Solutions
```
public static void main(String[] args) {
        List<Integer> nums1 = new ArrayList<>();
        Collections.addAll(nums1, new Integer[]{1, 20, 300});
        List<Integer> nums2 = new ArrayList<>();
        Collections.addAll(nums2, new Integer[]{1, 20, 300, 4000});
        List<Integer> nums3 = new ArrayList<>();
        Collections.addAll(nums3, new Integer[]{1, 20, 300, 4000, 50000});
        System.out.println(nums1.toString() + ": 1 => " + arrayFold(nums1, 1).toString());
        System.out.println(nums2.toString() + ": 1 => " + arrayFold(nums2, 1).toString());
        System.out.println(nums3.toString() + ": 2 => " + arrayFold(nums3, 2).toString());
   }
   
 public static List<Integer> arrayFold(List<Integer> nums,int times){
     //ArrayList<Integer> res = new ArrayList<Integer>();
     
     for(int i =0;i<times;i++){
        int left =0;
        int right = nums.size()-1;
        while (left<right){
            int cur_sum = 0;
            cur_sum= nums.get(left)+nums.get(right);
            nums.set(left, cur_sum);
            nums.remove(right);
            left+=1;
            right-=1;
        }
        if nums,sTest-Driven Development (TDD
     }
     return nums;

 }
```
