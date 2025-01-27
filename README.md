﻿## 概要
https://github.com/shinq/FallGuysRecord

PC版フォールガイズ(Fall Guys)向けの参加者戦績を集計するアプリです。

Fall Guys 起動してからの全参加者の戦績を Player.log から収集します。

https://github.com/circumark994/fallballstats

で作成された「フォールボール勝率収集アプリ」を元に汎用化したものになります。

独自のスコアリングルールを追加できるので、大会運営での戦績自動収集などに使えるかと思っての実験的なものです。

こちらのアプリは汎用化目的のものであり、フォールボール用は FallBallStats のほうがより詳細な情報を出力します。

※成績下位者も可視化されてしまう、参加者名が断りなく見えてしまう、といったあたりに懸念があり、大会運営用に裏で使うことや個人的な興味には有用ですが、このツールの情報を見せてしまうのは問題があるかもしれません。公開をやめて、入り用の方に特別にお渡しする、という配布方式に変更する可能性があります。カスタムのみに制限するといった対策もありえますが検討中です。
※ステージ中情報は使い方によってはゴースティングっぽい使い方(他者に知り得ない情報を自分だけが知った状態でのプレイ)に相当するので、これをゲームクリアや害悪行為のために使うのはやめてください。あくまで得られる情報を出してみただけで、作者には興味や知り合いを見つける以外の関心はありません。またこのような使い方が蔓延しそうであれば公開を取りやめます。

![実行イメージ](/screenshot.png?raw=true "実行イメージ")

## 初期設定
* Java 実行環境をインストールする必要があります。(https://java.com/)
* ダウンロード：上部の緑の「Code」ボタンから Download ZIP を選んでダウンロードし、展開してください。

## バージョンアップについて
* 更新版に差し替える場合、最新版 zip を展開後、もとの環境から state.dat / setting.ini ファイルだけ新しく展開したフォルダにコピーしてください。

## 使い方
* FallGuysRecord.jar をダブルクリックします。

## 機能概要
* 画面左下のドロップダウンで総合ランキングの集計ポリシーを選択できます。現在は以下を用意。
  * Final/Win：決勝進出者10pt、優勝者+10pt として集計するモードです。(初期設定での点数。settings.ini の書き換えで調整できます)
  * Feed Point：Final/Win のルールに加え、レース/ハンティングラウンドでの１位に 4pt を付与するモードです。細かい大会ルールへの対応実験です。
  * Squads：Squad 単位で決勝進出10pt、優勝+10ptとして集計します。自身が優勝しなくても所属スクワッドの優勝で20pt となります。
  * FallBall：FallBall の試合結果だけを集計するモードです。
  * Sweet Thieves: キャンディショーだけの戦績を集計するモードです。ガーディアン時、シーフ時それぞれの勝率を出力できます。
  * Snipes: ネタ的に、スナイプ数ランキングを表示します。同じマッチにいた回数ランキングです。

* 「マッチ一覧」は「ラウンド一覧」をショー単位表示にする目的のものです。「総合ランキング」には影響しません。
 * (NEW)画面下部に、選択したマッチの開始終了時刻と接続先サーバ情報が表示されます。
* 「ラウンド一覧」で選択したラウンドの結果が「ラウンド詳細」に表示されます。
* 「ラウンド詳細」はラウンド内の状況がリアルタイムで更新されます。ラウンド中に現在のラウンドを表示しておくと興味深いです。
* マッチ一覧の下部にある「ラウンド参加者選択」は、選択した参加者に対して右側でなにか操作するためのものです。現在選択しているラウンドの参加者リストになります。
* 「ラウンド参加者選択」の横には、その参加者の表示スタイル選択があります。ラウンド詳細で特定参加者を目立たせる目的のものです。用途はご自由に。
* 「ラウンドから参加者を外す」は、fallball での審判除外機能に基づいています。大会不参加のプレイヤーをラウンド情報から消すことで「総合ランキング」に反映されます。
  * 現在はアプリを起動中のみ除外情報を保持します。アプリを再起動した場合、再度この機能で除外指定を行う必要があります。
  * 「マッチから参加者を外す」は選択しているマッチ内の全ラウンドから除去するものです。
* settings.ini を書き換えてから起動することで、付与するポイント、ランキング部分のフォントサイズ、ラウンド名表示言語を変更できます。

## 制限、注意など
* 自分が抜けたあとのラウンド情報は記録されないので取得できません。
* FallGuys を再起動するとこれまでの情報は消えて最初からになります。状態保存は後に対応予定です。
* ラウンドごとのスコアは随時出力されるものとそうでないものがあります。ラウンド終了後に獲得スコアが出力されるのでそれを()内に表記しています。
  * レース：順位ベースのスコア(サーバベースの順位スコア)
  * ハンティング：ラウンド中獲得ポイント+クリア順位スコア(獲得ポイント) →FallGuysバグでこのような状況になっている
  * サバイバル：生存秒数ベーススコア
  * チーム：1pt(1pt)
* 総合ランキングでのスコアはモードごとに算定基準が異なります。ラウンドごとのスコアとは別の概念です。
* m戦n勝表示部分 (n/m 表示)は、基本的には優勝数/参加マッチ数になります。集計モードによっては勝利数/参加ラウンド数になったりします。
* 参加者のスタイルを総合ランキング部分表示にも反映させたいですがまだです。
* スタイルを設定ファイルでカスタマイズできるようにするのもまだです。
* ある参加者がいたら通知を出す、なんて機能も考えていますが悪用とのバランス上どこまでやるか、というところ。
* TOP/OWN タイム表示は、「ステージ開始」「プレイヤー消失」ログが出力された時刻の差で表示しており、厳密な時刻とはいえません。FallGuysStats でも同じです。0.1-0.3くらいの誤差はありえます。
* マッチの開始時刻はマッチングで数値が出た時刻-最終ラウンドが終了した瞬間の時刻です。１マッチにかかった時間総数とは少し異なります。次のマッチ開始時刻との差が実際にかかった時間と言えます。

## 履歴
2022/10/28 v0.994
* Treet Thieves 対応

2022/10/15 v0.993
* メインプログラムに余計なファイルまで含まれていたのでビルド環境改善(ソースファイル位置を移動)。

2022/10/14 v0.992
* ハンティングラウンドを以下に分類し、1st 判定対象を限定した。
 * 規定スコア先着勝ち抜け方式(HUNT-RACE)：大抵のハントはこれ
 * 制限時間時点でのスコア勝負(HUNT-SURVIVE)：ボタン、バレー
 * しっぽおにだけはいずれでもない(しっぽ所持時間スコアなど出力もされない)ため順位を取り扱わなくする。内部的に TEAM に分類させた。
 * RACE/HUNT-RACE以外の種目は集計時１位にポイントという対象から外している。
   HUNT-SURVIVE は最高得点者を一位とすることも可能だが同率もありうることから対象外に。
* 順位順表示について、これまでスコア順としていたが、qualified 順を基本とした。
  勝ち抜け系ハンティングで後から基準点を超えるスコア獲得者が上位に来る問題に対応。
  スクワッドでも個人獲得スコア表示はそのままだがスクワッドスコアとしては通過順位ベーススコアを加算して順位ズレを抑制した。

2022/10/06 v0.991
* ランキング、ラウンド詳細部分に余白を少し追加。
* しっぽ鬼をHUNTING扱いにしていたが、勝ち抜け方式でないため順位を決めることができないのでSURVIVAL扱いとして順位スコア対象外とした。
 * これまではqualifiedが最初に出力されたプレイヤーが一位扱いになってしまっていた。
* ハンティングの順位バグに暫定対応。
 * 現在、ハンティングラウンドでは正確な順位を出せなくなっている。ゲーム本体もバグっていて獲得スコアの多い順にメダルが授与されている。
 * バグが発生する前は、クリアした人に獲得スコアに加えてクリア順位スコアが加算されていたことで結果的に正しい順位となっていた。
 * 同様の制御をアプリ内で入れて、ログに出力されたスコアを信用しないようにした。
   ただし、スクワッドで３人チームが１位で４人チームが２位だった場合にスコア逆転になってしまうことはある…。
* 通常ステージやピクセルファイナルでの優勝確定時、それらのステージをファイナル扱いとして正しく優勝判定できるようにした。これまでは優勝判定できていなかった。
 * ただし、優勝が決まったステージをファイナルであるとみなす、という対応なので、そのステージ出場者にはファイナル進出ポイントも付与されることになる。
* ヘックスマラソンの予選がファイナルとみなされない対応。相変わらずファイナルであるか否かをきれいに判定する手段が提供されていない…。
* duo で少人数サッカーなどが決勝と判定される問題に対応。
* ランキング、ラウンド詳細以外の箇所のフォントサイズを settings.ini で指定可能とした。デフォルトは
  FONT_SIZE_BASE=12


2022/09/01 v0.990
* マッチ開始終了時刻/連勝数/サーバ情報をマッチごとに保持し、マッチ選択時に下部表示に反映するよう修正。
* TOPゴール時刻、自分のゴール時刻をラウンド詳細に表示するよう修正。目安として使えます。

2022/08/25 v0.986
* ビクトリー、バンジャーの決勝判定対応。SS2新ステージ対応。

2022/08/11 v0.985
* ジェリービーンズヒルゾーン対応。

2022/08/08 v0.984
* isFinalRound ログが出力されなくなっており final 判定が動作しない影響。サバイバルスクワッドに対応。内部ラウンド名の法則がかなり適当になっている。正直ログの方なおして欲しい…。

2022/07/28 v0.983
* isFinalRound ログが出力されなくなっており final 判定が動作しない影響。決勝ラウンドが予選に出てくるものの対応。またゲーム側ラウンド名が変わっていた。正直ログの方なおして欲しい…。

2022/07/17 v0.982
* 統計表示欄の名前部分からプラットフォーム表示は不要なので外す。

2022/07/16 v0.981
* isFinalRound ログが出力されなくなっており final 判定が動作しない影響。決勝ラウンドが予選に出てくるものの対応。正直ログの方なおして欲しい…。

2022/07/3 v0.980
* isFinalRound ログが出力されなくなっており final 判定が動作しない影響。GG の決勝判定も追加。正直ログの方なおして欲しい…。
* サバイバルラウンド中の生存秒数スコアがログ出力されないので０だったのを、自力でスコア加算するように修正。
  * 正確とはいえないが、ラウンド終了後にゲームで認識されているスコアを()内に表示する。
  * これで、自分より下位チームが全滅している(安心)かどうかなどがすぐに確認できるようになった。

2022/07/3 v0.979
* isFinalRound ログが出力されなくなっており final 判定が動作しない影響。
  * スパルタンの二戦目パキパキがファイナル判定されるのを回避。
  * ビクトリーの決勝チーム戦の検出漏れ。

2022/06/28 v0.978
* isFinalRound ログが出力されなくなっており final 判定が動作しないため、特定スクワッドチームラウンドを final とみなす対応。

2022/06/22 v0.977
* isFinalRound ログが出力されなくなっており final 判定が動作しないため特定ラウンドを final とみなす対応。
* ただし、マラソンや hex show などファイナルステージが final 以外で出てくるもので正常に動作しなくなる。

2022/06/21 v0.976
* プレイヤー名検出処理修正。S7でログ出力が変わっていたため。switch 版ユーザも正しく取得。

2022/06/20 v0.975
* S7ステージデータを投入。ある程度の動作確認。
* ユーザのプラットフォームも表示。(switch が正しく表示されるかは未確認)
* アプリ終了時にすべてのマッチの接続サーバ情報統計をコンソール出力。

2022/06/02 v0.973
* 接続サーバの表示について、IPからサーバの概ねの地域を検出して表示するよう修正。
  * 韓国を選んでいれば大体はシンガポールに繋がる。などがわかるように。Japan がどこに繋がるのかの調査として作成。country, region, city と timezone を表示している。
  * 日本を選んでカスタムを開始すると必ず Tokyo に繋がるようになっていたのでカスタムは日本を選んで開く、が基本になりそう。

2022/06/01 v0.972
* メインショーで獲得スコアを正常に読み取れないケースが有ったバグを修正。
* Player.log の出力に不正な情報(メインショーラウンド時に過去のスクワッドラウンドの戦績)が吐かれるようになってしまっていたため無視するよう修正。

2022/05/20 v0.971
* 多重起動抑制対応
  * この対応のためポート29878でサーバソケットを開こうとするので初回ネットワークアクセス警告が出るようになっておりますが、通信はしておりません。

2022/05/19 v0.97
* 知人などにマーキングすることで参加者一覧で色付けする機能を追加。アプリ終了後も記憶。様々な目的で利用できる。
* bot は名前が _ 始まりなので Bot_xxxx 表記にしてみる。

2022/05/15 v0.96
* settings.ini で付与するポイント、ランキング部分のフォントサイズ、ラウンド名表示言語を指定できるよう修正。(全域の国際化はまだ)

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
