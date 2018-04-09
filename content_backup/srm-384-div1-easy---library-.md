+++
title = "SRM 384 DIV1 Easy - Library ○"
date = 2015-07-28T04:01:00Z
updated = 2015-07-28T04:01:17Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=7659&amp;rd=10808" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=7659&amp;rd=10808</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />解くだけ。<br />setを使えば重複の考慮も不要で、条件を満たしているかも簡単に判断できる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class Library {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int documentAccess(vector&lt;string&gt; records, vector&lt;string&gt; userGroups, vector&lt;string&gt; roomRights) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>set&lt;string&gt; user,room;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,userGroups.size())user.insert(userGroups[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,roomRights.size())room.insert(roomRights[i]);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>set&lt;string&gt; ans;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,records.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>stringstream out(records[i]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>string doc,u,r;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>out &gt;&gt; doc &gt;&gt; r &gt;&gt; u;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(room.find(r)!=room.end() &amp;&amp; user.find(u)!=user.end()){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>ans.insert(doc);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans.size();<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>