﻿## 概要
https://github.com/shinq/FallGuysRecord

PC版フォールガイズ(Fall Guys)向けの参加者戦績を集計するアプリです。

Fall Guys 起動してからの全参加者の戦績を Player.log から収集します。

https://github.com/circumark994/fallballstats

で作成された「フォールボール勝率収集アプリ」を元に汎用化したものになります。

独自のスコアリングルールを追加できるので、大会運営での戦績自動収集などに使えるかと思っての実験的なものです。

こちらのアプリは汎用化目的のものであり、フォールボール用は FallBallStats のほうがより詳細な情報を出力します。

※成績下位者も可視化されてしまう、参加者名が断りなく見えてしまう、といったあたりに懸念があり、大会運営用に裏で使うことや個人的な興味には有用ですが、このツールの情報を見せてしまうのは問題があるかもしれません。公開をやめて、入り用の方に特別にお渡しする、という配布方式に変更する可能性があります。カスタムのみに制限するといった対策もありえますが検討中です。

![実行イメージ](/screenshot.png?raw=true "実行イメージ")

## 初期設定
* Java 実行環境をインストールする必要があります。(https://java.com/)

## 使い方
FallGuysRecord.jar をダブルクリックします。


## 機能概要
* 画面左下のドロップダウンで総合ランキングの集計ポリシーを選択できます。現在は以下を用意。
  * Final/Win：決勝進出者10pt、優勝者30pt として集計するモードです。
  * Feed Point：Final/Win のルールに加え、レース/ハンティングラウンドでの１位に 4pt を付与するモードです。細かい大会ルールへの対応実験です。
  * Squads：Squad 単位で決勝進出10pt、優勝30ptとして集計します。自身が優勝しなくても所属スクワッドの優勝で30pt となります。
  * FallBall：FallBall の試合結果だけを集計するモードです。
  * Sweet Thieves: キャンディショーだけの戦績を集計するモードです。ガーディアン時、シーフ時それぞれの勝率を出力できます。
  * Snipes: ネタ的に、スナイプ数ランキングを表示します。同じマッチにいた回数ランキングです。

* 「マッチ一覧」は「ラウンド一覧」をショー単位表示にする目的のものです。「総合ランキング」には影響しません。
* 「ラウンド一覧」で選択したラウンドの結果が「ラウンド詳細」に表示されます。
* 「ラウンド詳細」はラウンド内の状況がリアルタイムで更新されます。ラウンド中に現在のラウンドを表示しておくと興味深いです。
* 「ラウンドから参加者を外す」は、fallball での審判除外機能に基づいています。大会不参加のプレイヤーをラウンド情報から消すことで「総合ランキング」に反映されます。
  * 現在はアプリを起動中のみ除外情報を保持します。アプリを再起動した場合、再度この機能で除外指定を行う必要があります。
  * 「マッチから参加者を外す」は選択しているマッチ内の全ラウンドから除去するものです。

## 制限、注意など
* 自分が抜けたあとのラウンド情報は記録されないので取得できません。
* FallGuys を再起動するとこれまでの情報は消えて最初からになります。状態保存は後に対応予定です。
* ラウンドごとのスコアは随時出力されるものとそうでないものがあります。ラウンド終了後に獲得スコアが出力されるのでそれを()内に表記しています。
 * レースの場合は順位ベースのスコア(サーバベースの順位スコア)、ハンティングの場合はラウンド中獲得ポイント(貢献度スコア？)、サバイバル系は1pt(生存秒数ベーススコア)です。
* 総合ランキングでのスコアはモードごとに算定基準が異なります。ラウンドごとのスコアとは別の概念です。
* m戦n勝表示部分 (n/m 表示)は、基本的には優勝数/参加マッチ数になります。集計モードによっては勝利数/参加ラウンド数になったりします。

## 履歴
2022/05/08 v0.95
* パーティを可視化。ここまでやってしまうと正直危ないツールになってしまっている気もするが…。
* rates / RankingMaker 周りリファクタ。基本的に優勝数/参加マッチ数を表示する形に変更。特定種目のみ勝利/参加ラウンド数、とする形。
* round 詳細でリアルタイムに進行状況を表示。
* マッチから参加者を外すボタンを追加。大会主催者向け、あるいは集計で見せたくないプレイヤーを除外する目的など。
* finalScore を () 内に表示。
* 自分に★マークを付けて見やすく。

2022/05/07 v0.94
* path.ini を不要にして Player.log は自動で見つけるように修正。
* カスタムマッチの開始を検出できていなかったバグを修正。

2022/05/06 v0.93
* スクワッドランキングモードを追加。スクワッドとして決勝進出、優勝すればポイント加算される。
* スクワッドのラウンド詳細表示を、スクワッド単位順位と個人順位両方表示。
* ラウンド中、ハンティング獲得ポイントを表示。ただしラウンド終了後、貢献度スコアとおもしき物で上書きされる。
* スクアッドスコア基準の「参加者数」について、ラウンド開始前に切断した人数も含むようなので調整。
* 新たなラウンド開始時にそのラウンドが選択される仕様に。

2022/05/06 v0.92
* スクワッド単位順位表示対応。
* snipe ranking 追加(ネタ)。
* ウインドウサイズ変更に対応。

2022/05/05 v0.91
* 順位表示修正。
* 決勝で脱落した際に獲得クドス情報がステージ終了前に出力されたことで正しく修了判定できていなかったバグ修正。

2022/05/04 v0.9 committed
