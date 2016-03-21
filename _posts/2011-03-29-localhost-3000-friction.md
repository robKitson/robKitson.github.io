---
layout: post
title:  "localhost:3000 friction"
date:   2011-03-29 00:00:00 -0800
categories: 
---

If you're like me, you probably have more than a few rails projects on your machine. And, if you're like me, you probably don't worry too much about setting the port when you spin up webrick to test your stuff.

Recently I've been increasingly annoyed by my browser trying to autocomplete my http:://localhost:3000/ urls to paths that are relevant to different projects.  I think I've found a simple solution that's been working for me for the past few weeks. I edited my /etc/hosts file to include entries for project names that point to the localhost, like this:

{% highlight bash %}
127.0.0.1 new_project
127.0.0.1 other_project
127.0.0.1 sandbox
{% endhighlight %}


Now, when I'm working on 'other_project', the url is http://other_project:3000/ and the browser doesn't try to autocomplete paths for http://new_project:3000/ or http://sandbox:3000/. Of course, I have to be cognizant of the fact that any of my hosts entries will contact the webrick instance that is currently running on the port I'm designating in my url, but that's a bit less annoying than getting my url schemes mixed up between projects.