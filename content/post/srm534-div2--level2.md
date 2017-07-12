+++
title = "SRM534 DIV2 -Level2"
date = 2013-07-10T09:52:00Z
updated = 2015-04-03T12:00:04Z
tags = ["２人ゲーム"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br />①１次元の列が与えられ、ランダムな数の石がおかれている。<br />②この石は右に１マスもしくは３マス動かすことができる。<br />　３マス動かす時はその間の石を飛び越すことができる。<br />　しかし、動かした先に石がある場合は動かすことができない。<br />　最後のマスに達したときはその石は動かすことはできなく、消えてしまう。<br />③２人のプレイヤーが順にこの操作を行う。<br />　石を動かせなくなった方が負けとなる。<br />④このとき、最初のプレイヤーが勝つならＹＥＳ,負けるならＮＯを返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />デッドロックが発生する場合を想定すると複雑になりそうに見える。<br />しかし、そのように見える場合でも一番右の石は動かすことができるので、<br />それぞれの石は独立に考えることができる。<br /><br />これがわかれば、動かすことのできるマスが奇数の場合は最初のプレイヤーが勝ち、<br />偶数の場合は負けることがわかる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class EllysCheckers {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string getWinner(string board) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int parity=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,board.size()-1)if(board[i]=='o')parity+=(board.size()-1-i);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return parity%2!=0 ? "YES" : "NO" ;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
