### Selected LeetCode problems analysis  
[leetcode 72](https://leetcode.com/problems/edit-distance)
* Edit Distance (dynamic programmming)  
 
考虑到字符串```word```中间状态变化的复杂性，采用动态规划忽略对其每步操作的处理，抽象为对状态转移的研究。  
对于```dp```数组，定义```dp[i][j]```为 易给出初始```dp[i][0]```,```dp[0][j]```然后两重循环计算

```cpp
int minDistance(string word1, string word2) {
    int len1 = word1.length(),len2 = word2.length();
    int dp[len1+1][len2+1];
    for(int i=0;i<=len1;i++){
        dp[i][0] = i;
    }
    for(int j=0;j<=len2;j++){
        dp[0][j] = j;
    }
    for(int i=1;i<=len1;i++){
        for(int j=1;j<=len2;j++){
            if(word1[i-1]==word2[j-1]){
                dp[i][j] = dp[i-1][j-1];
            }
            else {
                dp[i][j] = min(dp[i-1][j-1],min(dp[i][j-1],dp[i-1][j])) + 1;
            }
        }
    }
    return dp[len1][len2];
}
```