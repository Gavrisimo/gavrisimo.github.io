---
title: How to start with Symfony 2 on Windows 7
author: Miloš Gavrilović
layout: post
permalink: /how-to-start-with-symfony-2-on-windows-7/
---
This task can be little bit scary at first, but it is really, really simple to do... :)

*Disclaimer: This is more of a reminder for me then what you might call "tutorial"...*

1. Download latest version of [EasyPHP](http://www.easyphp.org/download.php), install it and then start it.
2. In order to add php to your path follow [these](http://www.php.net/manual/en/faq.installation.php#faq.installation.addtopath) steps.
3. Download latest version of [Symfony 2](http://symfony.com/download).
4. Open [administration page](http://127.0.0.1/home/) of EasyPHP.
5. Extract Symfony 2 zip(or tgz) file and place it somewhere. Then [create alias in EasyPHP](http://127.0.0.1/home/index.php?to=add_alias_1) for that folder where you extracted Symfony 2 archive.
6. If you open that alias now in your `http://localhost` and go to `web/config.php` you will see some warnings.
7. You need to download [php_apc.dll](http://downloads.php.net/pierre/php_apc-20110109-5.3-vc9-x86.zip) file and then copy it to `%EasyPHP%/php/ext` folder. Now right click on `EasyPHP` icon in taskbar and click on `Configuration->PHP` extension.
8. Locate `php\_apc.dll` and `php\_intl.dll` and enable both of them. After that just restart EasyPHP.
9. Open Apache folder inside `%EasyPHP%` and copy `php.ini` to `C:/Windows`

Now when you go to `web/config.php` you won't see any warnings and you can easily follow instructions in [The Book](http://symfony.com/doc/current/book/index.html) and you can even use all those commands to auto generate bundles and whatnot in those examples... :)

After you complete step #9 you can do these commands:

1. Generate getters and setters for your entities: `php app/console doctrine:generate:entities Acme`
2. Create database based on your settings: `php app/console doctrine:database:create`
3. Create tables in your database based on your schema(if you want to drop already existing table before creating new one): `php app/console doctrine:schema:create (--dump-sql)`

Use `Doctrine Fixtures extension and bundle` to generate dummy content fast:

1. Add following lines to `deps` file located in your project root:
{% highlight linenos %}
[doctrine-fixtures]
	git=http://github.com/doctrine/data-fixtures.git
[DoctrineFixturesBundle]
	git=http://github.com/symfony/DoctrineFixturesBundle.git
	target=/bundles/Symfony/Bundle/DoctrineFixturesBundle
{% endhighlight linenos %}
3. Run this command to update your vendors: `php bin/vendors install`
4. Open `app/autoloader.php` and above this line: `Doctrine\Common' => __DIR__.'/../vendor/doctrine-common/lib'` add this line: `'Doctrine\Common\DataFixtures' => __DIR__.'/../vendor/doctrine-fixtures/lib'`
5. Open `app/AppKernel.php` and register new bundle: `new SymfonyBundleDoctrineFixturesBundleDoctrineFixturesBundle()`

After this you need to create your data fixtures file. You can see [here](http://tutorial.symblog.co.uk/docs/doctrine-2-the-blog-model.html#blog-fixtures) how to that.
