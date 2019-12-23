---
layout: post
title: "tmux - terminal multiplexer"
date: 2018-10-15 04:44:38
image: '/assets/img/'
description:
main-class: dev
color:
tags:
categories:
twitter_text:
introduction:
---

## Tmux - TerminalMUltipleXer

Tmux - это то же самое что и iTerm2, только везде. Единственная проблема, из за которой я его
до сих пор не использовал - мне было сложно запомнить все клавиатурный сокращения. Ну или хотя бы
самые основные.

С запуском - все просто:

{% highlight bash %}
    tmux
{% endhighlight %}

Все другие команды предваряются сочетанием нажатых *Ctrl-b*

Выйти - x

Новое окно - c

Список окон - w

Переключиться на следующее окно - n

--"-- на предыдущее - p

--"-- по номеру - 0

Разделить окно на две панели вертикально - % [# tmux split-window -v]
--"-- горизонтально - " [# tmux split-window -h]

Переход между панелями - стрелки

### Почитать по теме

[A Quick and Easy Guide to tmux: Ham Vocke](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

[Шпаргалка по работе с Tmux](https://habr.com/post/327630/)

[Приручаем Tmux для повседневных нужд](https://habr.com/post/165437/)
