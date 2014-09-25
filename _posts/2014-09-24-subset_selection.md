---
layout: post
---


今天下午换机油，晚上烙饼了。看的statistical learning的6.1节subset selection，以下是一些需要注意的地方：

1. 那些选子集的方法都是剩下不同个数的变量下的最好的模型，然后最后一步都是从别的方法挑哪个是最好的。为什么不还用之前的指标？因为RSS或者$R^2$都是单调的变量越多越好。这个有利于training error rate，而不（一定）利于testing error rate。事实：training error rate是testing error rate的很差估计。
2. 解决方法：第一种是间接的：修正一下RSS或者$R^2$指标。就有了$C_p$, AIC, BIC, adjust-$R^2$什么的。BIC比AIC惩罚变量个数惩罚得更厉害（系数更大n>7）。
3. 前三者都是越小越好，后面的adjust-$R^2$是越大越好。不过貌似后者没有前三个好。
4. 解决方法：第二种是直接的：直接估test error rate，就用validation或者cross-validation的方法。最后比如对不同个数的model算MSE，那后几个（变量个数多了）要是都差不多，怎么办？用one-standard-error rule：算不同模型的MSE的标准差，找最低点的一个标准差里面变量个数最小的那个。
5. 注：找变量个数最小的当然是为了模型简单。为什么不直接选那个MSE最小的，而去搞个一个标准差里面的某个（变量个数最少的）？是因为不同的data set什么的Vlidation或者CV之类的方法得到的结果不一定一样。但是在一个标准差里找应该就不会太差。

ccorknn的程序改了一下，貌似就是一个dimension搞错了。把1变成2就好了，就从单减变成单增了，好神奇。


<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>