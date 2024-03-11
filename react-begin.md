# React Beginner
## React 
Facebock社が開発したUIライブラリ　　

**コンポーネント(部品)** という概念が特徴  

このコンポーネントを組み合わせてWebの画面を作っていく  

## なぜReactを使うのか
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
jsxを使った場合
``` jsx
<button className={'btn-blue'}>
  Click!
</button>
```

jsxの特殊な構文
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
  1ファイル = 1コンポーネント
  
- 変更に強くするため🔧  
  1箇所を修正するだけでOK

### 基本的な使い方
- ファイルは大文字で
- 子コンポーネントで**export**
- 親コンポーネントで**import**
- **props**でデータを渡す






