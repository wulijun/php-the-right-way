---
title: 复杂问题
anchorid: complex_problem_title
isChild: true
---

<h2 id="complex_problem_title">复杂问题</h2>

如果你涉猎了依赖注入的有关内容，那么你很可能看到过 *"控制反转"* or *"依赖反转原则"* 这两个条目。这是依赖注入所能解决的复杂问题。

### 控制反转

控制反转是说，一个系统的控制反转是从我们的对象中通过保持组织控制的完全独立。
依赖反转的作用是在系统的其他地方去控制和实例化它们，以便降低耦合度。

多年来，PHP框架已经实现了控制反转，但是，随之而来的问题是，你反转了哪一部分的控制器，而且它又在哪里？例如，MVC框架通常提供了一个超级对象，或者基础的控制器，其他的控制器必须继承和依赖它。这就是依赖反转，是简单的移动他们而不是降低耦合。

依赖注入允许我们需要他们的时候，只有注入我们需要依赖，才能更优雅的解决这个问题，没有任何强代码的依赖性。

### 依赖反转原则

Dependency Inversion Principle is the "D" in the S.O.L.I.D set of object oriented design principles that states one should
*"Depend on Abstractions. Do not depend on concretions."*. Put simply, this means our dependencies should be interfaces/contracts or abstract
classes rather than concrete implementations. We can easily refactor the above example to follow this principle.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(AdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
}

interface AdapterInterface {}

class MysqlAdapter implements AdapterInterface {}
{% endhighlight %}

There are several benefits to the `Database` class now depending on an interface rather than a concretion.

Consider that you are working in a team and the adapter is being worked on by a colleague. In our first example, we would have
to wait for said colleague to finish the adapter before we could properly mock it for our unit tests. Now that the dependency
is an interface/contract we can happily mock that interface knowing that our colleague will build the adapter based on that contract.

An even bigger benefit to this method is that our code is now much more scalable. If a year down the line we decide that we
want to migrate to a different type of database, we can write an adapter that implements the original interface and inject that instead,
no more refactoring would be required as we can ensure that the adapter follows the contract set by the interface.
