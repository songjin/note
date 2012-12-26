

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




- http://www.infoq.com/cn/articles/sinatra-intro






Ruby主流的ORM库有Sequel，DataMapper和来自Rails的ActiveRecord


DataMapper
Sequel

<http://bytesofpi.com/post/23663592388/up-and-running-with-sinatra-and-activerecord>

<http://www.brandon-harris.com/sinatra/2010/03/28/simple-sinatra-activerecord-app-with-migrations.html>


<http://ruby.about.com/od/sinatra/a/datamapper.htm>

[datamapper入门](http://ruby-china.org/topics/6501)



	require 'dm-core'
	require 'dm-migrations'
	
	# Open the database test1.db
	DataMapper.setup :default, "sqlite3://#{Dir.pwd}/test1.db" 
	
	# Define the Person model
	class Person
	  include DataMapper::Resource
	
	  property :firstname, String
	  property :lastname, String
	  property :email, String, :key => true
	end
	
	# Automatically create the tables if they don't exist
	DataMapper.auto_migrate!
	
	# Create a new record
	p = Person.new
	p.attributes = {
	  :firstname => 'John',
	  :lastname => 'Doe',
	  :email => 'john.doe@email.com'
	}
	
	# Save it to the database
	p.save
	
	# Make some changes to the object
	p.lastname = 'Smith'
	p.save
	
	# Create a new object and destroy it
	p2 = Person.new
	p2.email = 'testing@testing.com'
	p2.save
	
	p2.destroy
	
	# Find a record from the database
	p3 = Person.get('john.doe@email.com')
	puts p3.inspect # => #<Person @firstname="John" @lastname="Smith" @email="john.doe@email.com">
	
	
#　模板语言

[HAML](http://haml.info)
[Slim](http://slim-lang.com)
