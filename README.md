# みんなでつくろう「おめシスホームページ」……のオーバーホールを目的としたリポジトリです

https://omegasisters.github.io/homepage

> みんなでつくろう「おめシスホームページ」という企画で作られたリポジトリ（ https://github.com/omegasisters/homepage ）がライセンス未規定につき（誰も訴えないとは思うけど）著作権的にリスキーになっているので0からオーバーホールをしてリスクを消したい

という気持ちで作ったプロジェクト。ついでに技術周りの刷新もしてみます。本家に取り込まれるかは分からないので、完成してから本家でissueを立ててみるつもり。


## 現状のツラミ

- ライセンス規定が無いからソースコードをいじるのに常にリスクが伴う

- みんなが自由に技術を入れているのでカオス


## こうしたい

- MITライセンスを標準搭載（要は、ここに投稿されたソースコードは誰でも何にでも使えるよ〜というもの）

- 技術周りをとりあえず一本化したい


## 元のリポジトリに手を入れない理由は？

元のリポジトリを改善する方向性の場合、新しく書き換えたファイル（MITライセンス）と元から残っている部分（ライセンス不明）が入り乱れてしまうので、0から作り直すことでライセンス的に完全に問題のない状態にします


## このプロジェクトに貢献できますか？

誰でもissue / pull requestを送って下さい


## 動かす方法

```
$ git clone git@github.com:ookam/omegasisters-overhaul.git
$ cd /omegasisters-overhaul
$ yarn install
$ yarn start
```

node + yarnがインストールされていればこれだけで動きます。超簡単

## ディレクトリ構成とファイル

設定ファイルと書いてあるものは詳しい人以外は触らないようにしましょう

1. /srcの中だけ編集する
2. 既存のファイルを消さない

これだけ守っておけばプロダクトを壊す事はほぼ無いです

ファイルの構成は以下のようになっています。編集する際は常に「似たような他のファイルを見て、真似して書く」ようにしましょう

```
　/
　├ dist/                  => 🚨出力用のディレクトリ、勝手に出力されるけど無視して良い（一切触らない）
　├ node_modules/          => 🚨yarn したら勝手に作られるけど無視して良い（一切触らない）
　├ src/                   => 🚨入力用のディレクトリ（初心者はここだけ触りましょう）
　│　├ packs/              => 🚨javascript, cssを置く場所
　│　│　├ javascripts.js   => 🚨jsを読み込む設定ファイル（分からない人は触ってはいけない / 触ることはほぼ無い）
　│　│　├ javascripts/     => 🚨jsファイルの配置ディレクトリ
　│　│　│　├ index.js      => 🚨jsを読み込む設定ファイル（分からない人は触ってはいけない / 触ることはほぼ無い）
　│　│　│　└ ***.js        => ✏️自由に追加できる
　│　│　├ stylesheets.js   => 🚨cssを読み込む設定ファイル（分からない人は触ってはいけない / 触ることはほぼ無い）
　│　│　└ stylesheets/     => 🚨cssファイルの配置ディレクトリ
　│　│　　　├ index.js      => 🚨cssを読み込む設定ファイル（分からない人は触ってはいけない / 触ることはほぼ無い）
　│　│　　　├ tailwind.scss => 🚨tailwindを読み込む設定ファイル（分からない人は触ってはいけない / 触ることはほぼ無い）
　│　│　　　└ ***.css       => ✏️自由に追加できる
　│　├ public/             => 🚨font, imageなどを設置する場所
　│　│　└ images/          => 🚨画像ファイルの配置ディレクトリ
　│　│　　　└ fish.svg      => ✏️サンプルなので消してOK
　│　└ app/
　│　　　├ _data
　│　　　│　└ default_meta_tags.json => ✏️サイトのデフォルトのメタタグ、あなたのサイトに合った設定をしよう
　│　　　├ _includes                 => 🚨viewsから読み込むパーツ類の設置ディレクトリ
　│　　　│　├ components/            => 🚨パーツの設置ディレクトリ
　│　　　│　│　├ sample_component.js => ✏️サンプルなので消してOK
　│　　　│　│　└ ***_component.js    => ✏️自由に追加できる
　│　　　│　└ layouts/               => 🚨レイアウトの設置ディレクトリ
　│　　　│　　　├ default_layout.js   => ✏️基本的に触らない
　│　　　│　　　└ default_layout/     => 🚨デフォルトレイアウトの設置ディレクトリ
　│　　　│　　　　　├ _header.njk      => ✏️サイト全体で表示したいヘッダー
　│　　　│　　　　　├ _footer.njk      => ✏️サイト全体で表示したいフッター
　│　　　│　　　　　├ _include_cdn.njk => ✏️サイトで使うファイルでcdnから読むものを書く
　│　　　│　　　　　└ _footer.njk      => ✏️メタタグを書く（触ることはほぼ無い）
　│　　　└ views
　│　　　　　├ index.njk              => ✏️サイトのトップページ、自由に編集しよう
　│　　　　　├ sample.jk              => ✏️サンプルなので消してOK
　│　　　　　└ ***.njk                => ✏️自由に追加できる
　│
　├ .vscode/              => 🚨エディタの設定（分からない人は触ってはいけない / たまに触る）
　├ .github/              => 🚨githubとの連携（分からない人は触ってはいけない / 触ることはほぼ無い）
　│
　├ package.json          => 🚨✏️スクリプト周りの基幹ファイル（分からない人は触ってはいけない / 結構触る）
　├ eleventy.js           => 🚨11tyの基幹ファイル（分からない人は触ってはいけない / 結構触る）
　│
　├ package.json          => 🚨スクリプト周りの基幹ファイル（分からない人は触ってはいけない / 結構触る）
　├ eleventy.js           => 🚨11tyの基幹ファイル（分からない人は触ってはいけない / 結構触る）
　│
　├ .lintstagedrc         => 🚨huskyと連携してlintを回す設定（分からない人は触ってはいけない / 触ることはほぼ無い）
　├ .htmlhintrc           => 🚨htmlhintの設定（分からない人は触ってはいけない / 触ることはほぼ無い）
　├ .gitignore            => 🚨ブランチに含めないものを設定する（分からない人は触ってはいけない / たまに触る）
　├ babel.config.js       => 🚨babel設定ファイル（分からない人は触ってはいけない / 触ることはほぼ無い）
　├ postcss.config.js     => 🚨PostCSSの設定（分からない人は触ってはいけない / 触ることはほぼ無い）
　├ tailwind.config.js    => 🚨tailwindの設定（分からない人は触ってはいけない / たまに触る）
　├ stylelint.config.js   => 🚨stylelintの設定（分からない人は触ってはいけない / 触ることはほぼ無い）
　├ webpack.config.js     => 🚨webpackの設定（分からない人は触ってはいけない / 触ることはほぼ無い）
　└ .yarn.lock            => 🚨自動生成ファイル（一切触らない）
```

## これをgithub pageで公開する方法

1. mainリポジトリにpush or pull request
2. github actionsにより自動でgh-pages branchが作成される
3. 自動で公開 https://ookam.github.io/omegasisters-overhaul/ （反映に5分くらいかかる時がある）

## これをcloneして自分のプロジェクトで使いたい

ご自由にどうぞ

/package.jsonを開いて下のリポジトリ指定を修正する&github側でgithub pagesをオンにすればすぐ使えます

```
  "name": "omegasisters-overhaul",
  "version": "0.0.1",
  "repository": "git@github.com:ookam/omegasisters-overhaul.git",
```
