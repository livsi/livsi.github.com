---
layout: post
title: "Docker for mac"
description: ""
category: 
tags: []
---

Попасть внутрь хостовой машины Docker for Mac можно с помощью команды:

{% highlight bash %}
screen ~/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux/tty
{% endhighlight %}

Чтобы выйти из **screen** - нажать Ctrl+A d

Получить сведенья о сети:

{% highlight bash %}
docker run --rm --privileged --net=host alpine ifconfig
{% endhighlight %}

percona/percona-server - для установки TokkuDB Engine - нужно:

Установить THP в докере - выполняем в хосте:

{% highlight bash %}
cat /sys/kernel/mm/transparent_hugepage/enabled
{% endhighlight %}

должно выводить never, если нет:

{% highlight bash %}
echo never > /sys/kernel/mm/transparent_hugepage/enabled
echo never > /sys/kernel/mm/transparent_hugepage/defrag
{% endhighlight %}
