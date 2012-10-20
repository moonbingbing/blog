---
layout: post
title: "ies4linux在新版本wine中安装问题及解决"
description: "描述ie4linux在较新版本wine下安装时出现的一些错误，并介绍了解决方案。"
category: 计算机
tags: [IE, Linux, Troubleshooting, Wine]
---
{% include JB/setup %}

<p>因为各种各样的原因，额，始终还是需要 IE6 的。<br /> winetricks<sup><small>[1]</small></sup> 里已经提供了 ie6 ( Internet Explorer 6 ) 的安装选项，安装过程也算是顺利，但稳定性和 ActiveX 的兼容性与 ies4linux<sup><small>[2]</small></sup> wine 出的效果仍有差距。<br />在新版本的 wine 环境中，运行 ies4linux 后终端里出现警告信息：</p>
<blockquote>IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com). </blockquote>
<p>这里我遇到了两个问题，解决办法：</p>
<ul>
	<li>
		python-gtk 的问题：
		
		<p>其实就是在 GUI 版本的 ies4linux 因 GTK 的问题没有办法运行，这里我们诉诸于 CLI，首先察看一下 ies4linux 的帮助信息：</p>
		
{% highlight bash %}
ies4linux-2.99.0$ ./ies4linux --full-help
{% endhighlight %}
		
		<p>从返回结果可以看到我们想要安装中文，无 Flash，安装字体，无各种菜单图标的参数：</p>
		
{% highlight bash nowrap=False %}
ies4linux-2.99.0$ ./ies4linux --install-corefonts --no-flash --no-desktop-icon --no-menu-icon --locale CN --no-gui
{% endhighlight %}

		但在 “Creating Wine Prefix” 这一步时会有错误信息出现：
		<blockquote>Your wine does not have wineprefixcreate installed. Maybe you are running an old Wine version. Try to update it to the latest version.</blockquote>
		<p>额，那现在我们进入下个问题。</p>
	</li>
	<li>
		wineprefixcreate 不存在的问题：
		
		<p>新的 wine 版本中（原谅我不知道是从哪个版本开始）使用 winecfg 代替了 wineprefixcerate，所以只要创建一个指向 winecfg 的链接即可：</p>
		
{% highlight bash %}
ies4linux-2.99.0$ sudo ln -s /usr/bin/winecfg /usr/bin/wineprefixcreate
{% endhighlight %}
		
		<p>然后：</p>
		
{% highlight bash %}
ies4linux-2.99.0$ ./ies4linux --install-corefonts --no-flash --no-desktop-icon --no-menu-icon --locale CN --no-gui
{% endhighlight %}
		
		<p>这时 ies4linux 就应该正常执行安装 ie6 了。</p>
	</li>
</ul>
<p><br /><br /></p>
<p>参考链接：</p>
<p style="text-align:left;">[1]&nbsp;winetricks - The Official Wine Wiki:&nbsp;&nbsp;<a href="http://wiki.winehq.org/winetricks">http://wiki.winehq.org/winetricks</a>;</p>
<p style="text-align:left;">[2]&nbsp;Main Page - IEs4Linux:&nbsp;&nbsp;<a href="http://www.tatanka.com.br/">http://www.tatanka.com.br/</a>;</p>
<p style="text-align:right;"><strong>全文完</strong></p>