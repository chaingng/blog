---
title: "文字コードとは"
date: 2018-02-01T10:00:00+09:00
tags: [ "technology"]
---

## 文字コード
広義では、文字にバイト表現を割り当て、その対応表を文字コードと呼ぶ


## 文字集合と符号化方式
- 文字コードは文字集合(ccs)と符号化方式(ces)の組み合わせからなる
- 文字集合１つに対して符号化方式が複数存在するもの（Unicode文字集合に対してUTF-8、UTF-16エンコーディング）がある
- 符号化方式１つに対して複数の文字集合が存在するもの（EUCエンコーディングに対してEUC-JP,EUC-KRなど）もある
- また、複数の文字集合＆符号化方式がセット（コードセットと呼ぶ）になる文字コードも存在する（「ASCII」＋「JIS X 0208をEUCで符号化」のセットであるEUC-JPなど）


## ISO/IEC 646
- ASCII7ビット文字コードの国際規格
- 拡張記号部分は国によって異なる
- ヨーロッパではISO/IEC 8859が主流で、こちらはあまり使われていない

## ISO/IEC 8859
- 8ビット文字コード
- ヨーロッパではこちらが主流
- 複数のマッピング、ISO-8859-nがある

## Unicode
- 文字集合（文字セット）が単一の大規模文字セット
- 世界で使われる全ての文字を共通の文字集合にて利用できるようにしようという考え
- 日本の文字については当初より JIS X 0201、JIS X 0208 と補助漢字を、Unicode 3.1 では JIS X 0213 の内容も収録

### UTF-8
* 可変長（1-4バイト）の8ビット符号単位で表現
* ASCIIに対して上位互換
* UTF-8であることが識別できるよう、データストリームの先頭に EF BB BF（U+FEFFのUTF-8での表現）の3バイトが付与されることがある

### UTF-16
* BMP文字を16ビット符号単位一つで、その他の文字をサロゲートペア（代用対）という仕組みを使い16ビット符号単位二つで表現
* 通常はファイルの先頭にバイト順マーク (BOM) が付与される。
* BOMとは、通信やファイルの読み書き等、8ビット単位の処理でバイト順を識別するための印であり、データストリームの先頭に付与される。値はU+FEFF

### UTF-32
* Unicodeのすべての符号位置を単一長の符号単位として32ビットで表現する文字符号化形式及び文字符号化スキーム
* 実際に使われるのは21ビット（Unicodeの符号空間がU+10FFFFまでであるため）であり、この21ビットの範囲内ではUCS-4と互換性がある

## ISO/IEC 10646
* UCSと呼ぶ
* Unicodeと概ね互換
* 日本の対応規格はJIS X 0221（国際符号化文字集合）
* 符号化方式はUTF-8やUTF-16が使われることが多い
* BMPにUnicodeをそっくり入れてその他の群・面は未使用という、実質2オクテットの符号

## Shift-JIS
* 現在のJIS X 0201の8ビット符号と、現在のJIS X 0208の両文字集合を表現しようとしたもの
* パソコンではすでに、JIS X 0201の8ビット符号、つまりGLに英数字、GRに1バイトカタカナ（半角カタカナ）を割り当てた符号が普及していた。英数字と1バイトカタカナの2つを動かすことは、文字化けの原因になるため避ける必要があった。そのため、ISO 2022の枠内の領域に漢字を混在させることは困難だった。1982年、漢字の符号位置を複雑に移動（シフト）し、符号空間の隙間に押し込むShift_JISが誕生
* JIS X 0208の文字集合を利用してはいるものの、ISO 2022の符号化の方針の範囲の外にある
* しかし現在では、JIS X 0208:1997の附属書1に、「シフト符号化表現」という名前で仕様が定義されている

## EUC
* Extended Unix Code(EUC)
* UNIX上で使われてきた文字コードの符号化方式

## EUC-JP
* UNIX上で日本語の文字を扱う場合にもっとも多く利用されている文字コード（符号化方式）のひとつ
* EUCのエンコード方式上にASCIIとJIS X 0208文字集合を配置したもので、半角カナ (JIS X 0201) とJIS補助漢字 (JIS X 0212) もオプションで含むことができる
* 半角カナと補助漢字を使用しない場合は、JIS X 0208で規定されている符号化方式「国際基準版・漢字用8ビット符号」と同一となる。ISO/IEC 2022に適合する
* JIS X 201 カタカナとJIS X 212 補助漢字は実装が必須ではないとされていた。このため、特にJIS X 0212は実装されていないことも多い。通信などで用いる場合はこの点に注意が必要である
* 日本語文字はJIS X 0208をGR領域に表現したものを基本としており、2バイトで表現され、1バイト目、2バイト目ともに0x80 - 0xFFの範囲内にある。このため英数字と日本語文字の区別がしやすく、プログラム上での扱いが楽である。ただし、半角カナはISO-2022-JPやShift_JISと異なり制御文字SS2（シングルシフトツー、0x8E）に続けて現れるので都合2バイト、補助漢字は制御文字SS3（シングルシフトスリー、0x8F）に続けて現れるので都合3バイトを要する
* EUC-JPには亜種が存在する（.eucJP-msとCP51932）

## 日本工業規格 (JIS) の制定している文字コード規格

### JIS X 0201
- 英数字・半角カナの文字集合
- 7ビット及び8ビット
- 図形文字の集合を規定するための規格であり、JIS X 0211 (ISO/IEC 6429) で規定される制御文字集合と組み合わせて使用
- ラテン文字用図形文字集合と片仮名用図形文字集合のふたつの文字集合よりなっている

### JIS X 0202
- 国際規格ISO/IEC 2022に対応
- 文字集合を7ビット符号または8ビット符号で表現するための技術、および複数の文字集合を単一の文字符号化方式に含める技術
- 日本語文字集合における文字コードはISO-2022JP
  - JISコードとも呼ばれる
  - 日本語メールに使われる
  - 文字集合としてJIS X 0211のC0集合（制御文字）、JIS X 0201のラテン文字集合、ISO 646の国際基準版図形文字、JIS X 0208の1978年版 (JIS C 6226-1978) と1983年および1990年版が利用できる。JIS X 0201の片仮名文字集合は利用できない。

### JIS X 0208
- 基本漢字の文字集合
- 2バイト
- 日本語表記、地名、人名などで用いられる6,879図形文字を含む

### JIS X 021２
- 情報交換用漢字符号－補助漢字
- JIS X 0208にない文字を集めた文字集合

### JIS X 0213
- 7ビット及び8ビットの2バイト情報交換用符号化拡張漢字集合
- JIS X 0208を拡張した規格で、JIS X 0208が規定する6879字の図形文字の集合に対して、日本語の文字コードで運用する必要性の高い4354字が追加され、計1万1233字の図形文字を規定
JIS X 0212とJIS X 0213との間に互換性はない


## Basic Multilingual Plane, BMP
- 最初の65536の符号位置である000016～FFFF16からなる
- 最もよく使う、基本的な文字・記号のほとんどが含まれる
- BMPの符号位置は、UTF-16やUTF-8では、他の面より少ないオクテット（バイト）数で符号化される。
  * UTF-8では、1〜3オクテットで符号化される。
  * UTF-16では、2オクテットで符号化される。サロゲートペア（代用対）は必要がないため使われない。
  * UTF-32では、他の面と同様、4オクテットで符号化される。

## サロゲートペア
- BMPと呼ばれる当初の構想では、Unicodeは16ビット固定長で、216 = 65,536 個の符号位置に必要な全ての文字を収録するものであった
- そこからの、中国、日本、台湾、ベトナム、シンガポールの追加漢字約1万5千字、古ハングル約5千字、未登録言語の文字などが拡張された
- それまでの16ビットを前提としたシステム（たとえばJavaのchar型や、Windows NT・Windows 95のAPI）をなるべくそのままにしたまま、広げられた空間にある符号位置を表現する方法
- 16ビットUnicodeの領域1024文字分を2つ使い（前半 U+D800 〜 U+DBFF、後半 U+DC00 〜 U+DFFF）、各々1個ずつからなるペアで1024 × 1024 = 1,048,576文字を表す
