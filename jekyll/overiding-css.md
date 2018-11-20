---
layout: menu
title: 覆盖现有样式
type: jekyll
permalink: /jekyll/overiding-css/
---

# 覆盖现有样式

### 第一步查看你现在正在实用的皮肤是什么，

```
打开你的 _config.yml
查找theme: 开头的一行例如：
theme: minima
```

### 找到你的皮肤的源码
https://github.com/jekyll/minima

通过阅读代码发现 minima 的css定义在include/head.html中。

把这个文件复制到你的工程里面，然后添加你需要的css信息即可

####示例：

修改前
{% raw %}
```html

<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  {%- seo -%}
  <link rel="stylesheet" href="{{ "/assets/main.css" | relative_url }}">
  {%- feed_meta -%}
  {%- if jekyll.environment == 'production' and site.google_analytics -%}
    {%- include google-analytics.html -%}
  {%- endif -%}
</head>

```

添加

```html

<link rel="stylesheet" href="{{ "/css/common.css" | relative_url }}">

```

修改后

```html

<head>

  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  {%- seo -%}
  <link rel="stylesheet" href="{{ "/assets/main.css" | relative_url }}">
  <link rel="stylesheet" href="{{ "/css/common.css" | relative_url }}">
  {%- feed_meta -%}
  {%- if jekyll.environment == 'production' and site.google_analytics -%}
    {%- include google-analytics.html -%}
  {%- endif -%}

</head>

```
{% endraw %}
