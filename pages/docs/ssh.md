---
title: SSH
keywords: software
sidebar: home_sidebar
permalink: ssh.html
folder: docs
summary: Tips and tricks for SSH
---

# SSH

## SSH Proxy server

```bash
ssh -C -D port remoteurl 
```

## SSH Tunnel

```bash
ssh -C -f remoteurl -L $LPORT:localhost:$RPORT -N
```

Where $LPORT is the local port to be tunneled to the remote port $RPORT.

{% include links.html %}
