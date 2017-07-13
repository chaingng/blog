+++
title = "SRM 601 DIV1 Easy - WinterAndPresents"
date = 2015-04-25T07:31:00Z
updated = 2015-04-25T07:31:59Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12860&amp;rd=15713" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12860&amp;rd=15713</a><br /><br />りんごとオレンジが入ったバッグが複数与えられる。<br />各バッグについて、りんごとオレンジそれぞれ何個入っているかわかっている。<br /><br />ここで、各バッグからX個ずつフルーツを取り出す。<br />このとき、取り出し方の総数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />各バッグから取り出す数は、各バッグのフルーツの総数の最小数Xとなる。<br />なので、各バッグから１個ずつ〜X個ずつの各ケースについて場合の数を求める。<br /><br />各バッグからX個ずつ取り出すときの総数について<br />すべての場合の数を計算していては間に合わない。<br /><br />ここで、りんごの取り出し方の最大数とオレンジの取り出し方の最大数さえわかれば<br />場合の数は計算できる。<br />２種類のフルーツで合計の数がわかっている場合、１種類だけに着目すれば<br />もう１種類は計算しなくてもよいのがコツ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class WinterAndPresents {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long getNumber(vector&lt;int&gt; apple, vector&lt;int&gt; orange) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=apple.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int minx=1e+9;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)minx=min(minx,apple[i]+orange[i]);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int x=1;x&lt;=minx;x++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int numa=0,numo=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>numa+=min(x,apple[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>numo+=min(x,orange[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(numa&lt;numo)swap(numa,numo);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=numa-(x*n-numo)+1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>