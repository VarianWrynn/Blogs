# What is modular arithmetic?

@(.NET开发)[编程语言, 技术扫盲, 命令式编程, LeetCode,SQL-取模, 取模运算]

[toc]



在刷LeetCode[第12题](https://leetcode-cn.com/problems/integer-to-roman/solution/zheng-shu-zhuan-luo-ma-shu-zi-by-leetcod-75rs/)的时候，对于硬编码的解法有点一脸懵逼，主要是对取模这个机制原来不理解。

- 1994%1000 = 994：获得的余数是百位数；

  > 把1994个水果**均分**给1000个人，最后还能剩下994个水果

- 1994% 100= 94：获得十位数

- 1994%10=4；获得个位数

- 1994%2=0

  >  把1994个水果**均分**给2个人，最后还能剩下多少个？0个

- 1994%1000=1994

  > 把1994个水果**均分**给1万个人？分不出去，只能留在自己手里啃了。

- -1994% 1000： 厚礼蟹，只能上[Stackoverflow](https://stackoverflow.com/questions/17524673/understanding-the-modulus-operator/17525046)和[可汗学院](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/what-is-modular-arithmetic)查这是啥意思了



## What is modular arithmetic?

## An Introduction to Modular Math

When we divide two integers we will have an equation that looks like the following:

 $$\dfrac{A}{B} = Q \text{ remainder } R $$



*A* is the dividend
*B* is the divisor
*Q* is the quotient
*R* is the remainder

Sometimes, we are only interested in what the **remainder** is when we divide A*A*A by B*B*B.
For these cases there is an operator called the modulo operator (abbreviated as mod).

Using the same A*A*A, B*B*B, Q*Q*Q, and R*R*R as above, we would have: A \text{ mod } B = R*A* mod *B*=*R*A, start text, space, m, o, d, space, end text, B, equals, R

We would say this as *A* *modulo* *B* *is equal to* R*R*R. Where B*B*B is referred to as the **modulus**.

For example:

> 13513 mod 5==2 remainder **3**

## Visualize modulus with clocks

Observe what happens when we increment numbers by one and then divide them by 3.

> 03132333435363=======0 remainder **0**0 remainder **1**0 remainder **2**1 remainder **0**1 remainder **1**1 remainder **2**2 remainder **0**

The remainders start at 0 and increases by 1 each time, until the number reaches one less than the number we are dividing by. After that, the sequence **repeats**.

By noticing this, we can visualize the modulo operator by using circles.

We write 0 at the top of a circle and continuing clockwise writing integers 1, 2, ... up to one less than the modulus.

For example, a clock with the 12 replaced by a 0 would be the circle for a modulus of 12.

![img](https://cdn.kastatic.org/ka-perseus-images/809662edbc068ea7e9c91becdcad5fd36078ee07.jpg)

To find the result of A \text{ mod } B*A* mod *B*A, start text, space, m, o, d, space, end text, B we can follow these steps:

1. Construct this clock for size B*B*B
2. Start at 0 and move around the clock A*A*A steps
3. Wherever we land is our solution.

(If the number is positive we step clockwise, if it's **negative** we step **counter-clockwise**.)

## Examples

$8 \text{ mod } 4 = ?$

With a modulus of 4 we make a clock with numbers 0, 1, 2, 3.
We start at 0 and go through 8 numbers in a clockwise sequence 1, 2, 3, 0, 1, 2, 3, 0.

![img](https://cdn.kastatic.org/ka-perseus-images/6985b5aad53b5290f3f0eb64bf9529428a0362cc.jpg)

We ended up at **0** so 8 \text{ mod } 4 = \bf{0}8 mod 4=**0**8, start text, space, m, o, d, space, end text, 4, equals, 0.

$$7 \text{ mod } 2 = ?$$

With a modulus of 2 we make a clock with numbers 0, 1.
We start at 0 and go through 7 numbers in a clockwise sequence 1, 0, 1, 0, 1, 0, 1.

![img](https://cdn.kastatic.org/ka-perseus-images/cc504f5d837e4bf480bf2f0acc5496ca1cfebdcc.jpg)

We ended up at **1** so 7 \text{ mod } 2 = \bf{1}7 mod 2=**1**7, start text, space, m, o, d, space, end text, 2, equals, 1.

$$-5 \text{ mod } 3 = ?$$

With a modulus of 3 we make a clock with numbers 0, 1, 2.
We start at 0 and go through 5 numbers in **counter-clockwise** sequence (5 is **negative**) 2, 1, 0, 2, 1.

![img](https://cdn.kastatic.org/ka-perseus-images/7182f3b5a4573a4846e1297388c97516550c3fba.jpg)

We ended up at **1** so -5 \text{ mod } 3 = \bf{1}−5 mod 3=**1**minus, 5, start text, space, m, o, d, space, end text, 3, equals, 1.

## Conclusion

If we have A \text{ mod } B*A* mod *B*A, start text, space, m, o, d, space, end text, B and we increase A*A*A by a **multiple of \bf{B}\**B\**B**, we will end up in the same spot, i.e.

$$A \text{ mod } B = (A + K \cdot B) \text{ mod } B  \text{  for Integer  K}$$

For example:

> 3 mod 10=313 mod 10=323 mod 10=333 mod 10=3

## Notes to the Reader

### mod in programming languages and calculators

Many programming languages, and calculators, have a mod operator, typically represented with the % symbol. If you calculate the result of a negative number, some languages will give you a negative result.
e.g.

```
-5 % 3 = -2.
```

### Congruence Modulo

You may see an expression like:

$$A \equiv B\ (\text{mod } C)$$

This says that A*A*A is **congruent** to B*B*B modulo C*C*C. It is similar to the expressions we used here, but not quite the same.

In the next article we will explain what it means and how it is related to the expressions above.





## Reference 

1. [What is modular arithmetic?--khanacademy](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/what-is-modular-arithmetic)
2. [[Understanding The Modulus Operator %](https://stackoverflow.com/questions/17524673/understanding-the-modulus-operator)--Stackoverflow](https://stackoverflow.com/questions/17524673/understanding-the-modulus-operator/17525046)

