+++
title = "SRM 395 DIV1 Easy - StreetWalking ○"
date = 2015-07-24T16:14:00Z
updated = 2015-07-24T16:15:33Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8464&amp;rd=11129" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8464&amp;rd=11129</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />以下の３通りのうち、最小のものが答えになる。<br />１．すべて直線で移動（直線移動のコストが小さい時に有効）<br />２．できるだけ斜めに移動して、残りを直線で移動（斜め移動のコストが小さいときに有効）<br />３．最短距離で移動（どちらの移動のコストも同程度のときに有効）<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class StreetWalking {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long minTime(int X, int Y, int walkTime, int sneakTime) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=(X+Y)*(long long)walkTime;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long wnum=max(X,Y)-min(X,Y);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long snum=min(X,Y);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ret=min(ret,snum*sneakTime+wnum*walkTime);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>snum+=(wnum/2)*2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>wnum%=2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ret=min(ret,snum*sneakTime+wnum*walkTime);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
