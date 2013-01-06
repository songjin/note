http://blog.seymourdev.com/?p=10

localhost:~ Alex$ sudo ssh -CfND 22 -i alex_rsa alex@tydus.tk

sock代理设置 localhost+端口号

解释一下:
sudo 获取权限
ssh 运行ssh
-CfND 绑定端口并且在后台运行
22 端口号, 和刚才填的一样就行
-i 选择私钥(private key)
alex_rsa 私钥名称(因为终端打开就在~/下了, btw不要学我把文件到处乱扔)
alex@tydus.tk username@host 用户名@地址

如果不用私钥登录就把私钥的参数去掉, 服务器会提示你输入密码, 麻烦点就是了.

退出的时候在网络设置里面把SOCKS代理的钩子去掉就好了, 如果想停止ssh, 就在终端输入:
sudo killall ssh
切记一定要加sudo, 不然killall就会在user的范围内杀进程, 而ssh是属于root的.

另外, 写了个.sh脚本, 不过不知道怎样让网络应用新的设置, 所以就不丢上来了.