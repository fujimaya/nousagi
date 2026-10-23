# Markdown Blog

1記事1Markdownで更新する、GitHub Pages用のJekyllブログです。日本語・スマホ表示・記事一覧・個別記事・タグ表示・前後の記事リンクに対応しています。

## GitHub Pagesで公開

1. GitHubで空の **Public** リポジトリを作成します。アカウントのトップページにするなら `ユーザー名.github.io`、それ以外なら `blog` などにします。
2. ZIPを展開し、**このREADMEと同じ階層のファイル一式**をリポジトリの直下へ入れて `main` ブランチにコミットします。外側の `markdown-blog` フォルダごと入れないでください。
3. `_config.yml` の `title` と `description` を変更します。
4. 公開先に合わせて `url` と `baseurl` を設定します。

```yaml
# リポジトリ名が blog の例
url: "https://YOUR-USERNAME.github.io"
baseurl: "/blog"
```

`YOUR-USERNAME.github.io` リポジトリなら `baseurl: ""` にします。

5. リポジトリの **Settings → Pages → Build and deployment** で **Source: Deploy from a branch**、**Branch: main / (root)** を選び、Saveします。
6. ビルド完了後、Pages画面に表示されるURLへアクセスします。失敗時は **Actions** のビルドログを確認してください。

この方式では `.nojekyll` を置かないでください。独自のActions設定やNode.jsは不要です。

## 記事を追加

`_posts/2026-10-23-my-note.md` のように `YYYY-MM-DD-英数字の識別名.md` で保存します。日付は公開日以前を指定してください。未来の日付の記事は通常表示されません。

```markdown
---
title: "記事のタイトル"
description: "一覧に表示する短い説明"
tags: [C++, 開発メモ]
---

ここから本文です。

## 見出し

- 項目A
- 項目B
```

プッシュするとGitHub側でHTMLを生成し、記事一覧と個別記事を更新します。既存のサンプル記事は削除・編集して使ってください。同じ識別名を別の記事で使うとURLが重なるため、識別名は一意にします。

## 画像

画像を `assets/images/example.png` に入れ、記事で次のように指定します。`relative_url` を使うとリポジトリ名を含む公開URLでも表示できます。

```liquid
![画像の説明]({{ '/assets/images/example.png' | relative_url }})
```

## デザイン変更

- `assets/style.css`: 配色、余白、フォント、スマホ表示。冒頭のCSS変数で色を変更できます。
- `_layouts/default.html`: 共通ヘッダー・フッター。
- `_layouts/post.html`: 記事ページ。
- `index.html`: 記事一覧。
- `about.md`: 自己紹介。

## ローカル確認（任意）

RubyとBundlerをインストール後、プロジェクトのフォルダで次を実行します。

```sh
bundle install
bundle exec jekyll serve
```

表示先は通常 http://localhost:4000 です。baseurlを `/blog` にした場合は http://localhost:4000/blog/ になります。

## 検証状況

ファイル構成、YAML、記事のメタデータ、参照先を静的に確認しました。作成環境にRubyがないため、Jekyllの実ビルドとブラウザ表示の確認は未実施です。GitHubへのアップロード・公開設定はまだ行っていません。

## 公式ドキュメント

- https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
