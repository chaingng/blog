---
title: "Javaとオブジェクト指向"
date: 2017-11-19T10:00:00+09:00
tags: [ "computer science"]
---

## javaファイルの作成と実行
MyFirstApp.java
```
public class MyFirstApp{
    public static void main(String [] args){
        System.out.println("Hello World!");
    }
}
```

```
$javac MyFirstApp.java
$java MyFirstApp
Hello World!
```

## JVMとコンパイラ
### JVM
- プログラムを動かす
– インタープリタ方式で逐次解釈・実行

### コンパイラ
- クラスファイルの作成(バイトコード)
- 構文チェック

## オブジェクト指向のメリット
- 実際の物事の動きをそのままプログラムに置き換えることができるので、プログラムの設計がしやすい
- 機能を追加するときに、既存のコードへの影響がないのがいい
- データとそれを操作するメソッドを１つのファイルにまとめることができるので便利
- すでに作ったクラスを再利用できる、継承して機能を追加するということも簡単

##　クラス
- インスタンス変数とメソッドを持つ
- インスタンス変数
  - オブジェクトごとに持つ変数
  - クラスのステート（状態）
- メソッド
  - オブジェクトが継承し実行できる関数
  - クラスの機能
- インスタンス化することでオブジェクトが作成できる
  - クラスはオブジェクトの設計図
- javaのプログラムはクラスの集まり
- クラスが膨大になったら.jarファイルにまとめることができる
  
## クラスの作成と使用
Dog.java
```
class Dog{
    int size;
    String breed;
    String name;
    void bark(){
        System.out.println("Ruff!Ruff!");
    }
}
```

DogTestDrive.java
```
class DogTestDrive{
    public static void main(String [] args){
        Dog d = new Dog();
        d.size = 40;
        d.bark();
    }
}
```

## 変数
- 大きく分けて、プリミティブ型（整数など）と参照型）（オブジェクトの参照）の２種類がある
- 変数に代入されるのは、オブジェクトそのものではなく、オブジェクトへの参照

## オブジェクトリファレンス
- 同じクラスの変数は再代入可能
- final宣言していると再代入不可
- nullを入れると参照がなくなる
- 参照がなくなったオブジェクトはガーベジコレクションされる

## 配列
- 配列自身は常にオブジェクト

```
Dog [] pets = new Dog[7];
Dog[0].name = 'Fido';
Dog[0].bark();
```

## カプセル化
- データ（インスタンス変数の値）の保護
  - 想定外の値にならないようにする。例えば負の値は許さない、など
- 外からはgetter,setterでのみしか扱えないようにする

GoodDog.java
```
class GoodDog{
    private int size;
    public int getSize(){
        return size;
    }

    public void setSize(int s){
        size = s;
    }

    void bark(){
        if(size > 60){
            System.out.println("Woof!");
        }else{
            System.out.println("Yip!");
        }
    }
}
```


GoodDogTestDrive.java
```
class GoodDogTestDrive{
    public static void main(String [] args){
        GoodDog one = new GoodDog();
        one.setSize(70);
        one.bark();

        GoodDog two = new GoodDog();
        two.setSize(10);
        two.bark();
    }
}
```

hoge
