---
layout: post
title: "Installing GitLab on FreeBSD"
date: 2011-11-05 20:41
published: false
comments: false
categories:
- FreeBSD
- Git
- GitLab
- Guide
---

**Dependencies/packages:**

- ftp/wget
- lang/v8
- database/sqlite3
- textproc/libxml2
- textproc/libxslt
- textproc/py-pygments

``` bash
cd /usr/ports/database/sqlite3 && sudo make install clean
cd /usr/ports/textproc/libxml2 && sudo make install clean
cd /usr/ports/textproc/libxslt && sudo make install clean
cd /usr/ports/textproc/py-pygments && sudo make install clean
cd /usr/ports/ftp/wget && sudo make install clean
cd /usr/ports/lang/v8 && sudo make install clean

wget http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.gz 
tar xzvf ruby-1.9.3-p0.tar.gz
cd ruby-1.9.3-p0
./configure
make
sudo make install

sudo gem update --system

git clone git://github.com/gitlabhq/gitlabhq.git
cd gitlabhq
bundle install0

```
