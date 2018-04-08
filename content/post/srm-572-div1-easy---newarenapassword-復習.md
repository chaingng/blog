+++
title = "SRM 572 DIV1 Easy - NewArenaPassword （復習○）"
date = 2013-08-20T08:09:00Z
updated = 2015-04-03T11:27:47Z
tags = ["ループ"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12386&amp;rd=15492" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12386&amp;rd=15492</a><br /><br />古いパスワードから新しいパスワードを作りたいが、できるだけ変更したくない。<br />また、パスワードの最初のＫ文字と最後のＫ文字は一致していないといけない。<br /><br />古いパスワードが与えられた時、最小の変更文字数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />正確にシミュレーションしてあげれば解ける問題。<br /><br />i文字目について、Ｎ-K文字を足した場所とリンクしていることがわかると、<br />最初からN-Kずつ足していった値に対して、最小のリンク関数を求めてあげればよい。<br />また、最初からＫもしくはＮ－Ｋまでの操作でよいことがわかる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class NewArenaPassword {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int minChange(string oldPassword, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int cost=0,n=oldPassword.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;n&amp;&amp;i&lt;n-K;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int count[26]={},num=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=i;j&lt;n;j+=n-K){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>count[oldPassword[j]-'a']++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>num++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cost+=num-*max_element(count,count+26);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return cost;<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
