---
layout: post
title: "对一类无穷乘积收敛的估计"
description: "对于无穷乘积一般都是取对数处理，本文直接对无穷乘积进行初等变换，而后对其值的范围进行估计。原发表于2007年第12期《数学通讯》。"
category: 数学
tags: [Infinite Product, Infinite Series, Mathematic, Mathematical Analysis]
isMath: 1
---
{% include JB/setup %}
<p>先给出结论：</p>
<blockquote class="r-background">
	<p>对于数列\(\{\varphi_{n}\},n\in\mathbf{N}^{+}\)，若有：</p>
	$$ \sum_{i=1}^\infty\varphi_{i}=\beta>1,\varphi_{i}\in(0,1) $$
	<p>那么：</p>
	$$(1-\varphi_{2})(1-\varphi_{3})(1-\varphi_{4})\cdots(1-\varphi_{n})>1+\varphi_{1}-\beta\qquad(1)$$
	$$(1+\varphi_{2})(1+\varphi_{3})(1+\varphi_{4})\cdots(1+\varphi_{n})&lt;\frac{1}{1+\varphi_{1}-\beta}\qquad(2)$$
</blockquote>
<p>下面我们先用数学归纳法来证明(1)式：</p>
<ol>
	<li>
		当\(n=2\)时，\(1-\varphi_{2}-(1+\varphi_{1}-\beta) = \beta - \varphi_{1} - \varphi_{2}&gt;0\)，命题成立。
	</li>
	<li>
		当\(n\geq3\)时，不妨设$$p_{n}=\prod_{i=2}^{n}(1-\varphi_{i})$$则\(p_{2}=1-\varphi_{2}\)，易得\(p_{n}&lt;1\)。
		
		$$\therefore p_{n} = (1-\varphi_{n})p_{n-1} = p_{n-1}-p_{n-1}\varphi_{n} = p_{n-1}-\varphi_{n}\;(n \geq 2)$$
		
		$$\therefore p_{n}&gt;p_{n-1}-\varphi_{n}&gt;p_{n-2}-(\varphi_{n-1}+\varphi_{n})&gt;\cdots&gt;p_{2}-\sum_{i=3}^{n}\varphi_{i}\\= 1-\sum_{i=2}^{n}\varphi_{i}&gt;1-\sum_{i=2}^{\infty}\varphi_{i}=1+\varphi_{1}-\beta$$
		
		$$\therefore p_{n}=(1-\varphi_{2})(1-\varphi_{3})\cdots(1-\varphi_{n})&gt;1+\varphi_{1}-\beta$$
	</li>
	<li>
		至此，(1)式证毕。
	</li>
</ol>
<p></p>
<p>下面我们来证明(2)式：</p>
<ul>
	<li>再设：
		$$p_{n}=\prod_{i=2}^{n}(1-\varphi_{i})，t_{n}=\prod_{i=2}^{n}(1+\varphi_{i})$$

		则有：
		$$k_{n}=p_{n}\cdot t_{n}=\prod_{i=2}^{n}(1-\varphi_{i}^{2})\quad(n\in\mathbf{N}^{+})$$

		又由(1)中结论得知\(p_{n}&gt;(1-\varphi_{1})(1+\varphi_{1}-\beta)&gt;0\)，而\(k_{n}&lt;1\)，
		$$\therefore t_{n}= \frac{k_{n}}{p_{n}}&lt;\frac{1}{(1-\varphi_{1})(1+\varphi_{1}-\beta)}$$故\(t_{n}\)必有上限。<br />
		设$$\lim_{n \to \infty}t_{n}=C$$
		则易知\(t_{n}&lt;C\)，\(t_{1}=1+\varphi_{1}\)，\(t_{n}=t_{n-1}\cdot(1+\varphi_{n})\quad(n\geq 2)\)<br />
	</li>
	<li>
		<p>下面用数学归纳法继续证明(2)成立：</p>
		<ol>
			<li>
				当\(n=2\)时，
				$$\because (1+\varphi_{2})-\frac{1}{1+\varphi_{1}-\beta}&gt;1+\varphi_{2}-\frac{1}{1-\varphi_{2}}=\frac{-\varphi_{2}^{2}}{1-\varphi_{2}}&lt;0$$
				$$\therefore 1+\varphi_{2}&lt;\frac{1}{1+\varphi_{1}-\beta}$$
			</li>
			<li>
				当\(n\geq3\)时，\(t_{n}&lt;t_{n-1}+\varphi_{n}\cdot C\)，

				$$\therefore t_{n}&lt;t_{n-1}+\varphi_{n}\cdot C&lt;t_{n-2}+(\varphi_{n-1}+\varphi_{n})\cdot C&lt;\cdots &lt;t_{1}+C\cdot \sum_{i=2}^{\infty}\varphi_{i}&lt;1+\varphi_{1}+C\cdot(\beta-\varphi_{1}),$$


				\(\therefore\)当\(n\to\infty\)时，\(C\leq1+\varphi_{1}+C\cdot(\beta-\varphi_{1})\)，可解得\(C\leq\frac{1+\varphi_{1}}{1+\varphi_{1}-\beta}\)，\(\therefore t_{n}&lt;\frac{1+\varphi_{1}}{1+\varphi_{1}-\beta}\)，
				$$\therefore (1+\varphi_{1})(1+\varphi_{2})\cdots(1+\varphi_{n})&lt;\frac{1}{1+\varphi_{1}-\beta}$$
			</li>
			<li>
				这样我们就证明了(2)。
			</li>
		</ol>
	</li>
</ul>
<p />
<p>由此我们可以获得一些有趣的结论（括号中是该结论所用到的极限）：</p>
<ol>
	<li>
		$$\prod_{i=2}^{\infty}\big(1-\frac{1}{i!}\big)&gt;\frac{7}{4}-\frac{e}{2},\quad\prod_{i=2}^{\infty}\big(1+\frac{1}{i!}\big)&lt\frac{3}{7-2e}\qquad\bigg(\sum_{i=2}^{\infty}{\frac{1}{i!}}=e-2\bigg)$$
	</li>
	<li>
		$$\prod_{i=2}^{\infty}\big(1-\frac{1}{i^{2}}\big)&gt;\frac{27}{16}-\frac{\pi^{2}}{8},\quad\prod_{i=2}^{\infty}\big(1+\frac{1}{i^{2}}\big)&lt\frac{15}{27-2\pi^{2}}\qquad\bigg(\sum_{i=2}^{\infty}{\frac{1}{i^{2}}}=\frac{\pi^{2}}{6}-1\bigg)$$
	</li>
	<li>
		$$\prod_{i=2}^{\infty}(1-C_{n}^{i}\cdot\frac{1}{i!})&gt;\frac{7}{4}-\frac{e}{2},\quad\prod_{i=2}^{\infty}(1+C_{n}^{i}\cdot\frac{1}{i!})&lt\frac{3}{7-2e}\\\Bigg(\lim_{n \to \infty}\bigg(\big(\frac{1}{n}+1\big)^{n}-2\bigg)=\lim_{n \to \infty}\bigg(\sum_{i=2}^{n}C_{n}^{i}\cdot\frac{1}{n^{i}}\bigg)=e-2\Bigg)$$
	</li>
</ol>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p style="text-align:right"><strong>全文完</strong></p>