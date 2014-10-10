---
layout: layout
title:  Linux 上部署 Django
category: 技术
---

<h2>{{ page.title }}</h2>


按照Django官方文档安装Django实在容易迷失，为此老汉写一贴。

我采用的是 ubuntu 12.04 版本 ＋ python 2.7 ，参考了 Ayman Farhat 和 PDX pixel文章，在此致谢。


更新部件

{% highlight linux-config %} sudo apt-get update {% endhighlight %}

安装vim

{% highlight linux-config %}sudo apt-get install vim{% endhighlight %}

安装pip (参考 https://pypi.python.org/pypi/pip/).

{% highlight linux-config %}
sudo apt-get install python-pip python-dev build-essential{% endhighlight %}


{% highlight linux-config %}
pip install --upgrade pip {% endhighlight %}

安装数据库和virtualenv

{% highlight linux-config %}pip apt-get install mysql-server{% endhighlight %}

{% highlight linux-config %}pip install virtualenv{% endhighlight %}

开始virtualenv使用

{% highlight linux-config %}
mkvirtualenv /home/mysite --no-site-packages{% endhighlight %}

安装Django

{% highlight linux-config %}
pip install Django==version number{% endhighlight %}

开始项目

{% highlight linux-config %}
mkdir /home/andy
cd /home/andy
source ./bin/activate

django-admin.py startproject andy{% endhighlight %}


安装和配置数据库

{% highlight html %}
mysql -u root -p ***** (database name)

CREATE DATABASE andy;
SHOW DATABASES;
{% endhighlight %}


{% highlight linux-config %}vim andy/andy/settings.py{% endhighlight %}

{% highlight html %}
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql', # Using 'mysql' for this tutorial.
        'NAME': 'mysite', # Database name.
        'USER': 'root',
        'PASSWORD': '******',
        'HOST': '', # Empty for localhost.
        'PORT': '', # Empty string for default.
    }
}
{% endhighlight %}

还是数据库 (顺利很重要！！！)

{% highlight linux-config %}
sudo apt-get install python-mysqldb
sudo apt-get install libmysqlclient-dev
pip install mysql-python{% endhighlight %}

同步
{% highlight linux-config %}python manage.py syncdb{% endhighlight %}


开始安装Apache 和 mod_wsgi

{% highlight linux-config %}
sudo apt-get install apache2 apache2.2-common apache2-mpm-prefork apache2-utils libexpat1
sudo apt-get install libapache2-mod-wsgi{% endhighlight %}

检查 Apache 安装情况

{% highlight linux-config %}sudo service apache2 restart{% endhighlight %}

Apache 配置

{% highlight linux-config %}vim /etc/apache2/sites-available/mysite{% endhighlight %}

安装WSGI有许多方法，以官方的文档为准

{% highlight linux-config %}vim /home/django_projects/mysite/mysite/wsgi.py{% endhighlight %}


{% highlight html %}
import os
import sys
import site

site.addsitedir('~/.virtualenvs/mysiteenv/local/lib/python2.7/site-packages')

sys.path.append('/home/django_projects/mysite')
sys.path.append('/home/django_projects/mysite/mysite')

os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler(){% endhighlight %}

配置Django静态文件

{% highlight linux-config %}
mkdir /var/www/mysite/static
vim /home/django_projects/mysite/mysite/settings.py{% endhighlight %}


收集静态文件

{% highlight linux-config %}python manage.py collectstatic --noinput{% endhighlight %}

重启Apache,一切OK

{% highlight linux-config %}sudo service apache2 restart{% endhighlight %}
