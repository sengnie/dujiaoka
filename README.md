# dujiaoka
使用docker运行独角数卡和Epusdt支付

导入数据库

进入epusdt目录
执行 初始化数据库


docker exec -i db2 sh -c 'exec mysql -uepusdt -pepusdt epusdt' < epusdt.sql

# Epusdt
查询Telegram ID
https://t.me/getmyid_bot

创建Telegram_bot
https://t.me/BotFather
