+++
title = "2014 TCO Celebrity Match DIV1 Easy - AnEasyProblem"
date = 2015-04-22T15:34:00Z
updated = 2015-04-22T15:35:51Z
tags = ["累積和"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13527&amp;rd=16191" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13527&amp;rd=16191</a><br /><br />・関数F（h,r）が与えられる。その要素は{1,2,3,...h-1,h,h-1...r+1,r}となる。<br />　（例）F(3,2)={1,2,3,2}<br />・関数Fの和があらかじめわかっているとき、その和を構成できる関数Fのうち<br />　最も少ない要素数を求める。<br />　そのようなFがない場合は−１を返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />和の最大が10^12であるため、n*(n+1)/2&lt;=10^12から<br />nは最大でも10^6程度なので全探索できそう。<br /><br />まず１から単調増加で和を計算していき、そのような和が構成できれば<br />それは最小要素なので答えになる。<br /><br />そのような最小要素がなければ、途中で折り返す要素を計算する。<br /><br />この場合最悪ケースで10^12になってしまうので、工夫が必要。<br /><br />このとき、折り返し分の要素は最大のnからn-1,n-2・・・の和のいずれかであるので<br />あらかじめ累積和を計算しておき、二分探索することで<br />計算量を20*10^6に収めることができる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">long long dp[1500000];<br /><br />class AnEasyProblem {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int solve(long long sum) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long cur=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(cur+n+1&lt;=sum){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>n++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cur+=n;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(cur==sum)return n;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0]=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=1;i&lt;=n;i++)dp[i]=dp[i-1]+i;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int x=n;x&gt;=1;x--){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(dp[x-1]*2+x&lt;sum)break;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>long long tmp=dp[x-1]-(sum-dp[x]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int m = (lower_bound(dp,dp+n,tmp)) - dp ;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(dp[m]==tmp)return (x-1)-m+x;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return -1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>