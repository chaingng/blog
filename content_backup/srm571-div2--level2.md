+++
title = "SRM571 DIV2 -Level2"
date = 2013-06-11T22:47:00Z
updated = 2013-06-11T22:47:16Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">&lt;問題&gt;<br />①数字Ｎが与えられる。<br />②１からＮまでの数字が付けられたｍｐ３ファイル、"1.mp3","2.mp3"..."n.mp3"が作られる。<br />③このとき、ファイル名を辞書順に並べたときの配列を返す。<br />　ただし、Ｎが５０を超える場合は最初の５０個を返す。<br /><br />＜解き方＞<br />辞書順、ということに気づいて文字列のソートができればＯＫ．<br />要素が５０個を超える場合は、最初の５０個のみ表示するということに注意。<br /><br />&lt;コード&gt;<br />class FoxAndMp3Easy {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: vector&lt;string&gt; playList(int n) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector &lt;string&gt; vx,ans;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=1;i&lt;=n;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>stringstream ss;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ss &lt;&lt; i &lt;&lt; ".mp3";<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>string tmp;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ss &gt;&gt;tmp;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vx.push_back(tmp);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(vx.begin(),vx.end());<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;min(50,n);i++)ans.push_back(vx[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br />};</div>
