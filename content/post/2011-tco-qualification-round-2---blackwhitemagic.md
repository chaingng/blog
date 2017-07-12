+++
title = "2011 TCO Qualification Round 2 - BlackWhiteMagic"
date = 2014-10-31T18:29:00Z
updated = 2015-03-26T19:22:27Z
tags = ["全探索"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11418&amp;rd=14530" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11418&amp;rd=14530</a><br /><br />・黒と白の石が並べられている配列が与えられる。<br />・その石をswapすることで、白白・・白黒黒・・黒としたい。<br />・ただし、swapできる距離１つごとに１回のswapしかできない。<br />・このとき、必要な最小の操作回数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・swapの距離によらず、各１回の操作で白と黒を入れ替えることができそう。<br />・白と黒が分かれるようにswapする。<br /><br />→system failed<br /><br />・問題文を見落としてしまった。<br />・まず問題文は白→黒の順と決まっていることと、白と黒の数は任意であること。<br />・問題文をきちんと読んで条件を整理する基本を徹底せねば。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class BlackWhiteMagic {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int count(string creatures) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=creatures.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int w=0,ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(creatures[i]=='W')w++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,w)if(creatures[i]=='B')ret++;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
