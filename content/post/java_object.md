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
- privateにはできないが、publicにしないことはできる
    - その場合、同じパッケージに属するクラスしか継承できないようになる
- final指定することで継承させないことができる
    - 勝手にメソッドの機能を書き換えさせたくない場合
    - 例えばStringクラスはfinalになっている
  
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
- インスタンス変数はクラスの中で宣言する
- ローカル変数はメソッドの中で宣言する
- インスタンス変数は初期化をしない場合、以下のデフォルト値が代入される　
    - int 0
    - float 0.0
    - boolean false
    - 参照型 null
- ローカル変数は利用する前に初期化が必要


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

## 型変換

```
Integer.parseInt("3");
```

## キャスト
```
log y = 42;
int x = (int)y;
```

## ArrayList
- 通常の配列と異なり、宣言時にサイズを決めなくても良い

```
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
 
public class ArrayListTest {
 
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();
 
        list.add(1);
        list.add(5);
        list.add(2);
        list.add(8);
        
        //size
        int theSize = list.size();
        System.out.println(theSize);
        
        //contain
        boolean isIn = list.contains(8);
        System.out.println(isIn);

        // index
        int idx = list.indexOf(1);
        System.out.println(idx);

        // check empty
        boolean empty = list.isEmpty();
        System.out.println(empty);
        
        list.remove(2);

        for(Iterator it = list.iterator(); it.hasNext();) {
            System.out.println(it.next());
        }
    }
}
```

## Java APIライブラリの使用
- java.langは例外的に指定しなくてもよい
    - String、Mathなど
- 標準拡張パッケージはjavax(今は標準パッケージと変わらないほど一般的になったものもあるが、慣例として分かれている)
- インポートはCのインクルードとは異なり、フルネームを逐一タイプする手間を省くもの


## 継承
- クラスのメソッドやインスタンス変数を引き継ぐ
- 元のクラスをスーパークラス、引き継いだクラスをサブクラスと呼ぶ
- メリット
    - コードの重複を減らす
    - 複数のクラスに共通のプロトコルを適用する（ポリモーフィズムも利用できる）
- Parsonクラスを引き継ぐJapaneseクラス
- Japanese is a Parson, Parson has a Japanseという関係になる
- privateを指定されたメンバは継承できない
- 継承する際の判断ポイント
    - 新たに作るクラスは、元のクラスよりも具体的なものでなくてはならない
    - 機能のかなりの部分が共通している同種のクラスを複数作る必要がある時に利用する
    - 再利用の目的だけで継承しない（例えば、同種でなければ継承するべきではない）
    - is a関係にする

```
public class FamilyDocter extends Doctor{
    void giveAdvice(){
    }
}
```

## ポリモーフィズム
- 非常にシンプルかつフレキシブルで、効率的なコードが書けるようになる
- プログラムにサブクラスが追加されても、コードを修正する必要はない

```
Animal [] animals = new Animal [5];
animals[0] = new Dog();
animals[1] = new Cat();
animals[2] = new Wolf();
animals[3] = new Hippo();
animals[4] = new Lion();

for(int i=0; i<animals.length; i++){
    animals[i].eat();
    animals[i].roam();
}
```

##　オーバーライド
- サブクラスでスーパークラスのメソッドを書き換える
- final指定されているメソッドはオーバーライドできない
- オーバーライド時にアクセスレベルを下げてはいけない
- 引数の型は変えてはいけない

## オーバーロード
- 名前が同じで指定できる引数の異なるメソッドを作ることができる
- 戻り値の型を変えることができる
- 戻り値の型だけを変えることはできない
-　アクセスレベルは上げることも下げることもできる

```
public class OverLoads{
    public int addNums(int a, int b){
    }
    
    public double addNums(double a, double b){
    }
}
```

##　抽象クラス
- インスタンス化させたくないクラス
- 例
    - それ自体は使わないスーパークラスなど

```
abstract class Canine{
    public void roam(){}
}
```

## 抽象メソッド
- サブクラスで必ずオーバーライドしなくてはいけない
- より具体性の高い下位のクラスに持たせるべきメソッドに適用する
- 抽象メソッドには本体がない
- １つでも抽象メソッドを含むクラスは、抽象クラスにしなければいけない

## Objectクラス
- JavaのクラスはすべてObjectクラスを継承したもの
- 明示的に何かのクラスを継承していないクラスは、自動的にObjectを直接継承しているとみなされる
- 持つメソッド
    - `equals`, `getClass()`, `hashCode()`, `toString()`
- Objectクラスに代入すると、元のクラスのメソッドは使えない


```
public abstract void eat();
```

## Objectクラスの型を元に戻す

```
Object o = al.get(index);
if(d instanceof Dog){
    Dog d = (Dog)o;
    d.roam();
}
```

## 多重継承
- 2つ以上のクラスを継承すること
- 例えばダイアモンド継承は、大きな問題を引き起こす
    - DigitalRecoderスーパークラスは、burn()メソッドをもつ
    - サブクラスCDBurner, DVDBurnerはburn()をオーバーライドする
    - CDBurner, DVDBurnerを継承したサブクラスComboDriveは、どちらのburnが実行されるかわからない
- Javaでは多重継承はできない
- 代わりにインタフェースを使う

## インタフェース
- 完全な抽象クラスと呼ぶべきようなもの
- インタフェース中のメソッドはすべて抽象メソッド
- インタフェースはあらゆるクラスでインプリメントできる
- 1つのクラスで複数のインタフェースをインプリメントすることもできる


Pet.java
```
public interface Pet{
    public abstract void beFriendly();
    public abstract void play();
}
```

Dog.java
```
public class Dog extends Canine implements Pet{
    public void beFriendly(){}
    public void play(){}
}
```

## スーパークラスのメソッドを利用

```
super.runReport();
```

hoge
