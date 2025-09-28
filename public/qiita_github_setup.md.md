---
title: Qiita CLIの導入とGitHubリポジトリとの紐付け(Mac)
tags:
  - 'Qiita'
  - 'QiitaCLI'
  - 'GitHub'
  - '初心者'
private: false
updated_at: ''
id: null
organization_url_name: null
slide: false
ignorePublish: false
---
# はじめに
- 本記事では、Qiita CLIの導入とGitHubリポジトリの紐付けを行う際の手順を参考にした記事を示しながら紹介しています
- また、GitHubの連携でつまづいた箇所も紹介しています


# Node.jsの導入
:::note info
Node.jsを導入済みの方は「Qiita CLI のインストール」まで読み飛ばしてください。
:::

Qiita CLIを使うにはNode.jsが必要なため、インストールします。
>Qiita CLI を使うには Node.js 20.0.0 以上が必要です。 Node.js をはじめて使う場合はインストールする必要があります。
（[Qiita CLIリポジトリ](https://github.com/increments/qiita-cli)より）


インストール手順は以下の記事を参考にしています。
詳細は省略しますが、参考にした記事では用語の整理やコマンドの意味など、より詳細に記載されていました。


https://qiita.com/ffggss/items/94f1c4c5d311db2ec71a

### nvmのインストール
nvmはNode.jsのバージョン管理ができるツールです。
プロジェクトごとにNode.jsのバージョンを切り替えられるので、今回はnvmを使ってNode.jsをインストールします。
[nvm公式リポジトリ](https://github.com/nvm-sh/nvm)

#### nvmのインストール

```bash:curlでのインストール
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

#### nvmのインストール検証
`nvm`と表示されたらインストール成功です。

```bash:検証コマンド
command -v nvm
```
(インストールした後に一度ターミナルを開き直す必要があるかもしれません。)
#### Node.jsのインストール

最新の安定版をダウンロードします。
```bash:stableバージョン
nvm install stable --latest-npm
nvm alias default stable
```

# Qiita CLI のインストール
ここからは、公式の記事の「Qiita CLI の利用方法について」と「Qiita CLI のセットアップ方法について」を参照し、セットアップを行います。

https://qiita.com/Qiita/items/666e190490d0af90a92b

# GitHubリポジトリとの紐付け
Qiita CLI のログインまでできたら、GitHubリポジトリと紐付けます。

https://qiita.com/Qiita/items/32c79014509987541130

上記記事の1~4を実行すれば、紐付けができます。

#### GitHub操作時のエラー
git操作時に失敗した記録を以下に残します。

- `fatal: not a git repository (or any of the parent directories): .git`
  ローカルでリポジトリを作っていない状態で`git remote add origin [リポジトリのURL]`
  を実行したため、エラーが起きました。
  以下のコマンドでリポジトリを作成して、エラーを解消しました。
  
  ```bash:gitコマンド
  git init
  ```

- `error: src refspec main does not match any`
  1回もコミットしていない状態で`git push -u origin main`を実行したため、
  エラーが起きました。
  READMEを作成してcommitした後にコマンド実行したところエラーが解消されたため、push実行前に一度commitしておかないとブランチが作成されず、エラーになるようです。
  



