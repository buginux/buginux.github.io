---
title: "在终端使用代理"
date: 2017-04-23
---

本人在 Mac 端使用的是 EurekaVPT 家的 SSLEdge，配合 GoAgentX 进行使用的。因为 SSLEdge 天然支持 http 协议，所以要在终端中使用代理相当容易：

```bash
$ export http_proxy=http://127.0.0.1:8016
$ export https_proxy=http://127.0.0.1:8016
```

为了方便起见，可以直接写入到 `.bashrc` 或者 `.zshrc` 当中。
