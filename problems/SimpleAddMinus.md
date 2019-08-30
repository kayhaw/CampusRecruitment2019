# 解析加减法运算

## :question:题目描述
解析加减法运算    
如：    
输入字符串："1+2+3" 输出："6"    
输入字符串："1+2-3" 输出："0"    
输入字符串："-1+2+3" 输出："4"    
输入字符串："1" 输出："1"    
输入字符串："-1" 输出："-1"    
已知条件：输入的运算都是整数运算，且只有加减运算    
要求：输出为String类型，不能使用内建的eval()函数

>输入描述:
字符串"1+2+3"

>输出描述:
6

## :bulb:解决思路
简单的加减法没有运算符优先级，只需要简单地把所有的数字解析出来，然后根据前面的+、-进行相应的运算，注意循环出来后还需要再写一行代码来计算最后一个运算

## :pencil2:代码
```c++
#include <cstdio>
using namespace std;
int main(void){
    char c;
    int res = 0, num = 0;
    bool positive = true;        //是否为正数
    while((c = getchar()) != '\n'){
        if(c == '+'){
            res += positive ? num : -num;
            positive = true;
            num = 0;
        }else if(c == '-'){
            res += positive ? num : -num;
            positive = false;
            num = 0;
        }else{
            num = num * 10;
            num += c - '0';
        }
    }
    res += positive ? num : -num;
    printf("%d\n", res);
    return 0;
}
```
[:arrow_left:上一题:字符串压缩](CompressStringII.md)
[:arrow_right:下一题:求连续子数组的最大和](MaxSumOfSubArray.md)