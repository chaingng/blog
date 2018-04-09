+++
title = "SRM574 DIV2 -Level2"
date = 2013-07-13T21:10:00Z
updated = 2015-04-03T11:22:45Z
tags = ["数学"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br />①数字が二つ与えられる。<br />②プレイヤーは一つ目の数字を１０で割る、もしくは逆にすることができる。<br />③上記の操作によって、２つ目の数字にするとき、最小の操作回数を求める。<br />　２つ目の数字にできないときはー１を返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />どのような法則があるか例を出して導く。<br /><br />289が求めたい数字のとき、<br />元の数字：１２８９　→３回<br />２８９１　→１回<br />１２８９１　→４回<br /><br />つまり、<br />・最初から含まれる　→文字数の差<br />・途中から含まれる　→文字列の差＋２<br /><br />ひっくり返した場合もシミュレーションすると、<br />ひっくり返した文字が含まれる　→文字数の差＋１回<br /><br />ただ求めたい数字の場合は両方一致するため、<br />返す数が少ない方から判定していく。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TheNumberGameDiv2 {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>string f(int n){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string str;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>stringstream out;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>out&lt;&lt;n;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>out&gt;&gt;str;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return str;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int minimumMoves(int A, int B) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string As=f(A);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string Bs=f(B);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int dis=As.size()-Bs.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int flag=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(As.find(Bs)!=string::npos)flag=1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(As.find(Bs)==0)return dis;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>reverse(Bs.begin(),Bs.end());<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(As.find(Bs)!=string::npos)return dis+1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(flag==1)return dis+2;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return -1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>