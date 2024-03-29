# 迷路的牛牛

## :question:题目描述
牛牛去犇犇老师家补课，出门的时候面向北方，但是现在他迷路了。虽然他手里有一张地图，但是他需要知道自己面向哪个方向，请你帮帮他。    
>输入描述:
每个输入包含一个测试用例。
每个测试用例的第一行包含一个正整数，表示转方向的次数N(N<=1000)。
接下来的一行包含一个长度为N的字符串，由L和R组成，L表示向左转，R表示向右转。

>输出描述:
输出牛牛最后面向的方向，N表示北，S表示南，E表示东，W表示西。

## :bulb:解决思路
- swith-case语句判断，模拟转向操作
- 方向数组加索引操作，代码更加简洁

## :pencil2:代码-1
```c++
#include <iostream>
using namespace std;

int main(void){
    int times;
    char location = 'N';
    char turn;
    
    cin>>times;
    for(int i = 0; i < times; i++){
        cin>>turn;
        if(turn == 'L'){
            switch(location){
                case 'N':
                    location = 'W';
                    break;
                case 'S':
                    location = 'E';
                    break;
                case 'E':
                    location = 'N';
                    break;
                case 'W':
                    location = 'S';
            }
        }else{
            switch(location){
                case 'N':
                    location = 'E';
                    break;
                case 'S':
                    location = 'W';
                    break;
                case 'E':
                    location = 'S';
                    break;
                case 'W':
                    location = 'N';
            }
        }
    }
    cout<<location;
    return 0;
}
```
## :pencil2:代码-2
```C++
#include <iostream>
using namespace std;
int main() {
    char ans[] = {'N', 'E', 'S', 'W'};
    char turn;
    int n, cnt = 0;
    cin >> n;
    for (int i = 0; i < n; ++i) {
        cin>>turn;
        cnt = (cnt + (turn == 'L' ? -1 : 1) + 4) % 4;
    }
    cout << ans[cnt % 4];
}
```
[:arrow_left:上一题:安置路灯](PlaceStreetLamp.md)
[:arrow_right:下一题:数对](CountNumOfPair.md)