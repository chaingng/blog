+++
title = "SRM 648 DIV2 Middle - Fragile2 (○)"
date = 2015-03-16T20:27:00Z
updated = 2015-04-03T11:56:09Z
tags = ["グラフ"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13648&amp;rd=16312" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13648&amp;rd=16312</a><br /><div><br /></div>・無向グラフの隣接行列のリストが与えられる。<br />・このうち２つの頂点を選び、グラフから消した時に木の集合が増える<br />　頂点の選び方を全て求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・頂点数は２０なので、頂点の選び方は２０C2となり全探索で解ける。<br /><br />・２つの頂点を選んだときにできる木の集合の数を求め、頂点を消さないときよりも<br />　集合の数が増えるかどうか判定すればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />int used[30],n;<br />vector&lt;string&gt; g;<br /><br />class Fragile2 {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>void dfs(int x){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>used[x]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(!used[i] &amp;&amp; g[x][i]=='Y')dfs(i);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int countPairs(vector&lt;string&gt; graph) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>n=graph.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>g=graph;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(used,0,sizeof(used));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int sum=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(!used[i]){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>sum++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>dfs(i);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,i+1,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>memset(used,0,sizeof(used));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>used[i]=1,used[j]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>g=graph;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(k,0,n)g[i][k]=g[k][i]=g[j][k]=g[k][j]='N';<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int tmp=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(k,0,n)if(!used[k]){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>tmp++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>dfs(k);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(tmp&gt;sum)ret++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>