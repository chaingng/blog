+++
title = "SRM537 DIV2 -Level2"
date = 2013-07-09T08:14:00Z
updated = 2015-04-03T11:22:45Z
tags = ["数学"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">問題<br /><br />①数字のペアＡ，Ｂが与えられる。<br />　このとき、０以上のｐ、ｑに対し、Ａ＊ｐ＋Ｂ＊ｑで数が生成できる。<br />②また、新たな数字Ｘが与えられる。<br />　このとき、Ａ，Ｂで表わせる全てのペアが、Ｘ，Ｙでも表わせるような<br />　Ｙの場合の数を求める。ただしＹが無限になる場合はー１を返す。<br /><br />解き方<br /><br />Ｘ，ＹにてＡ，Ｂが表わすことができれば、<br />Ａ，Ｂで現すことのできる全ての数はＸ，Ｙで現すことができる。<br /><br />Ｙのとりうる数は１～max(A,B) (Xを除く)なので、<br />全てのＹに対してＸ，ＹがＡ，Ｂで表わせるかを判定する。<br /><br />Ａ＝Ｘ＊ｐ＋Ｙ＊ｑ<br />ｑ＝１として、<br />pが０からＸ＊ｐがＡになるまで増やしていき、<br />Ｙで割ることができるか判定する。<br />ｑ＝０の場合も調べるため、ＡがＸで割り切れるかも判定する。<br /><br />全て数学的解法に頼らず、全探索との組み合わせで落とし所を探る。<br /><br />コード<br /><br />class KingXNewCurrency {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>bool f(int num,int x,int y){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(num%x==0)return true;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;x*i&lt;=num;i++)if((num-x*i)%y==0)return true;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return false;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int howMany(int A, int B, int X) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(A%X==0 &amp;&amp; B%X==0)return -1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ans=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int n=1;n&lt;=max(A,B);n++)if(X!=n &amp;&amp; f(A,X,n) &amp;&amp; f(B,X,n))ans++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};<br /><div><br /></div></div>
