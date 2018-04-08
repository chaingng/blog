+++
title = "SRM 543 DIV1 Easy - EllysXors"
date = 2013-07-12T08:36:00Z
updated = 2015-05-17T13:30:37Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br />①整数ＬとＲが与えられる。<br />②このとき、ＬからＲまでの間全ての数をＸＯＲした後の値を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />Ｌ，Ｒは４＊１０＾９のため単純なシミュレーションでは解くことができない。<br />そのため、数学的解法、法則を見つける。<br /><br />法則を見つけるために１からずっとＸＯＲをしたときの値を並べてみると、<br />整数ｎを４で割ったときの余りによって以下になることがわかる。<br /><br />余り０　→　ｎ<br />余り１　→　１<br />余り２　→　ｎ　ＸＯＲ　１<br />余り３　→　０<br /><br />最後に１からスタートしているわけではなくてＬからスタートしなければならない。<br /><br />これは１からＲまで求めた答えから、１からＬ－１まで求めた答えを引く、つまりＸＯＲしてあげればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class EllysXors {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>long long f(long long n){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long check=n%4;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(check==0)return n;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(check==1)return 1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(check==2)return n^1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return 0;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>long long getXor(long long L, long long R) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return f(R)^f(L-1);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
