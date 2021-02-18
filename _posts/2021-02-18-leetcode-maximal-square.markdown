---
layout: post
title:  "Leetcode: Maximal Square"
date:   2021-02-18 11:20:23 +0700
categories: [Algo]
---
Link: https://leetcode.com/problems/maximal-square/

Parsing JSON with Ruby is actually extremely easy. All you have to do is have the json gem installed (`gem install json`) and call the `JSON.parse` method on the JSON data to convert it to ruby hashes. If you look at this small program here, you can see how I have implemented parsing JSON in Ruby.

{% highlight java %}
public int maximalSquare(char[][] matrix) {
    int rows = matrix.length, cols = rows > 0 ? matrix[0].length : 0;
    int[][] dp = new int[rows + 1][cols + 1];
    int maxsqlen = 0;
    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= cols; j++) {
            if (matrix[i-1][j-1] == '1'){
                dp[i][j] = Math.min(Math.min(dp[i][j - 1], dp[i - 1][j]), dp[i - 1][j - 1]) + 1;
                maxsqlen = Math.max(maxsqlen, dp[i][j]);
            }
        }
    }
    return maxsqlen * maxsqlen;
}
{% endhighlight %}
