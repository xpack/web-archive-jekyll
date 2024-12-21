---

title: The xPack GNU sed releases
permalink: /sed/releases/

search: exclude
github_editme: false

comments: false
toc: false

date: 2022-10-04 10:32:00 +0300

# redirect_to: https://xpack-dev-tools.github.io/sed-xpack/docs/releases/

---

___
{% for post in site.posts %}{% if post.categories contains "releases" %}{% if post.categories contains "sed" %}
* [{{ post.title }}]({{ site.baseurl }}{{ post.url }}) [(download)]({{ post.download_url }}){% endif %}{% endif %}{% endfor %}
