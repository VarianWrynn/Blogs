# 编程范式：命令式编程、声明式编程和函数式编程

@(.NET开发)[编程语言, 技术扫盲, 命令式编程, LeetCode]





## 2021-9-7 [Two Sum](https://leetcode-cn.com/problems/two-sum/)

[两数之和](https://leetcode-cn.com/problems/two-sum/)

最大收获：由于缺乏VScode的强大IDE支持，发现许多基础的语法都已经不会了，比如for和foreach循环都不会写，数字的属性Lenght因为大小写问题编译一直报错等等：

- for (int i=1; i< nums.Length; i++) 第一个初始化，第二个是**defines the condition for executing the code block.** 第3个是**being executed (every time) after the code block has been executed.**

- 数组的长度是属性，需要大写，遵循[Pascal](https://www.theserverside.com/definition/Pascal-case)原则： int[] nums... nums.**Lenght**(而不是num.lenght)

- C#里面定义数组

  ```C#
  // return new array {0,i}; 一开始写成这样了
  // return new int[i,y]; 这种[]也是错的： Cannot implicitly convert type 'int[*,*]' to 'int[]'
  // return new int{i,y};： Cannot initialize type 'int' with a collection initializer because it does not implement 'System.Collections.IEnumerable
  return new int[]{0,i};
  ```

- **Length**容易打错成**Lenght**
- for(j=i+1;j<nums.Length;j++)==> J未定义

### 第一次提交：

```C#
public class Solution{
    public int[] TwoSum(int[] nums, int target)
    {
        for(int i=0;i<nums.Length;i++)
        {
            for int(j=1;j<nums.Lenght;j++)
            {
                if(nums[i]+nums[j]==target)
                {
                    return new int[]{i,j}
                }
            }
        }
        return null
    }
}
```

以下的测试用例failed:

<img src="./img/image-20210907121431702.png" alt="image-20210907121431702" style="zoom:67%;" />

```C#
[2,5,5,11]
10
```



原因是：当i=1的时候，其值为5； 而第二个嵌套循环的j=1，期值也为5，于是就出现[1,1]确实等于5，不是预期的[1,2]了；



### 第二次提交



```C#
public class Solution{
    public int[] TwoSum(int[] nums, int target)
    {
        for(int i=0;i<nums.Length;i++) //第一个数组的元素一定不是该数组的最后一个元素，因此可以为i<nums.Length -1 
        {
            for (int k = i+1;k<nums.Length;k++)
            {
                if(nums[i]+nums[k] ==target)
                {
                    return new int[] {i,k}
                }
            }
        }
        return null
    }
}
```



### [视频解题](https://leetcode-cn.com/problems/two-sum/solution/liang-shu-zhi-he-by-leetcode-solution/)：



思路：**以空间换时间**；(你可以通过加大内存来换取NASA火箭的发射速度，而不是为了节约内存而让登月登上几十年)





## 2021-9-8 [Binary Search](https://leetcode-cn.com/problems/binary-search/solution/er-fen-cha-zhao-by-leetcode-solution-f0xw/)

- while loop的语法

  ```C#
  while(condition)
  {
  	//code block
  }
  ```

  都是一些非常基础的，但是离开的IDE却发现是傻眼的，一是平时练的少，二是没有注意观察总结

- Math.Ceiling:需要做类型转化

  ```C#
  mid = Math.Ceiling((head + tail) / 2);
  =>
  int mid = (int)Math.Ceiling(double((head + tail) / 2)); //尼玛还是错的！Invalid expression term 'double' 
  =>
  int mid =(int)Math.Ceiling((double)((head + tail)/ 2))
  ```

  否则编译报错:The call is ambiguous between the following methods or properties: 'Math.Ceiling(decimal)' and 'Math.Ceiling(double)' 

- 错别字： Ceiling而不是 Cei**l**ling

-  **not all code paths return a value;** 需要注意一开始养成习惯



### 第一次提交代码：数组越界

```C#
public class Solution {
    public int Search(int[] nums, int target) {
        int head = 0;
        int tail = nums.Length;
        //int mid = (int)Math.Ceiling((double)((head + tail) / 2));
        while(tail >= head)
        {
            int mid = (int)Math.Ceiling((double)((head + tail) / 2));
            if(target == nums[mid]) return mid;
            if(target > nums[mid])
            {
                head = mid + 1;
                //mid = (int)Math.Ceiling((double)((head + tail) / 2));
                //这段代码出现了3次，一定有办法优化，这里是可以统一放到while loop里面优化
            }
            if(target < nums[mid])
            {
                tail = mid -1;
                //mid = (int)Math.Ceiling((double)((head + tail) / 2));
            }
        }
        return -1;
    }
}
```

```C#
[-1,0,3,5,9,12]
13
System.IndeOutOfRangeException: Index was outside the bounds of the array.
```



### 第二次提交

- public 和 class全是小写。。。

```C#
public class Solution {
    public int BinarySearch(int[] nums, int targe)
    {
        int head = 0;
        int tail = nums.Length -1; //这里一定要减去1，因为数组的下标是从0开始，而长度是从1开始；
        //while(tail > head)//必须考虑等于的情况，比如输入 [5],target=5,这种情况就会报错
        while(taile >=head) 
        {
            //int mid = (int)Math.Ceiling((double)(head + tail) / 2); //不能向上取整
            int mid = (int)((head + tail) /2);//默认向下取整
            if(targe = nums[mid])
            {
                return mid;
            }
            else if(target > nums[mid]) //目标数比中位数打，说明目标数在右边，需要改变左边的head的指针
            {
                head = mid +1 ;
            }
            else (target < nums[mid])//目标数比中位数小，在数字的右边，需要改变的是tail的指针
            {
                tail = mid -1;
            }
        }
        return -1;
    }
}
```



<img src="./img/image-20210908110951507.png" alt="image-20210908110951507" style="zoom: 67%;" />

#### 为何不能向上取整

```C#
[-1, 0, 3, 5, 9, 12 ]   

9
```

为例：

Loop1: (head + tail) /2 = (0+5) /2 = 3; 跳进(target > num[mid])内执行 3 +1 =4；

Loop2: (head + tail) / 2=(**4** +5) /2 =5; => num[5] = 12; 无法匹配到9；



### 第三次提交

```C#
public class Solution{
    public int BinarySearch(int[] nums, int target)
    {
        int left = 0;
        int right = nums.Length -1;//这里一定要减去1，因为数组的下标是从0开始，而长度是从1开始；
        while(right >=left) //必须考虑等于的情况，比如输入 [5],target=5,这种情况就会报错
        {
            int mid = (int)((left + right) /2);//默认向下取整
            if(target == nums[mid])
            {
                return mid;
            }
            if(target > nums[mid])//目标值比中间值大，于数组右边，需调整left的指针
            {
                left=mid +1;
            }
            if(target <num[mid])//目标值比中间小，于数字左边，需要调整right的指针
            {
                right = mid =1;
            }
        }
        return -1;
    }
}
```

```
执行用时：140 ms, 在所有 C# 提交中击败了22.93%的用户

内存消耗：35.1 MB, 在所有 C# 提交中击败了46.36%的用户
```





## 2021-9-9 First Bad Version

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which returns whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/first-bad-version
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



学到:

- 可以一次性申明2个同类型的变量： int head =0, buttom = n.Lenght;

- (head+buttom)/2 昨天我还没有意识到这样写有什么不对，今天才知道可能会导致**int溢出**

- 底部是 **bottom** 而不是 **buttom**,我之所以写错，大概是因为butt这个单词的混淆作用

  > Reference: [butt, bottom, buttock and ass?](https://ell.stackexchange.com/questions/39087/butt-bottom-buttock-and-ass)

- bottom有屁股的意思，尽量少用这个变量

### [第一次提交](https://leetcode-cn.com/problems/first-bad-version/solution/di-yi-ge-cuo-wu-ban-ben-by-leewang-x-v3we/)

```C#
/* The isBadVersion API is defined in the parent class VersionControl.
   bool IsBadVersion(int version); */
public class Solution:VersionControl{
    public int FirstBadVersion(int n)
    {
        int head = 0, bottom = n.Length;
        while(bottom >= head)
        {
            int mid = (bottom - head) /2 + head;
            if(IsBadVersion(mid))//中间的版本已经是出现错误了
            {
                if(IsBadVersion(mid-1))//再往前检查一位，如果前面那位是false，则说明中间版本是第一个错误版本
                {
                    return mid;
                }
                //中间版本就出现错误，说明第一个错误坐落在[head,mid]之间，因此需要修改bottom的指针
                bottom = mid -1;
            }
            else //中间的版本没有错误
            {
                if(IsBadVersion(mid+1))//往后检查一位，如果刚好出现true,则说明就是mid+1
                {
                    return mid +1;
                }
                //否则，说明错误坐落在[mid,bottom]之间，则需要调整head的指针
                head = mid +1;
            }
        }
    }
}
```

<img src="./img/image-20210909142435263.png" alt="image-20210909142435263" style="zoom: 50%;" />



<img src="./img/image-20210909142622356.png" alt="image-20210909142622356" style="zoom:50%;" />



```C#
执行用时：28 ms, 在所有 C# 提交中击败了99.40%的用户

内存消耗：14.9 MB, 在所有 C# 提交中击败了42.56%的用户
```

