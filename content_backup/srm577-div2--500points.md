+++
title = "SRM577 DIV2 -500points"
date = 2013-05-15T19:53:00Z
updated = 2013-05-15T19:53:48Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">＜問題＞<br />①Ｎ個の数字が与えられる。<br />例）42 911 666 17 13 1 1155 1094 815 5 1000 540<br />②一番最初の数字が自分の値。<br />③大きい数字の順から２０個取り出され、Ｒ個の部屋にそれぞれランダムに割り当てられる。<br />④１個の部屋には２０人まで収容できる。<br />⑤部屋の数はＮ／２０、またＮが２０の倍数ならＮ／２０＋１。<br />⑤このとき、一番最大の数字と自分の数字が同じ部屋に割り当てられる確率を返す。<br /><br />＜関数＞<br />数字がintではなくstringにて、空白区切りで与えられ、しかも複数のstringで与えられるのでvector&lt;int&gt;に戻す処理が必要。<br /><br />FORE(i,0,ratings.size())strg+=ratings[i];<br />にて複数のstring配列を一つにし、<br /><br />stringstream out(strg);<br />にて読み込み、<br /><br />while(out &gt;&gt; tmp)vx.push_back(tmp);<br />にてvector&lt;int&gt;に挿入してます。<br /><br />＜考え方＞<br />以下の場合に分けられる。<br />①数字が２０個以内であれば、必ず同じ部屋になる。　→１<br />②自分の数字の順位が降順で部屋の数以内であれば、同じ部屋にならない。→０<br />③それ以外の場合、１／Ｒ。<br />　また、Ｎの数字によってＲの場合分けをする。<br />　Ｎ＝１９　→　（１９＋１９）／２０＝１<br />　Ｎ＝２０　→　（２０＋１９）／２０＝１<br />　Ｎ＝２１　→　（２１＋１９）／２０＝２<br />　となるので、Ｒ＝（Ｎ＋１９）／２０となり、<br />　確率は１／（（Ｎ＋１９）／２０）。<br /><br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>double getProbability(vector&lt;string&gt; ratings) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n,tmp,rank=1,r;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector &lt;int&gt; vx;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string strg="";<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,ratings.size())strg+=ratings[i];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>stringstream out(strg);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(out &gt;&gt; tmp)vx.push_back(tmp);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>n=vx.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>r=(n+19)/20;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(vx[i]&gt;vx[0])rank++;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(n&lt;=20)return 1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(r&gt;=rank)return 0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return (double)(1.0/r);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><br /></div>