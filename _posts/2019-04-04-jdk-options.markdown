---
layout: post
title:  "JDK Launch Options"
date:   2019-04-04 11:30:00 +0300
categories: java
---

This is a quick cheat-sheet about some useful JDK launch options.

### Remote Debug
To enable remote debugging next options should be added:

{% highlight bash %}
-Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=7896
{% endhighlight %}

* **suspend** - JDK will be suspended until remote debugger is attached.
* **server** -  listen some port or attach to specified port to debugger application
* **address** - listen on this port (if server=y) or attach to this port (if server=n)

### System Properties

System property can be set in the next way:

{% highlight bash %}
-Dfoo="bar"
{% endhighlight %}

Then in runtime it can be read in the next way:

{% highlight java %}
System.getProperty("foo")
{% endhighlight %}

### Memory Settings

* **-Xmssize** Memory allocation pool initial size (start heap size)
* **-Xmxsize** Memory allocation pool maximum size (max heap size)
* **-Xsssize** Thread stack size

These settings can be specified in bytes, kilobytes(K), megabytes(M) and gigabytes(G)

{% highlight bash %}
-Xms128M -Xmx256M
{% endhighlight %}

{% highlight bash %}
-Xms1G -Xmx8G
{% endhighlight %}

### Logging
* **-verbose** or **-verbose:class** Prints names of the loaded classes

![verbose console output](/assets/jdk_options/verbose.png)

* **-verbose:gc**
Prints each GC event

![verbosegc console output](/assets/jdk_options/verbosegc.png)

* **-XX:-HeapDumpOnOutOfMemoryError**  When OutOfMemory happens JDK will dump heap to file.

![heap dump on oom](/assets/jdk_options/dump_1.png)


### Garbage collector selection

{% highlight bash %}
-XX:+UseParallelGC
{% endhighlight %}

{% highlight bash %}
-XX:+UseParallelOldGC
{% endhighlight %}

{% highlight bash %}
-XX:+UseParNewGC
{% endhighlight %}

{% highlight bash %}
-XX:+UseSerialGC
{% endhighlight %}

{% highlight bash %}
-XX:+UseG1GC
{% endhighlight %}

{% highlight bash %}
-XX:+UseConcMarkSweepGC
{% endhighlight %}
