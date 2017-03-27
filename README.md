長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
PTT_list<-list(URL=c("https://www.ptt.cc/bbs/Tech_Job/index.html",
                    "https://www.ptt.cc/bbs/Tech_Job/index2575.html",
                    "https://www.ptt.cc/bbs/Tech_Job/index2574.html",
                    "https://www.ptt.cc/bbs/Tech_Job/index2573.html",
                    "https://www.ptt.cc/bbs/Tech_Job/index2572.html",
                    "https://www.ptt.cc/bbs/Tech_Job/index2571.html"))


library(rvest) 
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
library(xml2)
PTT_Posts<- NULL

for(n in 1:6){
    content <-read_html(PTT_list$URL[n])
    title <- content %>% html_nodes("div.title") %>%html_text()
    pushnum <- content %>% html_nodes("div.nrec") %>% html_text()
    author <- content %>% html_nodes("div.author") %>% html_text()
    PTT_Posts1<- data.frame(Title=title ,PushNum=pushnum ,Author=author)
    PTT_Posts<- rbind(PTT_Posts,PTT_Posts1) 
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(PTT_Posts)
```

| Title                                                            | PushNum | Author       |
|:-----------------------------------------------------------------|:--------|:-------------|
| 捷普 綠點刀具                                                    | 1       | tn372845     |
| \[請益\] 日商安立知                                              | 2       | pjc202       |
| \[情報\] 蘋果申請具備iPhone核心之Macbook產品                     | 5       | zxcvxx       |
| \[請益\]有人收到德州儀器技術行銷工程師面試邀請?                  |         | wer11        |
| \[請益\] 請問陸資的IC設計公司                                    | 5       | DigiTalent   |
| \[請益\] 德州儀器設備工程師實習                                  | 1       | oeys         |
| \[討論\] 國家光電好嗎                                            |         | chag06       |
| Re: \[請益\] 請問陸資的IC設計公司                                | 8       | DigiTalent   |
| \[請益\] 是否該調往偏鄉工作？                                    | 5       | NakiXIII     |
| 律師為您解惑－線上勞動法免費諮詢即日為勞工 …                     | 爆      | pzs          |
| \[公告\] Tech\_Job板板規 2014.03.01                              | 7       | mmkntust     |
| \[公告\] 置底 檢舉/推薦 文章                                     | 爆      | mmkntust     |
| \[免費\]工作人生顧問                                             | 爆      | zodiac       |
| Fw: \[徵才\] 興豪傳媒科技 誠徵Javascript前端工程師               | 1       | cliffk321    |
| \[請益\] 福爾摩莎紙業股份有限公司高雄業務                        |         | edison81630  |
| \[聘書\] 研替offer請益(皮卡)                                     | 5       | paulu90      |
| \[新聞\] 吞iPhone緯創資本支出破百億　3年新高                     | 11      | qazxc1156892 |
| \[新聞\] 陳良基：與張忠謀溝通過「所有投資以台灣為優先            | 13      | wer11        |
| \[請益\] 竹科聯電製程                                            | 9       | berac16      |
| \[新聞\] 讀軍校免當軍人 中科院上班54K                            | 18      | tw689        |
| \[請益\] 日月光-歐美區(美國)客戶關係管理                         | 11      | lim10337     |
| \[請益\] 南科住華科技                                            | 12      | kurtgod      |
| \[請益\] Nvidia的Android Framework/SW Engineer                   | 16      | magic704226  |
| \[請益\] 亞德客or鑫陽鋼鐵                                        | 6       | eraser90310  |
| \[請益\] 云辰科技                                                |         | Intelgence   |
| \[請益\] NXP Service Engineer                                    | 7       | angelpeace   |
| \[情報\] 千竣科技違反勞基法，官司結果                            | 49      | GameHeven    |
| \[新聞\] 台積電試產 7 奈米良率超過七成                           | 43      | unrest       |
| \[請益\] 台積電的設備自己研發?                                   | 55      | sustaned     |
| \[請益\] offer選擇                                               | 7       | queenghost   |
| \[討論\] 公司要資遣人，需要通報勞工局嗎？                        | 12      | JE2K         |
| \[新聞\] 新日光虧損破紀錄 去年財報淨損63.1億                     | 16      | moonth66     |
| \[新聞\] 竹科IC產業衰退？ 科管局：研發力道仍強                   | 8       | breath35     |
| \[面試\] 關於弘塑科技業務工程師                                  | 2       | onlyveritas  |
| \[請益\] 自行保公會勞健保                                        | 2       | ann3222      |
| \[面試\] 南科艾爾斯半導體                                        | 5       | turtle6188   |
| \[新聞\] 謝金河：台積電打敗Intel！已是全球第一                   | 11      | soaping      |
| Re: \[請益\] 水果公司的工廠，工程師好跳嗎？                      | 7       | nomilkman    |
| Re: \[新聞\] 台積電 3 奈米赴美？關鍵在量子電腦                   |         | pig2014      |
| \[聘書\] offer 機構 vs 半導體CSE                                 | 5       | bboycookie   |
| \[請益\] 沒有中生代的公司                                        | 9       | randomly     |
| \[請益\] 測試/系統整合/自動化工程師                              | 2       | foreverwhat  |
| Re: \[新聞\] 績效獎金打6折？ 聯詠：不予回應                      | 3       | jeromeshih   |
| Re: \[請益\] 水果公司的工廠，工程師好跳嗎？                      |         | typewindow   |
| Re: Fw: \[新聞\] 新世代最崇拜企業家　郭董取代賈柏斯              |         | jeromeshih   |
| \[心情\] 連來台灣的外國朋友都會講"台積電"華文                    | 8       | terimakasih  |
| \[請益\] 獵人頭 網站 or APP                                      | 16      | sustaned     |
| \[新聞\] 台積電赴美設廠？ 科技部轉述：並無此計                   | 19      | TrueSpace    |
| \[請益\] 螃蟹OFFER請益(代PO)                                     | 6       | birdhackor   |
| \[請益\] 以下加班申請定合理嗎?                                   | 9       | zaxck        |
| Re: \[請益\] 獵人頭 網站 or APP                                  | 8       | appledavid   |
| \[請益\] 半年的技術員經歷                                        | 16      | ak080775     |
| \[請益\] 宏騰光電一些問題...                                     | 3       | qqming0721   |
| \[新聞\] 斥資600億 「綠能科學城」落腳台南沙崙                    | 26      | hottea88310  |
| 滷肉開獎                                                         | 57      | crafttt      |
| \[新聞\] 台積電3奈米廠出走？傳5000億落腳美國                     | 51      | popoallan    |
| Re: \[新聞\] 台積電3奈米廠出走？傳5000億落腳美國                 | 5       | appledavid   |
| \[新聞\] 台積電成環評箭靶　網友酸農地工廠卻就                    | 31      | wahaha23     |
| Fw: \[新聞\] 新世代最崇拜企業家　郭董取代賈柏斯                  | X4      | tw689        |
| \[請益\] 工作上想成長,想上點課程~                                | 7       | kevinZJL     |
| Re: \[心得\] 小公司的慎選...                                     | 1       | Sex5F        |
| \[請益\] 研替or一般替代役                                        | 34      | charisma007  |
| \[請益\] 達運光電(五股)                                          |         | smst         |
| \[情報\] 106年03月22日\_竹科\_IC設計產業座談會                   | 1       | SuperModel   |
| Re: \[請益\] 點序科技業務職面試請益                              | 2       | hueepf       |
| \[情報\] 整合深度學習的無人駕駛新創公司Drive.ai                  | 5       | zxcvxx       |
| \[請益\] 慧盛先進科技？                                          | 1       | amethystleaf |
| \[請益\] 3/11長春體檢                                            | 10      | elvisman     |
| \[新聞\] 績效獎金打6折？ 聯詠：不予回應                          | 13      | PerfectID    |
| \[新聞\] 台積電 3 奈米赴美？關鍵在量子電腦                       | 16      | evil7589     |
| \[請益\] 求職心力憔悴                                            | 66      | rko801024    |
| \[請益\] 代PO 交大半導體碩專班一問                               | 5       | remember246  |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 13      | yolosiku     |
| \[請益\] 請教大碩面試後等通知需要等多久？                        | 19      | uasalada     |
| Re: \[請益\] OFFER選擇 (群創光電V.S.台電機械職                   | 18      | lsz6404      |
| \[請益\] 台積電 EMITD 工作內容                                   | 19      | innocentguy  |
| \[新聞\] ic設計每股獲利洗牌 聯發科跌落3名外                      | 20      | LBJ2ndKing   |
| \[請益\] 住華 新技術開發 and 奇美材 製程 詢問                    | 5       | Edwardkiller |
| \[請益\] 研替offer(京元/緯創）                                   | 7       | starjli      |
| \[請益\] 碩一暑期實習                                            | 5       | a29417557    |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 5       | HateAnus     |
| \[請益\] 水果公司的工廠，工程師好跳嗎？                          | 17      | ggggggh      |
| \[面試\] 化工面試 住友/三井/花王/景碩/陶麗西/新光/清錄/麥特/艾克 | 57      | BCCAT        |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 30      | unclefucka   |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 1       | cacalota     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 17      | jessicabana  |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 19      | soufon       |
| \[心得\] 小公司的慎選...                                         |         | JT0816       |
| \[閒聊\] 海邊的一盤大棋                                          | 28      | balzark      |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 36      | smallchou    |
| \[請益\] 請問應徵台積OP是否有黑名單                              | 37      | kn0105209    |
| \[新聞\] 郭台銘：陸大學生動手能力差                              | 21      | BBMADE       |
| Re: \[新聞\] 郭台銘：陸大學生動手能力差                          |         | schizophrena |
| \[請益\] 台橡化工技術員面試一職                                  |         | minwoo0904   |
| \[請益\] 台塑宜蘭廠                                              | 9       | nerlens      |
| \[請益\] acer system engineer                                    |         | ccc0901      |
| Re: \[心得\] 南u製程工作心得                                     | XX      | livefishfish |
| \[面試\] 台積設備/應材客服/南亞科設備 請益                       | 9       | s50190       |
| Re: \[情報\] 106年IC layout人才養成班 (代PO)                     | 9       | SUPER22K     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 21      | Feases       |
| \[心得\] 船舶暨海洋產業研發中心 面試心得                         | 14      | kevin505     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 50      | cjb          |
| \[請益\] 科技部工作經歷在Linkedin上的名稱                        | 1       | Paravion     |
| Re: \[新聞\] 海邊台大校園徵才圓滿落幕　收穫逾2000履歷表          | 31      | LibertyWings |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 7       | zxlu         |
| \[討論\] 程式語言筆試面試的準備                                  | 1       | magic704226  |
| \[請益\] 大公司的話 個資可以放心填?                              |         | jason050117  |
| \[請益\] OFFER選擇 (群創光電V.S台電機械職員                      | 53      | Moran        |
| \[請益\] 請問螃蟹的Android/Media軟體設計工程師                   | 1       | magic704226  |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 爆      | AK47shoot    |
| \[請益\] 大立光物管工程師                                        | 14      | omes4219     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 42      | TSMCer       |
| \[徵才\] EasyStack徵才年薪120萬台幣起                            | 10      | mimi0213     |

解釋爬蟲結果
------------

``` r
str(PTT_Posts[1])
```

    ## 'data.frame':    113 obs. of  1 variable:
    ##  $ Title: Factor w/ 101 levels "\n\t\t\t\n\t\t\t\t[公告] Tech_Job板板規 2014.03.01\n\t\t\t\n\t\t\t",..: 13 6 5 10 9 8 4 11 7 12 ...

``` r
dim(PTT_Posts)
```

    ## [1] 113   3

``` r
nrow(PTT_Posts)
```

    ## [1] 113

用PTT\_posts\[1\]，取出PTT\_posts的第\[1\]個欄位也就是『標題』，得到結果為'data.frame': 109 obs. of 1 variable，可知有109個觀察值(標題數)。 (以上數值可能隨著時間網頁重整所變動)

``` r
MaxPost<-max(table(PTT_Posts$Author,exclude= "-"))

for(m in 1:(length(table(PTT_Posts$Author)))){
    if(((table(PTT_Posts$Author))[[m]])==MaxPost)
    {
     print((table(PTT_Posts$Author))[m])
    }
}
```

    ## magic704226 
    ##           3

MaxPost是先用Table找出同一個作者貼文數的次數統計，並用Max取出最大值。並把"-"作者排除在外(因為"-"代表已刪除文章，不列入計算)。 接著再用迴圈去找哪一個作者的貼文數剛好等於MaxPost，把他的名字跟貼文數Print出來。得到的結果為magic704226作者，貼文數為3則。 (以上數值可能隨著時間網頁重整所變動)

人工結論與解釋
--------------

1.在不同的時間debug，使用str()取出來的值都會不同，由此可知，我們要爬的資料是隨著時間而改變的。

2.在第一題，原本是想要做字串連接的方法，將六個網頁分別放入 PTT\_Posts1(2,3,4,5,6)，但是使用paste0()的函數卻沒辦法搭配rbind()或&lt;-data.frame使用，我們必須搭配一個空的資料框，將爬到的資料依序串連起來。

3.在第三題的第一小題，試著將老師所說的三種方法都Run一次，若要符合題意，只需要知道總共有幾個"觀察值"使用nrow()會比較適合，若是需要知道詳細一點的資料，使用str()取得資訊會比較適合，可得到呈現資料的詳細程度str()&gt;dim()&gt;=nrow (因為兩者只差在variable的值)。

4.在第三題的第二小題，若我們只用max(table(PTT\_Posts$Author,exclude= "-"))，只能夠取出貼文數，並沒辦法取出作者，而若我們只用table不使用max函數，我們必須考慮到資料量可能會便龐大，假設今天觀察值有上千個，我們不可能一個一個去比對，因此我加上了迴圈的方式，讓電腦去"搜尋貼文數==最大貼文數"的作者。
