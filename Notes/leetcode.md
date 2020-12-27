### Selected LeetCode problems analysis  
[leetcode 72](https://leetcode.com/problems/edit-distance)
* Edit Distance (dynamic programmming)  
 
���ǵ��ַ���```word```�м�״̬�仯�ĸ����ԣ����ö�̬�滮���Զ���ÿ�������Ĵ�������Ϊ��״̬ת�Ƶ��о���  
����```dp```���飬����```dp[i][j]```Ϊ �׸�����ʼ```dp[i][0]```,```dp[0][j]```Ȼ������ѭ������

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