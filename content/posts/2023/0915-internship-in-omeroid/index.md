+++
title = "インターンシップ in omeroid"
date = 2023-09-15T17:30:00+09:00
tags = ['体験記']
+++

## 概要
- 2023/09/04から14日までomeroidという会社のインターンシップに参加させていただきました。
- 学べたことをつらつらと記しておきます。

## 行ったこと
主にomeroid社内で使用するツールの開発に参加しました。既に仕様が決まっており、それに合わせてIssuesが割り振られ、各インターン生が開発を進めていくものでした。初日は開発環境を構築し、二日目、三日目で、社員さんにライブコーディングなどを行ってもらい、開発の仕方を実践的に学びました。四日目以降はインターン生が各自開発を進めていきました。

## 技術
人事評価を相互に行うためのシステムを構築することを目的に開発を行いました。システム構成として、AWS上にデプロイし、Slackから人事評価を行うことを想定していました。開発で用いた技術を紹介します。実際に触ったのは以下の一部部分です。
- Golangで開発を行った
- OpeaAPIという規格に沿って記述されたyamlファイルを基に、oapi-codegenというツールを用い、コードを自動生成させていた。yamlファイルの定義から、入力と出力のインターフェイスを持った関数と、URLがマッピングされたコードが自動で生成される。生成された関数の中身を今回のインターンで実施した
- マイグレーションツールにはgooseというツールを使用した。マイグレーションツールを使用することで、データベースの変更、更新などが容易に管理できる
- ORM(Object Relational Mapping)にはSQLBoilerを使用した。ORMとはSQLを使用せずに、データベースを操作する手法。SQLBoilerは実際に存在するデータベースから、データベースを扱うためのプログラムを自動生成してくれる。例えばAテーブルの外部キーとしてBテーブルの主キーが設定されているデータベースがあるとすると、AテーブルとBテーブルを結合したデータを取得することができる関数が自動で生成され、その関数を利用すると簡単に結合後のデータを取得できたりすることが可能。
- GitHubActionを使用したCI/CDを採用。コンパイルエラーが発生するプログラムやテストが通らないプログラムをmainブランチにマージできないように管理されていた。またコマンド1つでAWSへデプロイができる
- Terraformというサービスを使用し、AWS環境の構築、破壊、変更が操作1つで行われていた
- クリーンアーキテクチャという設計手法を活用していた


## 学んだこと
一番の大きな学びとして日本の会社の雰囲気、会社で働くという意味です。会社で業務として開発を行うことにたいする実感がわきました。また、今回は仕様に沿ってプログラムを開発することしかできませんでしたが、僕は仕様に従ってプログラムを書くだけではなく、課題を発見し、課題を解決するために、仕様自体を設計できるなりたいなあと思いました。
もう一つは、やはり英語は必要であるということです。Golangなどの周辺のツールは新しく出てきたものが多く、詳しく説明されているのは英語のサイトが殆どでした。

以下は詳しく説明しませんが、学んだことを記しておきます。
- Web系の業界の概要
- 初速の大切さ どうせ頑張るなら最初に頑張る
- MacBookは本当に充電が長持ちする！
- C言語をベースとして作られたGolangの文法(Cコンパイラ自作中なので興味深かった)
- おすすめのキーボードを教えてもらった(https://ergodox-ez.com/)
- 人は食べ物で幸せになれる

## 最後に
- 本をいただきました！ありがとうございます。
- 英語を勉強します。
- 本当にomeroid様ありがとうございました！
