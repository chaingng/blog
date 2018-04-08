+++
title = "SRM 431 DIV1 Easy - LaserShooting (復習××)"
date = 2013-10-19T07:36:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10258&amp;rd=13522" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10258&amp;rd=13522</a><br /><br />（０，０）の位置からレーザーが発射される。<br />レーザーは（ｘ、ｙ１）（ｘ、ｙ２）の二つの値が与えられ、その間を通るように発射される。ｙ１、ｙ２の範囲は[-2/PI,2/PI]。<br />このような（ｘ、ｙ１）（ｘ、ｙ２）が複数与えられるとき、ある点がレーザーに当たる確率を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />全ての点について確率を求めていては間に合わない。<br />そのため、各(x,y1)(x,y2)に対しレーザーの当たる範囲の確率を足していけばよい。<br /><br />arctanの使い方を忘れていたので、こちらのサイトを拝見させていただきました。<br /><a href="http://78578203.at.webry.info/201101/article_2.html">http://78578203.at.webry.info/201101/article_2.html</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LaserShooting {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double numberOfHits(vector&lt;int&gt; x, vector&lt;int&gt; y1, vector&lt;int&gt; y2) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double ret=0.0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=y1.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>double tmp1=atan((double)y1[i]/(double)x[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>double tmp2=atan((double)y2[i]/(double)x[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=fabs(tmp1-tmp2)/M_PI;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
