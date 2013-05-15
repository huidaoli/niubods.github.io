---
layout: post
title: "测试页面"
category: 随便写写
tags: [beginner, helloworld]
---

{% include JB/setup %}

标题二
----------------------------

正文：初步尝试了一下，感觉还行。能部署自己的博客系统感觉很不错。

下面试试代码高亮功能
-------------------
	
``` lua
-- Does a simple tokenization of html data. Returns the data as a list of tokens. 
-- Each token is a table with a type field (which is either "tag" or "text") and
-- a text field (which contains the original token data).
function tokenize_html(html)
	local tokens = {}
	local pos = 1
	while true do
		local start = find_first(html, {"<!%-%-", "<[a-z/!$]", "<%?"}, pos)
		if not start then
			table.insert(tokens, {type="text", text=html:sub(pos)})
			break
		end
		if start ~= pos then table.insert(tokens, {type="text", text = html:sub(pos, start-1)}) end
		
		local _, stop
		if html:match("^<!%-%-", start) then
			_,stop = html:find("%-%->", start)
		elseif html:match("^<%?", start) then
			_,stop = html:find("?>", start)
		else
			_,stop = html:find("%b<>", start)
		end
		if not stop then
			-- error("Could not match html tag " .. html:sub(start,start+30)) 
		 	table.insert(tokens, {type="text", text=html:sub(start, start)})
			pos = start + 1
		else
			table.insert(tokens, {type="tag", text=html:sub(start, stop)})
			pos = stop + 1
		end
	end
	return tokens
end
```

``` java
NullPointerException at org.springframework.core.GenericTypeResolver.getTypeVariableMap
```

```
python ez_setup.py setuptools-0.6c11-py2.6.egg
```

图片一张
------------------------------
![王国之心](https://lh6.googleusercontent.com/-bLnw-E0z_SA/T2vlXSehfMI/AAAAAAAAAW4/K14Rb-6K5YQ/s620/2-1.jpg)

再来张大图
![两只小猫](https://www.filepicker.io/api/file/RD4g9YWgQ4CiUCwnvlr4)


最后测试以下插入gist
--------------------------------

{% gist 5539127 main.lua %}
