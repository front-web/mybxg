## 登录页
![image login](https://github.com/AlertZq/mybxg/blob/master/img-folder/login.jpg)
## 主页
![image index](https://github.com/AlertZq/mybxg/blob/master/img-folder/index.jpg)
## 个人中心
![image user](https://github.com/AlertZq/mybxg/blob/master/img-folder/user.jpg)
## 讲师管理
![image tc](https://github.com/AlertZq/mybxg/blob/master/img-folder/tc.jpg)
## 查看讲师
![image tc_preview](https://github.com/AlertZq/mybxg/blob/master/img-folder/tc_preview.jpg)
## 添加讲师
![image tc_add](https://github.com/AlertZq/mybxg/blob/master/img-folder/tc_add.jpg)
## 编辑讲师
![image tc_info](https://github.com/AlertZq/mybxg/blob/master/img-folder/tc_info.jpg)
## 课程列表
![image course](https://github.com/AlertZq/mybxg/blob/master/img-folder/course.jpg)
## 课程信息
![image course_info](https://github.com/AlertZq/mybxg/blob/master/img-folder/course_info.jpg)
## 课程图片
![image course_pic](https://github.com/AlertZq/mybxg/blob/master/img-folder/course_pic.jpg)
## 课时管理
![image lesson](https://github.com/AlertZq/mybxg/blob/master/img-folder/lesson.jpg)
## 编辑课时
![image lesson_info](https://github.com/AlertZq/mybxg/blob/master/img-folder/lesson_info.jpg)

# 测试前准备
- 将mybxg-api后台数据down到本地
- mybxg-doc为接口文档

# 本地测试需要搭建自己的环境

# Apache配置
## 配置网站跟路径(239行)
```html
DocumentRoot "e:/heima6/"
<Directory "e:/heima6/">
```

## 配置虚拟主机 
### 步骤一：httpd.conf文件498行
```
# Virtual hosts
Include conf/extra/httpd-vhosts.conf
```
### 步骤二：extra/httpd-vhost.conf文件
```
<VirtualHost *:80>
    DocumentRoot "e:/myweb/ajax"
    ServerName studyit.com
    ServerAlias www.studyit.com
    DirectoryIndex abc.html
</VirtualHost>
```
### 步骤三：配置hosts文件（C:\Windows\System32\drivers\etc\hosts)
```
127.0.0.1       studyit.com
127.0.0.1       www.studyit.com
```
### 步骤四：重启Apache服务器

## 配置反向代理（解决跨域问题）
### 步骤一：配置httpd.conf文件（134行和142行）
```
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
```
### 步骤二：配置conf/extra/httpd-vhosts.conf文件
```
<VirtualHost *:80>
    DocumentRoot "e:/heima6/jerry/studyit-bxg"
    ServerName studyit.com
    ServerAlias www.studyit.com
    ProxyRequests Off
    ProxyPass /api http://api.studyit.com
</VirtualHost>
```

## 地址栏隐藏index.php配置
### 步骤一：拷贝.htaccess文件到项目根目录
### 步骤二：配置httpd.conf文件（149行）
```
LoadModule rewrite_module modules/mod_rewrite.so
```
### 步骤三：配置httpd.conf文件(260行)
```
AllowOverride All
```

