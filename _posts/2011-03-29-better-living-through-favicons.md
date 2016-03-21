---
layout: post
title:  "Better Living Through Favicons"
date:   2011-03-29 00:00:00 -0800
categories: 
---


I use tabs, lots of them, and usually in more than one browser window.  Recently I've found myself hunting for the specific tab that has the site I'm developing/testing locally, testing in a staging environment, or verifying in the production environment, and I’ve gradually been getting more annoyed with the friction.

Last night I had an epiphany: What if I provided a different favicon for each environment instead of the same one for each? A little research and I discovered that I didn’t have to have a file name favicon.ico, I could name it whatever I wanted AND you can use file formats other than .ico.

I grabbed the actual favicon.ico and converted it to a .png.  Then I made 2 distinctly different versions for my ‘development’ and ‘staging’ environments and saved with a naming schema that will allow me to quickly figure out which one to use.

These are the 3 I'll be using on one of my current projects:

![favicon.png][1] favicon.png

![favicon-staging.png][2] favicon-staging.png

![favicon-development.png][3] favicon-development.png

Next, I added this:

{% highlight erb %}
<link rel="icon" href="/favicon<%= ("-" + RAILS_ENV) unless RAILS_ENV == "production" %>.png" type="image/png">
{% endhighlight %}

to the HEAD block in the /views/layouts/application.rb file.  So now, when the site is loaded from production it uses favicon.png, but favicon-development.png and favicon-staging.png for the development and staging environments, respectively.

In hindsight it seems obvious, but this little hack reduced my tab hunting time drastically.


[1]:/post_assets/2011-03-29-better-living-through-favicons/favicon.png
[2]:/post_assets/2011-03-29-better-living-through-favicons/favicon-staging.png
[3]:/post_assets/2011-03-29-better-living-through-favicons/favicon-development.png