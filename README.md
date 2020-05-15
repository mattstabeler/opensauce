## Welcome to Matt's Open Sauce recipes

These are my collected recipes for cooking and brewing. 


**Food**

- [Yorkshire Puddings](recipes/Yorkshire_Puddings) 

**Brewing**

- [Cherry Wine](brewing/Cherry_Wine)



## Blog



<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>