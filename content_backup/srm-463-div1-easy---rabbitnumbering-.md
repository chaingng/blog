+++
title = "SRM 463 DIV1 Easy - RabbitNumbering ○"
date = 2015-05-03T21:44:00Z
updated = 2015-08-08T07:15:31Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10697&amp;rd=14148" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10697&amp;rd=14148</a><br /><br />複数のうさぎが存在し、すべてのうさぎに番号をつけたい。<br />それぞれのうさぎは違う番号をつける。<br />各うさぎはつけて欲しい番号の最大数を持っており、１～その最大数までの<br />いずれかの数字をつける。<br /><br />このとき、うさぎの番号の付け方の総数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />普通に考えると計算量がオーバーしてしまう。<br />各うさぎのmaxnumberでソートし、小さい数から順番に見ていくことで<br />総数を簡単に数えることができる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class RabbitNumbering {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int theCount(vector&lt;int&gt; maxNumber) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int MOD=1000000007;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=maxNumber.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(maxNumber));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret=(ret*1LL*(maxNumber[i]-i))%MOD;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
