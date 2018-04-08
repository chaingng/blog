+++
title = "SRM567 DIV2 -Level2"
date = 2013-06-29T10:46:00Z
updated = 2015-04-03T11:22:44Z
tags = ["数学"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">＜問題＞<br />①２つの整数ＮとＭが与えられる。<br />②１＜＝Ａ＜＝Ｎ、１＜＝Ｂ＜＝Ｍである、(sqrt(A)+sqrt(B))^2が整数であるＸが存在するとき、ＡとＢの組み合わせの数を返す。<br /><br />＜解き方＞<br />Ａが１のとき、Ｂ＝１，４，９，１６・・・<br />Ａが２のとき、Ｂ＝２＊１、２＊９、２＊１６・・・であることがわかります。<br />そのため、Ａを１からＮまでループさせ、<br />ＢをＡ＊１＾２、Ａ＊２＾２・・・と繰り返して数を足してあげて<br />最後にその和をかえしてあげればよいです。<br />Ｏ（８００００＊９００＝７２００００００＝７＊１０＾７）なので微妙。<br /><br />もう少し計算量を削減するには、<br />Ａが２で選ばれるＢの数と、<br />Ａが２＊２＾２、２＊３＾２・・・で選ばれるＢの数は一緒であることが分かります。<br />そこでＡもまとめて計算することで計算量が削減できます。<br />おおまかですがＯ（９００＊９００＝８１００００＝８＊１０＾５）ぐらい。<br /><br />＜コード＞<br />class TheSquareRootDilemma {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int countPairs(int N, int M) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; check(77778,0);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ans=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,M+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(check[i]==1)continue;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int x=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=1;j*j*i&lt;=M;j++){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(check[i*j*j]==1)continue;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>check[i*j*j]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>x++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int y=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=1;j*j*i&lt;=N;j++)y++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ans+=(x*y);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};<br /><br /></div>
