+++
title = "Sagemath example"
date = 2024-07-15
[taxonomies]
tags = ["math"]
[extra]
math = true
comment = true
+++

*Powered by [MathJax](https://www.mathjax.org/) and [SageMath](https://www.sagemath.org/)*

---

<p>When \(a \ne 0\), there are two solutions to \(ax^2 + bx + c = 0\) and they are
  \[x = {-b \pm \sqrt{b^2-4ac} \over 2a}.\]
</p>

### SageCell示例

#### 简单计算

<div class="sage"><code type="text/x-sage">
print("Hello from SageCell!")

#三角函数图像
plot(sin(x), (x, 0, 2*pi))
</code></div>

<div class="sage"><script type="text/x-sage">
[1,2,3]

#測試注釋

plot(cos(1/x), (x, 0, 2*pi))
</script></div>

#### 交互式计算

<div class="sage">
@interact
def _(a=(1, 10)):
    print(factorial(a))
</div>