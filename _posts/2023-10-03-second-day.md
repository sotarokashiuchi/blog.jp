---
layout: post
title: "2023/10/03 日記"
date: 2023-10-03 23:00
description: 夏休み明け、授業開始...
tags:
 - 日記
---

昨日から学校が始まりました。
電気回路という授業では直流から交流への分野へと内容が前期と一変するようです。一回目の授業はオリエンテーションだったため、なんとも言えませんが、回路図の設計とかできるようになるのかと、少し期待しています。
情報工学実験ではLEGOのEV3をC言語で制御する授業を行いました。私は中学2年生の時に既にしていたので、今の所問題なく進められています。授業では既にEV3RTの開発環境が整っており、プログラムを変更し、makeでコンパイルするだけでした。個人的には、開発環境を用意するところから授業をすればより理解が深まるのではないかと思いました。
情報処理ではC#を勉強し始めました。.NET Framewrokを用いて、Windowsアプリを制作するようです。C#はほとんど触ったことがないのでこれから勉強してみようかなと思ったり、思わなかったり。組み込み系のC、Web系のGo、デスクトップアプリ系のC#という感じで体系的に学ぶために勉強しようかな…?

自作Cコンパイラの方は、インクリメントとデクリメントを実装しました。i++をどのように実装するのかなと思っていましたが、((i += 1) -1)と評価すればよいということに驚きました。
