+++
title = "SRM 515 DIV1 Easy - RotatedClock"
date = 2015-05-10T12:57:00Z
updated = 2015-05-10T12:57:25Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11329&amp;rd=14540" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11329&amp;rd=14540</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />３０度ずつ回転させることが可能なので、全探索して<br />有効な数字の時の値を更新すればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class RotatedClock {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string getEarliest(int hourHand, int minuteHand) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string ret="";<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;=360;i+=30){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int h=(hourHand+i)%360;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int m=(minuteHand+i)%360;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((h%30)*12==m){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>char ch[20];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>sprintf(ch,"%02d:%02d",h/30,m/6);<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(ret.empty()||ch&lt;ret)ret=ch;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
