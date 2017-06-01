---
layout: post
title: "Kubernates - первый взгляд: любовь или ненависть?"
date: 2017-06-01 11:54:54
image: '/assets/img/'
description: "Первый опыт использования Kubernates в процессе разработки"
main-class: "devops"
color:
tags:
    - php
    - docker orces
categories:
twitter_text:
introduction: "Первый опыт использования Kubernates в процессе разработки. Сложности, вкусности, концепция. Как вообще с этим жить дальше 😁 🚀"
---

## Начало достаточно простое:

* Заходим на страницу [Container Engine](https://console.cloud.google.com/project/_/kubernetes/list) на Google Cloud Platform Console.
* Создаем или выбираем проект.
* Ждем когда API и связанные сервисы активируются. Это может занять некоторое время (2-3 минуты)
* Включаем биллинг для своего аккаунта

_Насчет простого - шутка конечно. Все что делается в гуглах - всегда совсем не просто 😁_


~~Точим ножи~~ Устанавливаем инструментарий:
CLOUD SDK для работы с Google Cloud [качаем](https://cloud.google.com/sdk/?hl=ru)

Авторизируемся в google cloud: 

```
gcloud auth application-default login
```

Смотрим на наши ~~фаланги~~ кластеры:

```
gcloud container clusters list
```

Для того чтобы управляться с kubectl - устанавливаем и его:

```
gcloud components install kubectl
```

Пробуем получить дашборду от kubectl:

```
kubectl proxy
```

Получаешь ошибку - The connection to the server localhost:8080 was refused - did you specify the right host or port? Думаем еще раз: верно, нужно авторизироваться. Гугл - он для телепатов 🐒

```
gcloud container clusters get-credentials APPLICATION
```

Теперь должно было заработать... Открывешь в браузере http://127.0.0.1:8001/ и видиш картинку. Что делать дальше? У тебя есть некая Docker-приложенька, состоящая из нескольких docker image. Их нужно куда то запушить. Если приложеньку зовут хомячок, и ни для кого она интереса и тайны не представляет - смело пользуйся docker хабом.

<span class="left"> ![Google Container Registry](/assets/img/Container-Registry-google.jpg) </span>Ну а если секретный хомяк? Тогда можно выбрать приватный Registry от Гугла: __Google Container Registry__

На синюю кнопочку обратил внимание? Она для того чтобы несколько улучшить UI пользования этим чертовски длинным левым меню - чтобы то, что тебе реально нужно всплывало вверх и там якорилось.

У тебя есть docker-compose для проекта? Хочешь превратить его в описалово ресурсов Kubernetes? Тогда пригодится __kompose__ специальная тулза, помогающая волшебным образом превратить docker-compose в файл годный для Kubernetes.

```
brew install kompose
```

Из одного симатичного docker-compose в итоге получаем кучку файлов 😱 Чего с ними делать? Пока сложил в папочку чтобы не мешались...


## What is a Pod?

Группа контейнеров (один или несколько), общее хранилище для этих контейнеров и варианты того, как запускать контейнеры.


### Продолжение следует ...
