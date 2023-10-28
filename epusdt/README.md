# epusdt
docker-compsoe up -d  后执行下面  导入数据库

docker exec -i epusdt-db-1 sh -c 'exec mysql -uepusdt -pchangeyourpassword epusdt' < epusdt.sql


1.
修改MYSQL_ROOT_PASSWORD数据库root密码
修改MYSQL_PASSWORD数据库用户密码
用户名和数据库名不用修改
如服务器8000端口可能被占用,需修改epusdt映射端口,例如58000:8000

2.
修改第 3 行app_uri为上文为epusdt准备的独立域名
修改第 24 行mysql_passwd为上节MYSQL_PASSWORD的用户密码(注意:非 root 密码)
修改第 55 行api_auth_token=123qweASD创建一个密码用于dujiaoka 支付设置中使用
注意:因为本项目是独立部署到 docker compose 内,所以第 21,33 行已经修改为db,redis,不能使用 127.0.0.1.
修改第 48 行tg_bot_token=为上文创建的 Telegram Bot 的Token
修改第 52 行tg_manage=为上文创建的 Telegram Bot 的ID

3.
将下述命令中的-pCHANGE_YOUR_PASSWORD的密码改为上述设置的新密码,注意需要保留前缀-p,例如上文修改密码MYSQL_PASSWORD=aaabbbccc,此处则为-paaabbbccc.

如下图执行后无任何显示代表成功,否则将会报错.

docker exec -i epusdt-db-1 sh -c 'exec mysql -uepusdt -pCHANGE_YOUR_PASSWORD epusdt' < epusdt.sql


BotFather   机器人创建
类似ID:6247111111:Asdajkdaksdhkajshi6aUa6pXH4Rxc
获取Telegram ID:   https://t.me/getmyid_bot
得到你的user ID，类似：980888097

插一个更新和卸载的方法，docker搭建通用。
cd /root/data/docker_data/epusdt

docker-compose down 

cp -r /root/data/docker_data/epusdt /root/data/docker_data/epusdt.archive  # 万事先备份，以防万一

docker-compose pull

docker-compose up -d    # 请不要使用 docker-compose stop 来停止容器，因为这么做需要额外的时间等待容器停止；docker-compose up -d 直接升级容器时会自动停止并立刻重建新的容器，完全没有必要浪费那些时间。

docker image prune  # prune 命令用来删除不再使用的 docker 对象。删除所有未被 tag 标记和未被容器使用的镜像


提示：
WARNING! This will remove all dangling images.
Are you sure you want to continue? [y/N] 

卸载 epusdt

cd /root/data/docker_data/epusdt

docker-compose down

cd ..

rm -rf /root/data/docker_data/epusdt  # 完全删除映射到本地的数据
