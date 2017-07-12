+++
title = "SRM536 DIV2 -Level2"
date = 2013-07-03T22:54:00Z
updated = 2015-04-03T11:20:04Z
tags = ["考察"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">&lt;問題&gt;<br />①１～９個の面を持つサイコロがあり、決められた数だけ存在する。<br />②どのサイコロを与えられたかはわからない。同じ面を持つサイコロは複数存在しうる。<br />③そのサイコロの集合を複数回投げて、出た表の面の集合が与えられる。<br />④このとき、可能性のあるサイコロの集合のうち最も面の数が少なくなるような和を返す。<br /><br />＜解き方＞<br />全ての面の出方についてそれぞれソートする。<br />ソートした後、それぞれの１番目の要素の中で最大のものが<br />１番目の要素の最小の答えとなる。<br />２番目以降も同様。<br />最後に求めた全ての要素の和を返す。<br /><br />＜コード＞<br />class RollingDiceDivTwo {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int minimumFaces(vector&lt;string&gt; rolls) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=rolls.size(),ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector &lt;int&gt; ans(rolls[0].size(),0);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)sort(rolls[i].begin(),rolls[i].end());<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,rolls[0].size()){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(ans[j]&lt;rolls[i][j]-'0')ans[j]=rolls[i][j]-'0';<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,rolls[0].size())ret+=ans[i];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div>
