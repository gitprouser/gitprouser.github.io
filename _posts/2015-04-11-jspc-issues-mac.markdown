---
layout: post
title:  "jspc compilation in mac"
date:   2015-04-11 18:23:18
categories: java support
---


Issue when trying to compile jsp using jspc-maven-plugin
-----------------------------------------------------------

For those of you who have used a mac to compile jspc and hit the following error:
When compiling jsp files in a mac. After setting the environment variable `JAVA_HOME` set to your jdk home directory.
When you actually get to compiling your jsp files you might hit the following issue.

{% highlight java %}
    Exception in thread "main" java.lang.AssertionError: Missing tools.jar at: /Library/Java/JavaVirtualMachines/jdk1.7.0_71.jdk/Contents/Home/Classes/classes.jar. Expression: file.exists()
{% endhighlight %}


The way to resolve this is create a new directory in `$JAVA_HOME/Classes` and link tools.jar to `$JAVA_HOME/Classes/classes.jar`.

Link Tools.jar to Classes.jar

{% highlight java linenos %}
sudo mkdir $JAVA_HOME/Classes
sudo ln -sf $JAVA_HOME/lib/tools.jar $JAVA_HOME/Classes/classes.jar
{% endhighlight %}


Now your jspc will compile without the missing tools.jar error.