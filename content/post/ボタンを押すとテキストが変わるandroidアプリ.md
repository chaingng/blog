+++
title = "ボタンを押すとテキストが変わるandroidアプリ"
date = 2014-10-13T22:16:00Z
updated = 2014-10-13T22:16:02Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />ドットインストールで学んだ、ボタンを押すとテキストが変わるサンプルアプリの<br />作り方を整理。<br /><a href="http://dotinstall.com/lessons/basic_android" target="_blank">http://dotinstall.com/lessons/basic_android</a><br /><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">部品にIDをつける</h3><br />レイアウト画面から、ボタンをドラッグ＆ドロップして設置。<br /><br />次に、テキストとボタンをダブルクリックして、IDをつける。<br />ここではテキストのIDはmyLabel、ボタンのIDはmyButtonとする。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">部品のプロパティにメソッド名を紐づけ</h3><br />今回はボタンを押したときの動作なので<br />右下のプロパティからonClickを選択し、クリックしたときに起動するメソッド名を入力。<br />ここではchangeLabelとする。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">MyActivity.javaにメソッドを書く</h3><br />先ほど名前をつけたchangeLabelメソッドをMyActivity.javaの中に書く。<br /><br />今回は引数にViewクラスを設定。<br /><br />ここでのLog.vはlogcatに出力されるメッセージ。<br />第一引数はタグ、第二引数が出力したいメッセージになる。<br /><br />今回はテキストのビューを変更したいので、Viewクラスの拡張である<br />TextViewクラスを用い、<br />変えたいテキストのIDを持つビューを探す。<br /><br />そしてそのビューに対し、クリック後のテキストをセットすればよい。<br /><br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">public class MyActivity extends Activity {<br /><br />&nbsp; &nbsp; @Override<br />&nbsp; &nbsp; protected void onCreate(Bundle savedInstanceState) {<br />&nbsp; &nbsp; &nbsp; &nbsp; super.onCreate(savedInstanceState);<br />&nbsp; &nbsp; &nbsp; &nbsp; setContentView(R.layout.activity_my);<br />&nbsp; &nbsp; }<br /><br />&nbsp; &nbsp; public void changeLabel(View view){<br />&nbsp; &nbsp; &nbsp; &nbsp; Log.v("TEST","Clicked");<br />&nbsp; &nbsp; &nbsp; &nbsp; TextView tv = (TextView)findViewById(R.id.myLabel);<br />&nbsp; &nbsp; &nbsp; &nbsp; tv.setText("Changed!");<br />&nbsp; &nbsp; }<br /><div><br /></div></div></div>
