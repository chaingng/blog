+++
title = "SRM569 DIV2 -Level2"
date = 2013-06-14T09:11:00Z
updated = 2015-04-03T11:59:14Z
tags = ["考察"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">＜問題＞<br />①０と１で構成される2次元配列が与えられる。<br />②各ビット列の任意の２つに対し、それぞれＯＲかＸＯＲかＡＮＤ演算をするデバイスがビット列分存在する。<br />③各ビット列に対しどの操作をするか決まっているが、それがどれかはわかっていない。<br />④このとき、各デバイスがどの操作をするか確かめることができれば”ＹＥＳ”、できなければ”ＮＯ”を返す。<br /><br />＜解き方＞<br />各ビット列に対し、特定の数字が含まれていればデバイスの操作を確かめることができる。<br />ＯＲとＡＮＤの場合<br />０，１→ＯＲだと１、ＡＮＤだと０<br />ＯＲとＸＯＲの場合<br />１，１→ＯＲだと１、ＸＯＲだと０<br />ＡＮＤとＸＯＲの場合<br />０，１→ＡＮＤだと０、ＸＯＲだと１<br />１，１→ＡＮＤだと１、ＸＯＲだと０<br /><br />この３つを判定するには、１が２つ、０が１つ最低あればよいことになる。<br />各ビット列に対し１が２つ、０が１つ以上あるか判定し、<br />なければＮＯ，あればＹＥＳを返す。<br /><br />＜コード＞<br />class TheDeviceDiv2 {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string identify(vector&lt;string&gt; plates) {<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(j,0,(int)plates[0].size()){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int one=0,zero=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,(int)plates.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(plates[i][j]=='1')one++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>else zero++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(!(one&gt;=2 &amp;&amp; zero&gt;=1))return "NO";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "YES";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div>
