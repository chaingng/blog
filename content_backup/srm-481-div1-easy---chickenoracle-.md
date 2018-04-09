+++
title = "SRM 481 DIV1 Easy - ChickenOracle △"
date = 2015-05-04T21:17:00Z
updated = 2015-08-09T20:55:48Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11004&amp;rd=14234" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11004&amp;rd=14234</a><br /><br />鶏が先か卵が先かという古典的な問題がある。<br />オラクルはどちらが答えかわかっており、ｎ人にその答えを伝えた。<br />ただし、liecount人には嘘の答えを教えている。<br /><br />また、ｎ人について鶏と答えた人数と卵と答えた人数がわかっている。<br />ただし、liarcount人は教えられたものと違う答えを答えている。<br /><br />このとき、答えが卵か鶏のどちらかを求める。<br />ただし、両方の場合が考えられる時はAmbiguousを、<br />オラクルが嘘をついているのであればThe oracle is a lieを返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />答えが卵である場合と、鶏である場合それぞれについて<br />最終的な数（卵が答えのときはｎ人ーliecount）はわかっている。<br /><br />ただし、嘘をついている人が何人どちらの答えを教えられているかは、<br />様々な場合が考えられるため、<br />この人数について全探索して一致するかどうかを調べればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class ChickenOracle {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string theTruth(int n, int e, int lieCount, int liarCount) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int c=n-e;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int flagc=0,flage=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int tmpc=n-lieCount,tmpe=n-tmpc;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int move=0;move&lt;=liarCount;move++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(move&gt;tmpc || liarCoun<span class="Apple-tab-span" style="white-space: pre;"> </span>t-move&gt;tmpe)continue;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(tmpc-move+(liarCount-move)==c || tmpe-(liarCount-move)+move==e){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>flagc=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>tmpe=n-lieCount,tmpc=n-tmpe;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int move=0;move&lt;=liarCount;move++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(move&gt;tmpc || liarCount-move&gt;tmpe)continue;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(tmpc-move+(liarCount-move)==c || tmpe-(liarCount-move)+move==e){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>flage=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(flagc &amp;&amp; flage)return "Ambiguous";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(flagc)return "The chicken";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(flage)return "The egg";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "The oracle is a lie";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>