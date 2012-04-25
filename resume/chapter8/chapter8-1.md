#Chapter 8
## Visualizing Spatial Relationships
空間的な関連の視覚化

地図はとても直感的に認識できるという利点を持っているVisualizationのサブカテゴリです。
<!-- あやしい --><!--子供でも読めます。-->
<!--  
父親の助手席に座って、とても大きな折りたたんだ地図を前にして、道案内していたのを覚えています。
今では、ダッシュボードの上にある小さな箱から方向を支持する
***オーストラリアンレディー？***の声が聞こえます。（カーナビ）
-->

特定のケースで、地図はあなたのデータを理解させる大きな助けとなります。
これらは実世界を縮小したものであり、どこにでもあります。
この章では、いくつかの空間データセットを用いて、空間や時系列の視覚化のパターンを見ていきます。基本的な地図はRで作成できます。また、より高度な地図はPythonやSVGで作成できます。最後にActionScriptやFlashによるインタラクティブな地図や地図を用いたアニメーションを提示します。

---

### What to Look For
地図は統計学的なグラフに似ている。

 * 緯度経度はx軸とy軸のデータ
 * 地図上の座標は都市と都市の関連（距離とか）
 * 点は抽象的なデータで単位はない
 * アニメーションにすると時系列データも扱える
 * インタラクティブな地図は読み手が興味があるところに注目できる
 
<!--
地図を読むことは統計学的なグラフを読むのと同じです。
地図の特定の場所について見ている時、あなたは、特定の地域のクラスタリングを予期しています。例えば、ある地域とその他の地域を比較したりです。
違いは、x軸やy軸の代わりに緯度経度を使用することです。
地図上の座標の他の座標との関連はある都市とその他の都市との関連と同じです。
地点Aと地点Bの間は距離で表すことができ、そこに到達する時間を予測することができます。
対照的に、点は抽象的であり、単位はありません。

***この違いは地図の作図に関する違いから発生します。？***
ニューヨーク・タイムスは地図のデザインを専門とするグループを持っていためです。
あなたはすべてのロケーションを正しく配置し、センスよく色を付け、ラベリングし、正しい投影法を使う必要があります。

この章は基本的な手法の一部をカバーしています。
***あなたのデータのストリーを見つける？？***

特定の時間に注目することができます。
一つの地図がある特定の時間を表しますが、複数の地図を使うと、複数のスライスを表現できます。
アニメーションにすることで、地理的な地域のビジネスの成長を見ることもできます。
明らかに特定の地域で急成長が起きているのが分かるし、マップがインタラクティブだったら、読み手がどんな変化が起きているかを見るために注目することも可能です。
地図は、棒グラフやドットプロットのような結果にはなりませんが、***データがすぐにパーソナルになることができます？？***
-->

### Specific Locations
地点の特定

 * 緯度経度の情報を地図上にプロットしましょう
 * GoogleやYahooの地図にプロットしたらいろいろできる
 * ただ、GoogleやYahooの地図はデザインが画一的という欠点も
 
<!--
地点のリストは空間データの最も簡単なタイプです。
緯度経度があれば、地図にのせたくなります。
犯罪のようなイベントがどこで発生したか知りたいでしょうし、それらのポイントが地域的にどこでまとまっているかをみたいでしょう。
これがわかりやすい方法ですし、多くの方法があります。

Web上では、GoogleやMicrosoftの地図にポイントをマップするのが最も一般的な方法です。
マッピングAPIを利用して、インタラクティブな地図を得ることができます。
数行のJavaScriptでズームやパンするような地図をです。
これらのAPIの利用方法については、多くの素晴らしいドキュメントやチュートリアルがオンラインで提供されています。

しかし、よくない側面もあります。
カスタマイズできる点が少ないことです。
それが見苦しいとは言いませんが、あなたがアプリケーションを開発したり、出版物に適したグラフをデザインするなら、デザインスキームにマッチした地図にしたいでしょう。
***これらの制限は時々方法です。。。。***
-->

### Find Latitude and Longitude
緯度経度の探し方

いつも緯度経度が有るわけじゃない。通常は住所とか通りの名前とか郵便番号とか。
住所から緯度経度を取得することを***ジオコーディング(geocoding)***と言う。
以下はジオコーディングするためのサービスやライブラリ。

 * [Geocoder.us](http://geocoder.us)
 * [Latitude Longiude Popup](http://www.gorissen.info/Pierre/maps/)
 * [Geopy](http://code.google.com/p/geopy)

こっちは本のサンプルのリンク

 * [USコストコの住所CSV](http://book.flowingdata.com/ch08/geocode/costcos-limited.csv)
 * [サンプルコードとか全部入り](http://book.flowingdata.com/code/code-n-data.zip)
 
*※CSVデータダウンロードのURLに誤植「0(ゼロ)」が「o(オー)」になってた」*

<!--
マッピングする前に利用できるデータとあなたが実際に必要としているデータについて考えなさい。
もし、あなたが必要とするデータを持ていなければ、ビジュアライズはできません。
現実のアプリケーションでは、地図にプロットするのに緯度経度が必要です
多くのデータセットはそれを提供してくれません。
代わりに、住所のリストが有るでしょう。

実際は、通りの名前や郵便番号や小さな地図でしょう。
そこから緯度経度を取得することをgeocodingと言います。
基本的には、住所を持っていて、それをサービスに与えます。
サービスは住所をマッチングするためにデータベースに問い合わせを行い、
サービスが見つけ出した緯度経度が得られます。

利用できるサービスはいくつかあります。
しかし、ジオコードにロケーションされたものがアレば、webサイトにて
手でやるほうが簡単です。
Geocoder.usはフリーです。
もし、あなたが求めている場所が性格でなくてもいいなら、Pierre GorissenのGoogleMap緯度経度Popupを試すことができます。
それは、GooogleMapsのインタフェースとして親切です。マップをクリックすれば緯度輝度が取得できる。

もし、ジオコードする情報を大量に持っているなら、プログラムで緯度経度を求める方がいいでしょう。
無駄にコピペする必要は無いです。GoogleやYahooやGeocoder.usや
MediawikiはジオコーディングするためのAPIを提供しています。
また、Pythonのジオコーディングライブラリ「Geopy」はこれらすべてをラップしてくれています。

 * [Geocoder.us](http://geocoder.us)
 * [Latitude Longiude Popup](http://www.gorissen.info/Pierre/maps/)
 * [Geopy](http://code.google.com/p/geopy)

Geopyプロジェクトページにパッケージのインストール方法や簡単な例による紹介があります。

 * [USコストコの住所CSV](http://book.flowingdata.com/ch08/geocode/costcos-limited.csv)
 * [サンプルコードとか全部入り](http://book.flowingdata.com/code/code-n-data.zip)

Geopyをインストールしたあと、アメリカのすべてのコストコの住所が入ったCSVファイルをダウンロードします。
しかし、緯度経度は入っていません。あなたが入れるのです。

新しいファイルを作ってgeoode-locations.pyという名前で保存しなさい。
Geopyのimportは次のようにします。あとは、必要なモノを適当にimportしなさい。

	from geopy import geocoders
	import csv

各サービス（GoogleMapsとか）はAPIキーが必要です。（情報古い？）
APIキーとかgeocoderの利用方法が続く。。。

Geopy経由で見つからなかった住所をGeocoder.usで手動で探すといったこともできるよ。
-->

### Just Points
地図のフレームワーク（図8-1）


<!--
緯度経度を入手したので、地図上にプロットできます。
紙の地図にピンを指すのと一緒です。
図8-1にフレームワークを示します。
次節以降で、簡単ですが、クラスタリングしたりするための特徴を見ていきます。
-->

### Map with Dots
Rのmapsパッケージの使い方と点のプロットと地図の扱い方。

 * *maps*パッケージを利用する。
 * 地図画像を最下レイヤーにしてその上に点をプロットするレイヤーを載せる
 * *state*（図8-1）と*world*（図8-5）
 * *region*引数の説明（州を特定して表示する方法：図8-6）
 

<!--
Rは限定されているが、地図上に点を表現するのが簡単にできます。
*maps*パッケージです。
Package Installerでインストールかコンソールでinstall.packages()を利用します。
インストールできたら、以下のようにロードします。

	library(maps)

次に、データをロードします。
さっき緯度経度を付与したコストコのデータを使うか、すでにジオコーディングしたデータを用意してあるのでそっちを利用してもいいです。

	costcos <- read.csv("http://book.flowingdata.com/ch08/geocode/costcos-geocoded.csv", sep=",")

レイヤーを利用してマップを作る。
最下層にマップを置いて、地理上の境界線を提示して、その上にデータをプロットしたレイヤーを載せる。
この例では、アメリカの地図を最下層に、コストコの位置をその上に載せる。
最初のレイヤーが図8-2

	map(database="sate")

2番めのレイヤーに*symbols()*関数でコストコをマップしていく。
これと同じ関数を6章でバブルチャートに利用したので、それと同じ方法です。
x軸y軸の代わりに緯度経度を利用するよ。
**add=TRUE**とすることで、地図上に点が追加されていく。
（***add=FALSEだとどうなるの？***）
同じサイズの*circles*でプロットしてく。点の大きさは*inches*で制御

図8-3がプロットしただけのデータ

図8-4地図と点の色を変更
地図をグレーに点を赤に。
図8-3だと塗りつぶされてない点と地図が全部一緒で同じ幅で混在してしまってる。けど、正しい配色をするとデータに注目できます。

コストコはカリフォルニアの北や南とワシントンの北に集中してるのがわかります。

しかし、これは省略されています。
アラスカやハワイは？これらもUSのいち部ですが、*map()*関数の「state」データベースを利用していますが、入ってません。
もし、アラスカやハワイのコストコの位置を見たいなら、「world」データベースを利用します。
図8-5がそれです。

これは空間の無駄だとわかります。
気まぐれにちょっとやって見ることはできますが、IllustratorでUSにズームして、他の国を消すことができます。

反対に、特定の州に地図居限定することも可能です。
*region*引数です。カリフォルニア、ネバダ、オレゴン、メキシコだけに特定してます。
いくつかの点が残ってるので、好きなツールで消してね。
-->

### Map with Lines

 * *line()*関数を使おう
 * traceすることが可能（図8-7）
 * １地点から放射状に線を接続できる（図8-8）

<!--
地図上の地点の関係を示すために、点を接続するのが有効です。
Foursquareのようなオンラインロケーションサービスでは、ロケーションをトレースするのが重要です。
線を書くのは*line()*関数を使うのが簡単です。
Fakesvilleという仮想の政府のスパイとして１週間、移動した地点をデモンストレーションしてみましょう。
データのロードから開始して、worldマップに描画します。

faketraceとしてデータのフレームを用意します。
８つの緯度経度が入ったデータです。
このデータは移動した順番に並んでいます。

*lines()*関数は２つのカラムの引数で線が描画できます。
また、色（*col*）や幅（*lwd*）を指定スルこともできみあす。

コストコの位置を表示した時のようにドットを追加することもできます。

Fakesville政府のスパイの移動のあと、私は私のためのデータではないとそれを決めました。
ジェームス・ボンドのように魅力的ではないです。

しかし、私は私が訪れタコとのある国全てを接続したくなりました。
ということで、私のいる地点から全ての他の地点へ線を引いてみましょう。（図8-8）

基本となる地図を作った後、各地点をループして、最後の地点から各地点へ線を引きます。
これは対して有益ではないけど、この利用方法はすぐに見つかるでしょう。
地図を書いて、Rの他の関数を使うことで緯度経度のデータを描画できるよ。
-->
<!--
### Scaled Points
大きさを持った点

実際のデータに話を戻すと、スパイが逃げるよりも面白いことがあったり、なかったりします。
売上や人口など、地点に対して他の付加的な情報を持っているでしょう。
マップに点を描画できるように、バブルチャートの手法を地図にも応用できます。

どのようにバブルの半径や面積のサイズを決めるかは説明していません。
-->

### Map with Bubbles
バブルチャートを地図に

 * *symbols()*関数に*sqrt()*関数を与えて大きさを設定する（図8-9）
 * *summary()*関数でサマリーを入れる（最小最大などの値が表示される？）
 * 凡例（円の大きさが表している数値）や注釈（どの値に注目して欲しいか）、導入文章などを入れてわかりやすくすること

<!--
例えば、United Nations Human Development Reportの若年女性の出産率（2008年の15歳から19歳の女性の出産数の1000分率）を見てみましょう。
GeoCommonsにより与えられた緯度経度情報があります。
これらの割合をバブルの大きさにシましょう。

コードは先ほどまでと同じものです。しかし、*symbols()*関数の円のサイズは固定のものとしました。
代わりに*sqrt()*にサイズを示すための割合を与えます。

図8-9が出力結果です。これを見るとアフリカの国々が割合が高いことがわかります。
ヨーロッパは低いです。
図だけだと判例がないので、サークルがどんな値を示しているかがわかりません。
*summary()*関数で凡例を入れましょう。

これで、すこしははっきりしました。ただ、どのデータに着目して欲しいかがわかりません。
最大値と最小値を持つ国に注釈をつけます。
多くの読み手がいる国についても記述します（例ではUS）。
また、導入文章も入れましょう。
図8-10が変更をいれたものです。
-->

### Regions
地域

 * 点ではなく、地域（郡、州、国、大陸など）として集計されたデータもよくある

<!--
これまでは地図上に一つの地点を表すだけでした。
郡、州、国、大陸など境界を持った地域があり，地図に関するデータはこの方法で集計されています。
例えば、簡単に見つけられるのは州や国の患者数や病院数といったデータです。
これらはプライバシーのため集計されたデータになって配信されます。
特別なデータを用いてどのようにするか見て行きましょう。
-->

### Color by Data
データによる配色

 * コロプレス地図＝カラースケールで定義した色による塗り分けを行う図（図8-11）
 * 色の塗り分け
  * 連続したデータ=>単色系の明度によるもの（図8-12）
  * 2つの属性値のデータ=>多色（diverging color scheme）のもの（図8-13）
  * クラスやカテゴリといった性質のデータ=>多様な色（qualitative color scheme）のもの（図8-14）

<!--
コロプレス地図は地域的なデータを表すもっとも一般的な図です。
あるメトリックに基づいた地域をカラースケールで定義した色によって塗り分けます。（図8-11）
エリアと場所はすでに定義されており、利用するのにふさわしい色を決定するのがあなたの仕事です。

前の章で触れたように、Cynthia Brewer's ColorBrewerが色を決めるためのよい方法です。
もし、連続的なデータを持っている場合、明度を利用した連続的な同じカラースケールがいいでしょう。（図8-12）

異なる色による方法は2つの側面（良い悪い、しきい値以上か以下か）を持つデータに良いでしょう。（図8-13）

最後にクラスやカテゴリといった性質を持つデータなら、ユニークなカラーを割り当てましょう（図8-14）

カラースキームを決めたら、次の2つのことを行います。
最初はデータの範囲に対して色を決める方法を決定することです。
2番目はあなたの選んだ色でかく地域を塗っていくことです。
PythonとSVGを例にして説明します。
-->

### Map Counties
地図上の郡

 * SVGとPythonによるサンプル（SVGのパース処理とCSVデータの処理とそれらの関連付け方法について）
 * [2010年8月の失業率](http://book.flowingdata.com/ch08/regions/unemployment-aug2010.txt)
 * [SVG白地図データ](http://commons.wikimedia.org/wiki/File:USA_Counties_with_FIPS_and_names.svg)
 * 参考：[日本の白地図](http://commons.wikimedia.org/wiki/File:Japan_template_large.svg)

<!--
アメリカ労働統計局（BLS : U.S. Bureau of Labor Statistics）は郡のレベルの月毎の失業者集を提供しています。
最新の失業率や数年間のデータをダウンロードできます。
しかし、提供されているデータブラウザは時代遅れで回りくどいです。
そのため簡略化するために、データをダウンロード出来るようにしました。
6つのカラムがあります。
最初はBLSが定義したコードです。
次の2つ（2、3カラム）は2つあわせて郡を特定するユニークIDです。
4、5カラムは郡の名称と対象となる月です。
最後のカラムがその郡の失業率になります。
以降の例では、郡のID（FIPSコード）と失業率を対象とします。

新しいマップを用意します。
前の例ではRで生成サれたMapでしたが、今回はPythonとSVGを利用します。
データの整形をしてから、マップにプロットします。
完全にスクラッチから行う必要はないです。
ブランクマップが用意されています。（図8-15）
PNGフォーマットの4つのサイズの地図へのリンクがあり、のこり一つがSVGです。
SVGファイルをダウンロードして、counties.svgとしてCSVデータと同じフォルダに保存してください。

SVGはありふれたものではありませんが、実際にはXMLファイルだということが重要です。
タグを持ったテキストであり、テキストエディタでHTMLファイルのように修正可能です。
ブラウザやイメージビューワはXMLファイルを読めますし、ブラウザは色や形を描くことで図として表示してくれます。

論点を理解するために、SVGマップファイルをテキストエディタで開いてみてください。
SVG宣言や。。。

スクロールしていくと&lt;path&gt;タグが現れます。
1つのタグにあるこれらの数値が州の境界を表しています。
これらには触らないでください。
各州の色を塗り分ける部分だけに注目します。
それには*style*属性を編集します。

	Tips
	SVGファイルは、テキストエディタで変更が簡単にできるXMLファイルです。
	これはSVGコードがプログラミングでパースしたりすることができることを意味します。

各&lt;path&gt;タグは*style*で始まっていることに気づくでしょう。
CSSで書かれていることがわかります。
*fill*属性は16進の色を定義しています。この部分を変えるとイメージの色が変更できます。
それぞれを手で修正もできますが、3000以上の州が存在します。
余りにも無駄です。代わりにPythonのXMLやHTMLを簡単に扱うことができるライブラリのBeautifl Soupを利用しましょう。

SVGマップと失業率データと同じディレクトリに新しいファイルとしてcolorize_svg.pyを用意します。
CSVをインポートして、SVGをBeautiful Soupでパースするために必要なパッケージをインポートします。

。。。ここからコードの説明
CSVのリーダーを用意し、SVGのリーダーを用意し処理します。
お互いのデータをどのように結びつけるの？ヒントは郡のユニークIDです。FIPSコードを思い出した方は正解です。

SVGファイルの各&lt;path&gt;のユニークな*id*はFIPSの州コードと郡コードをつなげたものです。
これは、CSVファイルのものと同じです。ただ、CSVファイルのデータは分割されています。
2つのコードをつなげればいいです。

データの回し方の話。
FIPSコード２つのデータを結びつけることになるよ。

FIPSコードを接続して保持（プログラム上で）することで、以降の処理が簡単にできるよ。Pythonのディクショナリと呼ばれる構造を使えば簡単です。
値とキーワードを関連付けて保存することができます。
今回のキーワードはFIPSの州コードと郡コードを接続したものになります。

次はBeautifulSoupによるSVGファイルのパースです。
タグは開始と終了タグをそれぞれ持っていますが、ここに出てくるタグは単体で閉じたタグです。
*findAll()*関数を利用して、マップにあるパスすべてを取得できます。

ColorBrewerから得た色を、リストとして保存します。保存して、
これは紫から赤への複数の色調を持つ連続したカラースキームです。

クライマックスに近づいています。SVGの各&lt;path&gt;のstyle属性を変更していきます。
色を塗っていくのに関心がありますが、全てではなく、styleすべてをパースする代わりに色の部分だけ置き換えます。
この変更で、グレーの代わりに白とします。

*fill*をし顎の部分に移動して、右辺を空白とします。これは、失業率ごとに変化が有るためです。

最後に色を変えていきます。
書くパスについて、処理を回して、色を与えます。失業率が10以上なら、darker shadeを2以下なら最も明るいし記帳です。

最後に、SVGファイルを*prettify()*関数でアウトプットします。
関数はブラウザで表示できる文字列への変換を行います。

Pythonスクリプトを実行して、新しいSVGファイルをcolored_map.svgとして保存します。（図8-17）

新しいコロプレス地図をイラストレータやSafariやChrome、Firefoxで開いてみると出力結果がわかります。
2010年8月の失業率の高い部分が簡単にわかります。
西海岸や南東が高い率になっているのがわかります。
中米は低いことがわかります。

さらなる訓練として、あなたが興味あることを地図にすることができます。
SVGファイルをイラストレータで更新し、ボーダーカラーやサイズ、アノテーションを追加して多くのオーディエンスに示すことができる図が作成できます。

このコードは最良がききます。FIPSコードを利用している他のデータセットに対して適用できます。
また、これと同じデータセットでカラースキームを変更することであなたのデータのテーマにフィットさせることもできます。

あなたのデータに依存して、各地域をどのように色付けするかのしきい値を変更することもできます。
例では、6つの色調の色を用いましたが、2ポイントごとに新しいクラスを指定しました。
各軍の失業率が10％より大きいクラスです。
郡の失業率が8から10、6から8という感じです。
他の方法として、4つの色を利用して、地域を4分割で表すことも可能です。

例えば、lower、middle、upperとそれ以外という具合です。
6.9、8.7、10.8％です。
これは、6.9％以下、6.9〜8.7、8.7〜10.8、10.8以上という4つになります。
このカラーリストw用いて色分けを変更したものは次のものになります。

より使いやすくするために、4分割している部分をハードコーディングではなく、プログラマブルに変更します。
Pythonで行い舞うs。
あなたののリストを保持し、最小から最大にソートします。
最初の1/4を見つけてという形でマークします。
この例も付属としてついていますが、最初のループを変更します。

こうすることで、どの部分が1/4の点かを計算できます。

ハードコーディングの代わりに、値をから計算できます。
こうすることで、異なるデータセットについてのデータについては、CSVファイルを変更するだけで処理が可能になります。

カラースケールはあなたのデータに依存し、あなたが何を語りたいかに依存します。
この例のデータセットに対しては、リニアなスケールが望ましいと思いました。
これは、国中の失業率の高い部分を表すのに適しているからです。
図8-18に対して判例やタイトルを追加したものが図8-20になります。
-->

### Map Countries

 * 前節と同じ方法で色分け可能
 * [World Bank](http://data.worldbank.org)（国別の人口統計データの最もよいリソース提供の一つ）
 * [世界白地図](http://en.wikipedia.org/wiki/File:BlankMap-World6.svg)
 * [ISO 3166-1](http://ja.wikipedia.org/wiki/ISO_3166-1)ISOで規定された国コード。2文字、3文字、3桁数字が存在する。
 
<!--
前の例で郡の色付けのプロセスでは、は限定されていませんでした。
同様のステップが州や国の色付けにも利用できます。
あなたが色付けしたい各地域に対してユニークなIDを持つSVGファイルが必要です。（Wikipediaから簡単にアクセスできるでしょう）
また、データのIDも同じです。
World Bankからオープンなデータを取得しましょう。

2008年の国ごとの、水資源の改良による人口増加の割合を見てみましょう。
World BankからExcelデータをダウンロードします。
簡易化のためにCSVファイルとして変換したデータを用意しました。
国レベルのデータとして扱うのが一般的なデータですが、いくつかの国を削除しています。
CSVファイルからこれらの行を削除しています。

7つのカラムが用意されています。
最初が国名です。
2番目が国コードです。
残りの5カラムが1990年から2008年のパーセンテージです。

基本地図をWikipediaから取得します。
SVGワールドマップは多くのデータがありますが、その中の一つを使います。
ダウンロードして、データと一緒のディレクトリに入れます。

SVGファイルをテキストエディタでオープンします。
XMLフォーマットですが、郡の項目で見たデータとは異なります。
pathはidもstyle属性もありません。pathは国コードのようなクラスを持っています。
これらは2文字でできています。
World Bankの国コードは3文字です。

World Bankのドキュメントでは、ISO 3166-1アルファ3コードが使われます。
WikipediaのSVGファイルはISO 3166-1アルファ2コードが利用されます。
名前は恐ろしいですが、心配しなくていいです。
Wikipediaは変換チャートも提供しています。
Excelのテーブルにコピー・ペーストして、重要な部分をテキストファイルとして保存します。
アルファ２とアルファ３の２つのカラムのデータになります。
ここからダウンロードできます。
この章では２つのコードの変換にこの表を利用します。

各国のスタイルの変更はこれまでと少しことなります。
pathタグの属性を直接変更する代わりに、パスタグの外部にあるCSSの色を使います。
見てみましょう。

generate_css.pyというファイルを作ります。
CSVパッケージをインポートして、国コードと水資源のパーセンテージを読み込みます。

この時、国コードを３から２に変換して保持します。
ディクショナリを利用します。

前の例と同様にwaterデータの各行に対して色を割り当てます。

このパートは次のプロセスです。

1. CSVファイルのヘッダスキップ
2. waterデータに対してイテレータを回します。
3. CSVからアルファ３コードに関連するアルファ２コードを取得して、データに関連付けます。
4. パーセンテージに応じて色を選びます。
5. データごとにCSSの１行として出力します。

generate_css.pyの実行結果を保存して**style.css**としてます。
最初の数行は以下のようになります。

これはスタンダードなCSSです。
最初の行は.afクラスに治して#7BCCC4という色を塗ります。

style.cssを開いて全コンテンツをコピーします。
SVGマップを１３５行目あたりに開いてペーストします。
これで、図8-22のようなコロプレス地図が出来上がりです。
暗い青が１００％を明るくなるについてパーセンテージが小さくなります。

グレーの国はデータが無かった国です。

ここで重要なのは、World Bankからデータがダウンロードできることであり、コードの数行を変更することで簡単にコロプレス地図が作成できることです。図8-22を小奇麗にするためにSVGファイルをイラストレータで開いて更新します。
タイトルや判例をつけて図8-23のよにします。
-->

### 感想
 * straightforward〜という表現がやたら多かった。
 * カラースケールの選択方法をもう少し知りたい。
 * 日本の市区町村レベルのデータもあるのか？
 * SVGさいこー