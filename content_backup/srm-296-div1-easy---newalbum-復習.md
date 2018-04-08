+++
title = "SRM 296 DIV1 Easy - NewAlbum (復習×○)"
date = 2014-01-24T00:34:00Z
updated = 2015-03-26T19:54:39Z
tags = ["DP"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=6085&amp;rd=9817" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=6085&amp;rd=9817</a><br /><br />・与えられた曲を全てＣＤに収録したい。<br />・曲の長さは全て同じ秒数。<br />・１つのＣＤに入れられる秒数も決められている。<br />・ＣＤに収録する際、曲の間には必ず１秒空けなければいけない。<br />・ただし、１つのＣＤに収録される曲数は１３の倍数になってはいけない。<br /><br />曲の長さと１つのＣＤに入れられる秒数、全曲数が与えられた時、<br />必要なＣＤの最小数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />数学的に解くことができるが、少しトリッキー。<br />ＣＤに入れられる曲数だけめいっぱい入れていき、<br />最後に余った曲数に対して、１３の倍数でなければ１曲のみ他のＣＤに移せばよいので、答えはＣＤに入れられる曲数で割った数になる。<br />１３の倍数のとき、他のＣＤがないとき、もしくは１引いたときその数が１３の倍数になるときは新たなＣＤに焼かなければいけないので＋１となる。<br /><br />上記のように少し考察が必要だが、ｄｐで解けば簡単に解くことができる。<br /><br />文字列のｄｐと同様１次元配列を用い、<br />その曲数までの最小ＣＤ数を求めてあげればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class NewAlbum {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int leastAmountOfCDs(int nSongs, int length, int cdCapacity) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int dp[nSongs+1];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int num=(cdCapacity+1)/(length+1);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0]=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,nSongs+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>dp[i]=100000;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,1,min(num,i)+1)if(j%13!=0)dp[i]=min(dp[i],1+dp[i-j]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return dp[nSongs];<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
