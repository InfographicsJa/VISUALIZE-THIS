# Visualizing Relationships

統計学は、データから関係を発見することについての学問です。
グループ間の類似性はあるのか？どちらかに含まれるのか？サブグループに含まれるのか？
多くの人が統計に関して聞き慣れている関係は相関です。例えば、平均身長が高くなれば、平均体重も増加するでしょう。これはシンプルな正の相関です。実世界のように、データの中にある関係は多くの要因があったり、線形ではないパターンがあるように、大変複雑です。この章では、そのような関係を発見し、ストーリーを伝えることを目的にした時にこれらを強調するために、Visualizationをどのようにつかうかについて議論します

-----
## What Relationships to Look For

* 時系列のトレンドを見てきた→異なる変数間の関係を調べる
* 何かが増えた時に他方が減少した場合、これは、因果関係か相関関係か？
    * 前者は量的な証明が非常に困難
    * 後者はより深い解析を可能にする相関係数を示すことは容易

* 複数の分布を比較することは広くデータを見ることを可能にする

* 結果が何を意味しているのかに答えることが重要
    * 期待していたものなのか？驚くべき結果なのか？

-----
## Correlation

* データの中の関係性と聞いた時に最初に思い浮かべるのが「相関」
    * 次が因果関係
* 因果関係は相関とは違う、教義です！

* 相関は「なにかが変化傾向を示した時に、他のものも変化をする」こと
    * 例) ガロンあたりのミルクとガソリンの価格が正の相関を示していて、両方が年次ごとに増加

* 相関は因果とは違う
    * 大事なことなので二回言いました
    * 大切なのは、ミルクの値段が上がったとして、ガソリンの価格が上がったからなのか、それとも、ストライキのような外部要因のためなのか

* 外部要因や複合要因を説明することは難しい。これが因果関係を証明することを難しくしている

-----

### More with Points

* 時系列での散布図を使ったが、2変数の関係を見るためにも使います
* 2変数に正相関があるばあい、右上がり/ 負相関の場合は逆/ 相関無しはフラット

* ガソリンの価格と人口増加は正の相関を示すことが、ガソリンの価格が人口増加を下げないように、因果関係は難しい

#### CEATE A SCATTERPLOT

*2005年のアメリカの各州の犯罪率(100,000人あたりの犯罪の種類ごと)

* Rで見ます

* 殺人と強盗の間に正相関が見られる
* 1つ外れ値があり、見づらくなっている(Washington DC 図6-3)
    * 除外して、プロットすると、見やすいです
    * (森藤注)これ、完成図に抜いた理由とかが記載してないんだけどいいのかな？？

* LOESS 曲線を引くと見やすくなります
* 読み手を考え、LOESS曲線を強調し、実データのドットを薄くした

----

### Exploring More Valiables

* 2変数以上を比較する
* 比較したい変数を選びだし、それぞれのペアの散布図を作成します
* この方法は関心のあるデータを無視したり、データを見る機会を失いやすくなる可能性がある

* 多変数の相関比較は、データを調べている段階で非常に有用
    * どこから着手していいかの手がかりが無い場合
* 散布図マトリクス
    * それぞれの変数が縦軸・横軸に並ぶ
    * それぞれのセルはそれぞれのペアを示す
    * 対角線は変数名を示している(相関は1で意味ないから)

#### CREATE A SCATTERPLOT MATRIX

* 先ほどの犯罪率のデータを使う
* 予想通り、多くの正相関が存在している
    * 強盗と加重暴行の相関は比較的高い
    * 殺人と窃盗の相関は明確ではない

* いかなる思い込みも持つべきではない、しかし、散布図マトリクスがどれほど有用かは明確

* Rで処理して、2変数と同様、LOESSを強調した

-----

### Bubbles

* Hans Rosling: International Health at Karolinska Institute の教授かつGapminder Foundationのチェア
    * motion chart：例のアレ

* motion chartは時間で動くけれど、性的なバージョン：バブルチャートを作ってみましょう

* バブルチャートは3つ目の軸を表現できる
    * x軸、y軸、バブルのサイズ
* バブルは面積で表現するべき
    * ×半径、直径、円周はダメ(起こりがちです！
    * 大きすぎたり、小さすぎたりしてしまう

* 面積と半径での比較(図6-13、6-14)

#### CREATE A BUBBLE CHART
* 犯罪率のデータを使います
    * 3つ目の軸=面積に人口をプロット
    * これにより、人口が多いほど、犯罪率が高いかを見ることができる
* 図6-15からは見られない(CaliforniaとかFloridaとかTexasとか

* Rで処理/illustratorで修正




