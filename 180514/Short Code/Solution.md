这题与GCJ2018 1C的第一题非常像，所以容易想到使用Trie树（又称前辍树）来表示这些不重复的字符串。

所以Trie树的任意一棵子树都可以理解成整个问题的一个子问题。

以以下的数据为例：

* code
* codeforces
* codehorses

假设我们有方法`f`可以解决最优压缩问题。

对于以`code`做为固定前辍的子树，那么我们的问题就变成了：

* forces
* horses

（"code"串在以上两个串的上一层节点中，故这里不考虑”

这两个字符串的最优压缩方式，为"h"和"f"。

然后我们考虑上一层子树的情况，我们发现如果以`cod`为前辍，那么三个串（考虑下一层子树的压缩结果）为：

* e
* eh
* ef

使用相同的方法推倒，结果依次为

* ("d", "de", "def")
* ("o", "od", "ode")
* ("c", "co", "cod")

所以，我们可以从最深的子树开始，一层一层上推，并且维护子树表示的字符串的最优压缩结果即可。

上推的规则如下：

* 如果当前节点代表字符串的结束，则新加入此字符串
* 否则，删除子树中的最长已压缩的字符串，使用当前单个字符表示原先最长的已压缩字符串（这里可以使用multiset<int>来加速）

总的说来，本题的思路是“在Trie上的数学归纳法”，或者说是“在Trie上的DP”。
