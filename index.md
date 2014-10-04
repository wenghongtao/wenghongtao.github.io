---
layout: page
title: Hello World!
tagline: 世界是你的，世界也是我的。
---
{% include JB/setup %}
    

{% for post in site.posts %}  

## <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>

<span>{{ post.date | date_to_string }}</span>  <span><a href="{{ BASE_PATH }}categories.html#{{ post.category}}-ref">{{ post.category }}</a></span>

{{ post.content }}

***
{% endfor %}




