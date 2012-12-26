鸟哥的Linux私房菜

Ubunut中文论坛





alias
- 关闭端口：使用 lsof -i :端口号 来得到该端口的PID,然后用 kill -9 PID 杀之.



	wget -r -p -np -k http://developer.chrome.com/extensions/
	-r, --recursive（递归） specify recursive download.（指定递归下载）
	-k, --convert-links（转换链接） make links in downloaded HTML point to local files.（将下载的HTML页面中的链接转换为相对链接即本地链接）
	-p, --page-requisites（页面必需元素） get all images, etc. needed to display HTML page.（下载所有的图片等页面显示所需的内容）
	-np, --no-parent（不追溯至父级） don't ascend to the parent directory