​
Notepad这是一个开源的网络记事本项目，这基于Minimalist-Web-Notepad项目，能够在每次打开的时候，提供一个独特的网址，用来临时保存文本内容，只要知道这个网址，就能在其他地方浏览到这些文本内容。

请参阅 https://nihaotang.com

在同一个平台上平时只需要记住后缀就可以了。



安装
在index.php文件顶部，更改$base_url变量以指向您的站点。

确保允许 Web 服务器写入_tmp目录。

在Apache
.htaccess您可能需要启用 mod_rewrite 并在站点配置中设置文件。请参阅如何为 Apache 设置 mod_rewrite。

在 Nginx 上
要启用 URL 重写，请在配置文件中添加如下内容：

如果项目位于根目录中：

​
```
location / {
    rewrite ^/([a-zA-Z0-9_-]+)$ /index.php?note=$1;
}
```

如果项目位于子目录中：
```
location ~* ^/notes/([a-zA-Z0-9_-]+)$ {
    try_files $uri /notes/index.php?note=$1;
}
```

