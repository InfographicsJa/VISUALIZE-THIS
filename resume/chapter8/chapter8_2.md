#Over Space and Time 
ここまでの例で、色、カテゴリーなどなど、伝えたいstoryに合わせて量的な観点からも質的な観点からも多くのタイプの可視化をできるようになっている（はず）。
しかし、もう一つの次元のデータ（ここでは位置情報を指している）を組み込むときには、時間と位置の変化を見ることができます。

Chapter4で時系列データを扱いましたが、そこに位置情報がつくと、地図上のパターンと変化を見ることができるようになります。そうすることで地域ごとにクラスタリングを行ったりなどが簡単になります。

##Small Multiples
Chapter6で学んだ方法を位置データにも応用します。

* Figure 8-24は棒グラフの代わりに小さな地図を利用します。
* 地図一つがある年を表しています。

こうすることで、変化を追いかけやすくなります。

##Take the Difference

変化を表現するのに必ずしも小さなmapを複数並べる必要はありません。１つの「差分」を表したmapの方が意味を持つこともあります。Figure 8-29のよな表現方法は、スペースをあまり使わず、変化を際立たせることができています。

* Figure 8-31は2005年の都市部に住んでいる人口の割合
* Figure 8-32は2009年の都市部に住んでいる人口の割合
* Figure 8-30は2005年から2009年にかけての都市部の人口の変化

差分を可視化したFigure 3-30を見ると、どの国が2005年から2009年の間に大きく変化したかというのが一目でわかります。

> For this particular example, it's clear that the single map is more infromative.

##Animation
　時間と位置の変化を表すのにより明確な方法はデータに動きをつけることです。個々のタイミングで図を切り取ったものを並べるよりも、１つ図で、起こった変化を表現することができるからです。

[the growth of Walmart across the United States (Figure 8-34)](http://datafl.ws/197 "")

アニメーションにすることで２つの大きな理由から興味を持ってもらえるようになる。

1. 時系列のプロット（年ごとに何件の店舗がオープンしたか）を見ることなく、Walmartの成長の過程を見ることができることである。
2. アニメーションだけを見ればいいため、特に知識を持たない読者にも即座に理解してもらいやすいことである。

###CREATE AN ANIMATED GROWTH MAP
ActionScriptで同じ事をやってみましょう（えー

* ActionScriptの地図ライブラリであるModest Mapsを使います
* [source code](http://book.flowingdata.com/ch08/Openings_src.zip "")

##Wrapping Up
* 地図は、データ自体に追加して位置情報を取り扱わなければならないため、トリッキーな可視化手法である。一方で、統計的なプロットだけで説明できた以上に深い説明を行うことが可能になります。
* このチャプターの例(Walmartの成長過程の可視化)はFlashを用いて行ったが、同様のことはJavascriptでもできます。どのツールを使うかは目的によります。
* ソフトウェアにかかわらず、大事なのはロジックである。シンタックスは変わるかもしれないが、同じ事は実現できる。

>The main thing, regardless of software, is the logic. The syntax might change, but you do the same with your data, and you look for the same flow in your storytelling.
