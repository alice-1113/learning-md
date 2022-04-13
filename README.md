# 入門 C言語

## 目次

1. [注意事項](#注意事項)
1. [実行環境](#実行環境)
1. [C言語に触れてみよう](#c言語に触れてみよう)
1. [プログラムを実行してみよう](#プログラムを実行してみよう)
1. [main関数](#main関数)
1. [変数の宣言と初期化](#変数の宣言と初期化)
    1. [変数名の考え方](#変数名の考え方)
    1. [データの型（数値型）](#データの型数値)
    1. [算術演算子](#算術演算子)
1. [文字を表示する](#文字を表示する)
    1. [変数の出力](#変数の出力数値型)
1. [プリプロセッサについて](#プリプロセッサについて)
1. [コメントを書こう](#コメントを書こう)
1. [インデントを付けよう](#インデントを付けよう)
1. [入力を受け付けよう](#入力を受け付けよう)
1. [条件分岐(if)](#条件分岐if)
1. [関係演算子](#関係演算子)
1. [条件式](#条件式)
1. [ブロック](#ブロック)
1. [条件分岐(else)](#条件分岐else)
1. [条件分岐(else-if)](#条件分岐else-if)
1. [論理演算し](#論理演算子)
1. [条件分岐のネスト](#条件分岐のネスト)
1. [反復処理(for)](#反復処理for)
1. [インクリメント/デクリメント](#インクリメントデクリメント)
1. [反復処理(while)](#反復処理while)
1. [条件分岐(switch)](#条件分岐swicth)
1. [break](#break)
1. [continue](#continue)
1. [反復処理のネスト](#反復処理のネスト)
1. [反復処理(do-while)](#反復処理do-while)
1. [複合代入演算子](#複合代入演算子)

1. 巻末付録
    1. C言語のインストール
    1. WSL2のインストール
    1. コンパイル方法
    1. エラーの対処

1. 参考資料


## 注意事項



## 実行環境

[paiza.io](https://paiza.io/jp)というオンライン環境を用います。

必要に応じて、アカウントを登録してください。

ローカル環境で開発する場合は[巻末付録](#巻末付録)の[C言語のインストール](#c言語のインストール)を参照されたい。


## C言語に触れてみよう

**コード作成を試してみる（無料）** をクリックする。
![paiza-コード作成](paiza_io1.png)

コードエディターが開かれるので、左上にあるPHPの横の▼をクリックし、Cをクリックする。

![paiza-言語選択](paiza_io2.png)

以下のような画面になったら、C言語のプログラムを実行することができます。
![paiza-C言語](paiza_io3.png)

**実行**ボタン、もしくは`Ctrl-Enter`キーを押すことで実行できます。

## プログラムを実行してみよう

4行目に`printf("Hello, World!\n");`を追加してください。

プログラム
```c
#include <stdio.h>
int main(void){
    // Your code here!
    printf("Hello, World!\n");
}
```

その後、実行してみましょう。

![paiza-C言語実行](paiza_io4.png)

上記のように表示されたでしょうか。

実行されなかった人はプログラムをもう一度確認するか、上記のコードをコピーして貼り付けて実行してみてください。

## main関数

```c
int main(void) {
    ...
}
```

上記のコードを`main`関数と呼びます。

C言語では、この`main`関数がプログラム開始の起点となります。

現時点では、`int`や`void`などのことはわからなくても大丈夫です。

## 変数の宣言と初期化

プログラムには変数というものがあります。

変数はデータを格納する入れ物です。

変数の宣言は`int var;`のように記述します.

プログラム
```c
#include <stdio.h>
int main(void) {
    int var;
}
```

`int`はデータの型で、`var`が変数の名前になります。

それは例えば、以下の画像のようなことです。

![C言語-変数](var_image.png)

本を入れるbookという箱、おもちゃを入れるtoyという箱などをイメージしてみるとわかりやすいでしょう。（おそらく…）

宣言は、箱を用意しただけに過ぎません。

そこで、**初期化**を行なう必要があります。

初期化は`int var=0;`のように記述します。

プログラム
```c
#include <stdio.h>
int main(void) {
    int var=0;
}
```

宣言と初期化をまとめて、**定義**と呼びます。

### 変数名の考え方

変数の名前はどんな名前をつけてもいいです。

ですが、読みにくい名前は避けるべきです。


例えば、あなたは自分の子どもに「あああ」という名前をつけるでしょうか？

それに似ています。

変数名のプラクティス

例として、「消費税込みの金額」を入れる変数の名前を考えます。

+ 名詞を意識する
    ```
    bad: zeikomidayo
    nice: zeikomikakaku
    ```
+ ローマ字にしない
    ```
    bad: zeikomikakaku, ...
    nice: p, price
    ```
+ 短いよりも長い名前
    ```
    bad: p, pr, pri, prc, ...
    nice: price
    ```
+ 意味のある名前（必要な情報を入れる）
    ```
    bad: price, ...
    nice: priceIncludingConsumptionTax
    ```
+ 不要な単語は省く
    ```
    bad: priceIncludingConsumptionTax
    nice: priceIncludingTax
    ```


上記を守れば、それなりにわかりやすい変数名を考えることができると思います。

最初からすべて考慮しながら変数名を考えることは難しいと思うので、まずはローマ字にしない、意味のある名前にするなどを意識しながら考えるのがいいと思います。


### データの型（数値）

|型名|入るもの|具体的な値|
|:--:|:--:|:--:|
|int|整数| -1234, -1, 0, 1, 123, 4567など |
|double|実数(倍精度)| 3.1415など |
|float|実数(単精度)| 3.14など |

※何かしらの事情がない限りは`float`よりも`double`を使うべきです。

### 算術演算子

変数を使って計算をすることができます。

そのためには**算術演算子**が必要です。

以下にまとめます。

|演算子|名前|記述例|意味|
|:--:|:--:|:--:|:--:|
|+|加算|a+b|aにbを加える|
|-|減算|a-b|aからbを引く|
|\*|乗算|a\*b|aにbを掛ける|
|/|除算|a/b|aをbで割る|
|%|剰余|a%b|aをbで割った余り|

優先順位は数学等と同じで、`()`を用いることもできます。

ここまでで、簡単な計算をするプログラムを作成することができるようになったと思います。


## 文字を表示する

簡単な計算をするプログラムを書けるようになりましたが、それだけでは処理が（正常に）完了したかどうかわかりません。

そこで、画面に文字を表示させましょう。

文字を表示するには、`printf`関数を用います。

`printf`関数を使うには`#include <stdio.h>`という文が必要なので、なければ1行目に記述してください。

プログラム
```c
#include <stdio.h>

int main(void) {
    printf("Hello, World!");
}
```

このように使います。

`printf()`の`()`の中にダブルクォーテーション(`"`)でくくった出力したい文字を入力します。

プログラム
```c
#include <stdio.h>

int main(void) {
    printf("Hello, World!");
    printf("こんにちは、世界！");
    printf("出力される文字");
}
```

実行結果
```result: 実行結果
Hello, World!こんにちは、世界！出力される文字
```
上記のように表示されたかと思います。

改行するためには`\n`を出力したい文字に付け足す必要があります。

プログラム
```c
#include <stdio.h>

int main(void) {
    printf("Hello, World!\n");
    printf("こんにちは、世界！\n");
    printf("出力される文字\n");
}
```

実行結果
```result: 実行結果
Hello, World!
こんにちは、世界！
出力される文字
```

`\n`は**エスケープシーケンス文字**といって、出力する文字の制御をする特殊な文字列です。

`\n`には**改行**が割り当てられています。

### 変数の出力（数値型）

変数を出力してみましょう。

例として、税抜き価格と消費税から税込み価格を計算してそれを表示するプログラムを作成してみます。

プログラム
```c
#include <stdio.h>

int main(void) {
    double rawPrice = 100.0;
    double tax = 10.0;
    double priceIncludingTax = rawPrice + rawPrice * (tax/100);

    printf("税抜き価格: rawPrice\n");
    printf("消費税    : tax\n");
    printf("税込み価格: priceIncludingTax\n");
}
```

実行結果
```
税抜き価格: rawPrice
消費税    : tax
税込み価格: priceIncludingTax
```

変数の名前がそのまま出力されてしまいましたね。

変数の中身を出力したいときは、出力したい文字列の中に`%d`や`%lf`などを使って、`printf("税抜き価格: %lf\n", rawPrice);`のように記述します。

`%d`は整数型の変数を、`%lf`は実数型の変数を出力します。

先ほどのプログラムを書き換えてみましょう。

プログラム
```c
#include <stdio.h>

int main(void) {
    double rawPrice = 100.0;
    double tax = 10.0;
    double priceIncludingTax = rawPrice + rawPrice * (tax/100);

    printf("税抜き価格: %lf\n", rawPrice);
    printf("消費税    : %lf\n", tax);
    printf("税込み価格: %lf\n", priceIncludingTax);
}
```

実行結果
```
税抜き価格: 100.000000
消費税    : 10.000000
税込み価格: 110.000000
```

これで、思った通りに動いたと思います。

しかし、これでは見栄えが悪いのでフォーマットを揃えたいですね。

そうです、できちゃうんです。

`%(表示幅).(小数点以下の表示幅)lf`や`%(表示幅)d`のように記述します。


税抜き価格、税込み価格を小数点以下2桁で、消費税を表示幅3桁、小数点以下0桁で表示してみます。

プログラム
```c
#include <stdio.h>

int main(void) {
    double rawPrice = 100.0;
    double tax = 10.0;
    double priceIncludingTax = rawPrice + rawPrice * (tax/100);

    printf("税抜き価格: %.2lf\n", rawPrice);
    printf("消費税    : %3.0lf\n", tax);
    printf("税込み価格: %.2lf\n", priceIncludingTax);
}
```

実行結果
```
税抜き価格: 100.00
消費税    :  10
税込み価格: 110.00
```

良い感じになりましたね。

色々試してみると面白いかもしれません。

## プリプロセッサについて

プリプロセッサとは、`#include <stdio.h>`のことです。
※この表現は正確ではありません。


`stdio.h`というヘッダーファイルを読み込んでいます。

`stdio.h`は`standard input/output`の略で標準入出力の関数が定義されているファイルです。

このファイルを読み込むことで、`printf`関数や後述する`scanf`関数を使うことができるようになります。


## コメントを書こう

コメントは、プログラム中に書くメモ書きや注意などのことです。
適切に書くことで、他人にわかりやすいプログラムにすることができます。

`//`で一行コメント、`/* */`で複数行コメントを記述できます。

プログラム
```c
#include <stdio.h>

int main(void) {
    // rawPrice 税抜き価格
    double rawPrice = 100.0;
    // tax 消費税
    double tax = 10.0;
    // priceIncludingTax 税込み価格
    double priceIncludingTax = rawPrice + rawPrice * (tax/100);

    printf("税抜き価格: %lf\n", rawPrice);
    printf("消費税    : %lf\n", tax);
    printf("税込み価格: %lf\n", priceIncludingTax);
}
```

このように記述します。

コメントのプラクティス
+ 自明なことは書かない
+ なぜそのコードにしたのか、する必要があったのかを書く

上記を踏まえてもう一度プログラムを書き直すと以下のようになるでしょう。

プログラム
```c
#include <stdio.h>

int main(void) {
    double rawPrice = 100.0;
    double tax = 10.0;  // 消費税 %形式
    // 消費税を小数点形式に変換して計算する
    double priceIncludingTax = rawPrice + rawPrice * (tax/100);

    printf("税抜き価格: %lf\n", rawPrice);
    printf("消費税    : %lf\n", tax);
    printf("税込み価格: %lf\n", priceIncludingTax);
}
```

## インデントを付けよう

インデントは、プログラムを読みやすくするために使います。
C言語のインデントには、タブが使われていることが多いですが、半角スペース（2つまたは4つ）でも大丈夫です。

慣れないうちは、`{}`の中ごとにインデントを増やしていくといいと思います。

下記画像の白丸部分がインデントに当たります。
![インデントサンプル](indent_image.png)


## 入力を受け付けよう

入力を受け付けるには、`scanf`関数を用います。

`scanf`関数は`scanf(指定子, &変数名);`のように記述します。

指定子は、`%d`や`%lf`などを使います。

変数名の前に`&`が必要なので、忘れないようにしましょう。

プログラム
```c
#include <stdio.h>

int main(void) {
    double rawPrice = 100.0;
    double tax = 10.0;
    scanf("%lf", &tax);
    double priceIncludingTax = rawPrice + rawPrice * (tax/100);

    printf("税抜き価格: %lf\n", rawPrice);
    printf("消費税    : %lf\n", tax);
    printf("税込み価格: %lf\n", priceIncludingTax);
}
```

[paiza.io](https://paiza.io/jp)では、以下の「入力」の欄に入力します。

![paiza.io 入力サンプル](paiza_io5.png)


以下の画像のようにすると実行することができます。

![paiza.io 入力サンプル2](paiza_io6.png)

実行結果
```result: 実行結果
税抜き価格: 100.000000
消費税    : 8.000000
税込み価格: 108.000000
```

`8`を入力したので、消費税を**10**%から**8**%にすることができました。

## 変数に代入しよう

変数の値を途中で変えたいこと、ありますよね。

そのときは、**代入**をします。

`var = 10;`のように記述します。

実は、変数の初期化は宣言と代入だったのです。

プログラム
```c
#include <stdio.h>

int main(void) {
    int var = 10;
    printf("var = %d\n", var);
    var = 20;
    printf("var = %d\n", var);
}
```

実行結果
```result: 実行結果
var = 10
var = 20
```

## 条件分岐(if)

例えば、ある値が一定値を超えたらある処理をしたいという場面がありますよね。

そういうときに条件分岐(`if`)が使えます。

`if (条件式) { ある処理 } `のように記述します。

実際に

プログラム
```c
#include <stdio.h>

int main(void) {
    int temperature = 25;

    if (temperature >= 25) {
        printf("It is warm today!\n");
    }

    printf("Hello World!\n");
}
```

実行結果
```
It is warm today!
Hello World!
```

プログラム
```c
#include <stdio.h>

int main(void) {
    int temperature = 15;

    if (temperature >= 25) {
        printf("It is warm today!\n");
    }

    printf("Hello World!\n");
}
```

実行結果
```
Hello World!
```

上記のように記述します。


## 関係演算子

関係演算子とは、一致・不一致や大小の比較を行なうための演算子です。

比較演算子とも言います。

結果を真偽値(true/false)で返します。

関係演算子を以下にまとめます。

|演算子|記述例|意味|
|:--:|:--:|:--:|
| == | a == b | aとbが同じか|
| != | a != b | aとbが異なるか|
| <  | a < b  | aがbより小さいか|
| >  | a > b  | aがbより大きいか|
| <= | a <= b | aがb以下か|
| >= | a>=b   | aがb以上か|

先ほどのプログラム中の`temperature >= 25`は **temperatureが25以上かどうか?** ということだったのです。

## 条件式

`if`文のところにも出てきました。

条件式は値や式の比較などを組み合わせたものです。

`if`文のほかに後述する`while`文や`switch`文などに使います。

## ブロック

ブロックは、`if`文や`while`文などの**スコープ**を表します。

スコープとは範囲のことで、`if`や`while`の処理の範囲と捉えて大丈夫です。

ブロックは`{ ... }`と記述します。

プログラム
```c
#include <stdio.h>

int main(void) {
    int tempareture = 25;

    if (tempareture >= 25) {
        // if文のブロック(スコープ)
        printf("It is warm today!\n");
    }
}
```

## 条件分岐(else)

さて、`if`での条件分岐はできるようになりましたが、
それ以外の時の処理をしたい場合はどうすればいいのでしょうか？

`if`の後ろに`else`という文をつなぎます。
`(if { ... }) else { ... }`と記述します。

プログラム
```c
#include <stdio.h>

int main(void) {
    int tempareture = 25;

    if (tempareture >= 25) {
        printf("It is warm today!\n");
    } else {
        printf("It is comfortable today!\n");
    }

    printf("Hello World!\n");
}
```

実行結果
```result: 実行結果
It is warm today!
Hello World!
```

プログラム
```c
#include <stdio.h>

int main(void) {
    int tempareture = 20;

    if (tempareture >= 25) {
        printf("It is warm today!\n");
    } else {
        printf("It is comfortable today!\n");
    }

    printf("Hello World!\n");
}
```

実行結果
```result: 実行結果
It is comfortable today!
Hello World!
```

このように、`if`の条件に合うときは`if`のブロックが、そうでないときに`else`のブロックの処理を行ないます。

## 条件分岐(else-if)

## 論理演算子

## 条件分岐のネスト

## 反復処理(for)

## インクリメント/デクリメント

## 反復処理(while)

## 条件分岐(swicth)

## break

## continue

## 反復処理のネスト

## 反復処理(do-while)

## 複合代入演算子


## 巻末付録

### C言語のインストール

### WSL2のインストール

### コンパイル方法

### エラーの対処


## 参考資料
