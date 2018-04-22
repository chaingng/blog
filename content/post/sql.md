---
title: "SQLの基礎"
date: 2018-01-15T10:00:00+09:00
tags: [ "algorithm"]
---

## SQLの実行順序
1. FROM
1. WHERE
1. GROUP BY
1. HAVING
1. SELECT
1. ORDER_GY

## DBの作成
```
CREATE DATABASE shop;
```

## テーブルの作成
```
CREATE TABLE Shohin 
(shohin_id CHAR(4) NOT NULL, 
shohin_mei VARCHAR(100) NOT NULL;
PRIMARY KEY (shohin_id)
); 
```

### DEFAULT制約をつければデフォルト値を入れられる
```
hanbai_tanka INTEGER DEFAULT 0
```

## テーブルの削除
```
DROP TABLE Shohin;
```

## テーブル定義の変更
```
ALTER TABLE ADD COLUMN shohin_mei;
ALTER TABLE DROP COLUMN shohin_mei;
```

## データの型
### CHAR
- 固定長文字列
- CHAR(10)と指定したら最後に空白を埋めて必ず１０文字になる

### VARCHAR　
- 可変長文字列

## SELECT
```
SELECT shohin_id, shohin_mei
    FROM Shohin;
```

### 全ての行を出力
```
SELECT * 
    FROM Shohin;
```

### 別名をつける
```
SELECT shohin_id AS id
    FROM Shohin;
```

### 定数をselect
```
SELECT shohin_id AS id, “2009-02-04” AS hizuke
    FROM Shohin;
```

### 重複を省く
```
SELECT DISTINCT shohin_id 
    FROM Shohin;
```

## WHERE
```
SELECT shohin_mei, shohin_bunrui
    FROM Shohin
WHERE shohin_bunrui = ‘衣服';
```

## 算術演算
`+,-,*,/`
```
SELECT shohin_mei, hanbai_tanka * 2, 
    FROM Shohin;
```
NULLを含むと結果はNULLになる

## 比較演算
### 等しくない場合　
```
SELECT shohin_mei, shohin_bunrui
    FROM Shohin
WHERE hanbai_tanka <> 500;
```
NULLは比較演算子は使えない

### NULLを調べる
```
SELECT shohin_mei, shohin_bunrui
    FROM Shohin
WHERE hanbai_tanka IS NULL;
```
逆は`IS NOT NULL`

## COUNT
### テーブルの全行数を数える
```
SELECT COUNT(*)
    FROM Shohin;
```

### NULLを除外した行数を数える
```
SELECT COUNT(shiire_tanka)
    FROM Shohin;
```

## SUM
```
SELECT SUM(hanbai_tanka)
    FROM Shohin;
```
NULLは無視される

## GROUP BY
列名で集約できる
```
SELECT shohin_bunrui, COUNT(*)
    FROM Shohin
GROUP BY shohin_bunrui;
```

- このときのshohin_bunruiを集約キー
- NULLのグループがあればそれも１つとして表示される

### 注意事項
- SELECTに定数、集約関数、集約キー以外を指定するとエラーになる
- 集約キーにSELECTの別名を使うとエラーになる（SELECTはGROUPBYより後に実行される）

## HAVING
GROUPBYの結果に対して条件指定したいときに使う
（WHEREはGROUPBYの前に実行されるため）

```
SELECT shohin_bunrui, COUNT(*)
    FROM Shohin
GROUP BY shohin_bunrui
HAVING COUNT(*) = 2;
```
指定できるのは定数＆集約関数＆集約キーのみ

## ORDER BY
検索結果の並び替え
```
SELECT shohin_id, hanbai_tanka
    FROM Shohin
ORDER BY hanbai_tanka;
```

NULLは先頭か末尾にまとめて表示される

### 降順に並び替え
```
ORDER BY hanbai_tanka DESC;
```

### 複数指定も可能
```
ORDER BY hanbai_tanka, shohin_id;
```

## INSERT
```
INSERT INTO ShohinIns (shohin_id, shohin_mei) VALUES (‘0001’, ’Tシャツ’);
```

- 全ての列に対してINSERTを行う場合は列リストは省略できる
- NULLを入れたい場合はNULLを明示する
- 明示的に`DEFAULT`と書くとデフォルト値が挿入される

### コピーの書き方
INSERT SELECT
```
INSERT INTO ShohinCopy (shohin_id, shohin_mei)
SELECT shohin_id, shohin_mei
    FROM Shohin;
```

## DELETE
### 全てのデータを削除
```
DELETE FROM Shohin;
```

### 条件指定で削除
```
DELETE FROM Shohin
    WHERE hanbai_tanka >= 4000;
```

## UPDATE
### 全てのレコードの列を変更
```
UPDATE Shohin
    SET torokubi = ‘2009-10-10'
```

複数列の更新も可能

### 条件に一致する行のみ変更
```
UPDATE Shohin
    SET torokubi = ‘2009-10-10’
WHERE shohin_bunrui = ‘キッチン用品'
```

## トランザクション
DBに対する１つ以上の更新をまとめて呼ぶときの名称

```
START TRANSACTION;
-- update文等
COMMIT;
```

トランザクションが暗黙に開始される設定もある（標準SQL規格で定められている）

### ROLLBACK
処理の取り消し
```
BEGIN TRANSACTION;
-— update
ROLLBACK;
```

### ACID特性を持つ
#### 原子性(Acid)
トランザクションが終わったとき、更新処理はすべて実行されるか１つも実行されないか

#### 一貫性(Consistency)
トランザクションに含まれる処理は、DB制約を満たす。満たさなければロールバックされる

#### 独立性(Isolation)
トランザクション同士が互いに干渉を受けない
あるトランザクションの実行内容は、コミットされるまで外からは隠蔽される

#### 永続性(Durability)
トランザクションが終了したときにはデータが保存されることを保証する
障害が発生してもログから復旧できる

## ビュー
- SQLの観点から見るとテーブルと同じ
- ただし実際のデータは保存していない
- ビューが保存しているのはSELECT文
- 実際のデータを保存しなくてよいので容量が節約できる

```
CREATE VIEW ShohinSum (shohin_bunrui, cnt_shohin)
AS
SELECT shohin_bunrui, COUNT(*)
    FROM Shohin
GROUP BY shohin_bunrui;
```

その後、ビュー名はテーブル名の用に使える
```
SELECT shohin_bunrui
    FROM ShohinSum;
```

### 注意事項
- ORDERBYは使えない（行には順序がないため）
- 条件を満たしたときのみビューに対して更新が可能
- SELECTにDISTINCTが含まれない
- FROMに含まれるテーブルが１つ
- GROUPBY、HAVINGを使っていない

### ビューの削除
```
DROP VIEW ShohinSum;
```

## サブクエリ
- 使い捨てのビュー
- ビュー定義のSELECT分をそのままFROMに持ち込んだもの

```
SELECT shohin_bunrui
    FROM (SELECT shohin_bunrui, COUNT(*)
        FROM Shohin
        GROUP BY shohin_bunrui) AS ShohinSum;
```

## スカラ・サブクエリ
- 必ず１行１列だけの戻り値を返す
- つまり、この結果を＝や＜＞などに使うこと
- 定数や列名を書けるところすべてに使える

```
SELECT shihin_id
    FROM Shohin
WHERE hanbai_tanka > (SELECT AVG(hanbai_tanka) FROM Shohin);   
```

## 相関サブクエリ
小分けにしたグループ内での比較をするときに使う
```
SELECT shohin_bunrui, shohin_mei
    FROM Shohin AS S1
WHERE hanbai_tanka > (SELECT AVG(hanbai_tanka) 
                        FROM Shohin AS S2
                        WHERE S1.shohin.bunrui = S2.shohin_bunrui
                        GROUP BY shohin_bunrui);
```

## 型変換
```
CAST（’0001’ AS INTEGER)
```

## NULLを値に変換
```
COALESCE(str1, str2, ...)
```

## 文字連結
str1str2を返す
```
str1 || str2  
```

## LIKE
部分一致
```
WHERE str LIKE ‘ddd%’;
WHERE str LIKE ‘%ddd%’;
WHERE str LIKE ‘%ddd’;
```

## IN
含むかどうか
```
WHERE shiire_tanka IN (320, 500, 5000);
```

## EXISTS
- 常に相関サブクエリを引数にとる
- レコードの存在有無しか見ないため、SELECTでどんな列が返されるか気にしない
- `SELECT　*`と書くのは慣習
-TRUEかFALSEだけ返す

```
SELECT shohin_mei
    FROM Shohin AS S
WHERE EXISTS (SELECT * 
                FROM TenpoShohinn AS TS
                WHERE TS.tenpo_id = ‘00C’ AND TS.shohin_id = S.shohin_id);
```

## CASE
```
SELECT shohin_mei, 
    CASE WHEN shohin_bunrui = ‘衣服’
        THEN ‘A:’ || shohin_bunrui
        WHEN shohin_bunrui = ‘事務用品’
        THEN ‘B:’ || shohin_bunrui
        ELSE NULL
    END AS shohin_bunrui
FROM Shohin;
```

## UNION
行の結合
```
SELECT shohin_id, shohin_mei
    FROM Shohin
UNION
SELECT shohin_id, shohin_mei
    FROM Shohin2;
```
重複行は削除される

### 注意事項
- レコードの列数は同じであること
- 対象列のデータ型が一致していること
- ORDER BYは最後に１つだけ

### 重複行を残す
```
SELECT shohin_id, shohin_mei
    FROM Shohin
UNION ALL
SELECT shohin_id, shohin_mei
    FROM Shohin2;
```

## INTERSECT
テーブルの共通部分の行選択
```
SELECT shohin_id, shohin_mei
    FROM Shohin
INTERSECT
SELECT shohin_id, shohin_mei
    FROM Shohin2;
```

## EXCEPT
行の引き算
```
SELECT shohin_id, shohin_mei
    FROM Shohin
EXCEPT
SELECT shohin_id, shohin_mei
    FROM Shohin2;
```

- ShohinテーブルからShohin2テーブルのレコードを引いた残りになる
- ベン図の引き算と同じ

## INNER　JOIN
- JOINは列の結合
- INNER JOINは両方に存在するレコードのみ出力される

```
SELECT TS.tenpo_id, TS.tenpo_mei, TS.shohin_id, S.shohin_mei, S.hanbai_tanka
    FROM TenpoShohin AS TS INNER JOIN Shohin AS S
        ON TS.shohin_id = S.shohin_id;
```

最後にWHEREを書いて、表示レコードに条件をつけることもできる

## OUTER JOIN
- 片方のみに存在するレコードも出力される
- OUTERは元のテーブルにない情報を結果に持ってくる、という意味

```
SELECT TS.tenpo_id, TS.tenpo_mei, TS.shohin_id, S.shohin_mei, S.hanbai_tanka
    FROM TenpoShohin AS TS RIGHT OUTER JOIN Shohin AS S
        ON TS.shohin_id = S.shohin_id;
    FROM Shohin
```

マスターにする方をLEFTもしくはRIGHTで指定できる

### 3つ以上のテーブルを内部結合する

```
SELECT TS.tenpo_id, TS.tenpo_mei, TS.shohin_id, S.shohin_mei, S.hanbai_tanka, ZS.zaiko_suryo
    FROM TenpoShohin AS TS INNER JOIN Shohin AS S
        ON TS.shohin_id = S.shohin_id;
            INNER JOIN ZaikoShohin AS ZS
                ON TS.shohin_id = ZS.shohin_id
```

## CROSS JOIN
- レコードのすべての組み合わせを作る
- すべての結合演算の基礎
```
SELECT TS.tenpo_id, TS.tenpo_mei, TS.shohin_id, S.shohin_mei, S.hanbai_tanka
    FROM TenpoShohin AS TS CROSS JOIN Shohin AS S;
```

つまり、集合演算の掛け算がこれにあたる

