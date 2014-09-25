---
layout: post
---


今天晚上上TA的数值分析课，同学们做project。看的statistical learning的6.2节shrinkage methods，以下是一些需要注意的地方：

1. 之前subset fit的方法都是用最小二乘。而这里的技巧是改变一下最小二乘的目标函数RSS，把系数加进去。Ridge惩罚项的系数是二次方。
2. Ridge不惩罚常数项，只惩罚系数。$\lambda$是tuning parameter，用cross-validation。
3. 用之前归一化一下方差。不同的scale对优化问题有影响。
4. 比最小二乘好的原因是舍弃（增加）了一点bias，换来了variance的减少（更多）。而且每个$\lambda$只需要fit一个模型。



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