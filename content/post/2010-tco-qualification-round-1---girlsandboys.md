+++
title = "2010 TCO Qualification Round 1 - GirlsAndBoys"
date = 2014-10-29T18:18:00Z
updated = 2015-03-26T19:23:40Z
tags = ["全探索"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=7794&amp;rd=14294" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=7794&amp;rd=14294</a><br /><br />・男の子と女の子が並んでいる。<br />・このうち、男の子と女の子が隣に並んでいる並びをできるだけ少なくしたい。<br />・並びを変えるには、一回の操作で任意の２人を入れ替えることができる。<br />・このときの、最小の操作回数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・最小の並べ方はBBBGGGもしくはGGGBBBとなる並べ方になる。<br />・よって、上の２つの並べ方のうち操作回数が小さいものが答えになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class GirlsAndBoys {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int sortThem(string row) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int INF=1e+8,n=row.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int cost=INF;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int tmpcost=0,pos=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int letter=0;letter&lt;n;letter++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(row[letter]!='B')continue;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>tmpcost+=abs(letter-pos);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>pos++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>cost=min(cost,tmpcost);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>tmpcost=0,pos=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int letter=0;letter&lt;n;letter++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(row[letter]!='G')continue;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>tmpcost+=abs(letter-pos);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>pos++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>cost=min(cost,tmpcost);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return cost;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>