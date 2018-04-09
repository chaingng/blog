+++
title = "SRM 658 DIV2 Hard - OddEvenTreeHard"
date = 2015-05-06T12:40:00Z
updated = 2015-08-06T09:51:36Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13784&amp;rd=16461" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13784&amp;rd=16461</a><br /><br />Div1 Easyでノード間の情報が？となっている場合が追加されている。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />まずは以下について判定し、有効な木か判定する。<br />・自分のノードへのエッジはOではない<br />・エッジi~jとj~iは等しい<br /><br />上記を満たす場合について、以下について判定し？が特定できる場合は埋めていく。<br />・あるノードからの距離が偶数同士のノード間距離は偶数<br />・あるノードからの距離が偶数と奇数のノード間距離は奇数<br /><div>・あるノードからの距離が奇数同士のノード間距離は偶数</div><div><br /></div><div>上記で？が存在する場合は、一つをOにして、？がなくなるまでDFSで判定していく。</div><div>最後にすべての状態がわかるので、そこからひとつのエッジ集合を返してあげればよい。</div><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">int d[60],n;<br />vector&lt;string&gt; x;<br /><br />class OddEvenTreeHard {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>bool dfs(){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int update=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(x[i][j]=='?'){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(d[i]!=-1 &amp;&amp; d[j]!=-1){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>x[i][j]= (d[i]^d[j]) ? 'O' : 'E';<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>x[j][i]=x[i][j];<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>update=1;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else{<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>int cur= x[i][j]=='O' ? 1 : 0;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(d[i]!=-1 &amp;&amp; d[j]!=-1){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>if(cur!=(d[i]^d[j]))return false;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>else if(d[i]!=-1 &amp;&amp; d[j]==-1)d[j]=(cur^d[i]),update=1;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>else if(d[i]==-1 &amp;&amp; d[j]!=-1)d[i]=(cur^d[j]),update=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(update)dfs();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return true;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>vector&lt;int&gt; getTree(vector&lt;string&gt; x_) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>x=x_;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>n=x.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(d,-1,sizeof(d));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; invalid;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>invalid.push_back(-1);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(x[i][i]=='O')return invalid;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>x[i][i]='E';<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(x[i][j]!='?' &amp;&amp; x[j][i]!='?' &amp;&amp; x[i][j]!=x[j][i])return invalid;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(x[i][j]=='?')x[i][j]=x[j][i];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else x[j][i]=x[i][j];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(x[0][i]=='O')d[i]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else if(x[0][i]=='E')d[i]=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(dfs()==false)return invalid;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int finish=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,n)FORE(j,0,n)if(x[i][j]=='?')finish=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(finish)break;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,n)if(x[0][i]=='?'){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>x[0][i]='O',x[i][0]='O';<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>d[i]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>break;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(dfs()==false)return invalid;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int r0=0,r1=-1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(x[0][i]=='O')r1=i;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(r1==-1)return invalid;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; ans;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans.push_back(r0),ans.push_back(r1);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,n)if(i!=r1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(d[i]){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>ans.push_back(r0),ans.push_back(i);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}else{<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>ans.push_back(i),ans.push_back(r1);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>