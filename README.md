# TCP 客户端

本项目采用 go 语言编写，提供一个 tcp 客户端，专门用作各种 socket 测试

## 作为 HTTP 客户端

本程序最主要的功能之一是作为一个 HTTP 客户端，下面是针对不通请求方式的具体用法。

### 普通 GET 请求

	# 发送普通 GET 请求到 localhost
	ztcp -http=:8080/app/doit?nm=f8f9
	
	# 发送普通 GET 请求到 localhost:80
	ztcp -http=/app/index.html
	
	# 发送普通 GET 到 www.google.com
	ztcp -http=www.google.com
	
### 发送 Cookie

    # 发送普通 cookie 字符串
    ztcp -http=/app/doit -cookie="CNZZDATA1291011=cnzz_eid;"

    # 发送文件里的 cookie 字符串
    ztcp -http=/app/doit -cookief="mycookie.txt"

### 普通 POST 请求
	
	# 发送简单的参数
	ztcp -http=:8080/app/doit -type=form -body="a=10&b=hello"
	
	# 可以把请求内容记录到文件里
	ztcp -http=:8080/app/doit -type=form -f=/home/xiaobai/form.txt
	--------------------------- form.txt 文件的内容就是 :
	a=10&b=hello
	
### JSON 请求
	
	# 发送 JSON 请求
	ztcp -type=json -http=localhost:8080/app/doit -body="{nm:'zozoh'}"
	
	# 采用文件的方式发送 JSON 请求
	ztcp -type=json -http=localhost:8080/app/doit \
	    -f=/home/xiaobai/test.json

### 控制 HTTP 返回的开关
	
	# 是否显示请求，响应，的头部信息，默认为 "none"
	tcp … -out=all,req,resp,none …
	
	    
### 支持的 -type

	form : application/x-www-form-urlencoded
	text : text/plain
	json : application/json
	css  : text/css
	html : text/html
	png  : image/png
    file : application/octet-stream
