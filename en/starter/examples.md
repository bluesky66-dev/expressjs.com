---
layout: page
title: Express examples
menu: starter
lang: en
redirect_from: "/starter/examples.html"
---

{% capture examples %}{% include readmes/express-master/examples.md %}{% endcapture %}
{{ examples | replace: "](.", "](https://github.com/expressjs/express/tree/master/examples" }}

###  [Previous: Static Files ](/expressjs.com/{{ page.lang }}/starter/static-files.html)&nbsp;&nbsp;&nbsp;&nbsp;[Next: FAQ ](/expressjs.com/{{ page.lang }}/starter/faq.html)
