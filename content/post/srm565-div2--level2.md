+++
title = "SRM565 DIV2 -Level2"
date = 2013-06-30T00:05:00Z
updated = 2015-03-26T19:55:03Z
tags = ["DP"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">＜問題＞<br />①モンスターの集合が与えられ、各モンスターは怖さの値とコインの値を持つ。<br />②プレイヤーは最初から順番にモンスターに遭遇する。<br />③このとき、プレイヤーはモンスターにそのコインの値を支払って仲間にすることができる。<br />④もしくは、仲間にしたモンスターの怖さの和がそのモンスターの怖さの値以上であれば、何もせずに通り過ぎることができる。それ未満であれば、仲間にしないといけない。<br />⑤このとき、すべてのモンスターに遭遇した後に最小のコイン消費枚数を返す。<br /><br />＜解き方＞<br />まさに動的計画法。<br /><br />参照用のvectorをグローバルで宣言してpush_backでコピーしようとしたんですが、<br />エラーが出たので引数で渡すことに。<br /><br />suztomoさんのページを拝見させていただいたのですが、<br />１０＾７以上のループに加え、あまり大きな数を扱ってもダメなのかもしれないです。<br /><a href="http://topcoder.g.hatena.ne.jp/suztomo/20081208/1228768981">http://topcoder.g.hatena.ne.jp/suztomo/20081208/1228768981</a><br /><br />＜コード＞<br />class MonstersValley2 {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int f(int cur, double cdread, vector&lt;int&gt; d, vector&lt;int&gt; p){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int coin=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(cur==n)return 0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(cdread&lt;d[cur])coin=p[cur]+f(cur+1,cdread+d[cur],d,p);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>else coin=min(f(cur+1,cdread,d,p),f(cur+1,cdread+d[cur],d,p)+p[cur]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return coin;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int minimumPrice(vector&lt;int&gt; dread, vector&lt;int&gt; price) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>n=dread.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return f(1,dread[0],dread,price)+price[0];<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};<br /><div><br /></div></div>
