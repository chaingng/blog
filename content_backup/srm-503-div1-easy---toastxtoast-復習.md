+++
title = "SRM 503 DIV1 Easy - ToastXToast (復習×○)"
date = 2013-10-19T08:26:00Z
updated = 2015-03-26T20:03:39Z
tags = ["考察"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11204&amp;rd=14432" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11204&amp;rd=14432</a><br /><br />様々な種類のトーストがあり、ある焼き時間になるとポッピングシャワーとなるが<br />その時間未満だと生焼け、その時間を過ぎると焼きすぎになる。<br />ポッピングシャワーとなる焼き時間はトーストの種類により異なる。<br /><br />生焼けのトーストとその焼き時間の集合、<br />焼きすぎのトーストとその焼き時間の集合が与えられた時、<br />最低何種類のトーストが存在したかを求める。<br />ただし、集合のうち生焼けと焼きすぎのペアは少なくとも１つは存在する。<br />そのようなペアが存在しなければー１を返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />生焼けと焼きすぎの境界が１つしかなければ、生焼けのものを１つ、焼きすぎのものを１つにまとめることができるので１種類。<br />一番生焼けのものが時間が一番早く、一番焦げすぎのものが一番遅ければ、<br />一番生焼けのもの＆一番焦げすぎのもの以外をまとめて１種類、<br />一番生焼け以外のもの＆一番焦げすぎのものをまとめて１種類なので<br />合計２種類。<br />一番生焼けのものが時間が一番早く、一番焦げすぎのものが一番遅くなければ<br />ペアが存在しないのでー１。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class ToastXToast {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int bake(vector&lt;int&gt; under, vector&lt;int&gt; over) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=under.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int m=over.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(under));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(over));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(under[0]&gt;over[0]||over[m-1]&lt;under[n-1])return -1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(under[n-1]&lt;over[0])return 1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return 2;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
