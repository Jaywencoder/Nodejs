# Nodejs

```
app.listen = function(){
  var server = http.createServer(this);
  return server.listen.apply(server, arguments);
};

const https = require('https');
const fs = require('fs');

const options = {
  key: fs.readFileSync('test/fixtures/keys/agent2-key.pem'),
  cert: fs.readFileSync('test/fixtures/keys/agent2-cert.pem')
};

https.createServer(options, (req, res) => {
  res.writeHead(200);
  res.end('hello world\n');
}).listen(8000);

```
PM2 

```
$ npm install pm2 -g     # 命令行安装 pm2 
$ pm2 start app.js -i 4 #后台运行pm2，启动4个app.js 
                                # 也可以把'max' 参数传递给 start
                                # 正确的进程数目依赖于Cpu的核心数目
$ pm2 start app.js --name my-api # 命名进程
$ pm2 list               # 显示所有进程状态
$ pm2 monit              # 监视所有进程
$ pm2 logs               #  显示所有进程日志
$ pm2 stop all           # 停止所有进程
$ pm2 restart all        # 重启所有进程
$ pm2 reload all         # 0秒停机重载进程 (用于 NETWORKED 进程)
$ pm2 stop 0             # 停止指定的进程
$ pm2 restart 0          # 重启指定的进程
$ pm2 startup            # 产生 init 脚本 保持进程活着
$ pm2 web                # 运行健壮的 computer API endpoint (http://localhost:9615)
$ pm2 delete 0           # 杀死指定的进程
$ pm2 delete all         # 杀死全部进程

运行进程的不同方式：
$ pm2 start app.js -i max  # 根据有效CPU数目启动最大进程数目
$ pm2 start app.js -i 3      # 启动3个进程
$ pm2 start app.js -x        #用fork模式启动 app.js 而不是使用 cluster
$ pm2 start app.js -x -- -a 23   # 用fork模式启动 app.js 并且传递参数 (-a 23)
$ pm2 start app.js --name serverone  # 启动一个进程并把它命名为 serverone
$ pm2 stop serverone       # 停止 serverone 进程
$ pm2 start app.json        # 启动进程, 在 app.json里设置选项
$ pm2 start app.js -i max -- -a 23                   #在--之后给 app.js 传递参数
$ pm2 start app.js -i max -e err.log -o out.log  # 启动 并 生成一个配置文件
你也可以执行用其他语言编写的app  ( fork 模式):
$ pm2 start my-bash-script.sh    -x --interpreter bash
$ pm2 start my-python-script.py -x --interpreter python
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

这是高阶标题(效果和一级标题一样)
=
这是次阶标题(效果和二级标题一样)
-
1. 第一点
2. 第二点
4. 第三点

- 这是无序列表项目
+ 这是无序列表项目
* 这是无序列表项目

 呵呵
    * 嘉嘉
    - 嘻嘻
    - 吼吼
        - 嘎嘎
        + 桀桀
* 哈哈


> 这是一级引用
>> 这是二级引用
>>> 这是三级引用

> 这是一级引用


```
/** 
   * nth element in the fibonacci series. 
   * @param n >= 0 
   * @return the nth element, >= 0. 
   */
 function fib(n) { 
     var a = 1, b = 1; 
     var tmp; 
     while (--n >= 0) { 
         tmp = a;
         a += b; 
         b = tmp;
     }
     return a; 
 }
 document.write(fib(10));
```


void main()
{
``
printf("Hello, Markdown.");
``
}

这就是行内链接：[baidu](http://www.baidu.com "baidu")