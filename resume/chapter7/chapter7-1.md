### Chapter 7 前半

### Spotting Differences
* 複数の評価軸の表現、common senseを使って.

### what to Look For
* 1変数での比較は簡単.
  * 猫の重さ…
* 2変数だと少し難しくなるが,まぁ可能.
  * 猫の重さ&毛の長さ
* 猫が100匹居たら? もっと変数が多くなったら?
* バスケットボール選手
  * リバウンド,スティール,ゲームあたりのプレイ時間…
  * 類似性や関係性を意識しつつ,違いを見つけたい(スポーツコメンテータのように).

### Comparing across Multiple Variables
* 思考が止まらないのであれば,全部の変数とsubsetを見ても良いが…
  * 全てのデータを一度見て,関心のある点から次の関心のある点へと見ていくのが良いこともある.

### Getting Warmer
* Heatmap
  * テーブル構造のデータを全て一度に見るための,最も直接的なvisualization.
  * 数字の代わりに色をValueとして使う.
  * 典型的には,Dark Colorsは大きい値,Lighter colorsは小さい値だが,変えても良い.
  * 大きいテーブルデータだとそれでも混乱することがあるが,正しい色使いと,幾らかのソートを行えば役立つ表現となる.

### Create a Heatmap
* RでHeatmapを描こう!
  * [2008年のNBAの選手データ(22カラム)](http://datasets.flowingdata.com/ppg2008.csv)をRにread.csv()で読ませる
  * 初期状態では point per gameでソートされているが,order()で任意項目のソート. リバウンド数とか.
  * heatmap()で描画.[Figure 7-3]
  * 色指定のオプションcm.colorsなど…
	  * もっと熱い感じに.[Figure 7-3]
* 色を選ぶなら => [0to255.com](http://0to255.com)
* 自分で色選びしたくないなら RColorBrewer packageを使うと良い. [Figure 7-7]
 * [interactive version of Colorbrewer](http://colorbrewer2.com)
 * illustratorで良い感じに仕上げる[7-8]

### See It in His Face
* チャーノフの顔(Chernoff Faces)
  * 一般的なAudienceには混乱させることになる可能性がある.
  * [Figure 7-9]
     * 耳,髪,目,鼻がある顔
     * 現実世界における人の顔として読むことで,小さな違いを認識する.
   * 大きいValueを大きな耳や大きな目,という風に顔の各部位の傾向をValueの傾向から反映させる.
  * サイズに加えて,口のカーブや顔の輪郭の形、のような対応表現もある.

### Create Chernoff Faces
* NBA選手データを使う
 * aplpackにfaces()関数があるのでこれを使う.
 * カラムと,対応する顔の部位のパラメタの対応を定義する(15)
   * 輪郭の高さ,幅
   * 輪郭の形
   * 口の高さ,幅
   * 唇の曲がり具合(Curve of Smile)
   * 目の高さ,幅
   * 髪の高さ,幅
   * ヘアスタイル
   * 鼻の高さ,幅
   * 耳の高さ,幅
* 顔の例　[Figure 7-10]
* 州ごとの犯罪率をChernoff Facesで表現[Figure 7-13]したら,人種差別主義的だと言う人がいた

### Star Chart / Radar Chart / Spider Chart
* いわゆるレーダーチャート [Figure 7-14]
  * Rで[州ごとの犯罪発生率データ](http://datasets.flowingdata.com/crimeRatesByState-formatted.csv)をStar Chartで描く
* stars()で描く.[Figure 7-15]
* ラベルとキー付き[Figure 7-16]
* 半円(上向き)内で描く[Figure 7-17]
* ナイチンゲールチャート(Polor Area Diagramsとも言う)[Figure 7-18]
  * もし使うのであれば,デフォルトの狂った色使いは変更した方がいい.