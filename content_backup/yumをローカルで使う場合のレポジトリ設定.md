+++
title = "yumをローカルで使う場合のレポジトリ設定"
date = 2014-10-05T22:10:00Z
updated = 2014-10-05T22:14:51Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />最初にCDをマウントして、ローカルにデータをコピー。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">mkdir -p /mnt/cdrom<br />mount /dev/cdrom /mnt/cdrom<br />mkdir /opt/redhat<br />cp -rp /mnt/cdrom/* /opt/redhat/<br />umount /mnt/cdrom</div><br />次に、必要なrpmパッケージをインストール。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">rpm -ivh /opt/redhat/Packages/*.rpm</div><br />レポジトリを作成するディレクトリを指定。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">createrepo /opt/redhat/<br />yum clean all</div><br />最後に、適当な名前（ここではfile.repo）でレポジトリを作成すれば完了。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">vi /etc/yum.repos.d/file.repo</div><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">[rhel-redhat]<br />name = Red Hat Enterprise Linux $releasever - $basearch<br />baseurl=file:///opt/redhat<br />enabled=1<br />gpgcheck=0</div></div>
