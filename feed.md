---
layout: null
---

<?xml version="1.0" encoding="utf-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">

 <title>{{ site.title }}</title>
 <link href="{{ site.url }}{{ site.baseurl }}/atom.xml" rel="self"/>
 <link href="{{ site.url }}{{ site.baseurl }}/"/>
 <updated>{{ site.time | date_to_xmlschema }}</updated>
 <id>{{ site.url }}</id>
 <author>
   <name>{{ site.author.name }}</name>
   <email>{{ site.author.email }}</email>
 </author>

 {% for post in site.posts %}
 <entry>
   <title>{{ post.title }}</title>
   <link href="{{ site.url }}{{ post.url }}"/>
   <updated>{{ post.date | date_to_xmlschema }}</updated>
   <id>{{ site.url }}{{ site.baseurl }}{{ post.id }}</id>
   <content type="html">
    {{ post.excerpt | xml_escape }}
    {% if post.excerpt != post.content %}
      {{"<a href=" | xml_escape}} {{site.url}}{{ post.url }} {{"/>Devamını OKu</a>" | xml_escape}}
    {% endif %}
  </content>
 </entry>
 {% endfor %}
</feed>