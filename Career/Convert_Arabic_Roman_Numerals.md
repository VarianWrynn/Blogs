# How to Convert Arabic Integers to Roman Numerals







Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

```C#
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, 2 is written as II in Roman numeral, just two one’s added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9.
X can be placed before L (50) and C (100) to make 40 and 90.
C can be placed before D (500) and M (1000) to make 400 and 900.
Given an integer, convert it to a roman numeral.

Example 1:
Input: num = 3
Output: “III”

Example 2:
Input: num = 4
Output: “IV”

Example 3:
Input: num = 9
Output: “IX”

Example 4:
Input: num = 58
Output: “LVIII”
Explanation: L = 50, V = 5, III = 3.

Example 5:
Input: num = 1994
Output: “MCMXCIV”
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

Constraints:
1 <= num <= 3999



## ALGORITHM TO CONVERT INTEGER TO ROMAN NUMERALS

Since we know the Mapping from Romans to Arabic and vice versa, we can greedily deduct the current biggest value in the mapping table and concatenate the result until the value reaches zero:

### C++ 

C++ CODE TO CONVERT NUMBERS TO ROMAN NUMERALS

```c++
class Solution {
public:
    string intToRoman(int num) {
        vector<pair<int, string>> romans({
            {1000, "M"},
            {900, "CM"},
            {500, "D"},
            {400, "CD"},
            {100, "C"},
            {90, "XC"},
            {50, "L"},
            {40, "XL"},
            {10, "X"},
            {9, "IX"},
            {5, "V"},
            {4, "IV"},
            {1, "I"}        
        });
        string roman = "";
        while (num > 0) {
            for (auto &[v, r]: romans) {
                if (num >= v) {
                    num -= v;
                    roman += r;
                    break;
                }
            }
        }
        return roman;
    }
};
```

### C# 

C# IMPLEMENTATION TO CONVERT ARABIC NUMBERS TO ROMAN

```C#
public class Solution {
        protected readonly Dictionary<int, string> RomanLetters = new Dictionary<int, string>
        {
            {1000, "M"},
            {900, "CM"},
            {500, "D"},
            {400, "CD"},
            {100, "C"},
            {90, "XC"},
            {50, "L"},
            {40, "XL"},
            {10, "X"},
            {9, "IX"},
            {5, "V"},
            {4, "IV"},
            {1, "I"}
        };
    
    public string IntToRoman(int value) {
            var romain = new StringBuilder();
            while (value > 0)
            {
                foreach (var key in RomanLetters.Keys)
                {
                    if (value >= key)
                    {
                        value -= key;
                        romain.Append(RomanLetters[key]);
                        break;
                    }
                }
            }
            return romain.ToString();        
    }
}
```



### PYTHON 

PYTHON IMPLEMENTATION TO CONVERT ARABIC NUMBERS TO ROMAN NUMERALS

```python
class Solution:
    def intToRoman(self, num: int) -> str:
        rules = (
            ("M", 1000),
            ("CM", 900),
            ("D",  500),
            ("CD", 400),
            ("C",  100),
            ("XC",  90),
            ("L",   50),
            ("XL",  40),
            ("XXX", 30),
            ("XX",  20),
            ("X",   10),
            ("IX",   9),
            ("V",    5),
            ("IV",   4),
            ("I",    1),
        )
        
        res = ""
        for suf, val in rules:
            while num >= val:
                num -= val
                res += suf
                
        return res
```



### JAVASCRIPT 

JAVASCRIPT CODE TO CONVERT ROMANS TO ARABIC INTEGERS

```javascript
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function(num) {
    const rules = {
        "M" : 1000,
        "CM" : 900,
        "D" : 500,
        "CD": 400,
        "C":  100,
        "XC":  90,
        "L":   50,
        "XL":  40,
        "XXX": 30,
        "XX":  20,
        "X":   10,
        "IX":   9,
        "V":    5,
        "IV":   4,
        "I":    1          
    }
    let res = "";
    const romans = Object.keys(rules);
    for (let i = 0; i < romans.length; ++ i) {
        const val = rules[romans[i]];
        while (num >= val) {
            num -= val;
            res += romans[i];
        }
    }
    return res;
};
```



To Convert Romans to Arabic, you can refer to this: [How to Convert Roman to Integer in C/C++?](https://helloacm.com/how-to-convert-roman-to-integer-in-cc/)

And here is [an online tool](https://helloacm.com/tools/romans/) with API to convert between Arabic and Roman Numerals.

–EOF ([The Ultimate Computing & Technology Blog](https://helloacm.com/)) —

## Reference

1. [How to Convert Arabic Integers to Roman Numerals?](https://helloacm.com/how-to-convert-arabic-integers-to-roman-numerals/)