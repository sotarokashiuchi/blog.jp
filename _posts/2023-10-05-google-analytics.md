---
layout: post
title: "2023/10/05 日記"
date: 2023-10-05 23:00
description: エニアグラム診断を行いました。またこのサイトをGoogle Analyticsに登録しました。
tags:
 - 日記
---

エニアグラム診断を現代国語の授業として行いました。エニアグラム診断とは心理学的な見地から人間を9タイプに分類し、特徴を細かく分析するもの。自分のタイプ(性格)を理解し、今後の人生に役立てようとういうものです。私の診断結果はなかなか当たっていることが多かったです。診断前に自分なりに自分とはどのような性格かと考えており、その考えと、診断結果がほぼ一致したため、謎の満足感がありました。

現代の世界という授業では第一次世界大戦の始まりを勉強しました。同盟を結んでいることで、次々と世界大戦に参加する国が増えていくことを見て、同盟は一見すると良いように思えるが、同調圧力を発生させる材料となり得るのだと思いました。

このサイトをGoogle Analyticsに登録しました。このGitHub Pageでは_config.ymlにGoogle Analyticsの測定IDを記入することで、全てのサイトに必要なjava scriptが挿入されるようです。しかし、このjava scriptの内容が第四世代と古く、現在の最新は第五世代のため、うまく動きませんでした。参考サイト[Google Analyticsのバージョン](https://www.t-web.co.jp/blog/tracking-code/)
そこで、`_includes/google-analytics.html`というファイルを第五世代向けのjava scriptに変更し、これを引用している`_includes/header.html`ファイルにも変更を加えました。その結果、無事にGoogle Analyticsに登録することができました。

Google Search Consoleにもこのサイトを登録しました。こうすることで、Googleの検索のインデックスに登録されるようです。インデックスに登録されることで、検索に引っかかるようになるようです。Google Search Consoleにこのサイトのサイトマップも登録しました。サイトマップは_config.yamlファイルに以下のように記述すると自動的に生成されます。
```yaml
plugins:
  - jekyll-sitemap
```

