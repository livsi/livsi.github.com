---
layout: post
title: "TokuDb в Docker for Mac"
date: 2016-09-14 10:20:54
description: "Запуск TokuDb на macOs"
main-class: "dev"
color: '#637a91'
tags:
    - "docker"
    - "MySQL"
introduction: "Запустить TokuDb на macOs сопряжен с рядом сложностей, в частности в включенными THP"
---
Запуск докер-контейнера с TokuDb на macOs вызывает проблему, при которой TokuDb виден в списке энжинов только при первичном создании, а при перезапуске пропадает. Это связано с тем, что при первичном запуске - снимается поддержка THP, а при перезапуске она появляется вновь. Установка THP - это уровень ядра, что не подвластно docker.
Так как докер запускается на macOs внутри виртуальной машины - то при запуске Docker for Mac нужно попасть внутрь
виртуалки Docker for Mac и снять поддержку THP:

{% highlight bash %}
screen ~/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux/tty
echo never > /sys/kernel/mm/transparent_hugepage/enabled
echo never > /sys/kernel/mm/transparent_hugepage/defrag
cat /sys/kernel/mm/transparent_hugepage/enabled
{% endhighlight %}

Последняя команда - проверяет, что поддержка THP - снята, должно выводиться never

Чтобы выйти из **screen** - нажать Ctrl+A d

Ранее я пользовался официальным докер-образом [percona/percona-server](https://github.com/percona/percona-docker) - 
для установки TokuDB Enginе нужно установить флаг конфигурации INIT_TOKUDB=true, но в связи с последними правками -
вынужден был перейти на реально работающий на macOs - [miguelangel/percona-tokudb](https://hub.docker.com/r/miguelangel/percona-tokudb/)

**UPDATE**: С конца 2016 года - эти танцы с бубном больше вроде как не нужны (в Moby по умолчанию отключили THP)[https://github.com/docker/docker.github.io/blob/master/docker-for-mac/release-notes.md#docker-for-mac-1121-2016-09-16-stable] - но при тесте я обнаружил что все же нет:

{% highlight bash %}
# cat /sys/kernel/mm/transparent_hugepage/enabled
always [madvise] never

а должно быть:

# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]
{% endhighlight %}

Так что инструкция до сих пор актуальна
