2. Handling Data
=====

Visualizationの視覚化パートに行く前に、実際のデータが必要ですよね。データこそが、ビジュアリゼーションを面白くするものです。もし、データに興味がないのであれば、忘れても構わないグラフや綺麗なだけで役に立たない絵を書くことはやめましょう。面白いデータをどこで見つけられるのでしょうか？そして、どのようにして入手するのでしょうか？

データを手に入れたら、データを整形しなければなりません。それをして、利用するソフトウェアにデータをロードすることができます。あなたは、カンマで区切られたテキストファイルや、Excelシートとしてデータを入手するでしょう。テキストデータはXMLのような形式にコンバートする必要があるでしょうし、またその逆もあるでしょう。おそらく、あなたが求めているデータは、項目ごとにWebアプリケーションから入手することができるでしょうが、求めているのは完全な計算表でシートだと思います。

データを入手し、処理する方法を学び、視覚化スキルはその後にしましょう。

-----

## Gather Data (pp.22-38)

* データは視覚化のコアであり、幸運なことにいたるところで見つかるでしょう

### Provided by Others

* 他者が提供しているデータは一般的な方法でが、多くのミスが含まれていることがあるので、注意が必要です。
* 集めたデータに最も多く含まれるのがtypoです。その他にも多くのミスが含まれています。
* 文脈にも気をつけてチェックする必要があります。オリジナルのデータがどこから来て、どのように集められて、何についてのデータであるかを知るべきです。(投票結果を見るときに、どこで行われた投票だったのか、誰が行った、誰が回答したのか、を知るべきです。明らかに1970年の投票結果は現在の結果とは異なっています。)
----

### Finding Sources

直接データを入手したのではない場合：悪いニュースは、仕事の成果があなたの方にかかっていることであり、良いニュースは、機械的に読み込めるデータになっていることが多いことでしょう。

#### SEARCH ENGINE
* ググれ
* [Wolfram|Alpha](http://walframalpha.com)

#### DIRECT FROM THE SOURCE
* emailで頼んでみましょう
* The New York Timesのような出版社の図表など
    * 関連記事にも含まれてるでしょう
  
#### UNIVERSITIES
* 大学院生なら図書館
    * 貴重なデータのアーカイブ
    * [Data and Story Library (DASL)](http://lib.stat.cmu.edu/DASL/)
    * [Berkeley Data Lab](http://sunsite3.berkeley.edu/wikis/datalab/)
    * [UCLA Statistics Data Sets](http://www.stat.ucla.edu/data/)

#### GENERAL DATA APPLICATIONS
* APIで提供されるTwitterのようなサービス
    * [Freebase](http://www.freebase.com)
    * [Infochimps](http://infochimps.org)
    * [Numbrary](http://numbrary.com)
    * [AggData](http://aggdata.com)
    * [Amazon Public Data Sets](http://aws.amazon.com/publicdatasets)
    * [Wikipedia](http://wikipedia.org)

#### TOPICAL DATA
* Geography
    * [TIGER](http://www.census.gov/geo/www/tiger)
    * [OpenStreetMap](http://www.openstreetmap.org)
    * [Geocommons](http://geocommons.com)
    * [Flickr Shapefiles](http:/www.flickr.com/servies/api/)
* Sports
    * [Basketball Reference](http://www.basketball-reference.com)
    * [Baseball DataBank](http://baseball-databank.org)
    * [databaseFootball](http://www.databasefootball.com)
* World
    * [Global Health  Facts](http://www.globalhealthfacts.org)
    * [UNdata](http://data.un.org)
    * [World Health Organization](htttp://www.who.int/research/en/)
    * [OECD Statistics](http://stats.oecd.org/)
    * [World Bank](http://data.worldbank.org)
* Government and Politics
    * [Census Bureau](http://www.census.gov/)
    * [Data.gov](http://data.gov/)
    * [Data.gov.uk](http://data.gov.uk/)
    * [DataSF](http://datasf.org/)
    * [NYC DataMine](http://nyc.gov/data/)
    * [Follow the Money](http://www.followthemoney.org)
    * [OpenSecrets](http://www.opensecrets.org/)

----

### Data Scraping
* データが多量のHTMLページや、複数のウェブサイトだったらどうすべきでしょうか？
* 一番時間がかかるのは、各ページを訪問したり、スプレッドシートに興味のあるデータをにゅうs力することです。
* 何千ページもある場合、何百だとしても、考えたくないでしょう。自動化すること、data scraping が一番簡単です。

#### EXAMPLE: SCRAPE A WEBSITE
* この一年の温度データが欲しいけれど、ある時間幅やある待ちのすべての数字を提供するデータがないとします。
* 幸運なことに、[Weather Underground]()で、過去の温度の歴史を提供しています(図2-1)
* 後はプログラムの説明だから簡潔にhttp://wunderground.com

* どっか適当な日付を選んでURLをゲット
    * http://www.wunderground.com/history/airport/RJTT/2012/3/18/DailyHistory.html
* そのサイトの日付をころころすれば所望のデータが含まれたHTML
* HTMLからデータを取り出すのに、pythonのurllib2とsoupを使えばおｋ
