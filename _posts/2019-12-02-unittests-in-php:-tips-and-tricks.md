---
layout: post
title: "UnitTests in PHP: tips and tricks"
date: 2019-12-02 11:04:46
image: '/assets/img/'
description:
main-class: dev
color:
tags:
categories:
twitter_text:
introduction:
---

## Использование анонимных классов для написания более простых тестов
Наши классы согластно инверсии зависимостей зависят от интерфейсов. Если нужно протестировать что тестируемый класс вызывает процедуру из вложенного в него интерфейса - то достаточно удобно не мокать все зависимости вложенного интерфейса, а создать анонимный класс, его реализующий:

{% highlight php %}
final class SomeService
{
   /**
    * @var SenderInterface
    */ 
    private $sender;

    public __constructor(SenderInterface $sender)
    {
        $this->sender = $sender;
    }

    public function publish(): void
    {
        // ... same code

        $this->sender->send();
    }
}

final class testSomeService extends TestCase
{
    /**
     * @test
     */
    public publish()
    {
        $sender = $this-createSender();
        $someService = new SomeService($sender);

        $someService->publish();
        
        $this->assertTrue($sender->isSended());

    }

    private function createSender(): SenderInterface
    {
        return new class() implements SenderInterface
        {
            private $isSend = false;
            public function send():void
            {
                $this->isSend = true;
            }

            public function isSended(): bool
            {
                return $this->isSend;
            }
        }
    }
}

{% endhighlight %}

... in progress ... 

### Источники:
[Using anonymous classes to write simpler tests](https://mnapoli.fr/anonymous-classes-in-tests/)