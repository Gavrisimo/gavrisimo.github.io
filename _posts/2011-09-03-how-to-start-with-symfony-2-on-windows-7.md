---
title: How to start with Symfony 2 on Windows 7
author: Miloš Gavrilović
layout: post
permalink: /how-to-start-with-symfony-2-on-windows-7/
categories:
  - PHP
---
This task can be little bit scary at first, but it is really, really simple to do... <img src="http://milos.gavrilovic.rs/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />

*Disclaimer: This is more of a reminder for me then what you might call &#8220;tutorial&#8221;...*

1.  Download latest version of <a title="http://www.easyphp.org/download.php" href="http://www.easyphp.org/download.php" target="_blank">EasyPHP</a>, install it and then start it.
2.  In order to add php to your path follow <a title="http://www.php.net/manual/en/faq.installation.php#faq.installation.addtopath" href="http://www.php.net/manual/en/faq.installation.php#faq.installation.addtopath" target="_blank">these</a> steps.
3.  Download latest version of <a title="http://symfony.com/download" href="http://symfony.com/download" target="_blank">Symfony 2</a>.
4.  Open <a title="http://127.0.0.1/home/" href="http://127.0.0.1/home/" target="_blank">administration page</a> of EasyPHP.
5.  Extract Symfony 2 zip(or tgz) file and place it somewhere. Then <a title="http://127.0.0.1/home/index.php?to=add_alias_1" href="http://127.0.0.1/home/index.php?to=add_alias_1" target="_blank">create alias in EasyPHP</a> for that folder where you extracted Symfony 2 archive.
6.  If you open that alias now in your localhost and go to web/config.php you will see some warnings.
7.  You need to download <a title="http://downloads.php.net/pierre/php_apc-20110109-5.3-vc9-x86.zip" href="http://downloads.php.net/pierre/php_apc-20110109-5.3-vc9-x86.zip" target="_blank">php_apc.dll</a> file and then copy it to %EasyPHP%/php/ext folder. Now right click on EasyPHP icon in taskbar and click on Configuration->PHP extension.
8.  Locate php\_apc.dll and php\_intl.dll and enable both of them. After that just restart EasyPHP.
9.  Open Apache folder inside %EasyPHP% and copy php.ini to C:/Windows

Now when you go to web/config.php you won't see any warnings and you can easily follow instructions in <a title="http://symfony.com/doc/current/book/index.html" href="http://symfony.com/doc/current/book/index.html" target="_blank"><strong>The Book</strong></a> and you can even use all those commands to auto generate bundles and whatnot in those examples... <img src="http://milos.gavrilovic.rs/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />

After you complete step #9 you can do these commands:

*   Generate getters and setters for your entities: <pre class="brush: plain; title: ; notranslate" title="">php app/console doctrine:generate:entities Acme
</pre>

*   Create database based on your settings: <pre class="brush: plain; title: ; notranslate" title="">php app/console doctrine:database:create
</pre>

*   Create tables in your database based on your schema(if you want to drop already existing table before creating new one): <pre class="brush: plain; title: ; notranslate" title="">php app/console doctrine:schema:create (--dump-sql)
</pre>

Use &#8220;Doctrine Fixtures extension and bundle&#8221; to generate dummy content fast:

*   Add following lines to &#8220;deps&#8221; file located in your project root: <pre class="brush: plain; title: ; notranslate" title="">[doctrine-fixtures]
	git=http://github.com/doctrine/data-fixtures.git

[DoctrineFixturesBundle]
	git=http://github.com/symfony/DoctrineFixturesBundle.git
	target=/bundles/Symfony/Bundle/DoctrineFixturesBundle
</pre>

*   Run this command to update your vendors: <pre class="brush: plain; title: ; notranslate" title="">php bin/vendors install</pre>

*   Open &#8220;app/autoloader.php&#8221; and above this line: <pre class="brush: plain; title: ; notranslate" title="">'Doctrine\Common'                  =&gt; __DIR__.'/../vendor/doctrine-common/lib',</pre>

    Add this line:

    <pre class="brush: plain; title: ; notranslate" title="">'Doctrine\Common\DataFixtures'    =&gt; __DIR__.'/../vendor/doctrine-fixtures/lib',</pre>

*   Open &#8220;app/AppKernel.php and register new bundle: <pre class="brush: plain; title: ; notranslate" title="">new SymfonyBundleDoctrineFixturesBundleDoctrineFixturesBundle(),</pre>

After this you need to create your data fixtures file. You can see <a title="http://tutorial.symblog.co.uk/docs/doctrine-2-the-blog-model.html#blog-fixtures" href="http://tutorial.symblog.co.uk/docs/doctrine-2-the-blog-model.html#blog-fixtures" target="_blank">here</a> how to that.
