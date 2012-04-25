4. Visualizing Patterns Over Time
=====


時系列データは、何についてでもあります。世論の変化、人口推移、ビジネスの成長。これらのことがどれくらい変化しているかを入るときには、時系列に目を向けることになります。あなたが用いるこの種のデータグラフックスはあなたが手にしてきたデータに依存しています。このため、この章では、離散的なあるいは連続的なデータを見てみましょう。また、RやAdobe illustratorの手垢がついているでしょう。この2つのプログラムは今後もともに付き合っていくことになります。

----

## What to Look for over Time
* 時間の経過は自然であり、それによりどのように物事が変化するかを見ることができる
* 時系列で最もありふれたものは、増えているか、減っているか、繰り返しているかといったトレンドデータ
* 図4−1は、ブッシュ政権の終わりと、オバマ政権樹立後の失業を表しています
    * この図からは新政権が失業に対して有意にポジティブな影響を与えているように見える
    * 図4−2では、ブッシュ政権でも、失業を改善している時期が見られている
* 例外は注目したい箇所であるときもあるが、それ以外の時には、異常値は誤りであることになる
* 全体図(文脈)をみることは、それがなんであるかを判断する手助けになります

## Discrete Points in Time
* 時間データは、離散と連続にカテゴライズ
    * データが属するカテゴリを理解することは、どのように視覚化するかの決定に役立つ
    * 例：各年のテスト合格者のパーセンテージ、各年のテスト受験者
    * スコアは後に変わらず、特定の日時に集計される
* 気温のようなデータは連続データ
    * どのような時間間隔の一日のいつでも測定可能で、いつも変化している
* 全体図が全てであることを覚えていてください

### Bars
* 最も利用されているチャートタイプであり、様々なデータで利用される。時系列データでもまた使われる
* 一般的には、バーの幅や隙間は値を表さず、高さが値に対応しています。
* 重要なこと「値に対しての視覚的な手がかりがバーの高さであること」
    * 値が低ければ、バーは短く、値が大きければ、バーは高くなる
* ポイント: 値の軸は常にゼロから始めなさい。そうでなければ、棒グラフは誤った関係を示してしまいます


#### CREATE A BAR GRAPH
* [Nathan Hot Dog](http://en.wikipedia.org/wiki/Nathan's_Hot_Dog_Eating_Contest) コンテストの30年の結果を使って、最初のグラフ作成を行いましょう
* 図4-5は、目標のグラフで、2つのステップで作成します
    1. Rで基本的な棒グラフを作成する
    2. Illustratorでグラフを綺麗にする
* 日本のフードファイターKobayashi Takeruが2001年に参加していきなり過去の歴史を塗り替えた話

1. Rでの処理

    hotdogs <- read.csv("[http://datasets.flowingdata.com/hot-dog-contest-winners.csv]", sep=",", header= TRUE)
    barplot(hotdogs$Dogs.eaten)
    barplot(hotdogs$Dogs.eaten, names.arg=hotdogs$Year)
    barplot(hotdogs$Dogs.eaten, names.arg=hotdogs$Year, col="red", border=NA, xlab="Year", ylab="Hot dogs and buns (HDB) eaten")
    fill_colors <- c()
    for( i in 1:length(hotdogs$Country)) {
        if(hotdogs$Country[i] == "United States") {
            fill_colors <- c(fill_colors, "#821122")
        } else {
            fill_colors <- c(fill_colors, "#CCCCCC")
        }
    }
     for( i in 1:length(hotdogs$New.record)) {
        if(hotdogs$New.record[i] == 1) {
            fill_colors <- c(fill_colors, "#821122")
        } else {
            fill_colors <- c(fill_colors, "#CCCCCC")
        }
    }
    barplot(hotdogs$Dogs.eaten, names.arg=hotdogs$Year, col="red", border=NA, space=0.3, xlab="Year", ylab="Hot dogs and buns (HDB) eaten")


#### REFINE YOUR GRAPH IN ILLUSTRATOR
* Rで悪くないグラフを描いたけれど、解析しただけです。単独の図で読み解くことができるようにしましょう
* データグラフィックスを作るときには、読者の立場に立ってください。データのどの部分に説明が必要でしょうか？

* ※ココから後はillustratorの使い方が続きます・・・

* グラフィックスの中にデータソースを記載するようにしましょう。文脈だけではなく、信頼性も得ることができるからです。

### Stack the Bars
* 積み上げグラフの作り方のRのコードが書かれているだけなので割愛します

### Points
* Pointsは、ある点から次の点への流れをよく表現できる
* このチャートタイプは、非時系列データを視覚化する際に散布図でよく使われる(6章参照)が、時系列データにおいてはx軸は時系列において表現されます。
* 時間を基準として、点と点を比較するので、y軸は必ずしもゼロから始まっていません。 

#### CREATE A SCATTERPLOT
* Rではplot()関数を使います。
* 後は引き続きillustratorの使い方なので割愛します




