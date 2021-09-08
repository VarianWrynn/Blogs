# 编程范式：命令式编程、声明式编程和函数式编程

@(.NET开发)[编程语言, 技术扫盲, 命令式编程, LeetCode]





## 2021-9-7

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





## 2021-9-8

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



<img src="./img/image-20210908110951507.png" alt="image-20210908110951507" style="zoom: 80%;" />

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

