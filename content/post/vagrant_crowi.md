---
title: "crowi用のvagrantを公開しました"
date: 2017-02-12T10:00:00+09:00
tags: ["library"]
---

情報集約用にwikiをいろいろ試していて、crowiを試してみることにした。  
いくつかセットアップが必要だったので、vagrantでワンタッチで立ち上げられるようにした。

https://github.com/chaingng/vagrant_crowi

## セットアップ

Ubuntu16.04用のboxをvagrantに追加して、`vagrant up`するだけ。

```
git clone git@github.com:chaingng/vagrant_crowi.git
vagrant box add ubuntu1604 https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box
vagrant up
```

これで[http://localhost:4000](http://localhost:4000)からアクセスできるようになる。

## 中身

VagrantFileでシェルを読み込んで、
シェルに以下必要なパッケージをセットアップ。  
一応mongodbはデーモンで立ち上げるようにした。

```bash
$cat script.sh
#!/bin/sh

# setup ndenv
git clone https://github.com/riywo/ndenv ~/.ndenv
echo 'export PATH="$HOME/.ndenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(ndenv init -)"' >> ~/.bash_profile

git clone https://github.com/riywo/node-build.git ~/.ndenv/plugins/node-build
. ~/.bash_profile
ndenv install v6.11.1
ndenv global v6.11.1
ndenv rehash

# setup mongodb
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
sudo apt-get update
sudo apt-get install -y mongodb-org

sudo cat << EOS | sudo tee /etc/systemd/system/mongod.service
[Unit]
Description=MongoDB Database Service
Wants=network.target
After=network.target

[Service]
ExecStart=/usr/bin/mongod --config /etc/mongod.conf
ExecReload=/bin/kill -HUP $MAINPID
Restart=always
User=mongodb
Group=mongodb
StandardOutput=syslog
StandardError=syslog

[Install]
WantedBy=multi-user.target
EOS

sudo service mongod start
sudo systemctl enable mongod

# setup crowi
git clone https://github.com/crowi/crowi.git
cd crowi
npm i -D node-sass
npm install
npm run build

echo 'PASSWORD_SEED=20170222crowitest' >> ~/.bash_profile
echo 'MONGO_URI=mongodb://localhost/crowi' >> ~/.bash_profile
. ~/.bash_profile

node app.js

```
