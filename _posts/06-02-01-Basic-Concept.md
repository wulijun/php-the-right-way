---
isChild: true
---

## 基本概念 {#basic_concept_title}

我们可以用一个简单而又天真的例子，来证明这个概念。

我们有一个 `Database` 的类，这个类要求适配数据库。我们在类的构造函数里实例化了这个适配器，并且创建了一个高耦合的依赖。 这才测试的时候会很困难，并且这就意味着 `Database` 类和适配器是高耦合关系。

{% highlight php %}

<?php

namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}

{% endhighlight %}

上面这个代码可以使用依赖来解耦合。

{% highlight php %}

<?php

namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}

{% endhighlight %}

现在我们可以创建 `Database` 类的依赖了，而不用创建它本身。我们甚至可以创建一个方法，接受依赖当作参数，然后设置它，或者如果`$adapter`这个属性是`public`的，我们可以直接去设置它。
