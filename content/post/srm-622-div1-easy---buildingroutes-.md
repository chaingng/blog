+++
title = "SRM 622 DIV1 Easy - BuildingRoutes ××○"
date = 2014-11-02T21:50:00Z
updated = 2015-07-28T04:45:15Z
tags = ["グラフ"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13193&amp;rd=15855" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13193&amp;rd=15855</a><br /><br />・有向グラフとエッジの距離が与えられる。<br />・ある点からある点に行くまでに通る最短の経路を考えるとき、<br />　すべての点から点までの最短経路で通る数がT以上であれば、その経路の距離の和を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3>・最短距離といえばワーシャルフロイドだが、途中の経路を知る必要がある。<br />・それではダイクストラ？でも途中の経路を知るのは難しい・・・で断念。<br /><br />→他の人のコードをみる<br /><br />・ワーシャルフロイドを適用したあと、ある最短経路のうちあるエッジを通るかは、<br />　そのエッジを含めた距離が最短経路と一致していればよい。<br /><br />・反省：最短経路と途中の経路の関係を応用できるようにすべき。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class BuildingRoutes {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int build(vector&lt;string&gt; dist, int T) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=dist.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int d[n][n],cnt[n][n];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(cnt,0,sizeof(cnt));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,0,n)d[i][j]=dist[i][j]-'0';<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(k,0,n)FORE(i,0,n)FORE(j,0,n)d[i][j]=min(d[i][j],d[i][k]+d[k][j]);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,0,n)if(i!=j){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(k,0,n)FORE(l,0,n)if(k!=l &amp;&amp; d[i][k]+dist[k][l]-'0'+d[l][j]==d[i][j])cnt[k][l]++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,0,n)if(cnt[i][j]&gt;=T)ret+=dist[i][j]-'0';<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>