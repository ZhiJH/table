# 配置

##express
```
var express = require('express');
var app = express();
```

##模板引擎
```
var ejs = require('ejs');

app.set("view engine","ejs");
```

##静态服务
```
app.use(express.static("./public"));
```


##cookie公式
```
var cookieParser  = require("cookie-parser");

app.use(cookieParser());
//赋值
res.cookie("name",username,{maxAge: 900000, httpOnly: true});
//取值
req.cookie.username
```

##session公式：
```
var session = require('express-session');
app.use(session({
    secret: 'keyboard cat',
    resave: false,
    saveUninitialized: true
}));
```


##socket.io公式：
```
var http = require('http').Server(app);
var io = require('socket.io')(http);
```

##nodejs API 原生写法
```
//引入http一个包
var http = require("http");
var fs = require("fs");
var url = require("url");

// 创建服务器
var server = http.createServer(function(req,res){
    if(req.url == "/zheng"){
        fs.readFile("./html/01.html",function(err,data){

            res.writeHead(200,{"Content-type":"text/html;charset=UTF-8"});
            res.end(data);

        })
    }else{
        res.writeHead(404,{"Content-type":"text/html;charset=UTF-8"});
        res.end("哈哈，没有这个页面");
    }



});

// 运行服务器，连接端口信息
server.listen(3000,"127.0.0.1");
```