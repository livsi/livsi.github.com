---
layout: post
title: "Symfony2 FOSUserBundle"
description: ""
category: 
tags: []
---

Понадобилось сменить пароль для пользователя - все что нужно сделать - выполнить консольную команду:

  {% highlight bash %}
$ php app/console fos:user:change-password USERNAME
  {% endhighlight %}


http://habrahabr.ru/post/202696/
Когда у вас есть файлы, которые специфичны для данного проекта и для вашего рабочего окружения(например, логи, third-party утилита) используйте .git/info/exclude. Этот файл не коммитуется и остается только в локальном репозитории.

  {% highlight bash %}
git config --global core.excludesfile ~/.gitexcludes
  {% endhighlight %}
