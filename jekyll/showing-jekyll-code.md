---
layout: menu
title: 显示jekyll源码
type: jekyll
permalink: /jekyll/showing-jekyll-code/
---

# 显示jekyll源码

{% raw %}

把你的代码包在raw endraw 间就可以了

```

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
{% endraw %}
