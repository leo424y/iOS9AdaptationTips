導航：

 1.  [對 APNs 的吐槽](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#對apns的吐槽)
 2.  [APNs新聞一欄](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#apns新聞一欄)
 3.  [新舊 APNs 協議工作示意圖對比](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#新舊-apns-協議工作示意圖對比)
 4.  [反人類的舊APNs協議設計](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#反人類的舊apns協議設計)
 5.  [基於 HTTP/2 的全新 APNs 協議](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#基於-http2-的全新-apns-協議)
 6.  [改進了，但仍需改進。還是有坑](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#改進了但仍需改進還是有坑)
 7.  [對App開發的影響](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#對app開發的影響)
 8.  [如何建立 Universal Push Notification Client SSL 證書](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#如何建立-universal-push-notification-client-ssl-證書)
 9.  [結束語](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#結束語)


## 對 APNs 的吐槽


 APNs 是 Apple Push Notification service 的簡稱（注意 APNs 的大小寫, s不需要大寫）。

 以下是我收集的一些關於 APNs 的吐槽，你先看下哪些吐槽比較“到位”：

 -- | 被吐槽的內容 | 吐槽
 -------------|-------------|-------------
 1 | 使用第三方SDK接入推送服務，SDK提供商卻告訴我，他們無法獲知哪條訊息成功傳送給了APNs，哪些失敗了，而且即使APNs接收了，APNs是否能保證投遞成功，他們也無能為力。| 我把訊息交給你了，你告訴什麼都保證不了？推送成功與否”基本靠猜“？
 2 | ![](http://ww1.sinaimg.cn/large/006tNbRwjw1f9w23sj9gsj30yg07jq3v.jpg)![](http://ww1.sinaimg.cn/large/006tNbRwjw1f9w23sltkhj30yi07naay.jpg) | 為什麼我推了多條訊息，APNs就只給我最後一條？！
 3 | 推送內容只能是 256 位元組 | 這也太小了，根本不夠用啊！
 4 | 生產環境推送證書、測試環境推送證書、tvOS推送證書、watchOS推送證書、VOIP推送證書。。 | 證書太多了，製作、切換證書太麻煩！


答案會穿插在下文中。


## APNs新聞一欄

時間 | 新聞 | 參考文件
-------------|-------------|-------------
2014年6月 | 2014年6月份WWDC搭載iOS8及以上系統的iOS裝置，能夠接收的最大playload大小提升到2KB。低於iOS8的裝置以及OS X裝置維持256位元組。 | [**What's New in Notifications - WWDC 2014 - Session 713 - iOS**]( https://developer.apple.com/videos/play/wwdc2014/713/)  ![enter image description here](http://i.stack.imgur.com/UW3ex.png)
2015年6月 | 2015年6月份WWDC宣佈將在不久的將來發布 “基於 HTTP/2 的全新 APNs 協議”，並在大會上釋出了僅僅支援測試證書的版本。| [**What's New in Notifications - WWDC 2015 - Session 720 - iOS, OS X**]( https://developer.apple.com/videos/play/wwdc2015/720/ )  ![enter image description here](http://i63.tinypic.com/2cy2ka0.jpg)
2015年12月17日 | 2015年12月17日起，釋出 “基於 HTTP/2 的全新 APNs 協議”,iOS 系統以及 OS X 系統，統一將最大 payload 大小提升到4KB。  | [**Apple Push Notification Service Update 12-17 2015**]( https://developer.apple.com/news/?id=12172015b )


## 新舊 APNs 協議工作示意圖對比

 基於 HTTP/2 的新 APNs 協議 | 基於二進位制的舊 APNs 協議
-------------|-------------
 ![enter image description here](http://i64.tinypic.com/szajom.jpg)| ![enter image description here](http://i68.tinypic.com/5wcxnr.jpg)


接下來我們分別對新舊協議進行一下介紹：

## 反人類的舊APNs協議設計

在介紹新版 APNs 前，讓我們來吐槽下舊的基於二進位制的 APNs 協議設計是多麼反人類：

在理論上，推送分發的伺服器要開啟一個同 APNs 閘道器伺服器的
連線，並保持這個連線。但在舊的協議下，APNs 服務卻不保證 socket 能維持這個連線。如果通道上沒有訊息往來，空閒下來到話，socket將被路由掐斷。也就是說：APNs 連線說斷就斷，而你無能為力。有意思的是：在舊的協議下，如果伺服器響應成功的話，你將不會收到任何迴應，但是如果伺服器響應失敗（例如，使用了一個非法的 Push token），伺服器將返回了一個錯誤編碼，並關閉這個socket。最重要的是，你必須重新傳送使用這個無效 token 以後傳送的所有推送（詳情見示意圖）。因此，你可能一直不能確定你的推送是否成功的被 APNs 伺服器接收。

成功了不響應，失敗了才響應，這個是最大的反人類。於是許多開發者想到了一個很 tricky 的辦法：利用這個“漏洞”，比如在每傳送10條後故意傳送一個錯誤的token，如果APNs有響應了，就可以確認 APNs 是處在可用狀態的，進而確認這10條訊息是傳送成功的。如果沒有響應就說明可能連線已經中斷，那麼這10條訊息很可能是丟失的，然後做進一步的處理。但代價顯而易見：將導致你們的推送系統效能低下。（本文中所說到“你們的推送系統”，如果是使用的第三方的SDK完成的推送服務，那麼就是指SDK提供商所搭建的推送系統。如果是你們公司自己搭建的推送系統，那麼就是指你們自己的推送系統。）蘋果有一個名為"feedback"的服務，我們可以定時呼叫這個服務來獲取invalid tokens的列表。這個服務你只要呼叫一次就可以獲得所有的invalid tokens 列表。所以，如果一個應用使用了很多不同公司的推送SDK，他們將會爭奪資源去輪詢查詢invalid tokens列表。invalid token越多，你們的推送系統效能將越低。而且 APNs 只要一發生錯誤就關閉這個連線，然後重新連線。也就是“重啟” socket 連線。

示意圖：

![enter image description here](http://i68.tinypic.com/5wcxnr.jpg)


圖中的 PN2 去哪裡了？它被放到了 feedback 列表裡，等待下次你呼叫 feedback 服務，然後重發。

為什麼Apple要在舊APNs中設計出“重啟”的策略？

為了效率。

就像PC機出問題，我們總說“重啟能解決90%的問題”。

為了理解“重啟”策略，我們可以類比下，熟悉 Erlang/OTP 的朋友可能知道， Erlang/OTP 在處理錯誤方面有獨到之處：監督樹（supervision trees）。大致來說，每一個 Erlang 程序都由一個監督程序發起並監視。當一個程序遇到了問題的時候，它就會退出。當程序退出的時候，其監督程序會將其重啟。

（這些監督程序由一個引導程序（bootstrap process）發起，當監督程序遇到錯誤的時候，引導程序會將其重啟）

其思想是，快速的失敗然後重啟比去處理錯誤要快。像這樣的錯誤處理看起來跟直覺相反 —— 當錯誤發生的時候通過放棄處理來獲得可靠性。但是重啟的確是解決暫時性錯誤的靈丹妙藥。


這也可能讓你想到 DNS 服務發展史：

 DNS 在設計之初是基於 UDP 的，顯然這樣的設計不能滿足當今社會的準確性的需求，於是湧現瞭如 DNSPod 這樣的基於 HTTP 的 DNS 解析服務。但是當時為什麼這樣設計，實際也很好理解，UDP 效率高，一來一回網路上傳輸的只有兩個包，而 HTTP則需要三次握手三個包，再一拆包，就需要四個包。這是受限於當時整個社會的頻寬水平較低，而現在沒人會感激 UDP 所節省的流量，所有人都在詬病DNS汙染問題。這樣你也許就理解了，為什麼舊的 APNs 設計如此反人類。這個是必經階段。

 那麼接下來就讓我們看看Apple為解決這些問題而推出的基於 HTTP/2 的全新 APNs 協議。

## 基於 HTTP/2 的全新 APNs 協議

來看下新版的 APNs 的新特性：

 - Request 和 Response 支援JSON網路協議
 - APNs支援狀態碼和返回 error 資訊
  - APNs推送成功時 Response 將返回狀態碼200，遠端通知是否傳送成功再也不用靠猜了！
  - APNs推送失敗時，Response 將返回 JSON 格式的 Error 資訊。
 - 最大推送長度提升到4096位元組（4Kb）
 - 可以通過 “HTTP/2 PING ” 心跳包功能檢測當前 APNs 連線是否可用，並能維持當前長連線。
 - 支援為不同的推送類型定義 “topic” 主題
 - 不同推送類型，只需要一種推送證書 Universal Push Notification Client SSL 證書。

示意圖：

 ![enter image description here](http://i64.tinypic.com/szajom.jpg)

其中最大的變化就是基於了 HTTP/2 協議，採用了長連線設計，並提供 “HTTP/2 PING ” 心跳包功能檢測、維持當前 APNs 連線，解決了老 APNs 無法維持連線的問題。
而且新增的狀態碼特性，也解決了這個問題：無法獲知訊息是否成功地從你們的推送系統投遞到了 APNs 上。理論上，你們可以保證訊息是100%投遞到了APNs的，因為你可以準確的知道哪條訊息到達了APNs，哪些沒到。重發特定失敗訊息成為可能。


所以上文開頭的吐槽中第一條，有一句是“不到位的”，因為現在SDK的提供商能夠準確地告訴你哪些訊息推送到APNs了，哪些沒有。


順便介紹下 HTTP/2 在客戶端開發上的應用：

 > HTTP/2 是 HTTP 協議釋出後的首個更新，於2015年2月17日被批准。它採用了一系列優化技術來整體提升 HTTP 協議的傳輸效能，如非同步連線複用、頭壓縮等等，可謂是當前網際網路應用開發中，網路層次架構優化的首選方案之一。

雖然服務端使用 HTTP/2 進行推送，對客戶端的協議選擇並沒有要求。但是我們還是推薦在客戶端的開發中，使用 HTTP/2 協議進行通訊。

Apple 對於 HTTP/2 的態度也非常積極，2015年5月 HTTP/2 正式發表後不久，便在緊接著6月召開的WWDC 2015大會中，向全球開發者宣佈，iOS 9 開始支援HTTP/2。如果我們要在客戶端上也使用 HTTP/2，那麼在網路庫的選擇上必然要使用 NSURLSession。

我們都知道 HTTP/2 是複用 TCP 管道連線的，而且 HTTP/2 也以高複用著稱，這也使新的 APNs 協議更加高效能。（題外話：這點也同樣體現在 NSURLSession 底層對於每個 session 是對多個 task 進行連線的複用。）

## Universal Push Notification Client SSL 證書

 在開發中，往往一條內容，需要向多個終端進行推送，終端有：iOS、tvOS、 and OS X devices, 和藉助iOS來實現推送的 Apple Watch。在以往的開發中，不同的推送，需要配置不同的推送證書：我們需要配置：dev證書、prod證書、VOIP證書、等等。而從2015年12月17日起，只使用一種證書就可以了，不再需要那麼多證書，這種證書就叫做Universal Push Notification Client SSL 證書（下文統一簡稱：Universal推送證書）。

## 改進了，但仍需改進。還是有坑

APNs的確改進來不少，但仍有需要改進對地方。還是有坑：

除了獲取TLS證書比較複雜未解決外，還有一些坑：

文章開頭提到過以下這種情況：

![](http://ww1.sinaimg.cn/large/006tNbRwjw1f9w23sj9gsj30yg07jq3v.jpg)

![](http://ww1.sinaimg.cn/large/006tNbRwjw1f9w23sltkhj30yi07naay.jpg)

很遺憾的告訴你，你的吐槽是“到位的”：你以後還得忍受這種反人類的設計。

這中間發生了什麼？

當 APNs 向你傳送了多條推送，但是你的裝置網路狀況不好，在 APNs 那裡下線了，這時 APNs 到你的手機的鏈路上有多條任務堆積，APNs 的處理方式是，只保留最後一條訊息推送給你，然後告知你推送數。那麼其他三條訊息呢？會被APNs丟棄。

有一些 App 的 IM 功能沒有維持長連線，是完全通過推送來實現到，通常情況下，這些 App 也已經考慮到了這種丟推送的情況，這些 App 的做法都是，每次收到推送之後，然後向自己的伺服器查詢當前使用者的未讀訊息。但是APNs也同樣無法保證這多條推送能至少有一條到達你的 App。很遺憾的告訴這些App，這次的更新對你們所遭受對這些坑，沒有改善。

為什麼這麼設計？APNs的儲存-轉發能力太弱，大量的訊息儲存和轉發將消耗Apple伺服器的資源，可能是出於儲存成本考慮，也可能是因為 Apple 轉發能力太弱。總之結果就是 APNs 從來不保證訊息的達到率。並且裝置上線之後也不會向伺服器上傳資訊。

所以上文開頭的吐槽中第一條，也有一句是“到位的”，因為現在SDK的提供商依然無法保證，訊息推到了 APNs，APNs能推到 App 那裡。

但Google Cloud Messaging就有這些特性。而且 GCM 現在也支援iOS裝置了，那麼 APNs 和 GCM 現在就形成了競爭關係。讓我共同期待 APNs 在2016年6月的 WWDC 的能有新的改進吧。

## 對App開發的影響

想使用新協議，如果你用的第三方推送，這裡最明顯的操作，就是你必須更新到支援新協議的SDK版本。因為新協議需要 SDK 上傳你 app 的 bundle id ,生成各個平臺推送用的 topic。如果你們自己搭建的服務，則需要你自己上傳。老協議不用上傳。

新 APNs 支援 iOS6 等全版本推送內容達4096位元組，舊 APNs 是14年6月之前只支援256位元組，在此之後支援 iOS8 以上2048位元組。以前受限於推送位元組，比如推文章 url，開發者選擇超出256後推送id，甚至不判斷直接推 id，接收後再請求完整 url。一旦請求錯誤，推送內容可能丟失。現在可以避免了。


## 補充說明

文中強調了 HTTP2 的長連線特性，HTTP1 也是可以有類似的 “長連線” 感念，但兩個概念還是有區別的，詳情可以參考[這裡](https://github.com/ChenYilong/iOSBlog/blob/master/Tips/基於Websocket的IM即時通訊技術/IM%20即時通訊技術在多應用場景下的技術實現，以及效能調優（iOS視角）.md#重連機制)。

## 如何建立 Universal Push Notification Client SSL 證書

 現在你知道什麼是 Universal Push Notification Client SSL 證書了，那麼如何建立它？

  ![what is Universal Push Notification Client SSL Certificate](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Art/12_ios_apns_certificate_2_2x.png)

  圖中其他方式，就叫做非 Universal 方式（下文簡稱：非 Universal 推送證書）：

  ![what is not Universal Push Notification Client SSL Certificate](http://i68.tinypic.com/dpg6jd.jpg)

這裡也推薦使用 Universal 推送證書來進行推送服務。詳細的建立步驟如下所示：

 1.  前往[蘋果開發者中心](https://developer.apple.com/account/)進行登入，並點選 “Certificates, Identifiers & Profiles”。
 ![enter Certificates, Identifiers & Profiles](http://i65.tinypic.com/xkyr0y.jpg)
 2. 選擇在 Certificates 欄下的“All”。
 3. 點選下圖中紅色邊框內的加號按鈕。
  ![Create SSL certificate](http://i64.tinypic.com/2z4y2q0.jpg)
 4. 選擇 “Production” 欄下的 “Apple Push Notification service SSL (Sandbox & Production)” 勾選後，點選下一步。
 ![Select push certificate](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Art/12_ios_apns_certificate_2_2x.png)
 5. 從 App ID 下拉選單中選擇你需要的 App ID ，點選下一步。
 ![select App ID](http://i64.tinypic.com/sql3pg.jpg)
 6. 這時會出現 **About Creating a Certificate Signing Request (CSR)**。
  ![guide to create a CSR](https://leancloud.cn/docs/images/ios_cert/cer2.png)

  根據它的說明建立 Certificate Signing Request。

  ![how to create a CSR](http://i67.tinypic.com/213hzc6.jpg)
 7. 點選下圖中的 “Choose File” 按鈕：
  ![upload CSR File](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Art/12_ios_apns_certificate_3_2x.png)
 8. 上傳剛剛生成的 .certSigningRequest 檔案 生成 APNs Push Certificate。
 9. 下載證書。
 10. 雙擊開啟證書，證書開啟時會啟動鑰匙串訪問工具。
  在鑰匙串訪問工具中，你的證書會顯示在 “證書” 中，注意選擇左下角的 “證書” 和左上角 “登入”。

   ![confirm create cer success](http://i64.tinypic.com/dc9289.jpg)

## 結束語

對於 APNs 而言，iOS9 的這一更新是有劃時代意義的，請即刻敦促你們公司的服務端進行升級，或者使用支援新 APNs 協議的 SDK 進行推送服務。 文中如有錯誤，並請幫忙指正，反饋請發往[微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/)。

參考連結：

 1. [**Configuring Push Notifications**](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html#//apple_ref/doc/uid/TP40012582-CH26-SW11)
 2. [**APNs Provider API**](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/APNsProviderAPI.html)
 3. [**HTTP/2 Protocol for iOS Push Notification Server(APNS)**]( https://dblog.laulkar.com/http2-protocol-for-apns.html )
