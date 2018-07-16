# Nginx install 

#### 应用场景
Nginx是一款轻量级的Web 服务器,并发能力强，提供反向代理和负载均衡。

#### 安装教程 
一、下载<br> 
目录/usr/local/nginx
>>sudo wget  http://nginx.org/download/nginx-1.13.3.tar.gz<br>

二、解压<br>
>>sudo tar -zxvf nginx-1.13.3.tar.gz

三、配置命令
>>cd nginx-1.13.3<br>
>>sudo ./configure --prefix=/usr/local/nginx

(如果报错，安装以下pcre包，再重新执行配置命令)
>>sudo apt-get update<br>
>>sudo apt-get install libpcre3 libpcre3-dev<br>

maybe need
>>sudo apt-get install openssl libssl-dev

四、安装
>>sudo make install<br>
>>启动服务 sudo /usr/local/nginx/sbin/nginx

五、请求转发基本配置<br>
目录 conf/nginx.xml<br>
```
http {
    server {
            listen       8084;
            server_name example.com;

            location /analysis/ {
                    proxy_pass http://example.com:prot/analysis/;
            }

            location /biu/ {
                    proxy_pass http://example.com:port/biu/;
            }
    }
}
```
六、Nginx关闭/开启命令<br>
>>从容关闭 kill -QUIT PID<br>
>>启动 sbin/ -> ./nginx <br>
>>或使用 sudo /usr/local/nginx/sbin/nginx 启动
