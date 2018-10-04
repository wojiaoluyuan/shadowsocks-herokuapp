到目前还能用，us比eu的要快，本人PC系统是opensuse,配合privoxy可以实现全局代理，手机为安卓6.0,也可以配合privoxy,然后设置wifi代理，或者设置手机网络的接受点（APN），同样也可以实现全局代理，一定要先运行node项目,再运行privoxy.

shadowsocks-heroku
==================

shadowsocks-heroku is a lightweight tunnel proxy which can help you get through firewalls. It is a port of [shadowsocks](https://github.com/clowwindy/shadowsocks), but through a different protocol.

shadowsocks-heroku uses WebSocket instead of raw sockets, so it can be deployed on [Heroku](https://www.heroku.com/).

Notice that the protocol is INCOMPATIBLE with the origin shadowsocks.

Heroku
------

### Usage

```
首先将本项目下载并解压
$ cd shadowsocks-herokuapp    //在项目中打开一个shell并进入到解压的项目中
本地上传
$ heroku login  //登录你的heroku账号
$ heroku create  yourappname  //或者直接在heroku 的网页后台创建app
$ git init
$ heroku git:remote -a yourappname
$ git add .
$ git commit -am "make it better"
$ git push heroku master
$ heroku config:set METHOD=rc4 KEY=foobar

Supported Ciphers //支持以下几种加密方式
-----------------

- rc4
- rc4-md5
- table
- bf-cfb
- des-cfb
- rc2-cfb
- idea-cfb
- seed-cfb
- cast5-cfb
- aes-128-cfb
- aes-192-cfb
- aes-256-cfb
- camellia-256-cfb
- camellia-192-cfb
- camellia-128-cfb

$ npm install //本地安装
$ node local.js -s yorappname.herokuapp.com -l 1080 -m rc4 -k foobar -r 80
server listening at { address: '127.0.0.1', family: 'IPv4', port: 1080 }
```

Change proxy settings of your browser into:

```
SOCKS5 127.0.0.1:1080
```

### Troubleshooting

If there is something wrong, you can check the logs by:

```
$ heroku logs -t --app yourappname
```

