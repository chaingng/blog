+++
title = "SRM 559 DIV1 Easy - HyperKnight"
date = 2015-05-25T10:32:00Z
updated = 2015-05-25T10:32:25Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12201&amp;rd=15181" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12201&amp;rd=15181</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />サンプルを表に書いて見ると、各動ける数ごとにどれだけのマスを占めるか<br />一意に決めることができる。ただきちんと表に落とすのがちょっと複雑。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class HyperKnight {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long countCells(int a_, int b_, int numRows, int numColumns, int k) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long R=numRows,C=numColumns,a=a_,b=b_;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(a&lt;b)swap(a,b);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ans[9]={};<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans[2]=b*b*4;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans[3]=b*(a-b)*8;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans[6]=(R-2*a)*(a-b)*2+(C-2*a)*(a-b)*2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans[8]=(R-2*a)*(C-2*a);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans[4]=R*C-ans[2]-ans[3]-ans[6]-ans[8];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans[k];<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
