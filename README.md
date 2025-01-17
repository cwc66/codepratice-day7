# codepratice-day7
代码随想录第七天
字符串操作基础。


[反转字符串 ](https://leetcode.cn/problems/reverse-string/)
双指针，交换到中间
```CPP
class Solution {
public:
    void reverseString(vector<char>& s) {
        for(int i=0,j=s.size()-1;i<s.size()/2;i++,j--)
        {
            swap(s[i],s[j]);
        }
    }
};
```

[反转字符串II](https://leetcode.cn/problems/reverse-string-ii/description/)
判断一下，最后的字符串还是否有k个以上到2k之间，如果是，只反转前K,否则全部反转(剩余小于k，即i+k<=s.size())
```CPP
class Solution {
public:
    void reverseString(vector<char>& s) {
        for(int i=0,j=s.size()-1;i<s.size()/2;i++,j--)
        {
            swap(s[i],s[j]);
        }
    }
};
```

替换数字
这道题目在卡码网，难度在于时间复杂度只在o(n)，需要双指针，首先如果有数字，扩充5倍数字数量。
然后双指针，一个在数字位，一个在后位，给number这个字符赋值，如果数字位这个指针没有遇到数字，就将数字位指针的字母给后位。



#include <iostream>
using namespace std;
int main()
{
    string s;
    while(cin>>s)
    {
        int soldindex=s.size()-1;
        int count=0;
        for(int i=0;i<s.size();i++)
        {
            if(s[i]>='0'&&s[i]<='9')
            {
                count++;
            }
        }
        
        s.resize(s.size()+count*5);
        int snewindex=s.size()-1;
        
        while(soldindex>=0)
        {
            if(s[soldindex]>='0'&&s[soldindex]<='9')
            {
                s[snewindex--]='r';
                s[snewindex--]='e';
                s[snewindex--]='b';
                s[snewindex--]='m';
                s[snewindex--]='u';
                s[snewindex--]='n';
            }
            else
            {
                s[snewindex--]=s[soldindex];
            }
            soldindex--;
        }
        cout<<s<<endl;
    }
}



