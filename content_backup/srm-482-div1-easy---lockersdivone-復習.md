+++
title = "SRM 482 DIV1 Easy - LockersDivOne （復習○）"
date = 2013-10-18T08:44:00Z
updated = 2015-03-26T19:28:27Z
tags = ["全探索"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11110&amp;rd=14235" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11110&amp;rd=14235</a><br /><br />N個のドアがある。<br />最初は一つおきにドアを開けていく。<br />次は空いているドアはないとみなして、２つおきにドアをあけていく。<br />次は３つおき・・・としたときに、最後に空けるドアを求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />Ｎ＝１０＾６。<br />全探索だとN+N/2+N/(2*3)+N/(2*3*4)・・・<br />=N(1/2+1/6+1/24...)<br />最大ケースを試しても240msほどなのでこれで解けます。<br /><br />こちらを拝見させていただくと、法則を出しても解けるそうです。<br /><a href="http://be.nucl.ap.titech.ac.jp/~kawada/indigo/view/memo341.html">http://be.nucl.ap.titech.ac.jp/~kawada/indigo/view/memo341.html</a><br /><a href="http://d.hatena.ne.jp/kusano_prog/20100915/1284572746">http://d.hatena.ne.jp/kusano_prog/20100915/1284572746</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LockersDivOne {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int lastOpened(int N) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; a;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,N)a.push_back(i+1);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int d=2;;d++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(a.size()==1)return a[0];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vector&lt;int&gt; b;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,a.size())if(i%d!=0)b.push_back(a[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>a.swap(b);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
