### 1878.Get-Biggest-Three-Rhombus-Sums-in-a-Grid

#### 解法1
枚举所有的点作为菱形的中心，然后计算它的“半径”的最大值```R=min(i,j,m-1-i,n-1-j)```。然后遍历所有半径，再暴力遍历它四条边所经过的所有格子。这个时间复杂度其实很大，枚举中心要o(MN)，固定中心之后枚举所有半径的菱形的边缘还需要o(MN)，你可以想象正中心的菱形，它需要遍历的格子与MN是相同数量级的。所以总的复杂度是o(MMNN).

#### 解法2
在解法1的基础上，在计算“一条边”的和时，我们容易想到用前缀和进行优化。我们提前计算左右对角线的前缀和数组。presum1[x][y]代表经过(x,y)的、从左上到右下的斜对角的前缀和。presum2[x][y]代表经过(x,y)的、从右上到左下的斜对角的前缀和。这样我们对于固定中心、半径后的菱形，每条边的计算就可以用前缀和之差来得到。时间复杂度是o(MN).