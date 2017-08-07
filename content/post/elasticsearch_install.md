---
title: "ElasticSearchの導入"
date: 2017-08-07T00:00:00+09:00
---

## 動作環境

- Ubuntu14.04

## インストール

Java8が必要
```
apt-get install -y openjdk-8-jdk
```

その後[公式](https://www.elastic.co/guide/en/elasticsearch/reference/current/deb.html)にそってelasticsearchをインストール
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install -y apt-transport-https
echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-5.x.list
sudo apt-get update
sudo apt-get install -y elasticsearch
```

## 自動起動設定

公式通り

```
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
sudo systemctl start elasticsearch.service
```

## プラグインのインストール

[Core ElasticSearch Plugins](https://www.elastic.co/guide/en/elasticsearch/plugins/current/installation.html)は
以下のようにインストール可能

```
sudo bin/elasticsearch-plugin install [plugin_name]
```


ただしbinは`/usr/share/elasticsearch/bin`にあるので、  
実際には以下のようにインストールする


```
sudo /usr/share/elasticsearch/bin/elasticsearch-plugin install analysis-kuromoji
```

## 起動確認

`curl http://localhost:9200`でレスポンスが返ってくればOK

```
# curl http://localhost:9200
{
  "name" : "954WKXE",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "tLyD95oxTaSDbs4ZG5T0VQ",
  "version" : {
    "number" : "5.5.1",
    "build_hash" : "19c13d0",
    "build_date" : "2017-07-18T20:44:24.823Z",
    "build_snapshot" : false,
    "lucene_version" : "6.6.0"
  },
  "tagline" : "You Know, for Search"
}
```

## 動かないとき

```
# curl http://localhost:9200
curl: (7) Failed to connect to localhost port 9200: 接続を拒否されました
```

service statusを調べる

```
# service elasticsearch status
● elasticsearch.service - Elasticsearch
  Loaded: loaded (/usr/lib/systemd/system/elasticsearch.service; disabled; vendor preset: enabled)
  Active: failed (Result: exit-code) since 金 2017-08-04 15:19:12 JST; 37s ago
  Docs: http://www.elastic.co
  Process: 3961 ExecStart=/usr/share/elasticsearch/bin/elasticsearch -p ${PID_DIR}/elasticsearch.pid --quiet -Edefault.path.logs=${LOG_DIR} -Edefault.path.data=${DATA_DIR} -Edefault.path.conf=${CONF_DIR}
  Process: 3956 ExecStartPre=/usr/share/elasticsearch/bin/elasticsearch-systemd-pre-exec (code=exited, status=0/SUCCESS)
 Main PID: 3961 (code=exited, status=1/FAILURE)

 8月 04 15:19:11 xxx systemd[1]: Starting Elasticsearch...
 8月 04 15:19:11 xxx systemd[1]: Started Elasticsearch.
 8月 04 15:19:12 xxx elasticsearch[3961]: OpenJDK 64-Bit Server VM warning: INFO: os::commit_memory(0x000000008a660000, 1973026816, 0) failed; error='Cannot allocate memory' (errno=12)
 8月 04 15:19:12 xxx elasticsearch[3961]: #
 8月 04 15:19:12 xxx elasticsearch[3961]: # There is insufficient memory for the Java Runtime Environment to continue.
 8月 04 15:19:12 xxx elasticsearch[3961]: # Native memory allocation (mmap) failed to map 1973026816 bytes for committing reserved memory.
 8月 04 15:19:12 xxx systemd[1]: elasticsearch.service: Main process exited, code=exited, status=1/FAILURE
 8月 04 15:19:12 xxx systemd[1]: elasticsearch.service: Unit entered failed state.
 8月 04 15:19:12 xxx systemd[1]: elasticsearch.service: Failed with result 'exit-code'.
```

公式に[Issue](https://github.com/elastic/elasticsearch/issues/15315)があり、メモリが足りない場合がある

よって`/etc/elasticsearch/jvm.options`を以下のように変更
```
# cat /etc/elasticsearch/jvm.options

# Xms represents the initial size of total heap space
# Xmx represents the maximum size of total heap space

#-Xms2g
#-Xmx2g
-Xms512m
-Xmx1g
```
メモリ不足であればこれで動くようになる

```
# service elasticsearch status
● elasticsearch.service - Elasticsearch
  Loaded: loaded (/usr/lib/systemd/system/elasticsearch.service; disabled; vendor preset: enabled)
  Active: active (running) since 金 2017-08-04 15:25:37 JST; 3s ago
  Docs: http://www.elastic.co
  Process: 4200 ExecStartPre=/usr/share/elasticsearch/bin/elasticsearch-systemd-pre-exec (code=exited, status=0/SUCCESS)
 Main PID: 4205 (java)
  CGroup: /system.slice/elasticsearch.service
  └─4205 /usr/bin/java -Xms512m -Xmx1g -XX:+UseConcMarkSweepGC -XX:CMSInitiatingOccupancyFraction=75 -XX:+UseCMSInitiatingOccupancyOnly -XX:+AlwaysPreTouch -server -Xss1m -Djava.awt.headless=true

 8月 04 15:25:37 xxx systemd[1]: Starting Elasticsearch...
 8月 04 15:25:37 xxx systemd[1]: Started Elasticsearch.
```


