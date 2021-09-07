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
        for(int i=0;i<nums.Lenght;i++)
        {
            for (int k = i+1;k<nums.Lenght;k++)
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

