## Welcome to Matt's Open Sauce recipes

These are my collected recipes for cooking and brewing. 


## Food

- [Yorkshire Puddings](recipes/Yorkshire_Puddings) 

### Brewing

- [How to Brew Beer](brewing/How_to_Brew_Beer)
- [How Much to Sparge](brewing/How_Much_To_Sparge)

### Recipes

- [English Ale Recipe](brewing/Simple_English_Ale)
- [Cherry Wine](brewing/Cherry_Wine)
- [Ben's Over-Hopped IPA](brewing/Bens_Overhopped_IPA)
- [Stout Recipe](brewing/Stout)
- [English Ale Recipe](brewing/English_Ale)


## Blog



<ul>
  {% for post in site.posts %}
    <li>
      <a href="/opensauce/{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>