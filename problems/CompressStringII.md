# 字符串压缩

## :question:题目描述
对字符串进行RLE压缩，将相邻的相同字符，用计数值和字符值来代替。例如：aaabccccccddeee，则可用3a1b6c2d3e来代替。

>输入描述:
输入为a-z,A-Z的字符串，且字符串不为空，如aaabccccccddeee

>输出描述:
压缩后的字符串，如3a1b6c2d3e

>示例:
输入
aaabccccccdd
输出
3a1b6c2d

## :bulb:解决思路
和字符串归一化类似，只不过不是统计全局的字符而是相邻的重复字符，我们使用pre表示上一次压缩的字符，初始化为#表示没有压缩，当前字符等于pre则计数加1，否则打印出来，这里还需要注意退出循环后最后一部分是没有打印出来的，所以还要手动补充上，类似的还有字符串单词转逆中的最后一个单词

## :pencil2:代码
```c++
#include <iostream>
#include <string>
using namespace std;
int main(void){
    int count = 0;
    char pre='#';
    string s, res;
    cin>>s;
    for(char c : s){
        if(pre == '#'){
            pre = c;
            ++count;
        }else if(c != pre){
            res.append(to_string(count)).append(1, pre);
            count = 1;
            pre = c;
        }else{
            ++count;
        }
    }
    //有些题目就是会出现还需要补上的情况
    res.append(to_string(count)).append(1, pre);
    cout<<res<<endl;
    return 0;
}
```
[:arrow_left:上一题:回文子串](SubstrPalindrome.md)
[:arrow_right:下一题:解析加减法运算](SimpleAddMinus.md)