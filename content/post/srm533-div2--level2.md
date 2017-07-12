+++
title = "SRM533 DIV2 -Level2"
date = 2013-07-10T09:33:00Z
updated = 2015-04-03T11:21:17Z
tags = ["全探索"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">問題<br />①数字の配列が与えられ、それぞれの配列は重さを表わす。<br />②最初と最後以外の要素を任意で選ぶことができ、選んだ要素の前と後の重さの積がスコアにプラスされる。<br />　選ばれた要素は消去される。<br />③このとき、最大となるスコアを求める。<br /><br />解き方<br />配列の数は最大で１０のため<br />全ての場合の数を求めてもＯ（８！＝４０３２０）となるので全探索可能。<br /><br />コード<br /><br />class CasketOfStarEasy {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int f(vector&lt;int&gt; &amp;w){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(w.size()==2)return 0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int score=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,w.size()-1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vector&lt;int&gt; tmp;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,w.size())if(j!=i)tmp.push_back(w[j]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>score=max(score,w[i-1]*w[i+1]+f(tmp));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return score;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int maxEnergy(vector&lt;int&gt; weight) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return f(weight);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br />};<br /><div><br /></div></div>
