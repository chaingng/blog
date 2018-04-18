+++
title = "android studioのプロキシ設定"
date = 2014-10-08T20:44:00Z
updated = 2014-10-08T20:45:01Z
tags = ["technology"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />android studioのプロキシ設定のメモ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">HTTP Proxy</h3><div><br /></div>File&gt;Setting&gt;HTTP Proxyから<br />Manual Proxy Settingを選んで設定。<br /><br />設定後、「Check Connection」ボタンで正しく設定されているか確認できる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">Gradle</h3><br />Gradleを使用するとき、proxy設定が必要な場合は以下のエラーが出る。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">Failed to refresh Gradle project 'dummy Application'<br />Could not GET 'http://repo1.maven.org/maven2/com/android/tools/build/gradle/'.<br />Received status code 407 from server:<br />Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied. )<br />Enable Gradle 'offline mode' and sync project</div><br />この際、File&gt;Setting&gt;Gradleから<br />Global Gradle Settingsのオプションにて以下の設定が必要。<br />（dummyHost, dummyPort, dummyUser, dummyPasswordにそれぞれ必要な設定を入れる）<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">-Dhttp.proxyHost=dummyHost -Dhttp.proxyPort=dummyPort -Dhttp.proxyUser=dummyUser -Dhttp.proxyPassword=dummyPassword</div></div>
