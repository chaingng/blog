+++
title = "SRM 506 DIV1 Easy - SlimeXSlimesCity"
date = 2015-05-09T15:55:00Z
updated = 2015-05-09T15:55:01Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11154&amp;rd=14435" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11154&amp;rd=14435</a><br /><br />スライムの島が複数あり、各島ごとに何匹スライムがいるかわかっている。<br />各島を１つに統合したい。<br />２つの島を統合するとき、もう一つの島にいるスライムの数以上であれば<br />その島の名前をつけることができる。<br /><br />このとき、最大で何通りの島の数が存在しうるか求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />配列をソートし、初期値をその名前を残したい島のスライムの数とする。<br />小さい方から統合していき、すべての島を統合できればその名前は残り、<br />そうでなければその名前は残らなくなる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class SlimeXSlimesCity {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int merge(vector&lt;int&gt; population) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=population.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(population));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>long long sum=population[i];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int at=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>while(at&lt;n){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(at==i){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>at++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>else if(sum&gt;=population[at]){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>sum+=population[at];<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>at++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>else break;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(at&gt;=n)ret++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>