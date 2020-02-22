# frog-step
一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：

输入：n = 2
输出：2

示例 2：

输入：n = 7
输出：21

class Solution {
public:
    int numWays(int n) {
        unordered_map<int,int> memo;
        memo[0] = 1;
        memo[1] = 1;
        return helper(n, memo);
    }
    int helper(int n, unordered_map<int,int>& m) {
        if(m.count(n)) return m[n];
        int res = helper(n-1, m) + helper(n-2, m);
        res %= 1000000007;
        m[n] = res;
        return res;
    }
};
