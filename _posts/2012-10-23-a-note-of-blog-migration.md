---
layout: post
title: "博客迁移小记"
description: "此博客原托管到Tumblr并绑定igorw.org的域名，由于种种原因迁移到GitHub（默认使用Jekyll解析静态页），我花了两个星期的闲暇时间断断续续的完成了这次迁移。这篇文章主要讲述我博客站点的来历和这次迁移的故事。"
category: 琐事 
tags: [Site Migration, Jekyll, Jekyll-Bootstrap, GitHub, Tumblr, MathJax, Pygments]
---
{% include JB/setup %}
<p>
	接触互联网后就有过几个博客，分布在百度Hi、校内/人人日志、BlogSpot、Tumblr、博客大巴、My Opera，blablabla...<br />
	不过完全都是处在随心瞎弄三天打渔两天晒网状态：或者是不爽了抱怨两句，或者是炫耀一下，或者是因为某种需要而开博。总结来说就是没有认真的对待过。
</p>
<p>
	让我真正有认认真真写博客的冲动是在疯狂的网络浮躁之后：<br />
	每天看着cnBeta上不断刷新的新闻以及里面没有深度为喷而喷的评论，硬件软件疯狂的更新换代，不同内容的网络骂战层出不穷 —— 新的事件不断的出现充斥着你的屏幕让人瞬间忘却昨天发生过什么。技术更迭和社交网络的各种信息碎片不断的涌现让满是流行词语的大脑木然而呆滞。<br />
</p>
<p>
	我在想：最新最强的硬件、唾手可得的信息给我们带来了什么？得到成千上万倍的处理器速度后真的比高中时用巴掌大小的破文曲星编写的程序更有乐趣，或者更多的创造力？对我来说答案非常确切，我丢失了那时的创造力和激情，羞愧于去回忆7、8年前的想法和创意，没有乐趣，麻木而痛苦。
</p>
<p>
	来点改变，做一些真正让自己感到脚碰触到地面的事情。
</p>
<p>
	近两年来的三个个人站点让我找到了自己还活着的感觉：
	<ol>
		<li>阮一峰的网络日志：<a href="http://www.ruanyifeng.com/blog/">http://www.ruanyifeng.com/blog/</a></li>
		<li>卢昌海的个人主页：<a href="http://www.changhai.org">http://www.changhai.org</a></li>
		<li>ShareYouCan: <a href="http://www.shareyoucan.com">http://www.shareyoucan.com</a></li>
	</ol>
</p>
<p>我并不耻于公开的说：那是我的榜样，我在模仿他们，甚至博客页面风格都是模仿<a href="http://www.ruanyifeng.com">阮一峰先生</a>的博客来的。</p>
<p>所以，有了这个想法，大概给自己的博客定了以下的标准（可能是幼稚不成熟的）：</p>
<blockquote class="r-background">
	<ul>
		<li>杜绝<strong>政治</strong>和实事内容；</li>
		<li>尽量避免可能引发<a href="http://baike.baidu.com/view/2871922.htm">三季人</a>式讨论或无聊争议的文章，对于此类的留言一概不回复；</li>
		<li>无个人情感内容在里面；</li>
		<li>坚持思考，坚持更新；</li>
	</ul>
</blockquote>
<p>事实上，不写个人观点不代表我没有个人观点，相反的，我不仅有个人观点而且非常强烈，亦如我博客里找不到性内容但这不代表我不淫荡。</p>
<p style="text-align:center;"><img style="border:solid; border-width:1px; width:500px;" src="/img/post/2012-10-23-a-note-of-blog-migration/A-big-F-to-all-P.jpg" /></p>
<p>
	有了这些想法以后事情变的明朗：我需要一个对读者来说易于阅读，对作者来说自由度高的博客平台。又由于自身条件的限制，我又需要一个经济支出最小的平台，能绑定域名。首先BlogSpot、Wordpress、Google App Engine因为众所周知的原因被排除（有免费的CDN加速后可访问，但连接速度还是太慢）。新浪、163、博客大巴、CSDN、点点等国内服务商又因为这样或那样的原因被否决（恕我孤陋寡闻，很有可能有更优秀的博客服务平台我不知道）。
</p>
<p>
	当时为我所知，剩下的只有Tumblr了，于是就把域名绑定Tumblr并开始写文章。
</p>
<p>
	但在使用了两三个月后，Tumblr的缺点凸显出来，愈发严重：
	<blockquote class="r-background">
		<ul>
			<li>自定义主题麻烦，可选择的免费主题要么不喜欢，要么不适合；</li>
			<li>
				<strong>
					编辑器简陋不堪，我没有找到办法自定义样式，即便是直接编辑html后提交后标签也会消失
				</strong>；
			</li>
			<li>代码语法高亮麻烦丑陋，用第三方方法插入公式后排版混乱；</li>
			<li>文章的URL生成带有冗长的ID，而我是个有心理洁癖的人；</li>
			<li>无法自定义<a href="/404">404页面</a>；</li>
			<li>...</li>
		</ul>
	</blockquote>
	特别是在排版上已经到了我无法容忍的地步，下定决心要换一个博客平台，碰巧看到了阮一峰的这篇文章：<a href="http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html">《搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门》</a>。
</p>
<p style="text-align:center;"><img style="border:solid; border-width:1px;" src="/img/post/2012-10-23-a-note-of-blog-migration/mess-tumblr-url-with-post-id.png" /><br /><span style="font-size:small;">Tumblr上混乱的URL</span></p>
<p>
	这样看起来，GitHub上建站的自由度是免费方案中除Google App Engine外最高的，而<a href="https://github.com/mojombo/jekyll">Jekyll</a>又自带有强大的<a href="http://pygments.org">Pygments</a>作为语法高亮方案，而默认的Markdown解析引擎Maruku又支持Latex生成png，所有的一切似乎都水到渠成。
</p>
<p>
	接下来在网上找到了<a href="http://jekyllbootstrap.com">Jekyll-Bootstrap</a>框架来使用，挑了里面的这个模板自己改了改，也顺便学习了HTML（哦，原谅我是个HTML痴吧）。把原来的博客连接都做了跳转处理，但因为GitHub无法配置301跳转，于是手工写了几个跳转页面。<br />
	此外还把博客的地址迁移到<a href="http://blog.igorw.org">blog.igorw.org</a>，而把<a href="http://igorw.org">igorw.org</a>改为了个人主页，主要放一些项目、个人简介等内容。</br>
	有兴趣的同学可以在<a href="https://github.com/waigx/blog">GitHub</a>上看到博客的源代码，如果觉得不错的话欢迎Fork。
</p>
<p>
	现在不爽的几件事：
</p>
<ul>
	<li>
		首先，到现在都没有搞清楚怎么用Maruku解析Latex，按照网上别人方法来也不行，现在用<a href="http://www.mathjax.org">MathJax</a>来处理数学公式。优点是可以复制，动态处理格式和大小；缺点是加载缓慢，性能不稳定偶尔排版会被打乱，<a href="/atom.xml">rss</a>输出后的格式也成问题；
	</li>
	<li>
		其次，原博客的DISQUS评论迁移请求已经提交，但到现在有的页面成功了，但是有的页面没成功，过几天有时间了再迁移一次试试吧；
	</li>
	<li>
		最后也是最重要的一点：新写的文章Google抓不到，回头再提交一下Sitemap看看 :)。
	</li>
</ul>
<p>&nbsp;</p>
<p style="text-align:right"><strong>全文完</strong></p>