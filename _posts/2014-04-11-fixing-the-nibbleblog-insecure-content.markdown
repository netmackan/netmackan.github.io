---
layout: post
title:  "Fixing the Nibbleblog insecure content"
date:   2014-04-11 18:34:47
categories: blogging
---

The cause of the [insecure content][prev-post] in Nibbleblog was the use of some Google fonts in the CSS.

Simply removing it solved the problem :)

{% highlight diff %}
--- ../../nibbleblog-orig/themes/simpler/css/main.css	2014-03-31 20:18:30.000000000 +0000
+++ themes/simpler/css/main.css	2014-04-11 16:29:41.173308467 +0000
@@ -1,4 +1,3 @@
-@import url(http://fonts.googleapis.com/css?family=Open+Sans:400,300,300italic,400italic,700,700italic&subset=latin,cyrillic);
 
 /*
 ========================================================================
@@ -168,4 +167,4 @@
 .nb-align-center {
 	display:block;
 	margin:0 auto 1em;
-}
\ No newline at end of file
+}
{% endhighlight %}


[prev-post]:    {{site.baseurl}}{% post_url 2014-04-11-nibbleblog-installation %}
