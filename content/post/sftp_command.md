---
title: "sftpコマンドまとめ"
date: 2017-11-12T10:00:00+09:00
tags: [ "library"]
---

## 基本操作

### get

#### ファイルをダウンロード

```
sftp> get example.log
Fetching /example.log to example.log
/example.log                                                                                                                        100%   69     1.8KB/s   00:00
```

#### ディレクトリを指定してのファイルダウンロード

```
> get hoge/example.log
Fetching /backup/hoge/example.log to example.log
/backup/hoge/example.log                                                                                                            100%   69     3.5KB/s   00:00
```

#### ディレクトリごとまとめてダウンロード
`-r`オプションをつける
```
> get -r hoge
Fetching /backup/hoge/ to hoge
Retrieving /backup/hoge
/backup/hoge/myicon.jpg                                                                                                             100%  177KB   2.2MB/s   00:00
/backup/hoge/example.log                                                                                                            100%   69     3.7KB/s   00:00
```


### put
#### ファイルをアップロード

```
> put tmpssh.log
Uploading tmpssh.log to /backup/tmpssh.log
tmpssh.log                                                                                                                          100%    0     0.0KB/s   00:00
```

#### ローカルディレクトリ内のファイルをアップロード

```
> put Documents/myicon.jpg
Uploading Documents/myicon.jpg to /backup/myicon.jpg
Documents/myicon.jpg                                                                                                                100%  177KB 507.5KB/s   00:00
```


##### アップロード先ディレクトリを指定してのファイルアップロード

```
> put example.log hoge/
Uploading example.log to /backup/hoge/example.log
example.log                                                                                                                         100%   69     7.2KB/s   00:00
```

### rm
ファイルを削除
```
> rm test.py
```

### rmdir

ディレクトリを削除

```
> rmdir hoge
```

ディレクトリ内にファイルがあると削除ができない

### quit / bye / exit
接続を閉じる
```
> quit
```

```
> bye
```

```
> exit
```

## リモートディレクトリ関連

### ls 
リモートディレクトリのファイル一覧を表示
```
sftp> ls
backup       example.log  test.py      upload
```

### pwd
リモートディレクトリのフルパスを表示
```
sftp> pwd
Remote working directory: /
```

### mkdir
リモートにディレクトリを作成
```
> lmkdir hoge
```

### cd
リモートディレクトリを移動
```
> cd hoge
```

## ローカルディレクトリ関連

### lls

ローカルディレクトリのファイル一覧を表示
```
> lls
hogefuga    Desktop                    emacs.d                    sample.csv
```

### lpwd
ローカルディレクトリのフルパスを表示
```
> lpwd
Local working directory: /Users/hondatakatomo
```

### lmkdir
ローカルにディレクトリを作成
```
> lmkdir hogefuga
```

### lcd
ローカルディレクトリを移動
```
> lcd Documents
```

## その他

### rename
ファイルをリネーム
```
> rename example.log fuga.log
```

### df
ディスク使用状況を表示
```
> df
        Size         Used        Avail       (root)    %Capacity
    30830568      5843356     24886964     24987212          18%
```

### help
ヘルプを表示
```
> help
Available commands:
bye                                Quit sftp
cd path                            Change remote directory to 'path'
chgrp grp path                     Change group of file 'path' to 'grp'
chmod mode path                    Change permissions of file 'path' to 'mode'
chown own path                     Change owner of file 'path' to 'own'
df [-hi] [path]                    Display statistics for current directory or
                                   filesystem containing 'path'
exit                               Quit sftp
get [-afPpRr] remote [local]       Download file
reget [-fPpRr] remote [local]      Resume download file
reput [-fPpRr] [local] remote      Resume upload file
help                               Display this help text
lcd path                           Change local directory to 'path'
lls [ls-options [path]]            Display local directory listing
lmkdir path                        Create local directory
ln [-s] oldpath newpath            Link remote file (-s for symlink)
lpwd                               Print local working directory
ls [-1afhlnrSt] [path]             Display remote directory listing
lumask umask                       Set local umask to 'umask'
mkdir path                         Create remote directory
progress                           Toggle display of progress meter
put [-afPpRr] local [remote]       Upload file
pwd                                Display remote working directory
quit                               Quit sftp
rename oldpath newpath             Rename remote file
rm path                            Delete remote file
rmdir path                         Remove remote directory
symlink oldpath newpath            Symlink remote file
version                            Show SFTP version
!command                           Execute 'command' in local shell
!                                  Escape to local shell
?                                  Synonym for help
```
