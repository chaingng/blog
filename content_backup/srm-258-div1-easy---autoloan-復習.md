+++
title = "SRM 258 DIV1 Easy - AutoLoan (復習○)"
date = 2014-02-01T09:18:00Z
updated = 2015-04-03T11:04:12Z
tags = ["二分探索"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=3970&amp;rd=7993" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=3970&amp;rd=7993</a><br /><br />・車をローンで購入する。<br />・車の費用はあらかじめわかっており、ディーラーは月額の固定支払額と払い終わるまでの月数を教えてくれる。<br />・ただしその場合のローン率は教えてくれない。<br />・支払いは毎月残額にたいしてローン率／１２が足された後、毎月の固定支払額が引かれる計算となる。<br />・このとき、ローン率がいくらになるか求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />２分探索で簡単に解くことができる。<br /><br />相対誤差で計算してもよいが、100回まわせば誤差1e-9に対して精度は10^2/10^100なので十分。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class AutoLoan {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double interestRate(double price, double monthlyPayment, int loanTerm) {<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double low=0.0,high=100.0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,100){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>double mid=(high+low)/2.0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>double cost=price;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,loanTerm){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>cost+=cost*mid/12.0;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>cost-=monthlyPayment;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(cost&lt;=0)low=mid;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else high=mid;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return low*100.0;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
