让Net::HTTP自动使用代理 [复制链接]
 
坛主

多币873 威望825 UID106537
串个门加好友打招呼发消息	
电梯直达1#
 车迷 发表于 2011-11-4 15:46:47 |只看该作者 |倒序浏览
拜和谐的大防火墙所赐，调用微薄，人人等国外克隆网站的api需要用代理，而老外写的第3方lib通常没有考虑代理支持。 

一个小技巧，只要这些lib是用Net::HTTP来访问的，那么只要用一段小代码就能自动切换到Net::HTTP:roxy，而无需改动原始代码： 

Ruby代码 
#这里从环境变量读取，可以改成从配置文件读取   
if ENV['http_proxy']   
  module Net   
    class << HTTP   
      alias ld_new :new  
  
      def new(address, port = nil)   
        proxy = URI.parse(ENV['http_proxy'])   
        Net::HTTP:roxy(proxy.host, proxy.port, proxy.user, proxy.password).old_new(address, port)   
      end  
    end  
  end  
end  

#这里从环境变量读取，可以改成从配置文件读取
if ENV['http_proxy']
  module Net
    class << HTTP
      alias ld_new :new

      def new(address, port = nil)
        proxy = URI.parse(ENV['http_proxy'])
        Net::HTTP:roxy(proxy.host, proxy.port, proxy.user, proxy.password).old_new(address, port)
      end
    end
  end
end