# Longest Common Subsequence( LCS)[最長共同子序列]
[演算法介紹](http://web.ntnu.edu.tw/~algo/Subsequence2.html)

---

單個最長共同子序列
``` c
#include<iostream>
#include<stdio.h>
#define S1 9
#define S2 7
using namespace std;
int s1[S1] = {2,5,7,9,3,1,2,4,6};
int s2[S2] = {3,5,3,2,8,7,9};
int length[S1+1][S2+1];
int LCS[S1+1][S2+1];
char dir[S1+1][S2+1];
int seq[5];

void printLCS_recursive(int i,int j){
    if(i == 0 || j == 0)
        return;
    if(LCS[i][j] == 0){
        printLCS_recursive(i - 1, j - 1);
        printf("%d ",s1[i-1]);
    }
    else if(LCS[i][j] == 1){
        printLCS_recursive(i, j - 1);
    }else{
        printLCS_recursive(i - 1,j);
    }
}
int main(){
    for(int i = 0; i <= S1; ++i){
        length[i][0] = 0;
    }
    for(int j = 0; j <= S2; ++j){
        length[0][j] = 0;
    }

    for(int i = 1; i <= S1; ++i){
        for(int j = 1; j <= S2; ++j){
            if(s1[i - 1] == s2[j-1]){
                length[i][j] = length[i -1][j - 1] + 1;
                LCS[i][j] = 0;
            }else{
                length[i][j] = max(length[i - 1][j],length[i][j - 1]);
                if(length[i - 1][j] < length[i][j - 1]){
                    length[i][j] = length[i][j - 1];
                    LCS[i][j] = 1;
                }
                else{
                    length[i][j] = length[i - 1][j];
                    LCS[i][j] = 2;
                }

            }
        }
    }
    string tmp;
    for(int i = 0;i <= S1; ++i){
        for(int j = 0; j<= S2; ++j){
            if(LCS[i][j] == 0){
                tmp = "↖ ";
            }
            else if(LCS[i][j] == 1){
                tmp = "← ";
            }else{
                tmp = "↑ ";
            }
            cout<<tmp<<length[i][j];
        }
        printf("\n");
    }
    printf("LCS length: %d\n",length[S1][S2]);
    printf("LCS (Recursive): ");
    printLCS_recursive(S1,S2);
    printf("\n");

    return 0;
}

```
多個最長共同子序列
``` c
#include<iostream>
#include<stdio.h>
#define S1 9
#define S2 7
using namespace std;
int s1[S1] = {2,5,7,9,3,1,2,4,6};
int s2[S2] = {3,5,3,2,8,7,9};
int length[S1+1][S2+1];
int LCS[S1+1][S2+1];
char dir[S1+1][S2+1];
int seq[5];
int num[20];//堆疊容器
int maxCount=0;//最長共同子序列的最大是多少字
int numCount=0;//目前堆疊容器到哪一個位置
int outnum=0;//輸出與上一個比對
void printLCS_recursive(int i,int j){
    if(i == 0 || j == 0)
        return;
    if(LCS[i][j] == 0){
        printLCS_recursive(i - 1, j - 1);
        printf("%d ",s1[i-1]);
    }
    else if(LCS[i][j] == 1){
        printLCS_recursive(i, j - 1);
    }else{
        printLCS_recursive(i - 1,j);
    }
}
int main(){
    for(int i = 0; i <= S1; ++i){
        length[i][0] = 0;
    }
    for(int j = 0; j <= S2; ++j){
        length[0][j] = 0;
    }

    for(int i = 1; i <= S1; ++i){
        for(int j = 1; j <= S2; ++j){
            if(s1[i - 1] == s2[j-1]){
                length[i][j] = length[i -1][j - 1] + 1;
                LCS[i][j] = 0;
            }else{
                length[i][j] = max(length[i - 1][j],length[i][j - 1]);
                if(length[i - 1][j] < length[i][j - 1]){
                    length[i][j] = length[i][j - 1];
                    LCS[i][j] = 1;
                }
                else{
                    length[i][j] = length[i - 1][j];
                    LCS[i][j] = 2;
                }

            }
        }
    }
    string tmp;
    for(int i = 0;i <= S1; ++i){
        for(int j = 0; j<= S2; ++j){
            if(LCS[i][j] == 0){
                tmp = "↖ ";
            }
            else if(LCS[i][j] == 1){
                tmp = "← ";
            }else{
                tmp = "↑ ";
            }
            cout<<tmp<<length[i][j];
        }
        printf("\n");
    }
    printf("LCS length: %d\n",length[S1][S2]);
    printf("LCS (Recursive): ");
    printLCS_recursive(S1,S2);
    printf("\n");

    return 0;
}

```