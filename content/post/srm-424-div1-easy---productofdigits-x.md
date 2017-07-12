+++
title = "SRM 424 DIV1 Easy - ProductOfDigits x"
date = 2015-05-09T15:34:00Z
updated = 2015-08-09T20:52:30Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10177&amp;rd=13515" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10177&amp;rd=13515</a><br /><br />ある整数Nが与えられる。<br />各桁の数の積がNになる整数について、<br />その最小の桁数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />Nを９から１で順番に割れるか確かめていって、その商の数が桁数になる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class ProductOfDigits {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int smallestNumber(int N) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=9;i&gt;1;i--){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>while(N%i==0)N/=i,ret++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(N!=1)return -1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(ret==0)return 1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
