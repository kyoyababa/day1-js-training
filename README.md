#day1

##JavaScriptとは何か
* ウェブブラウザではHTMLや画像を表示することしかできなかったが、JavaScriptでプログラムを実行することで様々な描画が行えるようになった
* JavaとJavaScriptはまったくの別物なので、JavaScriptをJavaとは略さないように

##変数について - p.26
* var による変数宣言、省略の仕方
* 変数への文字列値、数値の代入
* 定義した変数の変換（加減乗除など）
* 定義されていない変数の扱い

##定数について - p.28
* 定数の取り扱い

##関数について - p.29
* function を使った関数の定義、return の仕方
* 関数リテラル
* 無名関数、関数名を持った関数 - いずれも var で定義できる

##オブジェクトについて - p.32
* プロパティ（名前と値）の集合としてのオブジェクト
* オブジェクトリテラルとして定義
* 識別子、文字列値、数値などからプロパティを定義できる
* オブジェクトであるプロパティ値には foo.bar のようにドットで連結し演算できる
* プロパティへのアクセスはブラケット[]演算子でも可能

##new式　- p.35
* オブジェクトを明示的に生成する場合は new 式を用いる
``` javascript
new Date();
new Object();
```

##配列 - p.37
* 順序を持った値のまとまりを Array クラスのインスタンスとして定義し、演算や取り出しが可能
``` javascript
var array = [1,2,3,4,5];
```
* arr[] 型で任意の値を取り出すことができる

##文字列型 - p.41
* エスケープシーケンスについて知る
* 演算結果は連結となる
* 数値と同様、Unicode準拠で比較ができる
* String.prototype オブジェクトのプロパティを使って様々な操作が可能

##数値型 - p.50
* 数値リテラルの取り扱い
* 明示的に16進数で取り扱ったり、乗数を定義することも可能
* 浮動小数点による演算のため、あくまでも近似値であることに注意
* 数値ではないものを数値として扱おうとするとNaN型を返す

##演算子 - p.96
* 演算子を用いて計算ができる。
* 詳細は当該頁を参照。
* その他のプログラミング言語やCSSなどと同様、判定・優先の順序や規則があるので注意

##文字列と数値の変換 - p.63
* 以下の関数を使うことにより、文字列を数値化できる
``` javascript
Number();
parseInt();
parseFloat();
```
* 関数を使わずに、以下のように文字列値を数値化することもできる
``` javascript
'123' - 0;
+'123';
```
* 以下の関数を使うことにより、数値を文字列に変換できる
``` javascript
String();
```
* 関数を使わずに、以下のように数値を文字列化することもできる
``` javascript
'123'+'';
```

##boolean型 - p.57
* true と false で値の真偽値を判定する型をいう
###boolean型の型変換 - p.67
* 各種演算子を用いて比較ができる。
* 以下は、javascriptの公理として false になる
``` javascript
0,
NaN,
null,
undefined,
''
```
* オブジェクト型は、すでに定義され具体的な中身を持つので、常に true となる

##null型、undefined型 - p.60
* 定義だけされ、具体的な中身がない値はnull型を返す
* そもそも定義されていないものについてはundefined型を返す

##制御文 - p.76
 - 条件分岐
   - if-else文
   - switch-case文
 - 繰り返し
   - while文
   - do-while文
   - for文
   - for in文
 - ジャンプ
 - 例外
 - その他
   - withは基本的には使用しない

##変数とオブジェクト - p.109
 - 変数の宣言
   - 何も代入していない値はundefined
 - 変数の参照
   - 変数にオブジェクトを代入するとオブジェクトの参照が代入
   - オブジェクトは実態（コピー）ではなく参照
``` javascript
    //$b2がtrueなら$b2を使用しなければ{}を代入
    var $b2 = $b2 || {};
```
###変数とプロパティ - p.114
 - グローバル変数
   - 関数の外で宣言
   - グローバルオブジェクトのプロパティ
 - ローカル変数
   - 関数内で宣言
   - 関数が呼ばれてから抜けるまで
### オブジェクト - p.117
 - JavaScriptのオブジェクトはプロパティの集合
 - オブジェクト指向
   - カプセル化
   - 継承
   - ポリモーフィズム
 -  オブジェクトリテラル
 - シングルトンパターン
   - インスタンスを1つに限定
 - 多値データ
 - コンストラクタ代わりの関数
``` javascript
    //多値データの表現にオブジェクトリテラルが使える
    hoge({x:1, y:2, z:3});

    //コンストラクタ代わりの関数
    function constA(name) {
      return {
        name: name,
          job: 'engineer'
        }
      }
    var a = constA('hoge');
```
### コンストラクタとnew式 - p.121
  - コンストラクタはオブジェクト生成の為に使う関数
     - コンストラクタは普通の関数宣言と同じ
     - new式で呼び出す
     - 呼び出すnew式は新しく生成されたオブジェクト参照
     - new式で呼び出されたコンストラクタ内のthisは新しく生成されたオブジェクトを参照
``` javascript
    //コンストラクタとnew
    var Human = function(name){
      this._private = 'himitu'; //'_'は 触らないでね！っていうルールとする
      this.name = name;
      this.greeting = function(){
        console.log('hellow');
      }
    }
    var test = new Human('hoge'); //this は今後作られるものをさす。newをはずすとthisがグローバルになる。
    console.log(test.name);  //hoge
    test.greeting(); //hellow

    test.name = 'hogehoge'; //変えれてしまう
    test.address = '埼玉県';
    test['address'] = '埼玉県'; //上記と同じ
```
### this参照 - p.134
 - トップレベルコード（関数外）のthisはグローバルオブジェクトを参照
 - 関数内のthis参照は関数の呼び出し方法で異なる
### applyとcall - p.136
 - 呼び出したthis参照を指定した任意のオブジェクト参照にできる
 - applyとcallの違いは第1引数以外の引数の渡し方
   - applyは配列で渡す
   - callは引数形式のままで渡す
### プロトタイプ継承 - p.137
``` javascript
	//クラス定義相当（コンストラクタ）
	function MyClass(x, y){
		his.x = x;
		this.y = y;
	}

	//プロトタイプ継承
	MyClass.prototype.show = function() {
		console.log(this.x, this.y);
	}

	//コンストラクタ呼び出し（インスタンス生成）
	var obj = new MyClass(3, 2);
	//メソッド呼び出し
	obj.show(); //3 2
```
 - プロトタイプチェーン
   - すべての関数（オブジェクト）はprototypeという名のプロパティを持つ
   - すべてのオブジェクトは、オブジェクト生成に使ったコンストラクタのprototypeオブジェクトへのリンクを持つ
オブジェクトのプロパティ読み込みは次の順にプロパティを探す。
 1. オブジェクト自身のプロパティ
 2. 暗黙リンクの参照オブジェクト（コンストラクタのprototypeオブジェクト）のプロパティ
 3. 2.のオブジェクトの暗黙リンクの参照オブジェクトのプロパティ
 4. 3.の動作を検索が終わるまで続ける。
``` javascript
	//コンストラクタ
	function MyClass() {
		this.x = 'x'
	}

	//コンストラクタ呼び出し（インスタンス生成）
	var obj = new MyClass();

	//objのプロパティxにアクセス
	console.log(obj.x); // x

	//objのプロパティzにアクセス
	//プロパティzは無い
	console.log(obj.z); //undefined

	//＊関数オブジェクト（コンストラクタ）は暗黙にprototypeプロパティを持つ！！
	//コンストラクタのprototypeオブジェクトにプロパティ（z）を追加
	MyClass.prototype.z = 'z';

	//obj.z はコンストラクタのprototypeオブジェクトのプロパティにアクセス
	console.log(obj.z); // z
```
