---
comments: true
date: 2014-12-17
layout: post
title: 'Securing Chromium/Chrome'
subtitle: 'Disable SSLv3 and blacklist RC4 from Chromium/Chrome'
---

Both Chromium and Chrome *(up to version 39.0.2171.95)* have two security issues.

Firstly, SSLv3 is still enable by default so the browser is vulnerable to the [POODLE Attack](https://www.openssl.org/~bodo/ssl-poodle.pdf). Secondly, it allows the use of the insecure RC4 cipher.

To disable SSLv3 and blacklist each cipher that uses RC4 you must append to the `CHROMIUM_FLAGS` inside the file `/etc/chromium/default` the following string:

    --ssl-version-min=tls1 --cipher-suite-blacklist=0x0004,0x0005,0xc007,0xc011

Finally, you have to try if it is all ok by visiting [this](https://www.ssllabs.com/ssltest/viewMyClient.html) link. If you don't see any warning then everything went fine.
