+++
title = "SRM578 DIV2 -250points"
date = 2013-05-13T22:10:00Z
updated = 2013-05-13T22:26:44Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">問題<br /><br />①鹿の数と、落ちている角の数が与えられる。<br />例）　鹿３匹、角２本<br /><br />②鹿は角が０～２本である。<br /><br />③このとき、角が２本ある鹿の数の最小値と最大値を求める。<br /><br />関数<br />vector&lt;int &gt;が返り値なのでこれが使えれば。<br />vector &lt;int&gt; a;<br />a.push_back(b);でbを挿入できます。<br /><br />考え方<br /><br />最小値<br />鹿１匹につき角が１本落ちている場合なので<br />「鹿の数ー角の数」。<br /><br />最大値<br />鹿１匹につき角が２本落ちている場合。<br />「鹿の数ー角の数／２」だが、<br />整数の計算なので奇数の場合と偶数の場合で結果が異なってしまうので整理。<br /><br />鹿３匹、角１本　～　３－（１＋１）／２＝２匹<br />鹿３匹、角２本　～　３－（２＋１）／２＝２匹<br />鹿３匹、角３本　～　３－（３＋１）／２＝１匹<br />となるので、<br />「鹿の数ー（角の数＋１）／２」が最大値。<br /><br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>vector&lt;int&gt; getminmax(int N, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; ans(2);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans.push_back(N-K);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans.push_back(N-(K+1)/2);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><br /></div>
