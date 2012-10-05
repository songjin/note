

## Hello world

安装sinatra:

	gem install sinatra
	
写hello world很简单


	'sinatra'

	get '/hi' do
 	 "Hello World!"
	end

保存为hello.rb,执行

	ruby hello.rb

你会在终端中看到类似下面的信息：

	[2012-10-06 00:21:35] INFO  WEBrick 1.3.1
	[2012-10-06 00:21:35] INFO  ruby 1.9.3 (2012-02-16) [x86_64-darwin12.0.0]
	== Sinatra/1.3.3 has taken the stage on 4567 for development with backup from WEBrick
	[2012-10-06 00:21:35] INFO  WEBrick::HTTPServer#start: pid=973 port=4567
	
Sinatra默认使用WEBrick服务器，开启一个4567端口。现在，打开浏览器，打开0:0:0:0:4567,你就能看到Hello World了。

## 什么是Sinatra

Sinatra是Ruby写成的一个DSL（domain-specific language 领域专门语言），就是一门专门用来写网站的语言。其实就是Ruby加了一点语法而已。

它能帮你搞定HTTP请求什么的，你写几行代码就可以构建Web应用了。

## 什么是HTTP

HTTP是超文本传输协议（HTTP，HyperText Transfer Protocol，最初是设计用来传输HTML用的。

说白了，就是客户端和服务器之间怎么交流的方式，一种约定。