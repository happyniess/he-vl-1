

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/happyniess/he-vl-1/tree/master)

## 注意

Address: yourAppName.herokuapp.com   
Port: 443   
id: Your entered id   
Flow: xtls-rprx-direct   
encryption: none   
Transport: ws   
TLS: tls      

## 流量中转

可以使用cloudflare的workers来`中转流量`，配置为：  https://dash.cloudflare.com/login
```
addEventListener(
    "fetch",event => {
        let url=new URL(event.request.url);
        url.hostname="xx.xxxx.xx";//你的heroku域名
        let request=new Request(url,event.request);
        event.respondWith(
            fetch(request)
        )
    }
)
```

```
addEventListener(
  "fetch",event => {
     let url=new URL(event.request.url);
     if (new Date().getDate()%2==0) {
       url.hostname="first.herokuapp.com";//你的heroku域名
     } else {
       url.hostname="second.herokuapp.com";//你的heroku域名
     }
     let request=new Request(url,event.request);
     event.respondWith(
       fetch(request)
     )
  }
)
```

### 客户端软件推荐v2rayN
https://github.com/2dust/v2rayN/releases/tag/4.20
