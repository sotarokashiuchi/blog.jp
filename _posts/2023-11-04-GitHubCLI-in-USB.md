---
layout: post
title: "開発環境(Git, GitHub)をUSBに入れて持ち運ぶ"
date: 2023-11-04 23:25
description: USBに開発環境(Git, GitHub)を入れ、持ち運べるようにする
tags:
 - 技術
---

## 概要
USBで開発環境を一式移動させることができれば便利だなと思い、まずはGit、GitHubをUSBで持ち運べるようにしました。環境はWindowsを想定しています。  
この記事では、以下の項目を達成します。
- USBにインストールしたブラウザからGitHubのサイトのログイン状態を維持
- GitからGitHubへプッシュやプルする時に必要な認証情報をUSBに保持
- GitHub CLI(ghコマンド)を使用可能

## Portable Gitのインストール
まずはポータブル版のGitをダウンロードインストールします。
1. [公式ホームページ](https://git-scm.com/download/win)からPortable版をダウンロードする
1. USBの直下にインストールする
1. 正しくインストールされたか確認する。USB直下にある、git-bash.exeをダブルクリックし、そのシェルに`git --version`と入力し、バージョンが表示されればよい。

## Gitの設定
次にGitの初期設定を行います。
1. /home/\<username>ディレクトリを作成する。/home/\<username/の部分は適宜読み替えてもらって大丈夫です
1. 下のように、/etc/profileの末尾に`HOME=/home/<username>`を追記する。こうすることで`~/.config/`ディレクトリに設定ファイルを保存するソフトであっても、設定ファルごとUSBに入れて持ち運ぶことができます。
    ```shell
    ~~~ 省略 ~~~
    unset MAYBE_FIRST_START
    
    HOME=/home/<username>/
    ```
1. gitの初期設定を行う
    1. `git config --global user.name "<name>"`:ユーザ名を設定する
    1. `git config --global user.email "<email>"`:Eメールを設定する
    1. `git config --global safe.directory '*'`:信頼するディレクトリを指定。USB内のディレクトリはデフォルトでは信頼されていないディレクトリとして扱われる。`*`とするとすべてのディレクトリを信用するとこになるので、適宜ディレクトリを指定するほうがよいかと思う
1. 初期設定が適切に行われているか、確認する。~/.gitconfigファイルの中に先程設定した3項目が存在することを確認する。
    ```shell
    $ cat .gitconfig
    [user]
            name = KashiuchiSotaro
            email = XXXXX@gmail.com
    [safe]
            directory = *
    ```

## Browserのインストール
ブラウザをダウンロード、インストールします。ブラウザは主にGitHubのサイトを閲覧するために使用することを想定しています。そのため、GitHubへ毎回ログインしなくて良いように、USB内にcookieや認証情報が残っていてほしい。それらにデフォルトで対応しているブラウザはFireFoxしか確認できませんでした。(GoogleChrome, Operaも調べてみたのですが、デフォルトではセッション状態をパソコンをまたいで保持できませんでした。)そのため今回はFireFoxのポータブル版をインストールします。
1. [PortableApps](https://portableapps.com/apps/internet/firefox_portable)からダウンロードする
1. USB配下の好きなところにインストールする
1. インストールしたFireFoxのブラウザを使用し、GitHubのアカウントにログインする

## GitHub CLIのインストール&コピー
1. GitHub CLIの[公式ホームページ](https://github.com/cli/cli)に行き、Windowsのコマンドプロンプトで`winget install --id GitHub.cli`を実行する
1. C:/ProgramFile/Github CLI/gh.exeをUSBの/usr/bin/ディレクトリ配下にコピーする


## GitHub CLIの設定
GitHub CLIの設定ファイルを作成する
- ~/.config/ghディレクトリを作成する
- ghコマンド(GitHub CLI)が先程作成したディレクトリから、設定ファイルを読み込むように、/etc/profileの末尾に`export GH_CONFIG_DIR=/home/<username>/.config/gh/`と環境変数を追記する
- ghコマンドから呼び出されるブラウザを指定するために、次のコマンドを実行する。`gh config set browser "<Path>/FireFoxPortable.exe"` このコマンドの\<Path>部分にFireFoxをインストールした場所を指定する

## アクセストークを生成
Gitはリモートリポジトリの認証システムを外部のソフトに任せている。それらの話は[こちら](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E3%81%95%E3%81%BE%E3%81%96%E3%81%BE%E3%81%AA%E3%83%84%E3%83%BC%E3%83%AB-%E8%AA%8D%E8%A8%BC%E6%83%85%E5%A0%B1%E3%81%AE%E4%BF%9D%E5%AD%98)や、[こちら](https://zenn.dev/miya789/articles/manager-core-for-two-factor-authentication)で解説されている。その外部の認証システムとして今回はGitHub CLIを使用する。
1. `gh auth login --insecure-storage`とコマンドを入力することで、認証に必要なプロンプトが表示される。`--insecure-storage`オプションをつけると、認証情報を平文で保存するらしい(Save authentication credentials in plain text instead of credential store)。この平文の認証情報は~/config/gh/ディレクトリの中に保存されるため、USBで認証情報を持ち運ぶことができる。しかし平文で認証情報を持ち歩くことになることを理解しておかなければ行けない。デフォルトではOSのセキュアストレージに保存するようです([参考](https://github.com/cli/cli/releases/tag/v2.24.0), [参考](https://blog.kyanny.me/entry/2023/04/11/112410))
1. 以下の写真のようにプロンプトに沿って認証を行う。
    ![image](/blog.jp/assets/items/2023-11/2023-11-04-gh-auth-login.png)
1. アクセストークンが正常に生成され、USB内に保存されているかを確認する。`gh auth status`コマンドで確認することができる。
1. またGitがgithub.comに操作する時に、GitHub CLIが呼び出されるようになっているかを確認する。~/.gitconfigファイルを開き下のようになっていればよい。credential.helperの`!`はシェルとして呼び出すらしい
    ```shell
    [user]
            name = KashiuchiSotaro
            email = XXXXX@gmail.com
    [safe]
            directory = *
    [credential "https://github.com"]
            helper =
            helper = !'F:\\usr\\bin\\gh.exe' auth git-credential
    [credential "https://gist.github.com"]
            helper =
            helper = !'F:\\usr\\bin\\gh.exe' auth git-credential
    ```

## まとめ
これで、USBにインストールしたFireFox上でGitHubのサイトを開くことで、ログインし直さずに閲覧することができる。また、GitHubへの認証も毎度しなくてよく、`gh`コマンドが使用も使用できるようになった。  
問題としてはとんでもなくブラウザが遅いこと。これは私のUSBの速度が遅いのかもしれませんが、ブラウザを立ち上げて操作をすると、USBへのアクセスが集中しカクつきました。またできればGoogle Chromeを使いたいなと思っています。最終的には、USBにcookieなどの認証情報のプロファイルだけ保存されており、ブラウザの本体はパソコンにインストールされているのを使うという状態にできれば良いなと思っています。(現在考え中

