+++
title = "2023/10/08 日記"
date = 2023-10-08T23:00:00+09:00
tags = ['日記']
+++

## 10/03
昨日から学校が始まりました。
電気回路という授業では直流から交流への分野へと内容が前期と一変するようです。一回目の授業はオリエンテーションだったため、なんとも言えませんが、回路図の設計とかできるようになるのかと、少し期待しています。
情報工学実験ではLEGOのEV3をC言語で制御する授業を行いました。私は中学2年生の時に既にしていたので、今の所問題なく進められています。授業では既にEV3RTの開発環境が整っており、プログラムを変更し、makeでコンパイルするだけでした。個人的には、開発環境を用意するところから授業をすればより理解が深まるのではないかと思いました。
情報処理ではC#を勉強し始めました。.NET Framewrokを用いて、Windowsアプリを制作するようです。C#はほとんど触ったことがないのでこれから勉強してみようかなと思ったり、思わなかったり。組み込み系のC、Web系のGo、デスクトップアプリ系のC#という感じで体系的に学ぶために勉強しようかな…?

自作Cコンパイラの方は、インクリメントとデクリメントを実装しました。i++をどのように実装するのかなと思っていましたが、((i += 1) -1)と評価すればよいということに驚きました。

## 10/05
エニアグラム診断を現代国語の授業として行いました。エニアグラム診断とは心理学的な見地から人間を9タイプに分類し、特徴を細かく分析するもの。自分のタイプ(性格)を理解し、今後の人生に役立てようとういうものです。私の診断結果はなかなか当たっていることが多かったです。診断前に自分なりに自分とはどのような性格かと考えており、その考えと、診断結果がほぼ一致したため、謎の満足感がありました。

現代の世界という授業では第一次世界大戦の始まりを勉強しました。同盟を結んでいることで、次々と世界大戦に参加する国が増えていくことを見て、同盟は一見すると良いように思えるが、同調圧力を発生させる材料となり得るのだと思いました。

このサイトをGoogle Analyticsに登録しました。このGitHub Pageでは_config.ymlにGoogle Analyticsの測定IDを記入することで、全てのサイトに必要なjava scriptが挿入されるようです。しかし、このjava scriptの内容が第四世代と古く、現在の最新は第五世代のため、うまく動きませんでした。参考サイト[Google Analyticsのバージョン](https://www.t-web.co.jp/blog/tracking-code/)
そこで、`_includes/google-analytics.html`というファイルを第五世代向けのjava scriptに変更し、これを引用している`_includes/header.html`ファイルにも変更を加えました。その結果、無事にGoogle Analyticsに登録することができました。

Google Search Consoleにもこのサイトを登録しました。こうすることで、Googleの検索のインデックスに登録されるようです。インデックスに登録されることで、検索に引っかかるようになるようです。Google Search Consoleにこのサイトのサイトマップも登録しました。サイトマップは_config.yamlファイルに以下のように記述すると自動的に生成されます。
```yaml
plugins:
  - jekyll-sitemap
```

## 10/08
英検準2級を受験しました。夏休み中に勉強し、挑んだのですが、手応えがありません…
次に向けてがんばります。

夏休みの活動をまとめました。リンクは[こちら](/2023/10/summer-vacation)

ここで今後の目標と予定を整理しておきます。

- 明日からオンライン英会話をはじめて見る
- 10月10日にある石川高専のデジタル人材リテラシーという授業の試験を合格する！
- 10月15日までにCコンパイラのセルフホストを実現させる!
- 新しい部活作成のために必要な情報を収集し、計画を立てる

