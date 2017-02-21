---
title: "Syntax highlighting on Github Pages"
date: 2017-02-21
---

![Up on the hill](/images/2016-12-13-the-hill.jpeg)

Setup your config file _config.yml to use:
``` 
markdown: kramdown
highlighter: rouge
```

This will include specific classes to your rendered HTML-markup when you use syntax highlighting with code blocks. To make use of these classes you need to add some CSS-styles. Such as:

```css
.highlight .c { color: #8f5902; font-style: italic } /* Comment */
.highlight .err { color: #a40000; border: 1px solid #ef2929 } /* Error */
.highlight .g { color: #000000 } /* Generic */
.highlight .k { color: #204a87; font-weight: bold } /* Keyword */
.highlight .l { color: #000000 } /* Literal */
```

Have a look at this [repository](https://github.com/richleland/pygments-css) where you can copy and paste some styles. Note the styles served use the prefix .codehilte. Change this to highlight.

If you are doing a responsive site you might want to add some CSS to make the code block like a box where the text won't make the page wider but instead stay in the box. 

I use the following CSS:

```css
.highlighter-rouge {
	overflow:scroll; 
	background-color:#efefef;
	width:100%;
}

Next it's time to write some code blocks in your markdown file. To do this you write three backticks followed by the language you want to highlight. The above code block was create with the markdown below:

```markdown
{% raw %}
I use the following CSS:

```css
.highlighter-rouge {
	overflow:scroll; 
	background-color:#efefef;
	width:100%;
}
{% endraw %}
```

If you want to highlight Liquid code you need to use raw tags like below:

``` liquid
{% raw %}
	{% raw %}
{% endraw %}
{% raw %}
	{% for file in site.static_files %}
		{% if file.path contains '/images/' %}
			<div><img src="{{ file.path }}"/></div>
		{% endif %}
	{% endfor %}
{% endraw %}
{% raw %}
	{% endraw %}
{% endraw %}
```