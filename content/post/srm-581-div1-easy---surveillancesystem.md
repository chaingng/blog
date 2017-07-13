+++
title = "SRM 581 DIV1 Easy - SurveillanceSystem"
date = 2015-05-27T16:22:00Z
updated = 2015-05-27T16:22:01Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12588&amp;rd=15501" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12588&amp;rd=15501</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />監視してる数ごとに、どのような場合が成り立つか考える。<br /><br />その監視している数について、成り立つすべての場合をall、カメラの数をcntとすると<br />all-cnt以上その場合の数が存在した時は必ず＋となり、１位上であれば？となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class SurveillanceSystem {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string getContainerInfo(string containers, vector&lt;int&gt; reports, int L) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=containers.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string ret="";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)ret+='-';<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int p[n];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;=n;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int cnt=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,reports.size())if(reports[j]==i)cnt++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(cnt==0)continue;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int all=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>memset(p,0,sizeof(p));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=0;j+L-1&lt;n;j++){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>int tmp=0;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>FORE(k,0,L)if(containers[j+k]=='X')tmp++;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(tmp==i){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>all++;<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>FORE(k,0,L)p[j+k]++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(p[j]==0)continue;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(cnt&gt;all-p[j])ret[j]='+';<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>else if(ret[j]=='-')ret[j]='?';<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>