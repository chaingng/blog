+++
title = "SRM 521 DIV1 Easy - MissingParentheses （復習○）"
date = 2013-10-13T08:27:00Z
updated = 2015-03-26T20:38:04Z
tags = ["状態遷移"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10943&amp;rd=14546" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10943&amp;rd=14546</a><br /><br />カッコの並びが与えられる。<br />カッコがきちんと閉じた形になるために、追加で必要なカッコの数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />左カッコが出てきたら＋１、右カッコが出てきたらー１としてカッコの閉じ具合を走査する。<br />０から始め、マイナスになるときは必ず左にカッコが必要なので答えを＋１して数を０に戻す。<br />そうでない場合はそのまま走査し、最後に残った数を答えに足せばよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;"><br />class MissingParentheses {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int countCorrections(string par) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int left=0,ans=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,par.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(par[i]=='(')left++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else if(left&gt;0)left--;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else ans++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans+left;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
