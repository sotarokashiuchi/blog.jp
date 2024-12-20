+++
title = "Zellijの便利な機能"
date = 2023-09-28T16:20:00+09:00
tags = ['技術']
aliases = ["/2023/09/zellij/"]
+++


## 経緯
- NeoVimを使いはじめたので、Terminal Multiplexerも始めようと思いいろいろ試した結果Zellijが僕にとって使い勝手が良かった(Tmuxではないんか（笑）)
- Zellijを少し使い、便利な機能や設定を見つけたので紹介する

## Zellijの概要とインストール
- Zellijの概要やインストール方法は、以下の記事が非常に参考になった
- [Rust製ターミナルマルチプレクサのZellijに入門してみる](https://zenn.dev/gosarami/articles/4becaa18273216fec5ee)というサイトが非常に参考になる
- [Zellijの公式サイト](https://zellij.dev/)

## 設定ファイル
- ZellijはKDL形式の`config.kdl`設定ファイルに設定を記述する
- 設定ファイルの検索順序は以下の通り
    - Zellij実行時にオプション(`--config`, `--config-dir`)として設定ファイル又はディレクトリを指定
    - `ZELLIJ_CONFIG_DIR`という環境変数
    - `$HOME/.config/zellij`ディレクトリ
    - 以下のディレクト(default location)
        - Linux: `/home/alice/.config/zellij`
        - Mac: `/Users/Alice/Library/Application Support/org.Zellij-Contributors.Zellij`
    - `/etc/zellij`ディレクト(system location)
- 基本的に`$HOME/.config/zellij`に設定を記述していけばよい

## Theme
- Theme(テーマ)の変更方法を紹介する

### 既存のThemeから選ぶ
> config.kdl
{:.filename}
{% highlight bash %}
// Choose the theme that is specified in the themes section.
theme "ThemeName"
{% endhighlight %}
- [Theme](https://zellij.dev/documentation/theme-gallery)のサイトから好きなテーマを選ぶ
- config.kdlの`theme`の値に選んだテーマのThemeNameを記入する。ThemeNameは空白を`-`、大文字を小文字に変更すれば良い。

### 自分でThemeをカスタマイズする
> config.kdl
{:.filename}
{% highlight bash %}
// Choose the theme that is specified in the themes section.
theme "ThemeName"

// The folder in which Zellij will look for themes
theme_dir "/path/to/my/theme_dir"
{% endhighlight %}

> theme.kdl
{:.filename}
{% highlight bash %}
themes {
    ThemeName {
        fg 1
        bg 10
        black 20
        red 30
        green 40
        yellow 50
        blue 60
        magenta 70
        cyan 80
        white 90
        orange 254
    }
}
{% endhighlight %}

- Theme用の設定ファイルを、`$HOME/.config/zellij/themes/`ディレクトリ配下に置く。このディレクトリに置くことで、自動的にconfig.kdlから読み込まれる。このディレクトリ以外のディレクトリにTheme用の設定ファイルを置きたい場合はconfig.kdlに`theme_dir`にTheme用の設定ファイルを置くディレクトリを指定する
- Theme用の設定ファイルに、ThemeNameとそれに対応する設定を記入する
- config.kdlファイルの`theme`の部分の値として、themeの名前(ThemeName)を記入する
- 上記の設定で、テーマの変更ができる。私はnvimにeverforestというテーマを使用しているので、Zellijでも同じ設定を使用した。こうすることで統一感が出て美しい(気がする)。[everforest-dark-zellij](https://github.com/JotunnBeowulff/everforest-dark-zellij)から取得できる

## Scrollback Editor
- pane単位でshellの出力等をエディタで扱うことができる機能
- `ctr + s`を押した後、`e`を押すことでエディタを起動できる。

> config.kdl
{:.filename}
{% highlight bash %}
// Path to the default editor to use to edit pane scrollbuffer
scrollback_editor "/usr/bin/nvim"
{% endhighlight %}
- デフォルトでvimエディタが起動するようになっているので、config.kdlファイルの`scrollback_editor`に任意のエディタを指定することで、起動するエディタを変更できる。
- 私はnvimを指定した。こうすることで、コマンドの出力結果やコマンドをnvimを介して、コピーすることができ、非常に便利

## ToDo
- copy系の記述(何ができるのかよくわかっていない)
- layout系の記述
