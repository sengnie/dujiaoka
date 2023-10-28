# dujiaoka
使用docker运行独角数卡和Epusdt支付

导入数据库

进入epusdt目录
执行 初始化数据库


docker exec -i db2 sh -c 'exec mysql -uepusdt -pepusdt epusdt' < epusdt.sql
