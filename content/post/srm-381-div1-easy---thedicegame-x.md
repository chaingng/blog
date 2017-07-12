+++
title = "SRM 381 DIV1 Easy - TheDiceGame x"
date = 2015-08-05T10:04:00Z
updated = 2015-08-05T10:04:24Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8414&amp;rd=10804" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8414&amp;rd=10804</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />dpで解く。<br />前の状態から現在の状態までに行ける全ての場合について和をとっていく。<br />前の状態から＋１回かつサイコロなので1/6を掛けたものになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TheDiceGame {<br /><div><div><br /></div><div><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double expectedThrows(int candies) {</div><div><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(dp,0,sizeof(dp));</div><div><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=1;i&lt;=candies;i++){</div><div><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=1;j&lt;=6;j++){</div><div><span class="Apple-tab-span" style="white-space: pre;">    </span>int prev=max(0,i-j);</div><div><span class="Apple-tab-span" style="white-space: pre;">    </span>dp[i]+=(dp[prev]+1.0)/6.0;</div><div><span class="Apple-tab-span" style="white-space: pre;">   </span>}</div><div><span class="Apple-tab-span" style="white-space: pre;">  </span>}</div><div><br /></div><div><span class="Apple-tab-span" style="white-space: pre;">  </span>return dp[candies];</div><div><span class="Apple-tab-span" style="white-space: pre;"> </span>}</div><div><br /></div><div>};</div></div></div></div>
