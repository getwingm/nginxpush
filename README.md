nginxpush
=========

修改nginx-push-stream-module-0.3.5的离线消息发送模块，使其每次请求只发一条离线消息。


编译命令如下：

cd nginx-1.4.7

如果安装了pcre库，则如下
./configure --add-module=../nginx-push-stream-module-0.3.5 --add-module=../lua-nginx-module-0.9.3

有报pcre库连接错误，则
./configure --add-module=../nginx-push-stream-module-0.3.5 --add-module=../lua-nginx-module-0.9.3 --with-pcre=../pcre-8.35

还有错，再试
./configure --add-module=../nginx-push-stream-module-0.3.5 --add-module=../lua-nginx-module-0.9.3 --with-pcre=../pcre-8.35 --with-pcre-jit

make install

cp ../nginx-push-stream-module-0.3.5/misc/nginx-sjk.conf /usr/local/nginx/

根据环境需要修改nginx-sjk.conf的部份参数，例如CPU亲缘性。

运行程序
cd /usr/local/nginx

sbin/nginx -c nginx-sjk.conf

检查nginx是否已经运行起来。
ps -ef|grep nginx
