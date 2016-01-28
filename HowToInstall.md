## 安装指南 ##
  1. 下载程序
  1. 编写或下载oAuth发推的东西（可以按照 HowToEdit 页进行修改）
  1. 

&lt;del&gt;

在本地编辑work.php（修改头部的机器人账户设定）

&lt;/del&gt;


  1. 如果需要，再按照 HowToEdit 页进行更多修改
  1. 保存文件（编码为无BOM签名的UTF-8）
  1. 上传程序文件到服务器
  1. 最好设置文件所在文件夹及文件的权限为777（否则无法防止重复锐推）
  1. 在服务器的控制面板上设置好Cron Jobs(Linux)或者计划任务(Windows)

### 【参考】使用cPanel的空间的Cron Job设置方法 ###
  1. 登陆进入cPanel，找到Cron Jobs（时钟守护作业）
  1. 在Add New Cron Job下面将Minute设置为`*/5` （表示每5分钟执行一次），其他设置为`*`
  1. 将Command处修改为 `/usr/bin/php -q /home/你的cPanel用户名/public_html/你的程序php文件路径`
  1. 点击Add New Cron Job添加即可

至于修改方法，请参考 HowToEdit 页