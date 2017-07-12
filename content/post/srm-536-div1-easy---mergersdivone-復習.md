+++
title = "SRM 536 DIV1 Easy - MergersDivOne （復習○）"
date = 2013-08-18T10:30:00Z
updated = 2015-03-26T20:03:39Z
tags = ["考察"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11799&amp;rd=14728" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11799&amp;rd=14728</a><br /><br />複数の会社が与えられる。<br />そのうち任意の数を選択し、その価値の和／選択した数が合併した後の価値になる。<br />すべての会社を合併した時、最大となる価値を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />最初の数の順番は回答に関係しないので昇順にソート。<br />このとき、すべての点をプロットすると、２つずつ左から合併を繰り返した方がよいことがわかる。<br />（合併後の点が順に右に移動していく。仮に３つを選択した時はその中間になり間の値があまり意味を持たないため、２つずつがよいことがわかる）<br /><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class MergersDivOne {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double findMaximum(vector&lt;int&gt; revenues) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(revenues.begin(),revenues.end());<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double ans=revenues[0];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,revenues.size())ans=(ans+revenues[i])/2.0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
