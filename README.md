## Welcome to Matt's Open Sauce recipes

These are my collected recipes for cooking and brewing. 


**Food**

- [Yorkshire Puddings](recipes/Yorkshire_Puddings) 

**Brewing**

- [Cherry Wine](brewing/Cherry_Wine)
- [Ben's Over-Hopped IPA](brewing/Bens_Overhopped_IPA)
- [Stout Recipe](brewing/Bens_Stout)
- [English Ale Recipe](brewing/English_Ale)


## Blog



<ul>
  {% for post in site.posts %}
    <li>
      <a href="/opensauce/{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>