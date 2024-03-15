# Next.js Beginning
## Next.jsについて
Next.jsはVercelによって開発された**Reactのフレームワーク**

開発効率の向上だけでなく、サイトパフォーマンスやSEOの改善に貢献する  

こんな特徴がある  
- サーバーサイドレンダリング(SSR)
- 静的サイト生成(SSG,SG)
- ルーティング
- 自動コード分割

### なぜReactではなく、Next.jsを使うのか
「SEO対策とユーザーエクスペリエンスの向上」  
Next.jsにはプリレンダリングという大きな特徴がある  

これは、SEOを向上させるうえで、重要な機能


## pages ディレクトリを使う方法(Next.jsを学び始める際につまずいた為)
> https://qiita.com/mu_tomoya/items/7545bea039e82e483f9e  

以下のコマンドでプロジェクトを新規作成  
```
$ yarn create next-app  
```
ここで　**pagesディレクトリがない問題**  
> Next.js 13 からは App Router になった　から

はじめは、Pagesディレクトリで慣れて、その後App Routerに挑戦する  


まず、インストールを行う際に `Would you like to use App Router?`  と聞かれた際に、  
`No`と答えるとPagesディレクトリが作成される。

ここで、`Yes`を選択した際は、**src/app** と同じ階層にpagesディレクトリを作成しましょう  
```
$ mkdir src/pages
$ mkdir src/styles 
```
そして、appに入っている`page.tsx(page.js)`を`pages`ディレクトリに移しましょう  

次に、その`page.tsx(page.js)`を`index.tsx(index.js)`に移行させましょう  

`globals.css`も`styles`ディレクトリに移しましょう
```
$ mv src/app/page.tsx src/pages/index.tsx
$ mv src/app/globals.css src/styels
```

`_app.tsx(_app.jsx)`というファイルをpagesの直下に作りましょう(コードは参考へ)  

最後に`app`ディレクトリを削除しましょう    
(layout.tsxやfavicon.icoは削除してOK)
``` 
$ rm -rf src/app
```

これで、もう一度起動してみる  
```
$ yarn next dev
```

## CSS Modules
[name].module.css で名前を付ける必要がある  
