
POST请求   http://172.16.102.208:8089/wiapi/score?leaderboard_id=1&score=36&app_key=66

  目的1：通过脚本发送post请求。
  答案： curl -d "leaderboard_id=7778a8143f111272&score=19&app_key=8d49f16fe034b98b&_test_user=test01" "http://172.16.102.208:8089/wiapi/score"

  目的2：通过脚本发送post请求，顺便附带文本数据，比如通过"浏览"选择本地的card.txt并上传发送post请求
  答案：  curl  -F "blob=@card.txt;type=text/plain"  "http://172.16.102.208:8089/wiapi/score?leaderboard_id=7778a8143f111272&score=40&app_key=8d49f16fe034b98b&_test_user=test01"   

   其中-F 为带文件的形式发送post请求，   blob为文本框中的name元素对应的属性值。<type="text" name="blob">
