---
layout: post
title: "Файлы конфигурации для Vim"
description: ""
category: 
tags: []
---
В терминале vim --version - видим

system vimrc file: "$VIM/vimrc"
user vimrc file: "$HOME/.vimrc"
user exrc file: "$HOME/.exrc"

Про vimrc все знают и пользуются, знал и я, а вот про exrc - увидел впервые. Это файл, который регулирует Environment (окружение), что делать при открытии нового файла - задать нумерацию строк, табуляции, отступы и прочие настройки.

Типичный файл .exrc

<div class="col-lg-6">
{% highlight bash %}
set number
set autoindent
set nowrapscan
ab inc include
map Q :q!
{% endhighlight %}
</div>
