---
layout: post
title:  "Tunnel Here. Tunnel There. Reverse That"
date: 2019-03-01 
categories: ssh
---

Access VNC from far away.

```sh 
Host firstHop
    Hostname x.x.x.x
    User username
    IdentityFile ~/.ssh/firstHop-id_rsa
Host secondHop
    Hostname x.x.x.x
    User username
    IdentityFile ~/.ssh/secondHop-id_rsa
    ProxyCommand ssh firstHop -W %h:%p
Host thirdHop
    Hostname 127.0.0.1
    User username
    IdentityFile ~/.ssh/thirdHop-id_rsa
    ProxyCommand ssh secondHop -W %h:%p
    Port xxxx
    LocalForward xxxx 127.0.0.1:5901
```

