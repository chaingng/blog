+++
title = "SRM 649 DIV1 Easy - Decipherability"
date = 2015-04-12T21:35:00Z
updated = 2015-04-12T21:36:34Z
tags = ["文字列"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13656&amp;rd=16313" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13656&amp;rd=16313</a><br /><br />・a～ｚから成る文字列が与えられる。<br />・この文字列から、任意のK個の文字を取り除いたとき、それがどの箇所か<br />　特定できればCertain、特定できなければUncertainを返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />どのような文字列が削除されると特定できないかの法則を探す。<br /><br />まず、すべての文字列が削除された場合は特定できる。<br /><br />次に、文字列の対称性を考えた場合に、a***aの文字列があった場合<br />Kが４以上だとaだけを残すことができ、どちらを消したか特定できない。<br /><br />このような同じ文字ではさまれたサブ文字列すべてに対して判定を行い<br />ひとつでもあてはまれば特定できない文字列となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class Decipherability {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string check(string s, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=s.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(K==n)return "Certain";<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,i+1,n)if(s[i]==s[j]){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(j-i&lt;=K)return "Uncertain";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "Certain";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
