+++
title = "2014 TCO Semifinal2 DIV1 Easy - PlankTiling"
date = 2015-04-22T22:02:00Z
updated = 2015-04-22T22:02:29Z
tags = ["考察"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13437&amp;rd=16188" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13437&amp;rd=16188</a><br /><br />・１＊Hの棒が与えられる。<br />・この棒を、（２H-1）＊Wのセルに敷き詰める場合の数を求める。<br />・WはHの倍数となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />WがHの倍数のときにすべて敷き詰めることができる。<br />敷き詰め方としては、W＝３、H＝３のとき<br />---<br />---<br />---<br />---<br />---<br />が必ず１通り存在し、さらに<br />||<br />||<br />||<br />と縦に並べる並べ方がH通りあるので合計H＋１通り。<br />さらにWが３増えると（H+1）＊H通り＋（H+1）通りになる。<br /><br />加えて、WがH+1以上のときは<br />上記のようにWをH個のブロック区切りで考える他に、<br />区切りの間に敷き詰める方法がある。<br /><br />上記の３つについてｄｐを適用させていけば良い。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class PlankTiling {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int sumup(int H, int W) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int dp[W+1];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int MOD=1000000007;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(dp,0,sizeof(dp));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0]=1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;W;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(i+H&lt;=W)dp[i+H]=(dp[i+H]+dp[i])%MOD;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(i%H==0)dp[i+1]=(dp[i+1]+dp[i]*1LL*H)%MOD;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else dp[i+1]=(dp[i+1]+dp[i])%MOD;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return dp[W];<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
