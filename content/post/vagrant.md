---
title: "vagrantの使い方"
date: 2017-01-08T10:00:00+09:00
tags: [ "technology"]
---

### インストール
公式の[Download](https://www.vagrantup.com/downloads.html)ページから、対応するOSのパッケージをダウンロードしてインストール

### VagrantFileの作成
vagrant initを実行すると、VagrantFileがない場合は作成される
```
vagrant init
```

box nameが指定されたら config.vm.boxがセットされる
```
vagrant init [box name]
```

Box urlが指定されたらvm.box_urlがセットされる
```
vagrant init [box url]
```

### boxの追加

[ここ](http://www.vagrantbox.es/)から欲しいBOXを検索し、以下のコマンドで追加
```
vagrant box add ubuntu1604 https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box
```

### 現在取得済みのboxを確認
```
$ vagrant box list
centos7    (virtualbox, 0)
ubuntu1604 (virtualbox, 0)
```

### 起動
VagrantFileの内容が実行されて仮想マシンが起動
```
vagrant up
```

### ssh接続
```
vagrant ssh
```
Ctrl + Dで終了

### ssh接続情報の確認
```
$ vagrant ssh-config
Host default
  HostName 127.0.0.1
  User ubuntu
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /Users/hondatakatomo/github/studies/playbooks/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

この情報を利用して、vagrant sshではなく通常のsshコマンドでも接続できる
```
ssh -i /Users/hondatakatomo/github/studies/playbooks/.vagrant/machines/default/virtualbox/private_key ubuntu@127.0.0.1 -p 2222
```

### VagrantFileの変更を反映
```
vagrant provision
```

すでに仮想マシンが起動中で反映させたいとき
```
vagrant reload --provision
```

### 仮想マシンの状態を確認
```
$ vagrant status
Current machine states:

vagrant1                  running (virtualbox)
vagrant2                  running (virtualbox)
vagrant3                  running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

### 仮想マシンを一時停止
```
vagrant suspend
```

### 一時停止からの再開
```
vagrant resume
```

### 仮想マシンの停止
```
vagrant halt
```

### 仮想マシンの削除
boxは残る
```
vagrant destroy
```

### ポートフォワーディング
- ホストから8080でアクセスすると、ゲスト（仮想マシン）の80番ポートに接続
- ホストから8443でアクセスすると、ゲスト（仮想マシン）の443番ポートに接続
```
Vagrant.configure("2") do |config|
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 443, host: 8443
```


### 複数の仮想マシンで同じssh keyを使いたいとき

- デフォルトでは仮想マシンごとにそれぞれ異なるssh keyが払い出される
- 以下の設定を追加することで、すべての仮想マシンで同じssh keyが設定される
```
Vagrant.configure("2") do |config|
    config.ssh.private_key_path = "custom_key_file"
    config.ssh.forward_agent = true
End
```

### スクリプトを利用して設定を行う
```
Vagrant.configure("2") do |config|
  config.vm.provision "shell", path: "script.sh"
end
```

