+++
title = "SRM575 DIV2 -500points"
date = 2013-05-19T23:43:00Z
updated = 2013-07-06T21:38:21Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">＜問題＞<br />①ある正の整数が与えられる。<br />　例）１５<br />②整数は１かその数自身を除いた約数で除算ができる。<br />　例）１５－３＝１２<br />③ＪｏｈｎとＢｒｕｓの２人でゲームをし、除算ができなくなった方が負け。<br />　最初のターンはＪｏｈｎ。<br />④このとき、与えられた整数に対して勝つ方のプレイヤー名を返す。<br /><br />＜関数＞<br />memset(f,0,sizeof(f));<br />数字を０で初期化する関数。<br />これも使えますが、単純に宣言での初期化をしました。<br /><br />return f[n] ? "John" : "Brus";<br />f[n]が正の時は"John"、偽の時は"Brus"を返す。<br />これでもＯＫですが、if文でも。<br /><br />Challengeポイント<br />最初はjをj&lt;i/2としましたが、i/2は含めないといけなかったので<br />システムテストでfail。<br />安全にj&lt;iまで最後までまわした方がよいですね。<br /><br />＜考え方＞<br />特定の整数が与えられた際、勝ちか負けかが一意に決まる。<br />これを利用し１から初めて、<br />与えられた整数まで全ての数に対して勝ち負けの状態遷移を保存する。<br /><br />1,2,3～6ぐらいまでシミュレーションしてみると、<br />ある整数に対し、それ未満の割り切れる整数に対し<br />check[i-j]が0になれば勝ちなので1とする。それ以外は0のまま。<br /><br />＜コード＞<br />class TheNumberGameDivTwo {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string find(int n) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; check(n+1,0);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,n+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,2,i)if(i%j==0 &amp;&amp; check[i-j]==0)check[i]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(check[n]==1)return "John";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "Brus";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div>
