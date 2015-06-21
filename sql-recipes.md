---
layout: page
title: "Рецепты SQL"
description: ""
---
Рецепты решения отдельных задач в MySql
=======================================

Поиск дубликатов значений нескольких столбцов

{% highlight mysql %}
SELECT
    field_1, field_2, COUNT(*)
FROM
    table_name
GROUP BY
    field_1, field_2
HAVING 
    COUNT(*) > 1
{% endhighlight %}