---
layout: post
title: "什么是 UTF-8"
description: "关于UTF-8及相关编码格式简介的翻译。"
category: 计算机
tags: [UTF-8, Translation]
---
<ul>
	<li>本文翻译自卢昌海的个人主页：<a href="http://www.changhai.org" target="_blank">http://www.changhai.org</a></li>
	<li>原文链接：<a href="http://www.changhai.org/articles/technology/misc/utf-8.php" target="_blank">http://www.changhai.org/articles/technology/misc/utf-8.php</a></li>
	<li>请在转载前阅读卢昌海先生网站的版权说明：<a href="http://www.changhai.org/articles/introduction/copyright.php" target="_blank">http://www.changhai.org/articles/introduction/copyright.php</a></li>
</ul>
<p>==================</p>

<h2><strong>什么是 UTF-8</strong></h2>

<p>
	作者：卢昌海<br />
	翻译：Igor Wang<br />
	发布时间：2002年7月26日<br />
	翻译时间：2012年8月29日
</p>
<p>这篇文章收集了您理解 UTF-8编码（即本站所采用的编码方式）所需的最少信息。请访问 <em>Unicode</em> 组织网站以了解更多。</p>
<p>UTF-8 是一种遵循 Unicode/ISO-10646 标准的流行编码格式，如果您还不太了解它，请不用担心，阅读以下内容将会让您对 UTF-8 有一个更清晰的认识。</p>

<p>早先有两个相互独立的组织想要建立一个统一的字符集。一个是<em>国际标准化组织（ISO）</em>的 <em>ISO 10646</em> 计划，另一个则是后来被称为<em> Unicode 组织</em>的 <em>Unicode</em> 计划。ISO 提出的 <em>ISO 10646 </em>标准定义了一个31位的巨型<em>通用字符集（Universal Character Set，UCS）</em>。UCS 中包含一个16位的子集，叫做<em>基本多文种平面（Basic Multilingual Plane，BMP）</em>，它包含65534个字符并最先流传开来。另一方面，Unicode 组织一直致力于一个名为 Unicode 的标准。</p>

<p>两个相互不兼容的标准自然达不到&ldquo;统一&rdquo;的目的。1991年，ISO 和 Unicode 都意识到了这个问题并开始合并原有标准。至此以后 Unicode 标准的新版本开始完全兼容相应的 ISO 10646 标准。所有字符的位置和名称在两种标准中完全相同。</p>
<p>理论上，31位的 UCS 可以涵盖20亿个字符，但事实上其定义的字符数很少（不过数量仍然在增加中）。例如 Unicode 3.2 版本就包含了 95221 个字符（超过了 BMP）。Unicode 标准稳且严格，只有新字符会被添加到其中，不存在的字符将会被移除或重命名。</p>
<p>Unicode / ISO 10646 是第一个用整数来表示字符的码表。这些整数的16进制数值前通常要加上&ldquo;U+&rdquo;。例如，U+0041 代表&ldquo;拉丁文大写字母A&rdquo;。每给定一个整数，就可以通过字符编码标准（码表）中的序列号来确定其所代表的字符。</p>
<p>Unicode 标准定义了3个码表，它们可以让字符数据转化为一个字节、字或双字（即是每个编码单位为8位、16位或32位）。这三种编码格式分别称为 UTF-8、UTF-16 和 UTF-32。ISO 还定义了其他的码表。UTF 即是 Unicode 转换格式（ Unicode/UCS Transformation Format ）的缩写。</p>

<p>UTF-8 把所有的 Unicode 字符转化为一串可变长度的字节序列，转化方法如下：</p>

<ul>
	<li>从 U+0000 到 U+007F（ASCII码）被编码为 0x00 ~ 0x7F 的单字节，这意味着 UTF-8 完全兼容 ASCII 码。</li>
	<li>所有大于 U+007F 的字符被编码为一串多字节序列，它们都大于 0x7F（即非 ASCII 码），这样就可以区分一串多字节序列是多字节码还是 ASCII 码。</li>
	<li>多字节序列的第一个字节（代表着非 ASCII 码）落在 0xC0 到 0xFD 范围内。剩余的字节都落在 0x80 ~ 0xBF 内。这样即可确定多字节序列的边界（实际上第一个字节内包含有序列长度的冗余信息）。</li>
	<li>0xFE 和 0xFF 不会被用于 UTF-8 编码中。</li>
</ul>

<div>
	为了编码 UCS 中 2<sup>31&nbsp;</sup>个字符，UTF-8 编码字符最长可达六个字节，
	但是16位的 BMP 码最长只能达到三个字节。下表中列出了 UTF-8 码所对应字节系列的格式：
</div>

<pre>
Unicode 字符:			UTF-8 码:
U-00000000 - U-0000007F:	0xxxxxxx
U-00000080 - U-000007FF:	110xxxxx 10xxxxxx
U-00000800 - U-0000FFFF:	1110xxxx 10xxxxxx 10xxxxxx
U-00010000 - U-001FFFFF:	11110xxx 10xxxxxx 10xxxxxx 10xxxxxx
U-00200000 - U-03FFFFFF:	111110xx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx
U-04000000 - U-7FFFFFFF:	1111110x 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx
</pre>

<p>其中的"xxx"位应被替换为相应字符在 Unicode 标准中被定义的数字。例如，Unicode 字符 U+2260 = <strong>0010 0010 0110 0000</strong>（代表&ldquo;不等于&rdquo;的符号&ne;）属于上表中的第三个分类。把这16位替换掉其中的16个&ldquo;x&rdquo;，如下所示：</p>

<p style="text-align:center;">1110<strong>0010</strong> 10<strong>001001</strong> 10<strong>100000</strong></p>

<p>请注意加粗的数字和等式右侧的数字（上方加粗的数字）相同。</p>

<p>正如前面所提到的，UTF-8 编码是一种<em>流行的</em> Unicode 编码格式。它为什么如此流行呢？原因就在于所有的 ASCII 字符在 UTF-8 中都被编码为单字节，这样不仅有着完全的兼容性，而且对于美国和欧洲用户来存储效率更高。通常说来，UTF-8 在储存 ASCII 码时不需要占用更多的空间，在编码 ISO-8859-1（即涵盖西欧语言的 Latin-1 码）时只比原来多占用很少的空间，编码中日韩文时多占用50%的空间，编码希腊语和西里尔语时中多占用一倍的空间。作为对比，UTF-16 在编码中日韩文时不会占用更多的空间，而在编码 ASCII、ISO-8859-1、希腊语和西里尔语时要多占用一倍的空间。UTF-32 是固定长度的编码，意味着需要占用大量的空间。因为美国和西欧用户为最大的互联网使用群体，且英语是互联网上使用最多的语言（在写这篇文章时），所以UTF-8 迅速成为了互联网上最流行的 Unicode 编码格式。</p>
<p>最后说一下在网页上输入 UTF-8 码字符的通用方法。例如，想要在网页中输入 U+2014（破折号&ldquo;&mdash;&rdquo;），可以使用&ldquo;&amp;#x2014;&rdquo;（&ldquo;x&rdquo;表示接下来输入的数字是十六进制）或者&ldquo;&amp;#8212;&rdquo;（8212是x2014的十进制）。任何 Unicode 字符都可以用这种格式输入（不怎么方便，但是在没有输入法的时候还是很有用的）。</p>

<p style="text-align:right;"><strong>全文完</strong></p>

{% include JB/setup %}
