---
layout: post
title: How to Typeset Math in a Blog
categories: Website-Design
---

I want to write some math equations in this blog. [MathJax](https://www.mathjax.org/) is a Javascript library that displays mathematical notation on web browsers. Apparently, we just have to copy paste the following code in Tumblr HTML, just before the <\head> tag:

{% highlight html %}
<script type="text/x-mathjax-config">
       MathJax.Hub.Config({
       extensions: ["tex2jax.js"],
       jax: ["input/TeX", "output/HTML-CSS"],
       tex2jax: {
       inlineMath: [[ '$','$']],
       displayMath:  [['$$','$$']],
       processEscapes: true
       },
       "HTML-CSS": { availableFonts: ["TeX"] }
       });
</script> 

<script type="text/javascript" async
      src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
{% endhighlight %}

'''

Example code: 
Maths between dollars is inline: $p = \alpha C_{dyn} V_{dd}^2f + I_{leak}V_{dd}$

Maths between two dollar signs is display as a separate equation: $$ p = \alpha C_{dyn} V_{dd}^2f + I_{leak}V_{dd} $$ 

Example output:   

Maths between dollars is inline: $p = \alpha C_{dyn} V_{dd}^2f + I_{leak}V_{dd}$

Maths between two dollar signs is display as a separate equation: $$  p = \alpha C_{dyn} V_{dd}^2f + I_{leak}V_{dd}  $$

Tips: 
Make sure that you write the math as normal text. If it is code type in tumblr then it will not be rendered. 
You can change the identifiers to display inline vs display math in the code. Documentation [Link](http://docs.mathjax.org/en/latest/start.html)
