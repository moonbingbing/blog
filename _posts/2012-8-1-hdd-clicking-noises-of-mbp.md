---
layout: post
title: "MacBook Pro 硬盘异响原因及解决"
description: "MacBook Pro在安静的时候会发出轻微金属撞击的声音，这篇文章简单讨论了引起该声音的原因及解决办法。"
category: 计算机
tags: [Apple, HDD, Hardware, Mac, OS X, Troubleshooting]
---

<p>最近在我的 MacBook Pro (15-inch, Mid 2012) 上，特别是安静的时候，硬盘会随机出现类似于&ldquo;啪嗒&rdquo;的声音。</p>
<p>Google了一下&ldquo;<a href="https://www.google.com/search?hl=en&amp;newwindow=1&amp;q=Mac+HDD+random+clicking+noise">Mac HDD random clicking noise</a>&rdquo;，发现很多人都被类似的问题困扰，而且症状千奇百怪。OS X下磁碟式硬盘出现这类异响一般有三个原因：</p>
<ol>
	<li>
		<p>突发移动感应器 ( Sudden Motion Sensor ) 的作用：</p>
		<p>现在的很多移动设备都含有类似于&ldquo;突发移动感应器&rdquo;的装置，如 Thinkpad 的&ldquo; Active Protection System &rdquo;和 Sony 的&ldquo; HDD Protection &rdquo;，关于&ldquo;突发移动感应器&rdquo;Apple是<a href="http://support.apple.com/kb/HT1935?viewlocale=zh_CN">这样</a>解释的：</p>
		<blockquote class="r-background">
			突发移动感应器的设计旨在检测异常强烈的震动、位置突然改变和加速移动。如果感应器检测出上述任意问题，其会立即停止硬盘驱动器磁头，以降低因撞击造成硬盘驱动器损坏的可能性。磁头停止可能伴随有轻微的咔嚓声或&ldquo;叮当&rdquo;声，这是意料之中的正常现象。如果您正积极播放视频、音频或执行其他类似任务，可能会发现在 SMS 参与时任务会暂停。只要 SMS 处于可以脱离的状态，任务就该恢复。<p>
			</p>SMS 探测到电脑的位置再次稳定后，便会解开对硬盘驱动器磁头的锁定，并恢复为正常运营。
		</blockquote>
		但我并没有在移动中使用 MacBook Pro，所以这不是问题所在。</li>
	<li>
		<p>硬盘损坏噪音，也就是传说中的&ldquo; Click of death &rdquo;：</p>
		<p>这大概是最恶劣的情况。在这种情况下的硬盘异响是由于硬盘中磁头悬臂的异常运动所引起。在磁盘读取过程中，磁头悬臂为读取数据应移动到相应的位置，但如果因种种原因导致了磁头悬臂无法正常读取磁盘表面的数据，从而引发错误。硬盘控制芯片可能会通过取消操作来忽略这个错误，这时就会引发&ldquo;啪嗒&rdquo;的声音；另一些磁盘控制器反复尝试读取数据则会引起持续的&ldquo;啪嗒&rdquo;声。&nbsp;<sup>[1]</sup><br />详情参见 Wikipedia 上的&nbsp;<a href="http://en.wikipedia.org/wiki/Click_of_death">Click of death</a>&nbsp;词条。</p>
		<p>如果真是这样的话就要考虑换个硬盘了，而且数据极有可能丢失。</p>
	</li>
	<li>
		<p>磁头悬臂停靠而引起的噪声：</p>
		<p>在 Apple Support 里有这么一个页面：<a href="http://support.apple.com/kb/TS2354?viewlocale=zh_CN">Apple 便携式电脑：硬盘驱动器和噪音</a></p>
		<p>节选其中的一部分：</p>
		<blockquote class="r-background">在磁头停止时会发出咔哒声（驱动器闲置一段时间后便会停止磁头动作）。停止磁头有利于保护数据，因为当电脑掉落或进行搬移时，如果磁头未在驱动器盘片上方，则驱动器便不太容易丢失数据。</blockquote>
		<blockquote class="r-background">注：即使您正在频繁使用电脑，硬盘驱动器也可能进入闲置状态。 电脑进入睡眠状态或从睡眠状态唤醒时，您也可能听到这种声音。在硬盘驱动器加载和卸载读/写磁头时，发出这种声音属于正常现象。</blockquote>
		<p>事实上这种被称为硬盘高级电源管理 ( Advanced Power Management (APM) ) 的功能在符合 ATA/ATAPI-4 标准以上的硬盘上都有，对设备的节能有帮助，但相对应的会对磁盘性能产生影响。<sup>[2]</sup></p>
	</li>
</ol>

<p>好了，至此我祈祷自己听到的只是悬臂停靠的声因。</p>
<p>首先想尝试关闭 APM 功能，首先在节能选项里看到了&ldquo;如果可能，使硬盘进入睡眠&rdquo;的选项（如下图）。</p>
<p style="text-align:center;"><img src="/img/post/2012-8-1-hdd-clicking-noises-of-mbp/terminal.png" /></p>
<p>但是，尝试勾选掉它后仍然能听到随机的&ldquo;咔嗒&rdquo;声。</p>
<p>接下来在macrumors论坛里看到了一款名为<a href="http://mckinlay.net.nz/hdapm/">hdapm</a>的软件，该软件的描述翻译如下：</p>

<blockquote class="r-background">
	hdapm 是一款使用命令行工具设置硬盘 APM 等级的工具。
	它可以减弱一些笔记本硬盘的&ldquo;闲置噪音&rdquo;。
</blockquote>

<p><a href="http://mckinlay.net.nz/files/hdapm-installer.dmg">下载</a>后安装。</p>
<p>打开命令行后输入（注意，disk0 是系统盘所在位置）：</p>
{% highlight bash %}
$ sudo hdapm disk0 max
{% endhighlight %}
<p>问题解决了，说明&ldquo;咔嗒&rdquo;声确实是磁头悬臂停靠所引起。</p>
<p style="text-align:center;"><img src="/img/post/2012-8-1-hdd-clicking-noises-of-mbp/power-saver.png" /></p>
<p>这时的电耗可能也会高一些，此外，如果想要还原的话输入以下命令即可：</p>
{% highlight bash %}
$ sudo hdapm disk0 default
{% endhighlight %}
<p>关于这个软件更多的细节可以参考<a href="http://mckinlay.net.nz/hdapm/usage.html">这里</a>。</p>
<p><br /></p>

<p>参考链接：</p>
<p style="text-align:left;">[1]&nbsp;Click of death - Wikipedia, the free encyclopedia:<br /><a href="http://en.wikipedia.org/wiki/Click_of_death">http://en.wikipedia.org/wiki/Click_of_death</a>;</p>
<p style="text-align:left;">[2]&nbsp;Hard Disk Drive Advanced Power Management (APM):<br /><a href="http://www.smarthdd.com/en/apm.htm">http://www.smarthdd.com/en/apm.htm</a>;</p>
<p style="text-align:right;"><strong>全文完</strong>&nbsp;</p>

{% include JB/setup %}
