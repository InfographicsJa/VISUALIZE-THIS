7. Spotting Differences
====

## Running in Parallel
* Parallel coordinate
    * 他属性との関係性を視覚化する手法
    * 複数の軸をparallelに並べる
    * それぞれの軸のtopはmax, bottomはminを表す
    * lineは左から右へ描画され、値に応じて上下に動く
    * 例えば、バスケットボールを例にとり、それぞれのlineを選手、軸を得点、リバウンド数、ファウル数...とすると、得点が高い選手ほどファウル数も多いなどの傾向を見て取ることができる

* Create a Parallel Coordinates Plot
    * Protovis
    * GGobi
    * 異なるフィルターを一度に比較することができるため、interactiveではなく、staticなparallel coordinateがおすすめ
* Rの使い方...

## Reducing Dimensions
Chernoff FacesやParallel coordinatesを使う目的は、次元を下げることである。

* 多次元をクラスタリングによって低次元化できたらすばらしい。
* multidimensional scaling(MDS)のゴールの一つ
* MDSの例

## Make Use of Multidimendional Scaling
* なし

## Searching for Outliers
* outlier
    * 時にはそれはおもしろいものである
    * typoの場合もある
    * どちらにせよ何が起こっているのかチェックする必要がある
    * outlierを見つけたら強調するためにこれまで学んできた手法が使える

## Wrapping Up
* 初学者にとってデータグラフィクスをデザインする時に困難なことは、どこから始めるべきかということである
* 目の前にデータだけある
* 普通はデータに対して疑問を投げかけることから始めるべきである
* 何を疑問に持つべきかわからなければ本章が役立つだろう
* 一度にすべてのデータを俯瞰する方法を使えば、次にどの部分を解析すべきか見えてくる

## References
* protovis  
    * Parallel Coordinates <http://mbostock.github.com/protovis/ex/cars.html>
* eagereyes
    * <http://eagereyes.org/techniques/parallel-coordinates>


## Parallel Coordinates
* The Technique
    * 最も有名なvisualization techniqueの一つ
    * visualizationの分野では一般的
    * はじめは混乱するかもしれないが、多次元データセットを理解するためのツールとしてとてもpowerfulである
    * 多次元データを見るシンプルな方法はdata table
    * 全体を見るのではなくそれぞれの軸の間のスペースを見ると理解しやすい
    * categorical dataはparallel coordinatesには向かない
    * categoricalなdataのためにParallel Setsを開発した

*Brushing
    * parallel coordinatesのテクニックを使ってdataを理解するには、interactionも合わせると良い
    * parallel coordinatesではbrushingと呼ばれる方法がメイン
    * 範囲を指定し、その部分だけ色を変える

* Limitations
    * データが多すぎるとoverplotが生じ、可読性が下がる
    * 次元数も10次程度が限界
    * 前述のようにcategorical dataには向かない

* Software
    * visualizationの分野では文書はたくさんあるが、softwareはあまりない
    * browserでparallel coordinateで遊ぶには、protovisがある
    * parvisというjava実装のものもある

* conclusion
    * parallel coordinateは多目的に使える有用な手法である
    * 少しの経験によって、すばやくパターンを認識することができるようになる

