---
layout: post
title: "2023/10/09 日記"
date: 2023-10-09 23:00
description: 
tags:
 - 日記
---

&&演算子と||演算子を実現させるため、CコンパイラのBNF記法をもう一度読み直しました。私が読んだC言語のBNFはK&Rで定義されているものだったため、それをC99に対応させる必要があるなと思いました。しかし、&&演算子と||演算子を実装するだけでは、そこまで問題ないのでとりあえずはおいておき、今はK&RのBNFを私のプログラムに対応させて行きました。
BNFはプログラムで実装しやすいように手を少し加えたり、EBNF記法で書いたりと変更しました。例えば以下のコードの内、上を下のように変換したりしました。

```
<conditional-expression> ::= <logical-or-expression>
                           | <logical-or-expression> ? <expression> : <conditional-expression>
```
```
<conditional-expression> = <logical-or-expression> ( "?" <expression> ":" <conditional-expression> )?
```

```
equality_expr 		= relational_expr | equality_expr ("==" | "!=") relational_expr
```
```
equality_expr 		= relational_expr (("==" | "!=") relational_expr)*
```

C言語のBNFを読むコツはstatement系, expression系, その他共通部分をまとめる系の3つに分類することです。これを意識することで、だいぶ理解が進みました。
また、&&と||を実装するにあたり、短絡評価というものを意識する必要性を知りました。&&であれば、左の式が偽なら、右は評価しない。||であれば、左の式が真なら、右は評価しないなどのことです。無事実装できました。



今日初めてオンライン英会話をしました。こんなに難しいのかと思いました。

