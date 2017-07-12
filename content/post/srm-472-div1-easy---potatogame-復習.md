+++
title = "SRM 472 DIV1 Easy - PotatoGame (復習×○)"
date = 2014-02-01T11:26:00Z
updated = 2015-03-26T20:05:55Z
tags = ["２人ゲーム"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10759&amp;rd=14154" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10759&amp;rd=14154</a><br /><br />・TaroとHanakoの２人がゲームをする。<br />・ポテトの数が与えられて、４の階乗分だけ自分のターンのときに食べることができる。<br />・ポテトの数が０になったら勝ち。<br />・最初はTaroのターン。<br />・このとき、勝つ方のプレイヤーの名前を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />１０＾９のため全探索では解くことができない。<br /><br />パターンを見つけようとdpで１０００ほど出力させてみると、<br />MOD5のとき0もしくは２のときHanakoが勝つことがわかる。<br /><br />次に上記の証明。<br />4の階乗を引くということは、mod5で考えた時±1していることと同じ。<br />例えば、4のときは 4^2 mod5=-1 、16のときは 4^2 mod5=1となる。<br /><br />ここで、Taroが勝つポジションを n=1,3,4(mod5)としたとき、<br />4^Kを引いた場合に相手に負けるポジションに移動させることができる。<br />例外としてN=1,3のときは1を引くことしかできない。<br />N=1 のときは1を引くことで勝ちとなるのでＯＫ．<br />N=3 のときは1を引いてN=2と負けのポジションに移動させられるのでＯＫ．<br /><br />逆に、負けるポジション n=0,2(mod5)にいた場合は<br />4^Kを引いても相手を負けるポジションに移動させることができない。<br /><br />よって、最初のMOD5のときのポジションで勝ち負けが一意に決まる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class PotatoGame {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string theWinner(int n) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return n%5==0||n%5==2 ? "Hanako" : "Taro";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
