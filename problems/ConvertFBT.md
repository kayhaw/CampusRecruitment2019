# 将满二叉树转换为求和树

## :question:题目描述
给满出二叉树，编写算法将其转化为求和树
什么是求和树：二叉树的求和树， 是一颗同样结构的二叉树，其树中的每个节点将包含原始树中的左子树和右子树的和。
```
二叉树：
                  10
               /      \
             -2        6
           /   \      /  \ 
          8    -4    7    5

求和树：
                 20(4-2+12+6)
               /      \
           4(8-4)      12(7+5)
            /   \      /  \ 
          0      0    0    0
```
二叉树给出前序和中序输入，求和树要求中序输出；
所有处理数据不会大于int； 

>输入描述:
2行整数，第1行表示二叉树的前序遍历，第2行表示二叉树的中序遍历，以空格分割

>输出描述:
1行整数，表示求和树的中序遍历，以空格分割

>示例:
输入
10 -2 8 -4 6 7 5
8 -2 -4 10 7 6 5
输出
0 4 0 20 0 12 0

## :bulb:解决思路
因为是满二叉树，其实结果跟前序遍历数组无关，只和中序遍历数组有关，并且中序数组一定是奇数个，结果索引为偶数的一定为0，索引为奇数的值是中序遍历数组其他值之和(不包括自己)，使用二分法找到根节点，然后计算子树之和，**不用还原二叉树**

## :pencil2:代码
```c++
#include <iostream>
#include <sstream>
#include <vector>
#include <string>
#include <iterator>
#include <algorithm>
#include <numeric>
using namespace std;

void sumtree(vector<int> &inorder, int left, int right){
    int mid = (left + right)/2;
    if(mid == left){
        inorder[mid] = 0;
        return;
    }
    inorder[mid] = accumulate(inorder.begin()+left, inorder.begin()+right, -inorder[mid]);
    sumtree(inorder, left, mid);
    sumtree(inorder, mid+1, right);
}

int main(void){
    string line;
    getline(cin, line);
    istringstream pre_stream(line);
    vector<int> preorder((istream_iterator<int>(pre_stream)), istream_iterator<int>());
    getline(cin, line);
    istringstream in_stream(line);
    vector<int> inorder((istream_iterator<int>(in_stream)), istream_iterator<int>());
    sumtree(inorder, 0, inorder.size());
    copy(inorder.begin(), inorder.end(),ostream_iterator<int>(cout, " "));
    cout<<endl;
    return 0;
}
```
[:arrow_left:上一题:获得最多的奖金](FindMostBonus.md)
[:arrow_right:下一题:搭积木](PlayLego.md)