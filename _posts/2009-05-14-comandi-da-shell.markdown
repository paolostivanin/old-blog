---
author: pol@blog
comments: true
date: 2009-05-14 21:46:42+00:00
layout: post
slug: comandi-da-shell
title: Shell's cmd [1]!
wordpress_id: 708
categories:
- Debian &amp; Co
- Ubuntu
- Unix
---

Per vedere la top ten dei files/directory in ordine decrescente di grandezza:


`du -sb *|sort -nr|head|awk '{print $2}'|xargs du -sh`




[caption id="attachment_1101" align="alignnone" width="300" caption="risultato del comando"][![]({{ site.baseurl }}/images/2009/05/shellcm1-300x62.png)]({{ site.baseurl }}/images/2009/05/shellcm1.png)[/caption]
