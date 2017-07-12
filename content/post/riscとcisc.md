+++
title = "RISCとCISC"
date = 2014-10-17T23:28:00Z
updated = 2014-10-17T23:28:00Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">プロセッサを支える技術から、RISCとCISCについて整理。<br /><br />RISC（Reduced Instruction Set Computer）は固定長の単純な命令を実行する方式のコンピュータ。<br />CISC(Complex Instruction Set Computer)は可変長で命令体型が複雑なコンピュータ。<br /><br />RISCの命令は４バイト固定長。<br />メモリアクセスはロード命令、ストア命令という専用の命令を使う。<br />演算命令のオペランドはレジスタに限る。<br /><br />CISCはレジスタでもメモリでもオペランドとして使用できる。<br /><br />複雑な命令の処理はパイプライン処理は難しく、高機能の命令はコンパイラで有効に利用できない、等の問題点から固定長の命令を高速で実行できるプロセッサの方が高性能。<br /><br />ARM等のプロセッサはRISC方式の命令アーキテクチャを使用している。<br />Intel、AMDのx86プロセッサはCISC命令をRISCのような内部命令に変換してパイプライン実行を行っている。</div>
