+++
title = "SRM576 DIV2 -250points"
date = 2013-05-15T23:55:00Z
updated = 2013-05-15T23:55:09Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">＜問題＞<br />①蛇口の数と、蛇口ごとにそこから出る水滴の数が与えられる。<br />例）３，４，１，１，５，６<br />②スポンジの長さＬが与えられる。<br />例）Ｌ＝３<br />③それぞれのスポンジについて、上から降順に配列が与えられる。<br />　配列の値は、スポンジの左側の位置。<br />例）３，１，０<br />④蛇口の水滴は、一番最初に当たった水滴に吸収される。<br />⑤このとき、各スポンジが吸収した水滴の値を配列で返す。<br /><br />＜ポイント＞<br />・上にあるスポンジ、すなわちスポンジの配列の右側から<br />　その位置に相当する水滴の数を足してあげて、<br />　スポンジごとの合計を配列に格納する。<br />　「いったん吸収された水滴は０にクリアにする」ことで重複がなくなるのがポイント。<br /><br /><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;"> </span>vector&lt;int&gt; determineHumidity(vector&lt;int&gt; intensity, int L, vector&lt;int&gt; leftEnd) {</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">  </span>vector &lt;int&gt; ans;</span><br /><span style="font-size: x-small;"><br /></span><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,leftEnd.size()){</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">   </span>int tmp=0;</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">   </span>FOR(j,0,L){</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">    </span>tmp+=intensity[leftEnd[i]+j];</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">    </span>intensity[leftEnd[i]+j]=0;</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">   </span>}</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">   </span>ans.push_back(tmp);</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">  </span>}</span><br /><span style="font-size: x-small;"><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;</span><br /></div>
