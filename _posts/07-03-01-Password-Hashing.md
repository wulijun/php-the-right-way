---
isChild: true
---

## 密码哈希 {#password_hashing}

最终每个人都会需要创建一个依赖用户登录的 PHP 应用。 用户名和密码被存放在数据库以便在后面用户登录的时候用来验证。

重要的是你应该适当地在存储之前 [_哈希_][3] 密码。 密码哈希是一个不可逆的、单向的函数作用于用户的密码之上。这会产生一个固定长度的字符串让你不可能逆转，意味着你可以比较两个哈希来判断他们是否来自于同一个源字符串，但你不能得到原来的字符串是什么。如果密码没有哈希过并且你的数据库被未授权的第三方访问到，所有用户的账户都会受到影响。有些用户可能（不幸的）在其他服务上使用相同的密码，因此，安全问题需要慎重考虑。

**使用 `password_hash` 来哈希密码**

在 PHP 5.5 `password_hash` 将会被推出。这次它将使用 BCrypt，这是 PHP 当前支持的最强的算法。这将会根据未来的需要更新来支持更多的算法。`password_compat` 库被创建用于提供 PHP >= 5.3.7 的向前兼容。

下面我们会哈希一个字符串，然后和另一个新的字符串的哈希作比较。因为我们两个源字符串是不一样的('secret-password' 和 'bad-password') 这个验证不会通过。 

{% highlight php %}                                                                                                                                                                                              
<?php                                                                                                                                                                                                            
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    //Correct Password
} else {
    //Wrong password
}
{% endhighlight %}  



* [学习关于 `password_hash`] [1]
* [`password_compat` for PHP  >= 5.3.7 && < 5.5] [2]
* [学习密码学里面的哈希] [3]
* [PHP `password_hash` RFC] [4]

[1]: http://us2.php.net/manual/en/function.password-hash.php
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
