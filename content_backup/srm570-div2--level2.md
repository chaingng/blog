+++
title = "SRM570 DIV2 -Level2"
date = 2013-06-12T23:21:00Z
updated = 2015-04-03T12:00:35Z
tags = ["シミュレーション"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">&lt;問題&gt;<br />①数字の順列が与えられる。<br />②各数字に対して、ロボットはその数字の分前に進む。進んだ後は右に９０度回転する。<br />③最後の数字まで進む処理をＴ回繰り返す。<br />④このとき、最初と最後の位置のマンハッタン距離を返す。<br /><br />＜解き方＞<br />数字の数は最大５０個、Ｔは最大１００回なので最大の場合でもＯ（５０００）。<br />計算量が余裕で間に合うので純粋にシミュレーションを実装する。<br /><br />＜コード＞<br />class RobotHerbDiv2 {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int getdist(int T, vector&lt;int&gt; a) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int x=0,y=0,dir=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(h,0,T){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,a.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(dir%4==0)y+=a[i];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(dir%4==1)x+=a[i];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(dir%4==2)y-=a[i];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(dir%4==3)x-=a[i];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>dir+=(a[i]%4);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return abs(x)+abs(y);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div>
