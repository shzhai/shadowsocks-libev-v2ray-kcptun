# shadowsocks-libev-obfs-kcptun
Build integrated-shadowsocks-libev-obfs-plugin-with-kcptun on ubuntu 16.04 based on https://github.com/shadowsocks/shadowsocks-libev/releases/ and https://github.com/xtaci/kcptun/releases

[![](https://images.microbadger.com/badges/image/shzhai/shadowsocks-libev-obfs-kcptun.svg)](https://microbadger.com/images/shzhai/shadowsocks-libev-obfs-kcptun "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/shzhai/shadowsocks-libev-obfs-kcptun.svg)](https://microbadger.com/images/shzhai/shadowsocks-libev-obfs-kcptun "Get your own version badge on microbadger.com")
## support version 
  - Ubuntu 16.04
  - Shadowsocks-libev version 3.1.3
  - Kcptun version 20180316

## How to use this repo
```sh
docker run -d -p 2222:2222 -p 2222:2222/udp -p 3333:3333/udp --restart always --env-file ss-kcp.config shzhai/shadowsocks-libev-obfs-kcptun
```

> The first and second -p parameter will use to map shadowsockcs tcp/udp port 
> 2222 to external, and the third -p parameter will use to map kcptun udp port 
> 3333 to external, we will use an environment file ss-kcp.config to config 
> shadowsocks and kcptun parameters include the ports above. 
> For detail of the configurable parameters will list down below.
> You can also use -e to override the settings but that won't be necessary.

Download this environment config file from https://raw.githubusercontent.com/shzhai/shadowsocks-libev-obfs-kcptun/master/ss-kcp.config and change the settings according to your need.  

## Configurable Parameters for kcp-tun.config
### Shadowsocks
| Parameter | Default value | Common setting | Recommend Change |
| ------ | ------ |------ |------ |
| SERVER_ADDR | 0.0.0.0 | | |
| SERVER_PORT | 2222 | | ✅ |
| LOCAL_PORT | 1080 | | |
| PASSWORD | examplepwd | | ✅ |
| METHOD | chacha20-ietf-poly1305 |rc4-md5,aes-256-cfb,chacha20-ietf,chacha20-ietf-poly1305 | ✅ |
| TIMEOUT | 60 | | ✅ |
| FASTOPEN | --fast-open | | |
| UDP_RELAY | -u | | |
### Kcptun
| Parameter | Default value | Common setting | Recommend Change |
| ------ | ------ |------ |------ |
| KCP_LISTEN | 3333 | | ✅ |
| KCP_PASS | examplepwd | | ✅ |
| KCP_ENCRYPT | salsa20 | aes, aes-128, aes-192, salsa20 | ✅ |
| KCP_MODE | fast2 | fast,fast2 | |
| KCP_MTU | 1400 | | ✅ |
| KCP_SNDWND | 2048 | tune from 1024 (Bandwidth > 100M)| ✅ |
| KCP_RCVWND | 2048 | tune from 1024 (Bandwidth > 100M)| ✅ |
| KCP_DSCP | 46 | | ✅ |
| KCP_NOCOMP | false | | ✅ |

## Reference of KCPTun introduction and Tunning 
* https://blog.kuoruan.com/102.html

## Chagnelog
* 2018-4-14 Initialize this repository from github automation build.
* 2018-4-16 Correct ss-kcp.config and rebuild image.

## Contact
<Shawn.zhai@gmail.com>
