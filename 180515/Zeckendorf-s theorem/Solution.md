首先假设有方法`f(u)`可以将u转化为“齐肯多夫表示法”。

那么对于任一非斐波那契数n，易知肯定有 F<sub>i+1</sub> > n > F<sub>i</sub>。

由斐波那契数的性质，易得 n - F<sub>i</sub> < F<sub>i - 1</sub>。

所以，对于`f(n)`，我们有 f(n) = F<sub>i</sub> + f(v)。这里 v < F<sub>i - 1</sub>。

于是我们可以得出组成v的最大斐波那契数一定小于F<sub>i - 1</sub>，所以一定存在满足数n的“齐肯多夫表示法”。

代码详见文件夹里的"main.py"文件。

p.s. 如果我们再多想一步，本题可以直接使用贪心的做法来解。即预处理所有的斐波那契数，每一次选出并减去小于等于当前数的斐波那契数。最后也一定可以找到满足条件的组合。
