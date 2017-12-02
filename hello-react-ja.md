# React 入門

今回はインタラクティブな◯×ゲームを作っていきましょう!

ここに最終的な結果が載っています。
https://codepen.io/gaearon/pen/gWWZgR?editors=0010
未知の文法やコードの意味が分からなくても大丈夫。このチュートリアルをステップ・バイ・ステップ形式で進めていくことによってどうやって構築するかを学べます。

このゲームをプレイしてみましょう。右側のリストをクリックすれば、その時間に戻ることができ、移動が行われた直後のボードの状態を確認することができます。一度ゲームに軽く目を通したらタブを閉じてもらって、次のセクションから、親しみやすい簡単なテンプレートを使って始めていきましょう。

## 前提

あなたがHTMLをJavacriptにある程度なじみがある想定ですが、分からなくてもついてこられるはずです。最新のJavaScriptを確認する必要がある場合は、[当ガイド](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)を読むことをおすすめします。JavaScriptの最新バージョンであるES6の機能も使用しています。このチュートリアルでは、[アロー関数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)、[クラス](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)、[let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)、および[const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)を使用しています。[Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUPGDADkdECChWeASl4AlOMOBQAIgHkAssp0aIySpogoaFBUQmISdC48QA)を使用して、どのES6コードをコンパイルするかを確認できます。

## 取り組み方

このチュートリアルには2つの取り組み方があります。
・ブラウザの右側にコードを書いていく
・ローカル開発環境を構築する

好きな方法を選んでください。


### ブラウザにコードを書いていく場合

これが一番てっとり早い方法です！
はじめに、この[スターターコード](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)を新しいタブで開きます。空の◯×ゲームが開かれたら、それを編集しながらチュートリアルを進めていきます。
次のローカル開発環境の構築はスキップして、概要から始めることができます。


### 自分のエディタで開発する場合(ローカル開発環境)
あなたのマシン上にプロジェクトを設定する場合です。
※これはオプションで、このチュートリアルに必須の項目ではありません。

この方法では、手間ですがあなたの快適な環境で開発することができます。次の方法を試してください。
1. 最新バージョンのNode.jsをインストールしてください
2. [インストール紹介](https://reactjs.org/docs/installation.html#creating-a-new-application)を見て、新しいプロジェクトを作成してください
  ```
  npm install -g create-react-app
  create-react-app my-app
  ```

3. 新しいコンテンツができたら、```src/```以下の全てのコンテンツを削除してください。(フォルダは削除せず、中身だけです)
  ```
  cd my-app
  rm -f src/*
  ```

4. ```index.css```を```src/```以下に作成し、[このCSSを貼り付けしてください](https://codepen.io/gaearon/pen/oWWQNa?editors=0100)
5. ```index.js```を```src/```以下に作成し、[このJsを貼り付けしてください](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)
6. 以下の3行を、先ほど追加した```index.js```の先頭に貼り付けしてください。
  ```
  import React from 'react';
  import ReactDOM from 'react-dom';
  import './index.css';
  ```

プロジェクトフォルダ内で ``` npm start ``` を実行すれば、ブラウザの ``` http://localhost:3000 ``` で空の◯×ゲームが確認できるはずです。
[こちら](http://babeljs.io/docs/editors)の指示に従ってあなたのエディタ内のシンタックスハイライトを確認することをオススメします。



### 詰まってしまったら...
つまづいたら、[サポートコミュニティ](https://reactjs.org/community/support.html) 特に、Reactiflux chatに行ってみましょう。は早めに助けを求められるのでめっちゃ良いです。どこに行っても問題が解決しない場合は問題を報告してください。



## 概要
### Reactとは何ぞや？
Reactは宣言的で、効率的で、柔軟なUI構築のためのJavaScriptライブラリです。
Reactにはいくつかの種類のコンポーネントがありますが、 ``` React.Component ``` サブクラスから始めましょう
```
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
```

一瞬おかしなXMLタグのようなものに見えるでしょう。コンポーネントはあなたが何をレンダリングしたいかを伝えます。(この時、Reactは効率的に更新し、データの変更があったコンポーネントだけをレンダリングします)

ここでいう、ShoppingListは **React component class** または、 **React component type** です。コンポーネントは、**props** と呼ばれるパラメータをとり、 **render** メソッド を介してビューを返します。

```render```メソッドは、レンダリングしたいものの記述を返します。そして、Reactはその記述を取り込み、それを画面にレンダリングします。 特に、```render``` は**React element** を返します。これはレンダリング対象の軽量な記述です。 ほとんどのReact開発者は、JSXという特殊な構文を使用して、これらの構造を簡単に書くことができます。 ``` <div /> ``` 構文は、ビルド時に ``` React.createElement（'div'） ``` に変換されます。 上記の例は、次のものと同等です。
```
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 children ... */),
  React.createElement('ul', /* ... ul children ... */)
);
```

興味がある場合、``` createElement() ``` についてはAPIリファレンスで詳しく説明しますが、このチュートリアルでは直接使用しません。 代わりに、JSXを引き続き使用します。
JSXの中括弧の中に任意のJavaScript式を入れることができます。 各React要素は、変数に格納するか、プログラムを渡すことができる実際のJavaScriptオブジェクトです。
```ShoppingList```コンポーネントは組み込みのDOMコンポーネントのみをレンダリングしますが、``` <ShoppingList /> ``` を記述することで、カスタムReactコンポーネントを簡単に簡単に作成できます。 各コンポーネントはカプセル化されているため、独立して動作することができ、単純なコンポーネントから複雑なUIを構築できます。



### はじめよう
[次の例を見てみましょう](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)

今構築しているプロジェクトの雛形が入っています。JavaScriptを気にかけてほしいので、今回はスタイルを提供しています。
今、わたしたちは3つのコンポーネントを持っています。(四角・ボード・ゲーム)
Squareコンポーネントは単一の```<button>```をレンダリングし、```Board```は9つの四角形をレンダリングし、```Game```コンポーネントは後で記入するプレースホルダをボードにレンダリングします。 現時点では、どのコンポーネントもインタラクティブではありません。



### Propsを通じてデータを渡す
新しいことを始めるために、BoardコンポーネントからSquareコンポーネントにいくつかのデータを渡してみましょう。
Boardの```renderSquare```メソッドで、```prop```を```Square```に渡すようにコードを変更します。
```
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;
  }
```

Squareの```render```メソッドを変更して、```{/ * TODO * /}``` を ```{this.props.value}``` に置き換えてその値を表示します。
```
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
```

[現在のコード](https://codepen.io/gaearon/pen/aWWQOG?editors=0010)



### インタラクティブなComponent
Squareコンポーネントをクリックすると "X"を記入するようにしましょう。
Squareの ``` render() ``` 関数で返された```<button>```タグを次のように変更してみてください：

```
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

さっそく四角をクリックすると、ブラウザにアラートが表示されます。
これは、新しいJavaScriptのアロー関数の構文を使用します。
onClickプロパティとして関数を渡していることに注意してください。
``` onClick = {alert（ 'click'）} ``` を実行すると、ボタンがクリックされる代わりにすぐにアラートが表示されます。
Reactコンポーネントはコンストラクタ内で ``` this.state ``` を設定することで状態を持つことができます。
状態の正方形の現在の値を保存し、正方形がクリックされたときにそれを変更しましょう。
まず、コンストラクタをクラスに追加して状態を初期化します。
```
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

JavaScriptのクラスにおいて、サブクラスのコンストラクタを定義する時、明示的に ``` super(); ``` 関数を呼ぶ必要があります。

Squareレンダリングメソッドを変更して、現在の状態からの値を表示し、クリック時にそれを切り替えます。
- ```<button>```タグの中の ``` this.props.value ``` を ``` this.state.value ``` に置き換えます。
- ``` () => alert() ``` イベントハンドラを ``` () => this.setState({value: 'X'}) ``` に置き換えます。

今、 ``` <button> ```タグの中身はこのような感じです。
```
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => this.setState({value: 'X'})}>
        {this.state.value}
      </button>
    );
  }
}
```

``` this.setState ``` が呼び出されると、コンポーネントの更新がスケジュールされ、渡された状態の更新でReactがマージされ、
子孫とともにコンポーネントが再レンダリングされます。
コンポーネントが再び降りると、```this.state.value``` は 'X'になるので、グリッドにXが表示されます。
任意の四角形をクリックすると、その中にXが表示されます。

[現在のコード](https://codepen.io/gaearon/pen/VbbVLg?editors=0010)

### Developer Tools
ChromeとFirefoxの拡張機能の"React Devtools"では、ブラウザ内でReactコンポーネントツリーの検証が可能です。
これによってツリー内の任意のコンポーネントのプロパティや状態を調べることができます。

ただし、CodePenを使用する場合、いくつかの追加ステップがあります。
1. ログインまたは登録してメールを確認する
2. [フォーク]ボタンをクリックします
3. [ビューの変更]をクリックし、[デバッグモード]を選択します
4. 開いている新しいタブでは、devtoolsにReactタブが表示されます

## 状態を引き上げる
◯×ゲームのための基本的な要素があります。しかし、今はstateは各Squareコンポーネントにカプセル化されています。1人のプレイヤーがゲームに勝ったかどうかを確認し、XとOを交互に配置する必要があります。 誰が勝ったかどうかを調べるには、正方形の要素に分割するのではなく、1つの場所に9つの正方形のすべての値を設定する必要があります。

あなたはBoardは各Squareの現在の状態を調べるべきだと考えるかもしれません。これはReactでは技術的に可能ですが、コードを理解しにくく、脆く、リファクタリングするのが難しくなるため、おすすめしません。
かわりに、ここでのベストは各Squareの代わりにBoardコンポーネントにこの状態を格納することです。Boardコンポーネントは各Squareにどのように表示するかを伝えることができます。

**複数の子からのデータを集約する場合や、2つの子コンポーネントが互いに通信する場合は、親コンポーネントに存在するようにstateを上位に移動します。 親は、親コンポーネントを介して子にstateを戻すことができるので、子コンポーネントは常に互いに、親と同期します。**

Reactコンポーネントをリファクタリングするときには、このようにstateを上に引き寄せているので、この機会に試してみましょう。 Boardにコンストラクタを追加し、9つのSquareに対応する9つの```null```を持つ配列を含むように初期状態を設定します。
```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  renderSquare(i) {
    return <Square value={i} />;
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

後にこれを記入すると、Boardはこのような感じになります
```
[
  'O', null, 'X',
  'X', 'X', 'O',
  'O', null, null,
]
```

Boardの ``` renderSquare ``` メソッドは今このような感じです
```
renderSquare(i) {
  return <Square value={i} />;
}
```

Squareのpropに ``` value ``` を渡すため、このように修正します
```
renderSquare(i) {
  return <Square value={this.state.squares[i]} />;
}
```

[現在のコード](https://codepen.io/gaearon/pen/gWWQPY?editors=0010)

ここで、四角がクリックされた時の動作を変更する必要があります。Boardコンポーネントには、どの四角が塗りつぶされているかが保存されます。つまり、SquareがBoardの状態を更新する方法が必要です。コンポーネントの状態は、```private```とみなされるため、Boardの状態をSquareから直接更新することはできません。
ここでよくあるパターンは、四角をクリックすると呼び出される関数をBoardからSquareに渡します。Boardの```renderSquare``` を再度変更し、次のようにします。
```
renderSquare(i) {
  return (
    <Square
      value={this.state.squares[i]}
      onClick={() => this.handleClick(i)}
    />
  );
}
```

わたしたちは、返された要素を複数の行に分けて読みやすくし、JavaScriptの前後にセミコロンを挿入しないようにしました。

今度はBoardからSquareへ2つのプロパティを渡しています(すなわち ``` value ``` と ``` onClick ``` を渡しています。)後者はSquareが呼び出すことができる関数です。Squareに以下の変更を加えましょう。
- Squareの ``` render ``` で ``` this.state.value ``` を ``` this.props.value ``` に置き換えます
- Squareの ``` render ``` で ``` This.setState() ``` を ``` this.props.value ``` に置き換えます
- 状態を持たないのでSquareからコンストラクタ定義を削除してください

これらの変更の後、Squareコンポーネント全体は以下のようになります。
```
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => this.props.onClick()}>
        {this.props.value}
      </button>
    );
  }
}
```

今、四角がクリックされると、Boardによって渡されたonClick関数が呼び出されます。ここで何が起きるかを要約すると、
1. 組み込みのDOM```<button>```コンポーネントの```onClick prop```は、Reactにクリックイベントリスナーの設定を指示します。
2. ボタンがクリックされると、ReactはSquareの```render()```メソッドで定義されたonClickイベントハンドラを呼び出します。
3. このイベントハンドラは```this.props.onClick()```を呼び出します。Squareの```prop```は、Boardによって指定されています。
4. BoardはSquareに ``` onClick={() => this.handleClick(i)} ``` を渡しているので、呼び出されるとBoard上で```this.handleClick(i)```が実行されます。
5. まだBoard上で```handleClick()```メソッドを定義していないので、コードがクラッシュします。

DOM```<button>``` 要素のonClick属性は、Reactにとって特別な意味を持っていますが、Squareの```onClick prop```またはBoardの```handleClick```メソッドには異なる名前をつけることができます。しかし、Reactアプリケーションでは、属性には ``` on* ```を、ハンドラメソッドには ``` handle* ``` を命名するのが一般的です。

四角をクリックしてみてください。```handleClick```をまだ定義していないので、エラーが発生します。これをBoardクラスに追加します。
```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = 'X';
    this.setState({squares: squares});
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

[現在のコード](https://codepen.io/gaearon/pen/ybbQJX?editors=0010)

``` .slice() ``` を呼び出して、既存の配列を変更する代わりに、四角の配列をコピーします。不変性がなぜ重要であるかを学ぶために、次のセクションに進んでください。

今度は、四角をクリックして再度入力する必要がありますが、状態は各Squareの代わりにBoardコンポーネントに保存されており、ゲームを構築しています、Boardの状態が変わる度にSquareコンポーネントは自動的に再レンダリングされます。

Squareはもはや自身の状態を保持しません。それは親Boardからその値を受け取り、それがクリックされた時にその親に通知します。我々は、このようなコンポーネントを制御されたコンポーネントと呼びます。

### 不変性が重要な理由
前のコードサンプルでは、 ``` .slice() ``` 演算子を使用して、変更を加える前に四角の配列をコピーし、既存の配列の変更を防ぐことを勧めました。これが何を意味し、なぜ学ぶ必要がある重要な概念なのかを話します。

一般的に、データを変更するには2つの方法があります。1つ目は、変数の値を直接変更してデータを変更する方法です。2つ目は、望んだ変更を含むオブジェクトの新しいコピーデータで置き換えることです。

#### 変化によるデータ変更
```
var player = {score: 1, name: 'Jeff'};
player.score = 2;
// Now player is {score: 2, name: 'Jeff'}
```

#### 変化のないデータ変化
```
var player = {score: 1, name: 'Jeff'};

var newPlayer = Object.assign({}, player, {score: 2});
// Now player is unchanged, but newPlayer is {score: 2, name: 'Jeff'}

// Or if you are using object spread syntax proposal, you can write:
// var newPlayer = {...player, score: 2};
```

最終的な結果は同じですが、変化することなく(または元になるデータを変更して)、コンポーネントをアプリケーションの全体的なパフォーマンスを向上させることができます。

#### 簡単な「元に戻す/やり直し」と時間旅行
不変性はまた、複雑な機能を実装するのをはるかに容易にします。例えば、このチュートリアルでは、ゲームの様々な段階の時間の移動を実装します。データの変更を避けることで、古いバージョンのデータへの参照を保持し、必要に応じてそれらの間で切り替えることができます。

#### 変更を追跡する
変更されたオブジェクトが変更されたかどうかを判断するには、オブジェクトに直接変更が加えられるため複雑です。これは、現在のオブジェクトを前のコピーと比較し、オブジェクトツリー全体をトラバースし、各変数と値を比較する必要があります。このプロセスはますます複雑になる可能性があります。

不変なオブジェクトがどのように変更されたかを判断することはかなり簡単です。参照されるオブジェクトが以前と異なる場合、オブジェクトは変更されています。それでおしまいです。

#### Reactでの再レンダリング定義
Reactでの不変性の最大のメリットは、単純純粋なコンポーネントを構築するときです。不変なデータは、変更が行われたかをより簡単に判断できるため、コンポーネントの再レンダリングが必要な時を判断するのにも役立ちます。

``` shouldComponentUpdate() ``` の詳細と純粋なコンポーネントを構築する方法については、[パフォーマンスの最適化](https://reactjs.org/docs/optimizing-performance.html#examples)を参照してください。

### Functional Components
わたしたちは、コンストラクタを削除しました。実際、Reactは```render```メソッドのみで構成されるSquareのようなコンポーネントタイプのための**functional components**と呼ばれる、よりシンプルな構文をサポートしています。```React.Component```を継承するクラスを定義するのではなく、単にpropsをとり、レンダリングすべきものを返す関数を書くだけです。Squareクラス全体をこの関数で置き換えます。
```
function Square(props) {
  return (
    <button className="square" onClick={props.onClick}>
      {props.value}
    </button>
  );
}
```

あなたは```this.props```を変更する必要があります。アプリケーションの多くのコンポーネントは、functional componentとして記述することができます。これらのコンポーネントは書きやすく、Reactは今後さらに最適化します。

わたしたちはコードを整理していますが、``` onClick={() => props.onClick()} ``` を ``` onClick={props.onClick} ``` に変更しました。
``` onClick={props.onClick()} ``` は、渡す代わりにすぐに ``` props.onClick ``` を呼び出すため、機能しません。

[現在のコード](https://codepen.io/gaearon/pen/QvvJOv?editors=0010)



### ターンを作る
明らかに不足しているのは、Xだけがプレイできることです。それを修正しましょう。
最初の移動をデフォルトでXにしましょう。Boardコンストラクタで開始状態を変更します。
```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  }
・・・
```

わたしたちが移動するたび、boolean値を反転して、状態を保存することによって```xIsNext```をトグルさせます。Boardの```handleClick```関数を更新して```xIsNext```の値を変更させます。
```
handleClick(i) {
  const squares = this.state.squares.slice();
  squares[i] = this.state.xIsNext ? 'X' : 'O';
  this.setState({
    squares: squares,
    xIsNext: !this.state.xIsNext,
  });
}
```

今度はXとOが交代します。次のBoardの```render```内の```status```テキストを変更して、次に誰が表示されるかを表示します。
```
render() {
  const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');

  return (
    // the rest has not changed
・・・
```

これらを変更した後、Boardコンポーネントはこのような状態になっています。
```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

[現在のコード](https://codepen.io/gaearon/pen/KmmrBy?editors=0010)



### 勝者の定義
ゲームに勝利した時を見てみましょう。このヘルパー関数をファイルの最後に追加します。
```
function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
```

Boardのrender関数でそれを呼び出すことで、誰が勝利したかをチェックし、どちらかが勝利した時に```status```テキストを「勝者：[X/O]」とすることができます。
Boardのrenderでstatus宣言を次のコードに置き換えます。
```
render() {
  const winner = calculateWinner(this.state.squares);
  let status;
  if (winner) {
    status = 'Winner: ' + winner;
  } else {
    status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
  }

  return (
    // the rest has not changed
・・・
```

誰かが既にゲームに勝利している場合、または既に四角がいっぱいになっている場合は、Boardの```handleClick```を先にreturnして、クリックを無視するように変更します。
```
handleClick(i) {
  const squares = this.state.squares.slice();
  if (calculateWinner(squares) || squares[i]) {
    return;
  }
  squares[i] = this.state.xIsNext ? 'X' : 'O';
  this.setState({
    squares: squares,
    xIsNext: !this.state.xIsNext,
  });
}
```

おめでとう！あなたは今◯×ゲームを動かしています。そして、あなたはReactの基礎を知っています。あなたは恐らくここでは真の勝者というわけです。

[現在のコード](https://codepen.io/gaearon/pen/LyyXgK?editors=0010)



## 履歴の保存
Boardの古い状態に戻って、以前の動きの後にどのように見えるかを見ることができるようにしましょう。移動が行われるたびに、すでに新しい四角の配列が作成されています。これは過去のボードの状態を同時に簡単に保存できることを意味します。

このようなオブジェクトを状態に格納するとしましょう
```
history = [
  {
    squares: [
      null, null, null,
      null, null, null,
      null, null, null,
    ]
  },
  {
    squares: [
      null, null, null,
      null, 'X', null,
      null, null, null,
    ]
  },
  // ...
]
```

上位のレベルのGameコンポーネントが移動リストの表示を担当するようにします。それで、SquareからBoardに状態を引き上げた時のように、BoardからGameに再び引き上げましょう。上位のレベルで必要なすべての情報が得られるようにしましょう。

はじめに、コンストラクタを追加してGameの初期状態を設定します。
```
class Game extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      xIsNext: true,
    };
  }

  render() {
    return (
      <div className="game">
        <div className="game-board">
          <Board />
        </div>
        <div className="game-info">
          <div>{/* status */}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
}
```

Boardを変更して、propsを介して四角をとり、Squareが以前に行った変形のように、Gameによって指定された独自のonClickプロパティを持っています。各四角の位置をクリックハンドラに渡すことができるので、クリックされた四角は分かります。必要な手順の一覧は次の通りです。

- Boardでコンストラクタを削除します
- Boradの ``` renderSquare ``` で ``` this.state.squares[i] ``` を ``` this.props.squares[i] ``` に置き換えます
- Boardの ``` renderSquare ``` で ``` this.handleClick(i) ``` を ``` this.props.onClick(i) ``` に置き換えます

Board全体のコンポーネントは次のようになります。
```
class Board extends React.Component {
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.props.squares[i]}
        onClick={() => this.props.onClick(i)}
      />
    );
  }

  render() {
    const winner = calculateWinner(this.state.squares);
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

Gameのrenderでは、最新の履歴エントリが表示され、ゲーム状態の計算を引き継ぐことができます。
```
render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />

        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
```

Gameが状態をレンダリングしているので、Boardのrender関数から ``` <div className="status">{status}</div> ``` とステータスを計算するコードを削除できます。
```
render() {
    return (
      <div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
```

次に、```handleClick```メソッドをBoardからGameに移す必要があります。Boardクラスから切り取ってGameクラスに貼り付けることができます。
ゲームの状態は構造が異なるため、少し変更する必要があります。Gameの```handleClick```は、新しい履歴項目を連結して、新しい履歴配列をつくることによって、新しい項目をスタックにプッシュすることができます。
```
handleClick(i) {
  const history = this.state.history;
  const current = history[history.length - 1];
  const squares = current.squares.slice();
  if (calculateWinner(squares) || squares[i]) {
    return;
  }
  squares[i] = this.state.xIsNext ? 'X' : 'O';
  this.setState({
    history: history.concat([{
      squares: squares,
    }]),
    xIsNext: !this.state.xIsNext,
  });
}

```

この時点で、Boardは```renderSquare```と```render```だけを必要としています。状態の初期化とクリックハンドラは両方ともゲームに存在する必要があります。

[現在のコード](https://codepen.io/gaearon/pen/EmmOqJ?editors=0010)



### 移動を見る
これまでのゲームで行われた以前の動きを見てみましょう。先ほどわたしたちは、React要素はファーストクラスのJavaScriptオブジェクトであり、保存したり、渡したりできることを学びました。Reactで複数の項目をレンダリングするには、React要素の配列を渡します。その配列を構築する最も一般的な方法は、データの配列をマップすることです。Gameの```render```メソッドでそれをやってみましょう。

```
render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    const moves = history.map((step, move) => {
      const desc = move ?
        'Go to move #' + move :
        'Go to game start';
      return (
        <li>
          <button onClick={() => this.jumpTo(move)}>{desc}</button>
        </li>
      );
    });

    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />
        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{moves}</ol>
        </div>
      </div>
    );
  }
```

[現在のコード](https://codepen.io/gaearon/pen/EmmGEa?editors=0010)

履歴の各ステップについて、すぐに実装するクリックハンドラを持つ ``` <button> ``` を含むリストアイテム ``` <li> ``` を作成します。このコードを使用すると、ゲーム内で行われた移動の一覧と、次の警告が表示されます。

> Warning: Each child in an array or iterator should have a unique “key” prop. Check the render method of “Game”.

この警告が何を意味するのかを話しましょう。



### Keys
アイテムをレンダリングすると、Reactは常に各アイテムの情報をリストに保存します。状態を持つコンポーネントをレンダリングする場合は、その状態を保存する必要があります。コンポーネントの実装方法に関係なく、Reactはバッキングネイティブビューへの参照を保存します。

そのリストを更新するとき、Reactは何が変更されたかを判断する必要があります。リスト内の項目を追加、削除、再配置、または更新できました。
次の場合を想像してみましょう
```
<li>Alexa: 7 tasks left</li>
<li>Ben: 5 tasks left</li>
```

から
```
<li>Ben: 9 tasks left</li>
<li>Claudia: 8 tasks left</li>
<li>Alexa: 5 tasks left</li>
```

わたしたちには、AlexaとBenが場所を入れ替え、Claudiaが追加されたように見えますが、Reactは単なるプログラムであり、あなたが意図したかどうかは分かりません。結果、Reactはリスト内の各要素にkeyプロパティを指定し、各コンポーネントと兄弟を区別するための文字列を指定するように求めます。この場合、Alexa、ben、Claudiaは感覚的なkeyになるかもしれません。アイテムがデータベース内のオブジェクトに対応する場合、通常はデータベースのIDが適切です。
```
<li key={user.id}>{user.name}: {user.taskCount} tasks left</li>

```

```key```はReactによって予約された特別なプロパティです。(refと一緒、より高度な機能です)
要素が作成されると、Reactは```key```プロパティをプルオフし、```key```を返された要素に直接格納します。それはプロパティの一部であるように見えるかもしれませんが、``` this.props.key ``` で参照するこはできません。Reactは```key```を自動的に使用して、更新する子要素を決定します。コンポーネントが独自の```key```について問い合わせる方法はありません。

リストが再レンダリングされると、Reactは新しいバージョンの各要素を受け取り、前のリストで一致する```key```を持つ要素を探します。```key```がセットに追加されると、コンポーネントが作成されます。```key```が削除されると、コンポーネントが破棄されます。```key```はReactに各コンポーネントのアイデンティティを伝えるので、rerenders間で状態を維持することができます。コンポーネントの```key```を変更すると、コンポーネントは完全に破棄され、新しい状態で再作成されます。

**動的なリストを作成するたびに、適切なkeyを割り当てることを強くおすすめします。**
適切な```key```を手元においていない場合は、データの再構成を検討してください。

```key```を指定していない場合、Reactはあなたに警告し、配列のインデックスを```key```として使用します。リスト内の要素の順序を変更したり、アイテムの追加/削除を行う場合には正しい選択ではありません。明示的に ``` key={i} ``` を渡すと警告が消えますが、同じ問題がありますので、ほとんどの場合は推奨されていません。

コンポーネントの```key```は、グローバルに一意である必要はなく、直接の兄弟に対して一意である必要があります。



### 時間移動の実装
移動リストについては、各ステップごとに固有のID(移動が発生した回数)が既にあります。Gameの```render```メソッドでkeyを``` <li key={move}> ``` として追加し、keyの警告が消えるはずです。
```
const moves = history.map((step, move) => {
  const desc = move ?
    'Go to move #' + move :
    'Go to game start';
  return (
    <li key={move}>
      <button onClick={() => this.jumpTo(move)}>{desc}</button>
    </li>
  );
});
```

[現在のコード](https://codepen.io/gaearon/pen/PmmXRE?editors=0010)

``` jumpTo ``` が未定義であるため、移動ボタンのいずれかをクリックするとエラーが発生します。Gameの状態に新しいkeyを追加して、現在表示しているステップを示しましょう。
まず、 ``` stepNumber: 0 ``` をGameのコンストラクタの初期状態に追加します。
```
class Game extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      stepNumber: 0,
      xIsNext: true,
    };
  }
```

次に、ゲームでその状態を更新する```jumpTo```メソッドを定義します。また、```xlsNext```を更新したいです。移動番号のインデックスが偶数の場合は、```xlsNext```を```true```に設定します。
Gameクラスに```jumpTo```というメソッドを追加します。
```
handleClick(i) {
  // this method has not changed
}

jumpTo(step) {
  this.setState({
    stepNumber: step,
    xIsNext: (step % 2) === 0,
  });
}

render() {
  // this method has not changed
}
```

その後、新しい移動が行われた時に```stepNumber```を更新するには、Gameの```handleClick```の状態更新に ``` stepNumber: history.length ``` を追加します。現在のボード状態を読み込んでいるときに```stepNumber```を認識するように```handleClick```を更新し、Boardに戻って新しいエントリを作成します。
```
handleClick(i) {
  const history = this.state.history.slice(0, this.state.stepNumber + 1);
  const current = history[history.length - 1];
  const squares = current.squares.slice();
  if (calculateWinner(squares) || squares[i]) {
    return;
  }
  squares[i] = this.state.xIsNext ? 'X' : 'O';
  this.setState({
    history: history.concat([{
      squares: squares
    }]),
    stepNumber: history.length,
    xIsNext: !this.state.xIsNext,
  });
}
```

これで、Gameのrenderを変更して、履歴のそのステップから読み込むことができます。
```
render() {
  const history = this.state.history;
  const current = history[this.state.stepNumber];
  const winner = calculateWinner(current.squares);

  // the rest has not changed
```

[現在のコード](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)

さっそく移動ボタンをクリックすると、ボードはすぐに更新され、その時のゲームの様子が表示されます。



### Wrapping Up
さて、あなたは◯×ゲームを作ることができました。
- あなたはこれで遊ぶことができ
- 1人のプレイヤーが勝利した時はそれを示し
- ゲーム中の移動の履歴を記憶し、
- プレイヤーは古いバージョンのゲームボードを見に時間を遡りジャンプすることができます。
  よくできました！Reactの仕組みがよく理解できれば幸いです。

[最終的な結果はこちら](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)

時間がもっとあったり、新しいスキルを練習したければ、次のような改善のアイデアを難易度の高い順に並べておきます。
1. 移動履歴リストに各移動の位置を「col, row」の形式で表示します
2. 移動リストで現在選択されている項目を太文字にします
3. Boardを書き直してハードコーディングする代わりに2つのループを使って四角を作ってください。
4. トグルボタンを追加すると、移動を昇順または降順のいずれかで並び替えることができます
5. どちらかが勝利したら勝利の要因となった3つの四角を強調表示します

このチュートリアルでは、要素、コンポーネント、プロパティ、状態を含むいくつかのReactの概念について触れました。これらの各トピックの詳細については、[残りのドキュメント](https://reactjs.org/docs/hello-world.html)を参照してください。コンポーネントの定義の詳細については、[React.Component　APIリファレンス](https://reactjs.org/docs/react-component.html)を参照してください。
