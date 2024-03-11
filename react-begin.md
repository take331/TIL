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



