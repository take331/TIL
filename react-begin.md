# React Beginner
## React 
Facebock社が開発したUIライブラリ　　

**コンポーネント(部品)** という概念が特徴  

このコンポーネントを組み合わせてWebの画面を作っていく  

### なぜReactを使うのか
Reactを使用しない画面描画では、DOMを直接変更してHTMLを再描画する必要があり、これはコストが高い😥
※DOM(Document Object Model) = HTMLにアクセスする窓口

**仮想DOM** という解決策

ブラウザのDOMツリーをJSのオブジェクトとして扱う  
- ブラウザに負荷をかけずJSエンジンのメモリを使うことで効率の良いレンダリングを行う

- DOMの状態をJSで管理することができる = Reactのコンポーネントは「状態をもつUI」

## JSX
JavaScriptの拡張言語  
HTMLライクな記述 + JSの構文を使うことができる  →　楽に記述できる(シンタックスシュガー)
JSXは最終的にReact要素を生成する  

jsxを使わない場合
``` js
React.createElement(
  'button',
  {className: 'btn-blue',
  'Click!'
}
```
JSXを使った場合
``` jsx
<button className={'btn-blue'}>
  Click!
</button>
```

JSXの特殊な構文
- JSXは階層構造で記述する必要がある🖐️
- React.Fragmentで囲む(省略OK)

ダメな例
```
return (
  <p>ramen sushi udon</p>
  <p>yakiniku sukjyaki tempura</p>
);
```
※一つのコンポーネントをFragmentで囲むのは意味がない
```
return (
  <>
    <p>ramen sushi udon</p>
  </>
);
```

良い例
``` jsx
return (
  <React.Fragment>
    <p>ramen sushi udon</p>
    <p>yakiniku sukjyaki tempura</p>
  </React.Fragment>
);
```

## 環境構築
### Create React App
Reactのツールチェイン  
> Reactで新しいシングルページアプリケーション(SPA)を作成するのに最も良い方法です

本来のReact環境構築には以下の設定が必要😒
- トランスパイラのBabel
- バンドラーのWebpack
→　Reactの初学者がやるべきことではない！

```
npx create-react-app [app name]
```
→　Happy hucking!　が表示されたらOK😊

```
cd [app name]
code .
```

<img src="https://github.com/take331/TIL/assets/73569757/c99b8654-6358-44ef-b970-bfafd910110e" width=300px />  
初期状態  

- src  
  開発用ファイルが格納される  
  ReactのコンポーネントのJSXファイルなどを格納するフォルダ
  
- public  
  静的ファイルが格納される  (htmlファイルや画像ファイルなど)
  
- build(npm run build で生成)  
  デプロイするファイルが格納される

### scripts(package.json)  
<img src="https://github.com/take331/TIL/assets/73569757/010cb9b7-f317-4d94-b800-a386f96a3c9c" width= 300px />  

- npm start
  ローカルサーバーを起動してReactアプリを確認できる👀  
  (ホットリロード)

- num run build  
  本番用ファイルを作成してbuildディレクトリ二出力👉  
  srcとpublicを一つにまとめる(バンドル)

- npm run eject  
  BabalやWebpackの設定を変えたいときに使う

## コンポーネント
見た目と機能を持つUI部品  
大きく２種類のコンポーネントに分かれる  
- クラスコンポーネント(現在はほとんど使われていない)
- 関数コンポーネント
(昔はクラスコンポーネントでないとできないことがあったが、React Hooksの登場によって同じ機能が使えるようになった)

### なぜコンポーネントを使うのか
- 再利用するため♻️  
  同じ記述を何度もする必要がない
  
- コードの見通しを良くするため  
  原則 1ファイル = 1コンポーネント(なんのためのパーツなのか、責務を明確にする)
  
- 変更に強くするため🔧  
  1箇所を修正するだけでOK

### 基本的な使い方
- ファイルは大文字で
- 子コンポーネントで**export**
- 親コンポーネントで**import**
- **props**でデータを渡す

## improt・export
- default export (名前なしexport)

宣言したアロー関数をexport
``` jsx
const Title = (props) => {
  return <h2>{props.title}</h2>
};
export default title
```
名前付き関数宣言と同時にexport
``` jsx
export default function Title(props) {
  return <h2>{props.title}</h2>
};
 ```

- default import (名前なしimport)
``` jsx
import Article from "./compornents/Article";
 ```

- named export (名前付きexport)

Reactではエントリポイント(index.js)でよく使う
``` jsx
// default という名前のモジュールにエイリアス(別名)をつけてexport
export {default as Article} from './Article';
export {default as Title} from './Title';
export {default as Content} from './Content';
```

- named import (名前付きimprot)
``` jsx
import { Content, Title } from "./index";
```

## State
Hooks = クラスコンポーネントの機能に接続する(Hook Up)

### なぜStateを使うのか
コンポーネント内の要素をDOMで書き換えるのは、NG🙅‍♂️  
新しい値をつかって再レンダリングさせる🙆‍♂️  
Reactが再レンダリングを行うきっかけ  
- Stateが変更されたとき
- propsが変更されたとき

#### propsとstateは何が違う？🤔
propsは引数のように**親から子に渡される値** (逆はできない)  
stateは**コンポーネントの内部で宣言、制御される値** (stateはpropsに渡すこともできる)   

### useState
1. useStateによるstateの宣言
``` jsx
// state: 現在の状態
// setState: 更新関数
// initialState: 初期値
const [state, setState] = useState(initilState);
```
2. stateの更新 
``` jsx
// newState: 新しい値
setState(newState);
```
### stateをpropsに渡す
``` jsx

const Article = (props) => {
  const [isPublished, setIsPublished] = useState(false);
  // 更新関数はそのままpropsとして渡さずに関数化して渡す
  const publishArticle = () => {
    setIsPublished(true);
  }
  return (
    <div>
      <Title title={props.title} />
      <Content content={props.content} />
      <PublishButton isPublished=isPublished onClick={setIsPublished} />
  );
};

```

※ propsへ状態関数を渡す際の注意点  
OKな渡し方
``` jsx
// 関数自体を渡す
<PublishButton isPublished={isPublished} onClick={publishArticle} />
```
``` jsx
// コールバック関数を渡す
<PublishButton isPublished={isPublished} onClick={() => publishArticle()} />
```

NGな渡し方
``` jsx
// 渡すときに関数を実行する(無限ループに陥る)
<PublishButton isPublished={isPublished} onClick={publishArticle()} />
```

## ライフサイクルとuseEffect
### ライフサイクル
コンポーネントのライフサイクルとは・・・  
**「コンポーネントが生まれてから破棄されるまでの流れ」** のこと

３種類のライフサイクル  
- Mounting(配置)  
  初期化→レンダリング→マウント後の処理  
  
- Updating(変更)  
  レンダリング→更新後の処理  
  
- Unmounting(破棄)  
- アンマウント前の処理  

### useEffect
関数コンポーネントでは **useEffect** という副作用Hookを使ってライフサイクルを表現することができる  
(副作用 = レンダリングによって引き起こされる処理) → レンダリングの度に行いたい処理を記述する  

``` jsx
// 再レンダリングが行われるときは毎回実行される
useEffect(() => {
  console.log("Current count is...", count)
});
```

``` jsx
// 初回レンダリング時のみ実行
useEffect(() => {
  console.log("Current count is...", count)
}, []);
```

``` jsx
// triggerが変更されるたびに実行
useEffect(() => {
  console.log("Current count is...", count)
},[trigger]);
```

``` jsx
// trigger1かtrigger2が変更されるたびに実行
useEffect(() => {
  console.log("Current count is...", count)
}, [trigger1, trigger2);
```

### クリーンアップの概念
useEffectの中でクリーンアップ関数をreturnする  
クリーンアップ関数は、再レンダリングが行われる前に実行される  

### useEffectのユースケース
- APIやデータベースから非同期通信でデータを取得(fetch)する
- 特定の値が変わったらデータを再取得(refetch)する



