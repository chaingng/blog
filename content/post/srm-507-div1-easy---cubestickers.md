+++
title = "SRM 507 DIV1 Easy - CubeStickers"
date = 2015-05-09T15:50:00Z
updated = 2015-05-09T15:50:36Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11315&amp;rd=14436" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11315&amp;rd=14436</a><br /><br />６面体を与えられた色を使って塗りたい。<br />ただし、隣り合う面は違う色で塗らなくてはいけない。<br /><br />使える色の集合が与えられたとき、６面体を塗ることができれば”Yes”、塗れなければ<br />”No”を返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />各色について、２色までであれば反対側の面で使うことができる。<br />よって各色についてその色の数もしくは２のうちの最小のものを足していき<br />最後にその数の和が６以上であれば６面体を塗ることができる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class CubeStickers {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string isPossible(vector&lt;string&gt; sticker) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=sticker.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>map&lt;string,int&gt; m;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)m[sticker[i]]++;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int sum=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(map&lt;string,int&gt;::iterator it=m.begin();it!=m.end();it++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>sum+=min(2,it-&gt;second);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return sum&gt;=6 ? "YES" : "NO";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
