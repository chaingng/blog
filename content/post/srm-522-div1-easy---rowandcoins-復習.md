+++
title = "SRM 522 DIV1 Easy - RowAndCoins （復習○）"
date = 2013-10-13T08:19:00Z
updated = 2015-03-26T20:07:03Z
tags = ["２人ゲーム"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11566&amp;rd=14547" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11566&amp;rd=14547</a><br /><br />AliceとBobの２人で行うゲーム。<br />一行のマスの並びが与えられて、各マスにはＡかＢのどちらかが書かれている。<br />ゲームはAliceから始まり、連続する任意のマスにコインを置くことができる。<br />ただし、マスは最低一つコインを置かずに残さなければいけない。<br />このとき、残った最後のマスがＡならAliceの勝ち、そうでなければBobの勝ちとなる。<br /><br />一行のマスが与えられた時、どちらが勝つかを求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />単純なシミュレーションに見えるが、全ての手の全探索は難しそう。<br /><br />ここで「勝ちの法則」がないかを考える。<br />まず、Aliceは１マスを除いて好きなだけ連続するマスに置けるので、<br />最初か最後のマスがＡであれば必ず勝ちになる。<br />次にそうでない場合（両端がＢ）、どう消してもBは残ってしまうので<br />どうやってもAliceは勝つことができない。<br />例）BAAABABのとき<br />①左のＢを消す　　：AAABAB →次に右端以外を消されてしまう<br />②右のＢを消す　　：上記と同様<br />②真ん中のＢを消す：BAAA*AB 左もしくは右のAを消されてＢは残る(B*AB or BA*B)<br /><br />つまり、両端のどちらかがＡであればAlice、そうでなければBobの勝ちとなる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;"><br />class RowAndCoins {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string getWinner(string cells) {<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return cells[0]=='B'&amp;&amp;cells[cells.size()-1]=='B' ? "Bob" : "Alice";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
