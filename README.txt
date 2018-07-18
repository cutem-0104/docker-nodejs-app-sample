docker-composeを使ったnodejsのtodoアプリケーション
docker-compose up -dで起動
127.0.0.1:3000/todosにアクセスするとアプリケーションにアクセスできます。

mysqlにテーブルを作成
use sampleDb;

CREATE TABLE `todos` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(128) DEFAULT NULL,
  `image_url` varchar(256) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

ストレージの作成
127.0.0.1:9000にアクセスし、下記のbucketを作成する
docker-local-sample-bucket


bucketの可視化設定※うまく行かなかったけど念の為メモ
mcコンテナに接続
mc ls
vi /root/.mc/config.json
  localブロック内を編集
  url http://s3:9000
  accessKey minio
  secretKey minio123

mc ls local
mc policy public local/docker-local-sample-bucket
