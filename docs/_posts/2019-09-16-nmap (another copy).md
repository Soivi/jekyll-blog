---
layout: post
title:  "Nmap"
categories: scan deny
summary: Nmap is a network scanning tool
---

{% include instructions.md %}

# {{page.title}}
Nmap is a network scanning tool.

Scan 1000 most common ports. Delay is about 1 second.

{% highlight shell %}
# nmap --top-ports 1000 -T2 [victim ip address]
{% endhighlight %}
Scan all ports aggressively

{% highlight shell %}
# nmap -p- -T4 [victim ip address]
{% endhighlight %}
Try to determine Operation system. Scan 1000 most common ports and try to determine service and version.

{% highlight shell %}
# nmap -O -sV --top-ports 1000 -T4 [victim ip address]
{% endhighlight %}
Scan insane fast in parallel and use decoys. In a target computer it looks like 3 different IP addresses are trying to scan it ports.

{% highlight shell %}
# nmap -p- -T5 --min-parallelism 5 [victim ip address zone] -D[decoy ip address],[decoy ip address]
{% endhighlight %}

