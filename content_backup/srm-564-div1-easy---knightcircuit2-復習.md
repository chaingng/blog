+++
title = "SRM 564 DIV1 Easy - KnightCircuit2 （復習○）"
date = 2013-08-18T16:36:00Z
updated = 2015-05-24T11:00:44Z
tags = ["移動"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10968&amp;rd=15186" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10968&amp;rd=15186</a><br /><br />ボードの長さと高さが与えられる。<br />このとき、ナイトが動けるマスを返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />１辺の最大の長さは４５０００のため、Ｏ（１０＾８）となり全探索では求められない。<br />そこで法則を探すことにする。<br /><br />１）マスの１辺が１のとき<br />　動くことができないので、答えは１<br /><br />２）マスの１辺が２のとき<br />　もう一つの辺の長さによって答えが変わる。<br />　１マスのときは＋１、２マスの時は＋１、３マスのときは＋２、４マスのときは＋２<br />　これが繰り返される。<br /><br />３）マスが３*３のとき<br />　３＊３のときは真ん中だけいけないので８．<br /><br />４）それ以外<br />　全てのマスに行くことができるので全てのマスの数が答え。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class KnightCircuit2 {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int maxSize(int w, int h) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(w&gt;h)swap(w,h);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(w==1)return 1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(w==2)return (h+1)/2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(w==3 &amp;&amp; h==3)return 8;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return w*h;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
