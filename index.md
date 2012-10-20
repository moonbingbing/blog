---
layout: page
title: Welcome to Igor's blog
tagline: Supporting tagline
---
<div>
	<div id="LatestArticleDIV">
		<h1><a href="{{BASE_PATH}}{{ site.posts[0].url }}">{{ site.posts[0].title }}</a></h1>
		<hr class="LatestArticleHR"/>
		<div style="margin:1em 1em;">
			<p>{{ site.posts[0].description }}</p>
		</div>
		<p style="font-size: smaller; text-align:right; margin-bottom: 0em;"><a href="{{BASE_PATH}}{{ site.posts[0].url }}">阅读全文...</a></p>
		<hr class="LatestArticleHR"/>
		<div style="margin:0em 3em; font-size: x-small;">
			<p>
				Categories&nbsp;:&nbsp;<a href="{{BASE_PATH}}categories.html#{{site.posts[0].categories}}-ref">{{ site.posts[0].categories }}</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;		
				Author&nbsp;:&nbsp;<a class="author" href="http://igorw.org">{{ site.author.name }}</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
				Date&nbsp;:&nbsp;<span class="date">{{ site.posts[0].date | date_to_long_string }}</span>
			</p>
		</div>
	</div>
	<div id="LowerPart">
		<div id="RecentArticlesDIV">
			<div>近期文章 / Recent Articles</div>
			<div id="RecentArticlesBorder">   </div>
			<div id="RecentArticles">
				<ul class="posts">
					{% for post in site.posts limit:10 offset:1 %}
			    	<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
			  		{% endfor %}
				</ul>
			</div>
		</div>
		<div id="BlogInfo">
			<div>关于 / About</div>
			<div id="BlogInfoBorderH"> </div>
			<div id="BlogInfoBorderV">
				<div id="BlogInfoContents">
					<p style="text-align:left;">
						--&nbsp;This Blog&nbsp;--<br />
						RSS Feed:&nbsp;<a href="/atom.xml">Atom</a>,&nbsp;feedbsf<br />
						Article Count:&nbsp;{{ site.posts | size }}<br />
						Source Code On <a href="https://github.com/waigx/blog">GitHub</a>.<br />
					</p>
					<p>
						--&nbsp;About Me&nbsp;--<br />
						Living In:&nbsp;Jilin, China<br />
						Home Page:&nbsp;<a href="http://igorw.org">http://igorw.org</a><br />
						Email:&nbsp;<a href="mailto:igor@igorw.org">igor@igorw.org</a>
					</p>
				</div>
			</div>
		</div>
	</div>
</div>
{% include JB/setup %}

