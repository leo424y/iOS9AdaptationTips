# iOS9AdaptationTips（iOS9開發學習交流群：515295083）



iOS9適配系列教程【中文在[頁面下方](https://github.com/ChenYilong/iOS9AdaptationTips#1-demo1_ios9網路適配_ats改用更安全的https)】

相關連結：[iOS10適配系列教程](https://github.com/ChenYilong/iOS10AdaptationTips)。

（截至2016年4月17日共有12篇，後續還將持續更新。更多iOS開發乾貨，歡迎關注  [微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/) ）

#中文快速導航：

 1.  [iOS9網路適配_ATS：改用更安全的HTTPS（見Demo1）](https://github.com/ChenYilong/iOS9AdaptationTips#1-demo1_ios9網路適配_ats改用更安全的https)
  1. [WHAT（什麼是SSL/TLS？跟HTTP和HTTPS有什麼關係）](https://github.com/ChenYilong/iOS9AdaptationTips#what什麼是ssltls跟http和https有什麼關係)
  2.  [WHY（以前的HTTP不是也能用嗎？為什麼要用SSL/TLS？Apple是不是又在反人類？）](https://github.com/ChenYilong/iOS9AdaptationTips#why以前的http不是也能用嗎為什麼要用ssltlsapple是不是又在反人類)
  3.  [HOW（如何適配？---弱弱地問下：加班要多久？）](https://github.com/ChenYilong/iOS9AdaptationTips#how如何適配---弱弱地問下加班要多久)
     1.  [第1種情況：HTTPS Only （只有HTTPS，所有情況下都使用ATS）](https://github.com/ChenYilong/iOS9AdaptationTips#1https-only-只有https所有情況下都使用ats)
     2.  [第2種情況：Mix & Match（混合）](https://github.com/ChenYilong/iOS9AdaptationTips#2mix--match混合)
     3.  [第3種情況：Opt Out（禁用ATS）](https://github.com/ChenYilong/iOS9AdaptationTips#3-opt-out禁用ats)
     4.  [第4種情況：Opt Out With Exceptions（除特殊情況外，都不使用ATS）](https://github.com/ChenYilong/iOS9AdaptationTips#4-opt-out-with-exceptions除特殊情況外都不使用ats)
     4.  [Certificate Transparency](https://github.com/ChenYilong/iOS9AdaptationTips#certificate-transparency)
  4.  [Q-A](https://github.com/ChenYilong/iOS9AdaptationTips#q-a)
 2.  [iOS9新特性_更靈活的後臺定位（見Demo2）](https://github.com/ChenYilong/iOS9AdaptationTips#2demo2_ios9新特性_更靈活的後臺定位)
 3.  [企業級分發](https://github.com/ChenYilong/iOS9AdaptationTips#3企業級分發)
  1.  [iOS9以後，企業級分發ipa包將遭到與Mac上dmg安裝包一樣的待遇：預設不能安裝，也不再出現“信任按鈕”](https://github.com/ChenYilong/iOS9AdaptationTips#1-ios9以後企業級分發ipa包將遭到與mac上dmg安裝包一樣的待遇預設不能安裝也不再出現信任按鈕)
  2.  [iOS9以後，企業分發時可能存在：下載的ipa包與網頁兩者的 bundle ID 無法匹配而導致下載失敗的情況](https://github.com/ChenYilong/iOS9AdaptationTips#2-ios9以後企業分發時可能存在下載的ipa包與網頁兩者的-bundle-id-無法匹配而導致下載失敗的情況)
  3.   [iOS9以後，企業APP安裝之後，在網路情況為Wi-Fi環境的時候，可能會出現無法驗證應用的情況](https://github.com/ChenYilong/iOS9AdaptationTips#3-企業app安裝之後在網路情況為wi-fi環境的時候可能會出現無法驗證應用的情況出現以下提示)
 4.  [Bitcode](https://github.com/ChenYilong/iOS9AdaptationTips#4bitcode)
 5.  [iOS9 URL Scheme 適配_引入白名單概念（見Demo3）](https://github.com/ChenYilong/iOS9AdaptationTips#5demo3---ios9-url-scheme-適配_引入白名單概念)
     1.   [常見 URL Scheme](https://github.com/ChenYilong/iOS9AdaptationTips#常見-url-scheme)
     2.   [Q-A](https://github.com/ChenYilong/iOS9AdaptationTips#q-a-1)
 6.  [ iPad適配Slide Over 和 Split View](https://github.com/ChenYilong/iOS9AdaptationTips#6-ipad適配slide-over-和-split-view)
 7.  [字型間隙變大導致 UI 顯示異常](https://github.com/ChenYilong/iOS9AdaptationTips#7字型間隙變大導致-ui-顯示異常)
 8.  [升級 Xcode7 後的崩潰與警告](https://github.com/ChenYilong/iOS9AdaptationTips#8升級-xcode7-後的崩潰與警告)
  1.  [iOS9 下使用 Masonry 會引起崩潰的一種情況](https://github.com/ChenYilong/iOS9AdaptationTips#ios9-下使用-masonry-會引起崩潰的一種情況)
  2.  [Xcode 升級後，舊的狀態列的樣式設定方式會引起警告](https://github.com/ChenYilong/iOS9AdaptationTips#xcode-升級後舊的狀態列的樣式設定方式會引起警告)
        1.  [Demo4---navigationController狀態列樣式新的設定方法](https://github.com/ChenYilong/iOS9AdaptationTips#demo4---navigationcontroller狀態列樣式新的設定方法)
  3.  [Xcode7 在 debug 狀態下也生成 .dSYM 檔案引起的警告](https://github.com/ChenYilong/iOS9AdaptationTips#xcode7-在-debug-狀態下也生成-dsym-檔案引起的警告)
  4.  [Xcode7 無法使用 8.x 系統的裝置偵錯，一執行就報錯 there is an intenal API error](https://github.com/ChenYilong/iOS9AdaptationTips#xcode7-無法使用-8x-系統的裝置偵錯一執行就報錯-there-is-an-intenal-api-error)
  5.  [使用了 HTML 的 iframe 元素可能導致無法從 Safari 跳轉至 App](https://github.com/ChenYilong/iOS9AdaptationTips#使用了-html-的-iframe-元素可能導致無法從-safari-跳轉至-app)
  6.  [iOS9鎖屏控制檯會列印警告](https://github.com/ChenYilong/iOS9AdaptationTips#ios9鎖屏控制檯會列印警告)
  7. [Xcode7 上傳應用時提示 ITMS-90535 Unable to publish iOS app with xxx SDK 的問題](http://stackoverflow.com/questions/32622899/itms-90535-unable-to-publish-ios-app-with-latest-google-signin-sdk)
  8.  [在didFinishLaunchingWithOptions結束後還沒有設定window的rootViewController會導致崩潰](https://github.com/ChenYilong/iOS9AdaptationTips#在didfinishlaunchingwithoptions結束後還沒有設定window的rootview
controller會導致崩潰)
 9.  [Demo5、Demo6--- 搜尋 API](https://github.com/ChenYilong/iOS9AdaptationTips#9demo5demo6----搜尋-api)
 10.   [iOS國際化問題：當前裝置語言字元串返回有變化](https://github.com/ChenYilong/iOS9AdaptationTips#10ios國際化問題當前裝置語言字元串返回有變化)
 11.  [UITableView顯示異常](https://github.com/ChenYilong/iOS9AdaptationTips#11uitableview顯示異常)
  1.  [程式碼建立的 tableView 無法隱藏 cell 分割線](https://github.com/ChenYilong/iOS9AdaptationTips#程式碼建立的-tableview-無法隱藏-cell-分割線)
  2. [reloadData 重新整理失效](https://github.com/ChenYilong/iOS9AdaptationTips#reloaddata-重新整理失效)
 12.  [基於 HTTP/2 的新 APNs 協議](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE/%E5%9F%BA%E4%BA%8EHTTP2%E7%9A%84%E5%85%A8%E6%96%B0APNs%E5%8D%8F%E8%AE%AE.md#如何建立-universal-push-notification-client-ssl-證書)



# English⬇️⬇️

For more infomation ，welcome to follow [my twitter](https://twitter.com/stevechen1010)

Reference：[iOS 10 Adaptation Tips](https://github.com/ChenYilong/iOS10AdaptationTips)。

## 1. Demo1_You'd Better Convert HTTP to HTTPS


How to deal with the SSL in iOS9，One solution is as follows:

![enter image description here](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/Demo1_iOS9網路適配_改用更安全的HTTPS/微博%40iOS程式犭袁/http問題.gif)

As  [Apple](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-DontLinkElementID_13) say :


  ![enter image description here](https://i.imgur.com/eTgSHZY.png)

![enter image description here](https://i.imgur.com/Tc0fS6p.jpg)

![enter image description here](https://i.imgur.com/v2Tskwh.jpg)

iOS 9 and OSX 10.11 require TLSv1.2 SSL for all hosts you plan to request data from, unless you specify exception domains in your app's Info.plist file.

The syntax for the Info.plist configuration looks like this:

    <key>NSAppTransportSecurity</key>
    <dict>
      <key>NSExceptionDomains</key>
      <dict>
        <key>yourserver.com</key>
        <dict>
          <!--Include to allow subdomains-->
          <key>NSIncludesSubdomains</key>
          <true/>
          <!--Include to allow insecure HTTP requests-->
          <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
          <true/>
          <!--Include to specify minimum TLS version-->
          <key>NSTemporaryExceptionMinimumTLSVersion</key>
          <string>TLSv1.1</string>
        </dict>
      </dict>
    </dict>

If your application (a third-party web browser, for instance) needs to connect to arbitrary hosts, you can configure it like this:

    <key>NSAppTransportSecurity</key>
    <dict>
        <!--Connect to anything (this is probably BAD)-->
	    <key>NSAllowsArbitraryLoads</key>
	    <true/>
    </dict>

If you have to do this, it's probably best to update your servers to support TLSv1.2 and SSL. This should be considered a temporary workaround.

As of today, the prerelease documentation makes no mention of any of these configuration options in any specific way. Once it does, I'll update the answer to link to the relevant documentation.

Even though your sever supports TLSv1.2, you may also have to follow what I wrote above to ensure connecting successfully in iOS 9:

After some discussion with Apple Support, the issue is due to the self signed certificate.

ATS only trusts certificate signed by a well known CA, all others are rejected. As a consequence, the only solution with a Self signed certificate is to set an exception with NSExceptionDomains.

## 2.Demo2_iOS9 new feature  in CoreLocation : backgroud when needed

If you're using CoreLocation framework in your app in Xcode7(pre-released), you may notice that there is a newly added property called allowsBackgroundLocationUpdates in CLLocationManager class.

This new property is explained in the WWDC session ["What's New in Core Location"][6].
 ![enter image description here][7]

  [7]: https://i.imgur.com/pvVh1fx.png
The default value is `NO` if you link against iOS 9.

If your app uses location in the background without showing the blue status bar, you have to set `allowsBackgroundLocationUpdates` to `YES` in addition to setting the background mode capability in Info.plist. Otherwise location updates are only delivered in foreground. The advantage is that, in the same app, you can now have some of the location managers update locations in background, while others at foreground. You can also reset the value to `NO` to change the behavior.

The documentation makes it pretty clear:

> By default, this is NO for applications linked against iOS 9.0 or
> later, regardless of minimum deployment target.
>
> With UIBackgroundModes set to include "location" in Info.plist, you
> must also set this property to YES at runtime whenever calling
> -startUpdatingLocation with the intent to continue in the background.
>
> Setting this property to YES when UIBackgroundModes does not include
> "location" is a fatal error.
>
> Resetting this property to NO is equivalent to omitting "location"
> from the UIBackgroundModes value.  Access to location is still
> permitted whenever the application is running (ie not suspended), and
> has sufficient authorization (ie it has WhenInUse authorization and is
> in use, or it has Always authorization).  However, the app will still
> be subject to the usual task suspension rules.
>
> See -requestWhenInUseAuthorization and -requestAlwaysAuthorization for
> more details on possible authorization values.


  [6]: https://developer.apple.com/videos/wwdc/2015/?id=714
Set  Info.plist like this：
 ![enter image description here][8]

  [8]:https://i.imgur.com/MAoKbUe.png

The syntax for the Info.plist configuration looks like this:

    <key>NSLocationAlwaysUsageDescription</key>
    <string>微博@iOS程式犭袁 請求後臺定位許可權</string>

    <key>UIBackgroundModes</key>
    <array>
        <string>location</string>
    </array>

Use like:

    _locationManager = [[CLLocationManager alloc] init];
    _locationManager.delegate = self;
    [_locationManager setDesiredAccuracy:kCLLocationAccuracyBest];
    if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 8) {
        [_locationManager requestAlwaysAuthorization];
    }
    if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 9) {
        _locationManager.allowsBackgroundLocationUpdates = YES;
    }
    [_locationManager startUpdatingLocation];
## 3.iOS 9 Dealing With Untrusted Enterprise Developer

Since iOS 9, there is no more “trust” option for an enterprise build.

Before iOS 9, there used to have an alert popped like this:

 ![enter image description here][10]

  [10]: http://i.stack.imgur.com/WwF76.png

Now:

 ![enter image description here][11]

  [11]: https://i.imgur.com/Skn9iXk.png

Users have to do the configuration themselves:
Go to Settings - General - Profiles - tap on your Profile - tap on Trust button.

  ![enter image description here][12]

  [12]: https://i.imgur.com/AdGNYHe.gif


## 4.bitcode option
After Xcode 7, bitcode option is set enabled by default. If your library is complied without bitcode while the bitcode option is enabled in your project setting, you can




>  1. Update your library with bit code, or you'll get warnings like:

> (null): URGENT: all bitcode will be dropped because
> '/Users/myname/Library/Mobile
> Documents/com~apple~CloudDocs/foldername/appname/GoogleMobileAds.framework/GoogleMobileAds(GADSlot+AdEvents.o)'
> was built without bitcode. You must rebuild it with bitcode enabled
> (Xcode setting ENABLE_BITCODE), obtain an updated library from the
> vendor, or disable bitcode for this target. Note: This will be an
> error in the future.




>  2.  Say NO to Enable Bitcode in your target Build Settings





>  ![enter image description here][15]



  [15]: https://i.imgur.com/OoOogUe.gif

and the Library Build Settings to remove the warnings

For more information,go to
[documentation of bitcode in developer library][16]


  [16]: https://developer.apple.com/library/prerelease/watchos/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html#//apple_ref/doc/uid/TP40012582-CH35-SW2

,and WWDC 2015 Session 102: ["Platforms State of the Union"][17]


  [17]: https://developer.apple.com/videos/wwdc/2015/?id=102

 ![enter image description here][18]

  [18]: http://mobileforward.net/wp-content/uploads/2015/06/Screen-Shot-2015-06-12-at-6.57.54-PM-697x351.png
## 5.Privacy and Your App【URL scheme changes】
iOS 9 has made a small change to the handling of URL scheme. You must whitelist the url's that your app will call out by using the `LSApplicationQueriesSchemes` key in your `Info.plist`.

Please see the post here: http://awkwardhare.com/post/121196006730/quick-take-on-ios-9-url-scheme-changes

The main conclusion is that:

> If you call the “canOpenURL” method on a URL that is not in your whitelist, it will return “NO”, even if there is an app installed that has registered to handle this scheme. A “This app is not allowed to query for scheme xxx” syslog entry will appear.

> If you call the “openURL” method on a URL that is not in your whitelist, it will fail silently. A “This app is not allowed to query for scheme xxx” syslog entry will appear.

The author also speculates that this is a bug with the OS and Apple will fix this in a subsequent release.

This is a new security feature of iOS 9. Watch [WWDC 2015 Session 703][19] for more information.

 ![enter image description here][20]

  [20]: https://i.imgur.com/2HxWQqq.png

Any app built with SDK 9 needs to provide an `LSApplicationQueriesSchemes` entry in its plist file, declaring which scheme it attempts to query.

    <key>LSApplicationQueriesSchemes</key>
    <array>
     <string>urlscheme</string>
     <string>urlscheme2</string>
     <string>urlscheme3</string>
     <string>urlscheme4</string>
    </array>

  [19]: https://developer.apple.com/videos/wwdc/2015/?id=703

Assuming that we have two apps: Test A and Test B. TestB wants to check whether TestA is installed or not. "TestA" defines the following URL scheme in its info.plist file:

	<key>CFBundleURLTypes</key>
	<array>
		<dict>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>testA</string>
			</array>
		</dict>
	</array>

The second app "TestB" tries to find out if "TestA" is installed by calling:

    [[UIApplication sharedApplication]
                        canOpenURL:[NSURL URLWithString:@"TestA://"]];

But this will generally return NO in iOS9, because "TestA" needs to be added to the LSApplicationQueriesSchemes entry in TestB's info.plist file. This is done by adding the following code to TestB's info.plist file:

    <key>LSApplicationQueriesSchemes</key>
    <array>
        <string>TestA</string>
    </array>

A working implementation can be found here:
https://github.com/gatzsche/LSApplicationQueriesSchemes-Working-Example

## 6. Support Slide Over and Split View of iOS 9

![enter image description here](http://cdn1.tnwcdn.com/wp-content/blogs.dir/1/files/2015/06/ew-.gif)
How to make an old project support Slide Over and Split View in iOS 9?
You may find all the demo projects was written by storyboard or xib,
but the older project's UI is written by code！

I would suggest switching to storyboards to make your life easy.

I would highly recommend you to watch the following WWDC videos and then think about what exactly you need to do in order to support multi tasking.


 1. [Mysteries of Auto Layout, Part 1](https://developer.apple.com/videos/wwdc/2015/?id=218)

 2. [What's New in Storyboards](https://developer.apple.com/videos/wwdc/2015/?id=215)

 3. [Implementing UI Designs in Interface Builder](https://developer.apple.com/videos/wwdc/2015/?id=407)

 4. [Getting Started with Multitasking on iPad in iOS 9](https://developer.apple.com/videos/wwdc/2015/?id=205)

 5. [Optimizing Your App for Multitasking on iPad in iOS](https://developer.apple.com/videos/wwdc/2015/?id=212)

## ￼7. UI Display Problem Due to Enlarged Character Space
iOS 9 introduced a new font of Chinese characters. The enlarged character space may cause display problems of text labels, especially for fixed label width.
To avoid this, we prefer to use ‘sizeToFit’ and ‘ceilf’ methods to calculate label size dynamically.
## 8. Crash and Warnings
Sina SDK crashes on iOS 9 with the following information: Solution: update SDK.
A case of Masonry crashing on iOS 9
left & leading, trailing & right: not equivalent any more. Some other modifications to make:
Old way of setting status bar style lead to errors. Solution: delete ‘View controller-based status bar appearance’ key in ‘Info.plist’, apply new methods to set status bay style.
Demo4 — set status bar style of navigationController
If it still does not work after using the above method, the problem is probably on your rootViewController.
Xcode 7 generates .dSYM file under debug circumstance and causes warnings. Solution: change debug setting. Prevent Xcode from generating .dSYM.
Xcode 7 cannot debugging on 8.x devices.
Solution: ensure the project name not including Chinese character.
Problem of jumping between Safari and other apps.
This is probably caused by using ‘iframe’ element in HTML.
Warning when locking screen while executing tasks in apps. Haven’t found a solution.
Crash when rootViewController not set in didFinishLaunchingWithOptions
Solution: initialize rootViewController in didFinishLaunchingWithOptions and replace it afterwards.
## 9. Search API
Import related frameworks, and configure ‘search elements’ just as configuring tableview cells: Demo 6 shows how to combine CoreSpotlightSearch and tableView:
## 10. Change of Device Language Return String
Before iOS 9: the above code returns language string code (e.g. “zh-Hans”).
￼iOS 9: returns language string code + area code (e.g. “zh-Hans-US"). Be careful when checking current language.
##11. UITableView Display Problem
A project running well on Xcode 6 may encounter the following problems on Xcode 7:
 1. Tableview created by code cannot hide cell separators.
 2.  reloadData does not work.
For cell separators, we provide two solutions (the first one preferred):
As for reloadData, we assume this may conflict with some new features. We can use local reload as an alternative:

##License

Posted by [微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/)

 [Creative Commons BY-NC-ND 3.0](http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh)





> 中文

## 1. Demo1_iOS9網路適配_ATS：改用更安全的HTTPS

[摘要]為了強制增強資料訪問安全， iOS9 預設會把 <del>所有的http請求</del> 所有從`NSURLConnection` 、 `CFURL` 、 `NSURLSession`發出的 HTTP 請求，都改為 HTTPS 請求：iOS9.x-SDK編譯時，預設會讓所有從`NSURLConnection` 、 `CFURL` 、 `NSURLSession`發出的 HTTP 請求統一採用TLS 1.2 協議。因為 AFNetworking 現在的版本底層使用了 `NSURLConnection` ，眾多App將被影響（基於iOS8.x-SDK的App不受影響）。伺服器因此需要更新，以解析相關資料。如不更新，可通過在 Info.plist 中聲明，倒退回不安全的網路請求。而這一做法，官方文件稱為ATS，全稱為App Transport Security，是iOS9的一個新特性。

一個符合 ATS 要求的 HTTPS，應該滿足如下條件：

 1. Transport Layer Security協議版本要求TLS1.2以上
 2. 服務的Ciphers配置要求支援Forward Secrecy等
 3. 證書籤名演算法符合ATS要求等

官方文件 [ ***App Transport Security Technote*** ](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/index.html#//apple_ref/doc/uid/TP40016240) 對ATS 的介紹：

![enter image description here](http://i58.tinypic.com/ajsf0j.jpg)


注：有童鞋反映：伺服器已支援TLS 1.2 SSL ，但iOS9上還是不行，還要進行本文提出的適配操作。

那是因為：要注意 App Transport Security 要求 TLS 1.2，而且它要求站點使用支援forward secrecy協議的密碼。證書也要求是符合ATS規格的，ATS只信任知名CA頒發的證書，小公司所使用的 self signed certificate，還是會被ATS攔截。。因此慎重檢查與你的應用互動的伺服器是不是符合ATS的要求非常重要。對此，建議使用下文中給出的NSExceptionDomains，並將你們公司的域名掛在下面。下文也會詳細描述該問題。


官方文件 [ ***App Transport Security Technote*** ](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/index.html#//apple_ref/doc/uid/TP40016240) 對CA頒發的證書要求：

 > Certificates must be signed using a SHA256 or better signature hash algorithm, with either a 2048 bit or greater RSA key or a 256 bit or greater Elliptic-Curve (ECC) key.
Invalid certificates result in a hard failure and no connection


在討論之前，跟往常一樣，先說下iOS程式猿們最關心的問題：

###跟我有毛關係？需要我加班嗎？！

首先咱們來看下業內對Apple這一做法的評論：

![enter image description here](https://i.imgur.com/Q17QDG0.png)

這是某社交App上討論，看來業內還是吐槽聲和肯定聲同在。

結論是：

> 跟你很有關係，加班吧，少年！

書歸正傳【嚴肅臉】，我們正式討論下 WHAT，WHY，HOW：

 1. WHAT（什麼是SSL/TLS？跟HTTP和HTTPS有什麼關係）
 2. WHY（以前的HTTP不是也能用嗎？為什麼要用SSL/TLS？！Apple是不是又在反人類？）
 3. HOW（如何適配？---弱弱地問下：加班要多久？）

###WHAT（什麼是SSL/TLS？跟HTTP和HTTPS有什麼關係）

什麼是SSL/TLS？
SSL你一定知道，在此不做贅述。主要說下什麼是TLS，還有跟HTTP和HTTPS有什麼關係。

TLS 是 SSL 新的別稱：

“TLS1.0”之於“SSL3.1”，猶“公元2015”之於“民國104”，“一千克”之於“一公斤”：稱呼不同，意思相同。

SSL 3.0版本之後的迭代版本被重新命名為TLS 1.0：**TLS 1.0＝SSL 3.1**。所以我們平常也經常見到 “SSL/TLS” 這種說法。

目前，應用最廣泛的是TLS 1.0，接下來是SSL 3.0。目前主流瀏覽器都已經實現了TLS 1.2的支援。

常用的有下面這些：

 - SSL 2.0
 - SSL 3.0
 - TLS 1.0 (SSL 3.1)
 - TLS 1.1 (SSL 3.1)
 - TLS 1.2 (SSL 3.1)

那為什麼標題是“使用HTTPS”而沒有提及SSL和TLS什麼事？
“SSL/TLS”跟HTTP和HTTPS有什麼關係？

要理解這個，要看下他們之間的關係：

> HTTP+SSL/TLS+TCP = HTTPS

![HTTP+SSL/TLS+TCP](http://www.zytrax.com/tech/survival/ssl-layers.gif)

或者

> HTTPS = “HTTP over SSL”

也就是說：

> Apple讓你的HTTP採用SSL/TLS協議，就是讓你從HTTP轉到HTTPS。而這一做法，官方文件稱為ATS，全稱為App Transport Security。

###WHY（以前的HTTP不是也能用嗎？為什麼要用SSL/TLS？Apple是不是又在反人類？）

> 不使用SSL/TLS的HTTP通訊，就是不加密的通訊！

 不使用SSL/TLS的HTTP通訊，所有資訊明文傳播，帶來了三大風險：

 1. 竊聽風險（eavesdropping）：第三方可以獲知通訊內容。
 2. 篡改風險（tampering）：第三方可以修改通訊內容。
 3. 冒充風險（pretending）：第三方可以冒充他人身份參與通訊。

SSL/TLS協議是為了解決這三大風險而設計的，希望達到：
 1. 所有資訊都是加密傳播，第三方無法竊聽。
 2. 具有校驗機制，一旦被篡改，通訊雙方會立刻發現。
 3. 配備身份證書，防止身份被冒充。

SSL/TLS的作用，打個比方來講：

如果原來的 HTTP 是塑料水管，容易被戳破；那麼如今新設計的 HTTPS 就像是在原有的塑料水管之外，再包一層金屬水管（SSL/TLS協議）。一來，原有的塑料水管照樣執行；二來，用金屬加固了之後，不容易被戳破。





### HOW（如何適配？---弱弱地問下：加班要多久？）

正如文章開頭所說：

> TLS 1.2 協議 強制增強資料訪問安全 系統 Foundation 框架下的“相關網路請求”將不再預設使用 HTTP 等不安全的網路協議，而預設採用 TLS 1.2。伺服器因此需要更新，以解析相關資料。如不更新，可通過在 Info.plist 中聲明，倒退回不安全的網路請求。

總之：

> 要麼咱們iOS程式猿加班，要麼後臺加班：


方案一：立即讓公司的服務端升級使用TLS 1.2，以解析相關資料。

方案二：雖Apple不建議，但可通過在 Info.plist 中聲明，倒退回不安全的網路請求依然能讓App訪問指定http，甚至任意的http，具體做法見gif圖，示例Demo見 [Demo1](https://github.com/ChenYilong/iOS9AdaptationTips)

![enter image description here](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/Demo1_iOS9網路適配_改用更安全的HTTPS/微博%40iOS程式犭袁/http問題.gif)

這也是官方文件和WWDC給出的解決方案：

 1.   [Apple官方文件](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-DontLinkElementID_13)  ![enter image description here](https://i.imgur.com/eTgSHZY.png)


 2. [WWDC Session： "Networking with NSURLSession" session（ 【WWDC 2015 session 703, “Privacy and Your App” O網頁連結 】, 時間在30:18左右）](https://developer.apple.com/videos/wwdc/2015/?id=703)





 ![enter image description here](https://i.imgur.com/Tc0fS6p.jpg)

 ![enter image description here](https://i.imgur.com/v2Tskwh.jpg)

  ![enter image description here](https://cdn-images-1.medium.com/max/800/1*9-VeRXU5SAI6lLZeWLI0hQ.png)


即使你的應用使用的是：你沒有許可權控制的CDN (Content Delivery Network)，而且它不支援HTTPS！

也別擔心，Apple都替你考慮好了：

 ![enter image description here](http://i61.tinypic.com/ae9tgj.jpg)

 正如你在上圖中看到的：蘋果官方提供了一些可選配置項來決定是否開啟ATS模式，也就是可以選擇開啟或者不開啟。

 開發者可以針對某些確定的URL不使用ATS，這需要在工程中的info.plist中標記NSExceptionDomains。在NSExceptionDomains字典中，可以顯式的指定一些不使用ATS的URL。這些你可以使用的例子可以是:

  - NSIncludesSubdomains

  - NSExceptionAllowInsecureHTTPLoads

  - NSExceptionRequiresForwardSecrecy

  - NSExceptionMinimumTLSVersion

  - NSThirdPartyExceptionAllowsInsecureHTTPLoads

  - NSThirdPartyExceptionMinimumTLSVersion

  - NSThirdPartyExceptionRequiresForwardSecrecy



這些關鍵字使我們可以更加細緻的設定針對不使用ATS的域名情況下禁用ATS或者一些特殊的ATS選項。

你可能注意到一些關鍵字像是使用了一些其他關鍵字中的詞但是在前面加上了"ThirdParty"字樣，比如列表裡最後三個：

- NSThirdPartyExceptionAllowsInsecureHTTPLoads

- NSThirdPartyExceptionMinimumTLSVersion

- NSThirdPartyExceptionRequiresForwardSecrecy

在功能上，這些關鍵字與不含有"ThirdParty"的關鍵字有同樣的效果。而且實際執行中所呼叫的程式碼將會完全忽略是否使用"ThirdParty"關鍵字。你應該使用適用於你的場景的關鍵字而不必過多考慮這些。

關於App Transport Security，每個應用都屬於4個大類當中的一類。我們來看看每一個大類都是怎樣影響應用的。


|--| 分類名|解釋|
-------------|-------------|-------------
1.|HTTPS Only （只有HTTPS，所有情況下都使用ATS）|如果你的應用只基於支援HTTPS的伺服器，你的應用不需要做任何改變。但是，注意App Transport Security要求TLS 1.2，而且它要求站點使用支援forward secrecy協議的密碼。證書也要求是符合ATS規格的。因此慎重檢查與你的應用互動的伺服器是不是符合ATS的要求。
2.|Mix & Match（混合）|如果你的伺服器不符合ATS要求，你需要在你的應用的 Info.plist 檔案中說明哪些地址是不符合ATS要求的。
3.|Opt Out（禁用ATS）|如果你在建立一個網頁瀏覽器，因為你不能確定使用者將要訪問哪個網頁，也就不可能指明這些網頁是否支援ATS要求且在HTTPS上傳輸。在這種情況下，只能配置為禁用ATS。
4.|Opt Out With Exceptions（除特殊情況外，都不使用ATS）|如果想禁用ATS的同時又想定義一些例外。這個應用場景是當你的應用需要從很多不符合ATS要求的伺服器上取資料，但是也要與一個你可控的API(符合ATS要求)互動。在這種情況下，需要在應用的 Info.plist 檔案中配置為允許所有請求，但是你也指定了一個或多個例外來表明哪些請求是必須符合ATS的要求。

下面分別做一下介紹：

####1.HTTPS Only （只有HTTPS，所有情況下都使用ATS）
如果你的應用只基於支援HTTPS的伺服器，那麼你太幸運了。你的應用不需要做任何改變。

唯一需要做的事情就是使用  `NSURLSession` 。如果你的開發目標是iOS 9或者 OS X EI Capitan之後，ATS 的最佳實踐將會應用到所有基於 `NSURLSession` 的網路。

但也有人遇到過這樣的疑惑：伺服器已支援TLS 1.2 SSL ，但iOS9上還是不行，還要進行本文提出的適配操作。


那是因為：要注意 App Transport Security 要求 TLS 1.2，而且它要求站點使用支援forward secrecy協議的密碼。證書也要求是符合ATS規格的，ATS只信任知名CA頒發的證書，小公司所使用的 self signed certificate，還是會被ATS攔截。因此慎重檢查與你的應用互動的伺服器是不是符合ATS的要求非常重要。對此，建議使用下文中給出的NSExceptionDomains，並將你們公司的域名掛在下面。

官方文件 [ ***App Transport Security Technote*** ](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/index.html#//apple_ref/doc/uid/TP40016240) 對CA頒發的證書要求：

 > Certificates must be signed using a SHA256 or better signature hash algorithm, with either a 2048 bit or greater RSA key or a 256 bit or greater Elliptic-Curve (ECC) key.
Invalid certificates result in a hard failure and no connection



####2.Mix & Match（混合）

如果你的伺服器不符合ATS要求。

比如當你遇到以下三個不符合 ATS 要求的伺服器的域名時：

 1. api.insecuredomain.com
 2. cdn.domain.com
 3. thatotherdomain.com

你可以分別設定如下：

 1. api.insecuredomain.com

 Info.plist 配置中的XML源碼如下所示:


 ```XML
    <key>NSAppTransportSecurity</key>
    <dict>
        <key>NSExceptionDomains</key>
        <dict>
            <key>api.insecuredomain.com</key>
            <dict>

                <!--允許App進行不安全的HTTP請求-->
                <key>NSExceptionAllowsInsecureHTTPLoads</key>
                <true/>

                <!--適用於這個特定域名下的所有子域-->
                <key>NSIncludesSubdomains</key>
                <true/>
            </dict>
        </dict>
    </dict>
 ```


 在 plist 檔案裡顯示如下：


 ![enter image description here](http://i59.tinypic.com/fxtk0j.jpg)

 我們定義的第一個“例外”（Exception）告訴ATS當與這個子域互動的時候撤銷了必須使用HTTPS的要求。注意這個僅僅針對在“例外”（Exception）中聲明瞭的子域。非常重要的一點是要理解NSExceptionAllowsInsecureHTTPLoads關鍵字並不僅僅只是與使用HTTPS相關。這個“例外”（Exception）指明瞭對於那個域名，所有的App Transport Security的要求都被撤銷了。



 2. cdn.domain.com
 Info.plist 配置中的XML源碼如下所示:


 ```XML
	<key>NSAppTransportSecurity</key>
	<dict>
		<key>NSExceptionDomains</key>
		<dict>
			<key>cdn.somedomain.com</key>
			<dict>
				<key>NSThirdPartyExceptionMinimumTLSVersion</key>
				<string>TLSv1.1</string>
			</dict>
		</dict>
	</dict>
 ```


 在 plist 檔案裡顯示如下：

  ![enter image description here](http://i58.tinypic.com/29atm5k.jpg)

 很可能你的應用是與一個支援HTTPS傳輸資料的伺服器互動，但是並沒有使用TLS 1.2或更高。在這種情況下，你定義一個“例外”（Exception），它指明應該使用的最小的TLS的版本。這比完全撤銷那個域名的App Transport Security要更好更安全。

 3. thatotherdomain.com

 Info.plist 配置中的XML源碼如下所示:

 ```XML
       <key>NSAppTransportSecurity</key>
        <dict>
            <key>NSExceptionDomains</key>
            <dict>
                <key>thatotherdomain.com</key>
                <dict>
                    <!--適用於這個特定域名下的所有子域-->
                    <key>NSIncludesSubdomains</key>
                    <true/>
                    <!--擴充套件可接受的密碼列表：這個域名可以使用不支援 forward secrecy 協議的密碼-->
                    <key>NSExceptionRequiresForwardSecrecy</key>
                    <false/>
                    <!--允許App進行不安全的HTTP請求-->
                    <key>NSExceptionAllowsInsecureHTTPLoads</key>
                    <true/>
                    <!--在這裡聲明所支援的 TLS 最低版本-->
                    <key>NSExceptionMinimumTLSVersion</key>
                    <string>TLSv1.1</string>
                </dict>
            </dict>
        </dict>
 ```

 在 plist 檔案裡顯示如下：


 ![enter image description here](http://i61.tinypic.com/w6xn43.jpg)

 `NSIncludesSubdomains` 關鍵字告訴 App Transport Security 這個“例外”（Exception）適用於這個特定域名的所有子域。這個“例外”（Exception）還進一步通過擴充套件可接受的密碼列表來定義這個域名可以使用不支援forward secrecy( `NSExceptionRequiresForwardSecrecy` )  協議的密碼。想了解更多關於forward secrecy的資訊，推薦去看官方文件  [ ***Apple's technote*** ](https://developer.apple.com/library/prerelease/mac/technotes/App-Transport-Security-Technote/index.html) 。

如果你的App中同時用到了這三個域名，那麼應該是這樣：

 ```XML
     <key>NSAppTransportSecurity</key>
        <dict>
            <key>NSExceptionDomains</key>
            <dict>
                <key>api.insecuredomain.com</key>
                <dict>
                    <key>NSExceptionAllowsInsecureHTTPLoads</key>
                    <false/>
                </dict>
                <key>cdn.somedomain.com</key>
                <dict>
                    <key>NSThirdPartyExceptionMinimumTLSVersion</key>
                    <string>TLSv1.1</string>
                </dict>
                <key>thatotherdomain.com</key>
                <dict>
                    <key>NSIncludesSubdomains</key>
                    <true/>
                    <key>NSExceptionRequiresForwardSecrecy</key>
                    <false/>
                </dict>
            </dict>
        </dict>
 ```

![enter image description here](http://i61.tinypic.com/13ynggk.jpg)

#### 3. Opt Out（禁用ATS）
上面是比較嚴謹的做法，指定了能訪問哪些特定的HTTP。當然也有暴力的做法：
徹底倒退回不安全的HTTP網路請求，能任意進行HTTP請求，比如你在開發一款瀏覽器App，或者你想偷懶，或者後臺想偷懶，或者公司不給你升級伺服器。。。

你可以在Info.plist 配置中改用下面的XML源碼：


 ```XML
    <key>NSAppTransportSecurity</key>
    <dict>
        <!--徹底倒退回不安全的HTTP網路請求，能任意進行HTTP請求 (不建議這樣做)-->
	    <key>NSAllowsArbitraryLoads</key>
	    <true/>
    </dict>
 ```


在 plist 檔案裡顯示如下：

![enter image description here](http://i57.tinypic.com/9uq2c7.jpg)

#### 4. Opt Out With Exceptions（除特殊情況外，都不使用ATS）

上面已經介紹了三種情景，還有一種可能你也會遇到：

當你禁用ATS的同時又想定義一些“例外”（Exception）。這個應用場景是當你的應用需要從很多不符合ATS要求的伺服器上取資料，但是也要與一個你可控的API(符合ATS要求)互動。在這種情況下，在應用的Info.plist檔案中配置為允許所有請求，但是你也指定了一個或多個“例外”（Exception）來表明哪些地址是必須符合 App Transport Security 要求的。下面是Info.plist檔案應該會有的內容：


 ```XML
<key>NSAppTransportSecurity</key>
        <dict>
            <key>NSAllowsArbitraryLoads</key>
            <true/>
            <key>NSExceptionDomains</key>
            <dict>
                <key>api.tutsplus.com</key>
                <dict>
                    <key>NSExceptionAllowsInsecureHTTPLoads</key>
                    <false/>
                </dict>
            </dict>
        </dict>
 ```

 在 plist 檔案裡顯示如下：

![enter image description here](http://i62.tinypic.com/de1rw9.jpg)


 <p><del>【注：以上在Info.plist配置中的做法已經驗證可行，但目前Apple的prerelease版本的官方文件並未提及Info.plist中配置的程式碼，我將密切關注官方文件，如有提及，再來更新[本文](https://github.com/ChenYilong/iOS9AdaptationTips) .你若發現官方文件有提及了，也可在[微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/)通知下我。】（官方文件已經有闡述）</del></p>

####Certificate Transparency

雖然ATS大多數安全特性都是預設可用的，Certificate Transparency 是必須設定的。如果你有支援Certificate Transparency的證書，你可以檢查NSRequiresCertificateTransparency關鍵字來使用Certificate Transparency。再次強調，如果你的證書不支援Certificate Transparency，此項需要設定為不可用。

如果需要偵錯一些由於採用了ATS而產生的問題，需要設定CFNETWORK_DIAGNOSTICS為1，這樣就會列印出包含被訪問的URL和ATS錯誤在內的NSURLSession錯誤資訊。要確保處理了遇到的所有的錯誤訊息，這樣才能使ATS易於提高可靠性和擴充套件性。

####Q-A

Q：我用xcode7編譯的app，如果不在plist裡面加關鍵字說明，ios9下不能進行網路請求，因為我們伺服器並不支援 TLS 1.2 ，我要是直接下載app store上的，什麼也沒有做，也是能正常網路請求。

A：本文中所羅列的新特性，多數情況下指的是 iOS9.X-SDK 新特性，AppStore 的版本是基於 iOS8.X-SDK或 iOS7.X-SDK，所以並不受 iOS9新特性約束。也就是說：**Xcode7給iOS8打裝置包可以請求到網路，Xcode7給iOS9裝置打的包請求不到網路，Xcode7和iOS9缺一不可，才需要網路適配ATS。**


那麼，如何確認自己項目所使用的 SDK？在Targets->Build Setting-->Architectures


![enter image description here](http://i58.tinypic.com/amsa9u.jpg)

Q：伺服器已支援TLS 1.2 SSL ，但iOS9上還是不行，還要進行本文提出的適配操作。


A：那是因為：要注意 App Transport Security 要求 TLS 1.2，而且它要求站點使用支援forward secrecy協議的密碼。證書也要求是符合ATS規格的，ATS只信任知名CA頒發的證書，小公司所使用的 self signed certificate，還是會被ATS攔截。。因此慎重檢查與你的應用互動的伺服器是不是符合ATS的要求非常重要。對此，建議使用下文中給出的NSExceptionDomains，並將你們公司的域名掛在下面。


官方文件 [ ***App Transport Security Technote*** ](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/index.html#//apple_ref/doc/uid/TP40016240) 對CA頒發的證書要求：

 > Certificates must be signed using a SHA256 or better signature hash algorithm, with either a 2048 bit or greater RSA key or a 256 bit or greater Elliptic-Curve (ECC) key.
Invalid certificates result in a hard failure and no connection

Q：我使用的是第三方的網路框架，比如 AFNetworking 、ASIHTTPRequest、CFSocket 等，這個有影響沒有？

A： AFNetworking 有影響，其它沒影響。

 ATS 是隻針對 `NSURLConnection` 、 `CFURL` 、 `NSURLSession` ，如果底層涉及到這三個類就會有影響。

現在的 AFNetworking 的 AFHTTPRequestOperationManager 實現是使用的 `NSURLConnection` 。

但 AFNetworking 也有更新計劃，移除 `NSURLConnection` 相關API，遷移到 AFHTTPSessionManager ，但還未執行，詳情見：[https://github.com/AFNetworking/AFNetworking/issues/2806](https://github.com/AFNetworking/AFNetworking/issues/2806)。


Q：試了一下禁用 ATS 的方法 但是還是無法聯網 仍然提示要使用https?


 > App Transport Security has blocked a cleartext HTTP (http://) resource load since it is insecure. Temporary exceptions can be configured via your app&#039;s Info.plist file.
</p>The resource could not be loaded because the App Transport Security policy requires the use of a secure connection.


A：遇到這類問題，90%是出現在“一個 Project 多 Target ”的情況下，所以
請確保你修改的，確實是你的 Target 所屬的 Info.plist ！

如何確認？請前往這裡，確認你 Target 所屬的 Info.plist 究竟是哪個：

Project -> Your Target -> Build Settings -> Info.plist File

![enter image description here](http://i60.tinypic.com/sbrfrl.jpg)

或者更直截了當一點，直接修改：

Project -> Your Target —>info－> Custom iOS target properties－> 新增禁用 ATS 的屬性

![enter image description here](http://i60.tinypic.com/zvbt7b.jpg)

還有一種可能性是：禁用 ATS 的程式碼貼上進 plist 時，位置不對，可以嘗試放在第5行.


Q：我的項目是“一個 Project 多 Target ”，按照本文禁用 ATS 的方法，是不是每個 Info.plist 都要修改？

A：不需要，用到哪個 Target 修改哪個的 Info.plist ，Target 是獨立的，不受其他 Target 的影響，也不會影響其他 Target。

Q：如何檢測我們公司 HTTPS 是否符合 ATS 的要求？

A：
如果你的 App 的服務也在升級以適配ATS要求，可以使用如下的方式進行校驗：

在OS X EI Capitan系統的終端中通過nscurl命令來診斷檢查你的HTTPS服務配置是否滿足Apple的ATS要求:

 ```Objective-C
 $ nscurl --verbose --ats-diagnostics https://<your_server_domain>
 ```

當然，你也可以讓公司服務端的同事參考Apple提供官方指南App Transport Security Technote進行服務的升級配置以滿足ATS的要求：

一個符合 ATS 要求的 HTTPS，應該滿足如下條件：

 1. Transport Layer Security協議版本要求TLS1.2以上
 2. 服務的Ciphers配置要求支援Forward Secrecy等
 3. 證書籤名演算法符合ATS要求等


##2.Demo2_iOS9新特性_更靈活的後臺定位

【iOS9在定位的問題上，有一個壞訊息一個好訊息】壞訊息：如果不適配iOS9，就不能偷偷在後臺定位（不帶藍條，見圖）！好訊息：將允許出現這種場景：同一App中的多個location manager：一些只能在前臺定位，另一些可在後臺定位，並可隨時開啟或者關閉特定location manager的後臺定位。

如果沒有請求後臺定位的許可權，也是可以在後臺定位的，不過會帶藍條：
 ![enter image description here][9]
  [9]: https://i.imgur.com/UoqGHlG.png

如何偷偷在後臺定位：請求後臺定位許可權：

	 // 1. 例項化定位管理器
    _locationManager = [[CLLocationManager alloc] init];
    // 2. 設定代理
    _locationManager.delegate = self;
    // 3. 定位精度
    [_locationManager setDesiredAccuracy:kCLLocationAccuracyBest];
    // 4.請求使用者許可權：分為：⓵只在前臺開啟定位⓶在後臺也可定位，
    //注意：建議只請求⓵和⓶中的一個，如果兩個許可權都需要，只請求⓶即可，
    //⓵⓶這樣的順序，將導致bug：第一次啟動程式後，系統將只請求⓵的許可權，⓶的許可權系統不會請求，只會在下一次啟動應用時請求⓶
    if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 8) {
        //[_locationManager requestWhenInUseAuthorization];//⓵只在前臺開啟定位
        [_locationManager requestAlwaysAuthorization];//⓶在後臺也可定位
    }
    // 5.iOS9新特性：將允許出現這種場景：同一app中多個location manager：一些只能在前臺定位，另一些可在後臺定位（並可隨時禁止其後臺定位）。
    if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 9) {
        _locationManager.allowsBackgroundLocationUpdates = YES;
    }
    // 6. 更新使用者位置
    [_locationManager startUpdatingLocation];

但是如果照著這種方式嘗試，而沒有配置Info.plist，100%你的程式會崩潰掉，並報錯：

> *** Assertion failure in -[CLLocationManager setAllowsBackgroundLocationUpdates:], /BuildRoot/Library/Caches/com.apple.xbs/Sources/CoreLocationFramework_Sim/CoreLocation-1808.1.5/Framework/CoreLocation/CLLocationManager.m:593


這個問題，有兩種方式可以解決：

第一種：

要將  Info.plist 配置如下：
 ![enter image description here][8]

  [8]:https://i.imgur.com/MAoKbUe.png

對應的 Info.plist 的XML源碼是：

    <key>NSLocationAlwaysUsageDescription</key>
    <string>微博@iOS程式犭袁 請求後臺定位許可權</string>

    <key>UIBackgroundModes</key>
    <array>
        <string>location</string>
    </array>

第二種：

在對應 target 的 Capabilities -> Background Modes -> 開啟 Location Updates

![enter image description here](http://cdn2.raywenderlich.com/wp-content/uploads/2014/12/background_modes.png)



##3.企業級分發

有兩處變化：

 1. iOS9以後，企業級分發ipa包將遭到與Mac上dmg安裝包一樣的待遇：預設不能安裝，也不再出現“信任按鈕”
 2. iOS9以後，企業分發時可能存在：下載的ipa包與網頁兩者的 bundle ID 無法匹配而導致下載失敗的情況


###  1. iOS9以後，企業級分發ipa包將遭到與Mac上dmg安裝包一樣的待遇：預設不能安裝，也不再出現“信任按鈕”

iOS9之前，企業級分發十分方便：點選App出現“信任按鈕”，


 ![enter image description here][13]

  [13]: https://i.imgur.com/aSmM8bk.png

iOS9以後，企業級分發ipa包將遭到與Mac上dmg安裝包一樣的待遇：預設不能安裝，也不再出現“信任按鈕”

 ![enter image description here][11]

  [11]: http://i58.tinypic.com/2zecm83.jpg

必須讓使用者進行gif圖中的設定：


 ![enter image description here][14]

  [14]: https://i.imgur.com/PXM235L.gif

### 2. iOS9以後，企業分發時可能存在：下載的ipa包與網頁兩者的 bundle ID 無法匹配而導致下載失敗的情況

iOS9升級後眾多企業分發的 app 已經出現了不能安裝的情況，而iOS8或更早的系統不受影響。那是因為從iOS9以後，系統會在 ipa 包下載完之後，拿ipa包中的 bundle ID 與網頁中的 plist 檔案中的 bundle ID 進行比對，不一致不允許安裝。

錯誤提示如下：

![enter image description here](http://i57.tinypic.com/28jckus.jpg)

網頁中的 plist 檔案中的 bundle ID 的作用可參考 [《iOS:蘋果企業證書通過網頁分發安裝app》](http://blog.sina.com.cn/s/blog_6afb7d800101fa16.html) 。

正如這篇文章提到的，“網頁中的 plist 檔案”是習慣的叫法，也有人稱作“manifest檔案”，比如 [這篇文章](http://gknops.github.io/adHocGenerate/)。


而iOS9之前，蘋果不會檢查這一項，因此iOS9之前可以安裝。

導致這一錯誤的原因除了粗心，還有開發者是故意設定不一致，據開發者說：

 > 當初伺服器 plist 的 bundle id 上故意做成成不一致。是為了解決一些人安裝不上的問題。


詳情可參考： [《升級到ios 9，企業版釋出現在無法安裝成功了，有人遇到了這種問題嗎？》](http://www.cocoachina.com/bbs/read.php?tid-324230-fpage-2-page-1.html)




如何知道是因為 bundle id 不一致造成的無法安裝？

通過檢視裝置上的日誌資訊：有一個 itunesstored 程序提示安裝資訊：

      itunesstored →  <Warning>: [Download]: Download task did finish: 8 for download: 2325728577585828282
      itunesstored →  <Warning>: [ApplicationWorkspace] Installing download: 2325728577585828282 with step(s): Install
      itunesstored →  <Warning>: [ApplicationWorkspace]: Installing software package with bundleID: com.***.***: bundleVersion: 1.01 path: /var/mobile/Media/Downloads/2325728577585828282/-1925357977307433048
      itunesstored →  <Warning>: BundleValidator: Failed bundleIdentifier: com.***.**** does not match expected bundleIdentifier: com.***.*********
      itunesstored →  <Warning>: [ApplicationWorkspace]: Bundle validated for bundleIdentifier: com.****.******success: 0
      itunesstored →  <Warning>: LaunchServices: Uninstalling placeholder for app <LSApplicationProxy: 0x12677be70> com.****.*******(Placeholder) <file:///private/var/mobile/Containers/Bundle/Application/B62D8EA3-2052-4393-8A7E-3FD27228BFC2/2325728577585828282.app>
      itunesstored →  <Warning>: LaunchServices: Uninstalling app <LSApplicationProxy: 0x12677be70> com.****.*****(Placeholder) <file:///private/var/mobile/Containers/Bundle/Application/B62D8EA3-2052-4393-8A7E-3FD27228BFC2/2325728577585828282.app>

其中的這一句很重要：

     itunesstored →  <Warning>: BundleValidator: Failed bundleIdentifier: com.***.**** does not match expected bundleIdentifier: com.***.*********

經過核對，果然是.ipa檔案中真實的Bundle ID和manifest檔案中配置的資訊不匹配，然後測試發現：

> iOS 9是校驗bundle-identifier值的，而iOS 9以下版本是不校驗，一旦iOS 9發現bundle-identifier不匹配，即使下載成功了，也會 Uninstall(日誌中提示的)app的。


適配方法：

 1. 兩者的 bundle id 修改一致

 一旦出現iOS9能夠安裝企業版本APP，iOS9以下版本不能安裝，一定先檢視安裝日誌，然後核對每個參數配置。

 manifest檔案的參考配置。

 ```XML
 <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
"http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
   <!-- array of downloads. -->
   <key>items</key>
   <array>
       <dict>
           <!-- an array of assets to download -->
           <key>assets</key>
           <array>
               <!-- software-package: the ipa to install. -->
               <dict>
                   <!-- required.  the asset kind. -->
                   <key>kind</key>
                   <string>software-package</string>
                   <!-- optional.  md5 every n bytes.  -->
                   <!-- will restart a chunk if md5 fails. -->
                   <key>md5-size</key>
                   <integer>10485760</integer>
                   <!-- optional.  array of md5 hashes -->
                   <key>md5s</key>
                   <array>
                       <string>41fa64bb7a7cae5a46bfb45821ac8bba</string>
                       <string>51fa64bb7a7cae5a46bfb45821ac8bba</string>
                   </array>
                   <!-- required.  the URL of the file to download. -->
                   <key>url</key>
                   <string>http://www.example.com/apps/foo.ipa</string>
               </dict>
               <!-- display-image: the icon to display during download. -->
               <dict>
                   <key>kind</key>
                   <string>display-image</string>
                   <!-- optional. icon needs shine effect applied. -->
                   <key>needs-shine</key>
                   <true/>
                   <key>url</key>
                   <string>http://www.example.com/image.57×57.png</string>
               </dict>
               <!-- full-size-image: the large 512×512 icon used by iTunes. -->
               <dict>
                   <key>kind</key>
                   <string>full-size-image</string>
                   <!-- optional.  one md5 hash for the entire file. -->
                   <key>md5</key>
                   <string>61fa64bb7a7cae5a46bfb45821ac8bba</string>
                   <key>needs-shine</key>
                   <true/>
                   <key>url</key>
                   <string>http://www.example.com/image.512×512.jpg</string>
               </dict>
           </array><key>metadata</key>
           <dict>
               <!-- required -->
               <key>bundle-identifier</key>
               <string>com.example.fooapp</string>
               <!-- optional (software only) -->
               <key>bundle-version</key>
               <string>1.0</string>
               <!-- required.  the download kind. -->
               <key>kind</key>
               <string>software</string>
               <!-- optional. displayed during download; -->
               <!-- typically company name -->
               <key>subtitle</key>
               <string>Apple</string>
               <!-- required.  the title to display during the download. -->
               <key>title</key>
               <string>Example Corporate App</string>
           </dict>
       </dict>
   </array>
</dict>
</plist>
 ```


 2. 使用fir.im等第三方分發平臺：上述“ bundle id 不一致導致下載失敗”這種情況只會出現在企業自己搭建網頁分發的情形下，事實證明第三方的分發平臺更加專業，已經很好地規避了該情況的發生。

### 3. 企業APP安裝之後，在網路情況為Wi-Fi環境的時候，可能會出現無法驗證應用的情況。出現以下提示：

**無法驗證"**** Co.,Ltd"應用，需要網路連線以在這臺iPhone上驗證"**** Co.,Ltd"應用。接入網際網路並重試。**

![](http://i63.tinypic.com/10ho85w.jpg)
![](http://i66.tinypic.com/30ucruo.jpg)
![](http://i66.tinypic.com/w14qi1.jpg)

而此時，Wi-Fi網路是接入網際網路的。如果多次驗證不通過的話，我們需要切換到非Wi-Fi網路環境下才能解決這個問題。

### Q-A

Q：企業分發，企業版證書在iOS9上安裝應用報 ` Ignore manifest download, already have bundleID: com.mycom.MyApp`  只有我的手機無法安裝，別人 iOS9 都可以安裝

A：這並非 iOS9的問題，iOS8及以前的系統也會出現，和快取有關係，請嘗試關機重啟手機，然後就可以安裝了。


 Q：為什麼用微信掃描二維碼不能直接下載？

 A：部分市場支援直接掃描二維碼下載（如蒲公英，fir.im等）,但是用微信掃描二維碼不能直接。因為安裝app所在頁面必須要符合蘋果`itms-services`協議，在不符合該協議的頁面點選安裝會沒有反應。比如使用微信、QQ掃描點選安裝會沒有反應。

此時需要在微信或QQ安裝頁面點選右上角按鈕，在彈出框裡找到使用Safari瀏覽器開啟選項，點選跳轉到系統瀏覽器Safari裡後再點選“安裝”按鈕進行安裝。

部分第三分瀏覽器支援`itms-services`協議，可以直接點選安裝。

## 4.Bitcode

【前言】未來， Watch 應用必須包含 bitcode ，iOS不強制，Mac OS不支援。
但最坑的一點是： Xcode7 及以上版本會預設開啟 bitcode 。

什麼是 bitcode ？

通俗解釋：線上版安卓ART模式。

Apple 官方文件--[ ***App Distribution Guide – App Thinning (iOS, watchOS)*** ](https://developer.apple.com/library/prerelease/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html#//apple_ref/doc/uid/TP40012582-CH35)是這樣定義的：

> Bitcode is an intermediate representation of a compiled program. Apps you upload to iTunes Connect that contain bitcode will be compiled and linked on the App Store. Including bitcode will allow Apple to re-optimize your app binary in the future without the need to submit a new version of your app to the store.

翻譯過來就是：

>  bitcode 是被編譯程式的一種中間形式的程式碼。包含 bitcode 配置的程式將會在 App Store 上被編譯和連結。 bitcode 允許蘋果在後期重新優化我們程式的二進位制檔案，而不需要我們重新提交一個新的版本到 App Store 上。


在 Xcode簡介--- [ ***What’s New in Xcode-New Features in Xcode 7*** ](https://developer.apple.com/library/prerelease/ios/documentation/DeveloperTools/Conceptual/WhatsNewXcode/Articles/xcode_7_0.html)中這樣描述：


 > Bitcode. When you archive for submission to the App Store, Xcode will compile your app into an intermediate representation. The App Store will then compile the bitcode down into the 64 or 32 bit executables as necessary.

也就是

 > 當我們提交程式到 App Store上時， Xcode 會將程式編譯為一箇中間表現形式( bitcode )。然後 App store 會再將這個 bitcode 編譯為可執行的64位或32位程式。


再看看這兩段描述都是放在App Thinning(App瘦身)一節中，可以看出其與包的優化有關了。

打個比方，沒有 bitcode  的 AppStore 裡所提供的 App，類似在新華書店裡賣捆綁銷售的《四大名著叢書--精裝版》，要買只能全買走，有了 bitcode 就好比這套四大名著每本都可以單賣，顧客就能按需購買。我們開發者在這個過程中扮演的角色是圖書出版商的角色，應該照顧那些沒錢一次買四本的顧客。（不要做不珍惜使用者流量和儲存空間的奸商。。）

那為什麼第三方的 SDK 不支援 bitcode，我的 app 也就不能支援？打個比方，《四大名著叢書》只要有一本是可以單賣的，那麼你很難再賣捆綁銷售款的《四大名著叢書》了，所以乾脆全都可以單賣，這大概就是 Apple 的邏輯。

 App Thinning 官方文件解釋如下：


 > The App Store and operating system optimize the installation of iOS and watchOS apps by tailoring app delivery to the capabilities of the user’s particular device, with minimal footprint. This optimization, called app thinning, lets you create apps that use the most device features, occupy minimum disk space, and accommodate future updates that can be applied by Apple. Faster downloads and more space for other apps and content provides a better user experience.


開發者都知道，當前 iOS App 的編譯打包方式是把適配相容多個裝置的執行檔案及資原始檔合併一個檔案，上傳和下載的檔案則包含了所有的這些檔案，導致佔用較多的儲存空間。

App Thinning是一個關於節省iOS裝置儲存空間的功能，它可以讓iOS裝置在安裝、更新及執行App等場景中僅下載所需的資源，減少App的佔用空間，從而節省裝置的儲存空間。

根據Apple官方文件的介紹，App Thinning主要有三個機制：


 1. Slicing

 開發者把App安裝包上傳到AppStore後，Apple服務會自動對安裝包切割為不同的應用變體(App variant)，當使用者下載安裝包時，系統會根據裝置型號下載安裝對應的單個應用變體。

 2. On-Demand Resources

 ORD(隨需資源)是指開發者對資源新增標籤上傳後，系統會根據App執行的情況，動態下載並載入所需資源，而在儲存空間不足時，自動刪除這類資源。

 3. Bitcode
 開啟Bitcode編譯後，可以使得開發者上傳App時只需上傳Intermediate Representation(中介軟體)，而非最終的可執行二進位制檔案。 在使用者下載App之前，AppStore會自動編譯中介軟體，產生裝置所需的執行檔案供使用者下載安裝。

（喵大(@onevcat)在其部落格 [《開發者所需要知道的 iOS 9 SDK 新特性》](http://onevcat.com/2015/06/ios9-sdk/) 中也描述了iOS 9中蘋果在App瘦身中所做的一些改進，大家可以轉場到那去研讀一下。）


其中，Bitcode的機制可以支援動態的進行App Slicing，而對於Apple未來進行硬體升級的措施，此機制可以保證在開發者不重新發布版本的情況下而相容新的裝置。

 Bitcode 是一種中間程式碼，那它是什麼格式的呢？ LLVM 官方文件有介紹這種檔案的格式：  [ ***LLVM Bitcode File Format*** ](http://llvm.org/docs/BitCodeFormat.html#llvm-bitcode-file-format) 。

如果你的應用也準備啟用 Bitcode 編譯機制，就需要注意以下幾點：

 1. Xcode 7預設開啟 Bitcode ，如果應用開啟 Bitcode，那麼其整合的其他第三方庫也需要是 Bitcode 編譯的包才能真正進行 Bitcode 編譯
 2. 開啟 Bitcode 編譯後，編譯產生的  `.app`  體積會變大(中間程式碼，不是使用者下載的包)，且  `.dSYM`  檔案不能用來崩潰日誌的符號化(使用者下載的包是 Apple 服務重新編譯產生的，有產生新的符號檔案)
 3. 通過 Archive 方式上傳 AppStore 的包，可以在Xcode的Organizer工具中下載對應安裝包的新的符號檔案


如何適配？

在上面的錯誤提示中，提到了如何處理我們遇到的問題：


 > You must rebuild it with bitcode enabled (Xcode setting ENABLE_BITCODE), obtain an updated library from the vendor, or disable bitcode for this target. for architecture arm64

正如開頭所說的：


 > 未來， Watch 應用必須包含 Bitcode ，iOS不強制，Mac OS不支援。
但最坑的一點是： Xcode7 及以上版本會預設開啟 Bitcode 。

Xcode 7 + 會開啟 Bitcode。

也就是說，也兩種方法適配：

方法一：更新 library 使包含 Bitcode ，否則會出現以下中的警告；

> (null): URGENT: all bitcode will be dropped because
> '/Users/myname/Library/Mobile
> Documents/com~apple~CloudDocs/foldername/appname/GoogleMobileAds.framework/GoogleMobileAds(GADSlot+AdEvents.o)'
> was built without bitcode. You must rebuild it with bitcode enabled
> (Xcode setting ENABLE_BITCODE), obtain an updated library from the
> vendor, or disable bitcode for this target. Note: This will be an
> error in the future.


甚至有的會報錯誤，無法通過編譯：

> ld: ‘/Users/**/Framework/SDKs/PolymerPay/Library/mobStat/lib**SDK.a(**ForSDK.o)’ does not contain bitcode. You must rebuild it with bitcode enabled (Xcode setting ENABLE_BITCODE), obtain an updated library from the vendor, or disable bitcode for this target. for architecture arm64

或：

 > ld: -undefined and -bitcode_bundle (Xcode setting  `ENABLE_BITCODE` =YES) cannot be used together
clang: error: linker command failed with exit code 1 (use -v to see invocation)

![enter image description here](http://i62.tinypic.com/330vhug.jpg)

無論是警告還是錯誤，得到的資訊是：我們引入的一個第三方庫不包含bitcode。

方法二：關閉Bitcode，方法見下圖

>  ![enter image description here][15]



  [15]: https://i.imgur.com/OoOogUe.gif

我們可以在”Build Settings”->”Enable Bitcode”選項中看到：

用 Xcode 7+ 新建一個 iOS 程式時， bitcode 選項預設是設定為YES的。現在需要改成NO。



如果我們開啟了 bitcode ，在提交包時，下面這個介面也會有個 bitcode 選項：

![enter image description here](http://i60.tinypic.com/5b2q7m.jpg)

這裡有一個坑，目前 Xcode 處理 Embedded Binaries 時還有些問題，解決辦法是，上圖中左下角的兩個選項不要同時勾選：

相關討論見： [ ***Missing BCSymbolMap for AppStore Submission - Xcode7B5*** ](https://forums.developer.apple.com/thread/14729)

用 AD_HOC 打測試包時，也有相應的 bitcode 選項：

![enter image description here](http://i64.tinypic.com/8vospi.jpg)

那麼 SDK 廠商如何支援 bitcode 呢？需要在 Xcode7上重新編譯，確保預設開啟的 bitcode 沒有去主動關閉。

但是如果僅僅是編譯一下，則會出現下類似的如下警告：

![enter image description here](http://image17-c.poco.cn/mypoco/myphoto/20150928/17/1733887242015092817143106.jpg?1462x120_120
)



 > ld: warning: full bitcode bundle could not be generated because 'Lookback(Lookback.o)' was built only with bitcode marker. The library must be generated from Xcode archive build with bitcode enabled (Xcode setting ENABLE_BITCODE)



警告的消除步驟：

模擬器、真機分開打包，SDK在build的時候，讓模擬器與真機分開build，模擬器不設定bitcode的參數，真機的加上，然後再合起來。（“合起來”指的是指令集，好比 x86_64 i386 跟 armv7 arm64合起來。）用命令列打包的話 加上這個參數OTHER_CFLAGS=“-fembed-bitcode”。

![enter image description here](https://cdn-images-1.medium.com/max/800/1*RHLu74QyT4DNqKY-7lo_6g.png)

詳情可移步：[ ***How do I xcodebuild a static library with Bitcode enabled?*** ](http://stackoverflow.com/a/31486233/3395008)

同時切記，為 release 狀態設定 `BITCODE_GENERATION_MODE=bitcode` ，開啟 `full bitcode` 模式，否則會報錯誤：`Failed to verify bitcode in  XXX.framework` :


![enter image description here](http://i64.tinypic.com/2cxukix.jpg)


![enter image description here](https://cdn-images-1.medium.com/max/800/1*cd9mvJ7BJCW51zXSglwhBQ.png)

詳見：

 1.  [**Static Libraries, Frameworks, and Bitcode**]( https://medium.com/@heitorburger/static-libraries-frameworks-and-bitcode-6d8f784478a9#.eq7rl2msf ) 。
 2.  [ ***Failed to verify bitcode in Alamofire*** ](https://github.com/Alamofire/Alamofire/issues/835)
 3.  用 xcodebuild 新增 bitcode 支援 [ ***How do I xcodebuild a static library with Bitcode enabled?*** ](http://stackoverflow.com/a/31486233/3395008)

更多資訊，請移步

 1. [bitcode 蘋果官方文件][16]


  [16]: https://developer.apple.com/library/prerelease/watchos/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html#//apple_ref/doc/uid/TP40012582-CH35-SW2

 2.  WWDC 2015 Session 102: ["Platforms State of the Union"][17]


  [17]: https://developer.apple.com/videos/wwdc/2015/?id=102

 ![enter image description here][18]

  [18]: http://mobileforward.net/wp-content/uploads/2015/06/Screen-Shot-2015-06-12-at-6.57.54-PM-697x351.png


##5.Demo3---iOS9 URL Scheme 適配_引入白名單概念

 [ ***WWDC 2015 Session 703: "Privacy and Your App*** ](https://developer.apple.com/videos/wwdc/2015/?id=703) （ 時間在30：18左右）關於 `URL scheme` 的介紹，指出：


 ![enter image description here][20]

  [20]: https://i.imgur.com/2HxWQqq.png

也就是說：在iOS9中，如果使用 `canOpenURL:` 方法，該方法所涉及到的  `URL scheme` 必須在"Info.plist"中將它們列為白名單，否則不能使用。key叫做LSApplicationQueriesSchemes ，鍵值內容是

	<key>LSApplicationQueriesSchemes</key>
	<array>
	 <string>urlscheme</string>
	 <string>urlscheme2</string>
	 <string>urlscheme3</string>
	 <string>urlscheme4</string>
	</array>

白名單上限是50個：

 [ ***WWDC 2015 Session 703: "Privacy and Your App*** ](https://developer.apple.com/videos/wwdc/2015/?id=703) ）有說明：

 >
 “So for apps that are linked before iOS 9 and are running on iOS 9, they will be given 50 distinct URL schemes.”  --  WWDC 2015 session 703 Privacy and Your App


 <p><del>
然而，我們卻發現了一件意外的事：
當我們在 iOS9-beta（截至本文釋出時，iOS9正式版還未釋出）中，使用 `openURL:`  方法時，不在白名單中的 URL 會報錯 > “This app is not allowed to query for scheme xxx” 。
無論是官方文件還是 WWDC 的視訊中都沒有提及 `openURL:`  方法的這一變動，所以猜測這是 beta 版本一個 bug ，截至本文釋出時，iOS9正式版還未釋出，期望在正式版中能得以修復。在此之前，可通過將 `openURL:`  用到的 `URL scheme` 列入白名單來解決這個 bug 。（經測試：iOS9 beta5中已經修復）</del></p>

iOS9中 `openURL:` 方法沒有什麼實質性的變化，僅僅多了一個確認動作：

![enter image description here](http://i57.tinypic.com/8zjh35.jpg)

蘋果為什麼要這麼做？

在 iOS9 之前，你可以使用 `canOpenURL:` 監測使用者手機裡到底裝沒裝微信，裝沒裝微博。但是也有一些別有用心的 App ，這些 App 有一張常用 App 的 `URL scheme`，然後他們會多次呼叫`canOpenURL:` 遍歷該表，來監測使用者手機都裝了什麼 App ，比如這個使用者裝了叫“大姨媽”的App，你就可以知道這個使用者是女性，你就可以只推給這個使用者女性用品的廣告。這是侵犯使用者隱私的行為。

這也許就是原因。

本項目中給出了一個演示用的 Demo ，倉庫的資料夾叫“Demo3_iOS9URLScheme適配_引入白名單概念”，Demo引用自[ ***LSApplicationQueriesSchemes-Working-Example*** ](https://github.com/gatzsche/LSApplicationQueriesSchemes-Working-Example)

Demo結構如下：

![enter image description here](http://i61.tinypic.com/2hyyuqv.jpg)

主要演示的情景是這樣的：

假設有兩個App： weixin(微信) and 我的App. 我的App 想監測 weixin(微信) 是否被安裝了. "weixin(微信)" 在 info.plist  中定義了 URL scheme :

    <key>CFBundleURLTypes</key>
    <array>
        <dict>
            <key>CFBundleURLSchemes</key>
            <array>
                <string>weixin</string>
            </array>
        </dict>
    </array>

 我的App 想監測 weixin(微信) 是否被安裝了 ：

    [[UIApplication sharedApplication]
                        canOpenURL:[NSURL URLWithString:@"weixin(微信)://"]];

即使你安裝了微信，在iOS9中，這有可能會返回NO：

因為你需要將 "weixin(微信)" 新增到 “我的App” 的 info.plist 檔案中：


    <key>LSApplicationQueriesSchemes</key>
    <array>
        <string>weixin</string>
    </array>

（以上只是為了演示，實際開發中，你不僅需要新增“weixin”還需要“wechat”這兩個。具體下文給出表格）


 <p><del>關於 `openURL:` 這個問題，可在 Demo3 中自行測試，如果該 bug 修復了的話，請私信[微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/)，我再來更新本文。（經測試：iOS9 beta5中已經修復）</del></p>


另外，推薦一篇[博文](http://awkwardhare.com/post/121196006730/quick-take-on-ios-9-url-scheme-changes)，其中最關鍵的是以下部分：

> If you call the “canOpenURL” method on a URL that is not in your whitelist, it will return “NO”, even if there is an app installed that has registered to handle this scheme. A “This app is not allowed to query for scheme xxx” syslog entry will appear.




 <p><del>> If you call the “openURL” method on a URL that is not in your whitelist, it will fail silently. A “This app is not allowed to query for scheme xxx” syslog entry will appear.
</del></p>


### 常見 URL Scheme

如果想一次性整合最常用的微信、新浪微博、QQ、支付寶四者的白名單，則配置如下：

 ```XML
 <key>LSApplicationQueriesSchemes</key>
<array>
    <!-- 微信 URL Scheme 白名單-->
    <string>wechat</string>
    <string>weixin</string>

    <!-- 新浪微博 URL Scheme 白名單-->
    <string>sinaweibohd</string>
    <string>sinaweibo</string>
    <string>sinaweibosso</string>
    <string>weibosdk</string>
    <string>weibosdk2.5</string>

    <!-- QQ、Qzone URL Scheme 白名單-->
    <string>mqqapi</string>
    <string>mqq</string>
    <string>mqqOpensdkSSoLogin</string>
    <string>mqqconnect</string>
    <string>mqqopensdkdataline</string>
    <string>mqqopensdkgrouptribeshare</string>
    <string>mqqopensdkfriend</string>
    <string>mqqopensdkapi</string>
    <string>mqqopensdkapiV2</string>
    <string>mqqopensdkapiV3</string>
    <string>mqzoneopensdk</string>
    <string>wtloginmqq</string>
    <string>wtloginmqq2</string>
    <string>mqqwpa</string>
    <string>mqzone</string>
    <string>mqzonev2</string>
    <string>mqzoneshare</string>
    <string>wtloginqzone</string>
    <string>mqzonewx</string>
    <string>mqzoneopensdkapiV2</string>
    <string>mqzoneopensdkapi19</string>
    <string>mqzoneopensdkapi</string>
    <string>mqzoneopensdk</string>

    <!-- 支付寶  URL Scheme 白名單-->
    <string>alipay</string>
    <string>alipayshare</string>

</array>
 ```
plist 檔案看起來會是這樣的：

![enter image description here](http://i58.tinypic.com/e5pyee.jpg)

其他平臺可在下面的列表中查詢：
各平臺OpenURL白名單說明

平臺名稱 | URL Schem  | 補充說明
-------------|-------------|-------------
微信 | wechat,</p> weixin
支付寶 | alipay,</p>alipayshare
QQ | mqqOpensdkSSoLogin, </p>mqqopensdkapiV2,</p>mqqopensdkapiV3,</p>wtloginmqq2,</p>mqq,</p>mqqapi |
QZONE | mqzoneopensdk, </p>mqzoneopensdkapi,</p>mqzoneopensdkapi19,</p>mqzoneopensdkapiV2,</p>mqqOpensdkSSoLogin,</p>mqqopensdkapiV2,</p>mqqopensdkapiV3,</p>wtloginmqq2,</p>mqqapi,</p>mqqwpa，</p>mqzone，</p>mqq | [注:若同時使用QQ和QZONE,則直接新增本格即可]
新浪微博 | sinaweibo,</p>sinaweibohd,</p>sinaweibosso,</p>sinaweibohdsso,</p>weibosdk,</p>weibosdk2.5 | [後兩個若匯入新浪SDK則需要]
豆瓣 |  無需配置 |
開心網 | 無需配置 |
易信 | yixin,</p> yixinopenapi
Google+ | googlechrome, </p>googlechrome-x-callback,</p>hasgplus4,</p>com.google.gppconsent,</p>com.google.gppconsent.2.2.0,</p>com.google.gppconsent.2.3.0,</p>com.google.gppconsent.2.4.0,</p>com.google.gppconsent.2.4.1 |
人人網 |  renrenapi,</p>renrenios,</p>renreniphone,</p>renren, |
Facebook | 見下文 |
Twitter | 無需配置 |
Pocket | pocket-oauth-v1|
Pinterest | pinit |
Instagram | instagram |
WhatsApp |  whatsapp |
Line | line |
KakaoTalk | kakaolink |
KaokaoStory | storylink |
LinkedIn | 無需配置 |
Tumblr | 無需配置 |
非平臺類 | 無需配置 | ( 如簡訊，複製，郵件等)




另外， Facebook 的URL Scheme白名單需要注意：

如果 SDK 版本低於 4.5 應補充
```
<key>LSApplicationQueriesSchemes</key>
<array>
    <string>fbapi</string>
    <string>fbapi20130214</string>
    <string>fbapi20130410</string>
    <string>fbapi20130702</string>
    <string>fbapi20131010</string>
    <string>fbapi20131219</string>
    <string>fbapi20140410</string>
    <string>fbapi20140116</string>
    <string>fbapi20150313</string>
    <string>fbapi20150629</string>
    <string>fbauth</string>
    <string>fbauth2</string>
    <string>fb-messenger-api20140430</string>
</array>
```

如果使用 FBSDKMessengerShareKit，還要加上
```
<string>fb-messenger-platform-20150128</string>
<string>fb-messenger-platform-20150218</string>
<string>fb-messenger-platform-20150305</string>
```

如果使用SDK版本高於4.6，則只需要加上
```
<key>LSApplicationQueriesSchemes</key>
<array>
        <string>fbapi</string>
        <string>fb-messenger-api</string>
        <string>fbauth2</string>
        <string>fbshareextension</string>
</array>
```

 [參考連結](https://developers.facebook.com/docs/ios/ios9) 。


### Q-A

Q：我用xcode7編譯的app，如果不在plist裡面加scheme，ios9下qq就會不顯示，因為我用了qqsdk裡的判斷是否安裝qq的方法，我要是直接下載app store上的，沒有加scheme，qq也是能顯示。

A：本文中所羅列的新特性，多數情況下指的是 iOS9.X-SDK 新特性，AppStore 的版本是基於 iOS8.X-SDK或 iOS7.X-SDK，所以並不受 iOS9新特性約束。也就是說：**Xcode7給iOS8打裝置包不需要白名單也能呼叫“canOpenURL” ，Xcode7給iOS9裝置打的包則不然，Xcode7和iOS9缺一不可，才需要適配URL Scheme。**


那麼，如何確認自己項目所使用的 SDK？在Targets->Build Setting-->Architectures


![enter image description here](http://i58.tinypic.com/amsa9u.jpg)

 Q：我們自己的應用跳到微信、支付寶、微博等的URLScheme是固定幾個，但是從微信、支付寶、微博跳回到我們的應用的URLScheme可能是成千上萬個，那他們那些大廠是如何做這個白名單？

A：白名單策略影響的僅僅是 canOpenURL: 介面，OpenURL: 不受影響，這些大廠只呼叫 openURL: 所以不受 iOS9 的影響。

Q：文中提到了設定白名單的原因，然而，如果這些別有用心的APP在它自己的白名單列出它關心的APP, 然後依次呼叫canOpenURL來檢測，照樣可以監控使用者都安裝了哪些APP啊？所以我依然不明白蘋果這樣做得原因。

A：白名單的數目上限是50個。蘋果這樣子做，使得最多隻能檢測50個App。

Q：按照文中的適配方法，error原因就沒有了的確沒問題了，但是還是會列印如下資訊：

 ```Objective-C
 -canOpenURL: failed for URL: "XXXXXXXXXX" - error: "(null)"。
 ```

A：這個模擬器的一個 bug，無論使用iOS9的真機還是模擬器均出現該問題，估計 Xcode 後續的升級中會修復掉。

那如何判斷日誌究竟是 Xcode bug 造成的還是沒有適配造成的？看error的值，如果是null，則是 bug。（2015-09-21更）


##6. iPad適配Slide Over 和 Split View

 ![enter image description here](http://cdn1.tnwcdn.com/wp-content/blogs.dir/1/files/2015/06/ew-.gif)

【iPad適配Slide Over 和 Split View】
若想適配multi tasking特性，唯一的建議：棄純程式碼，改用storyboard、xib，縱觀蘋果WWDC所有Demo均是如此：


 1. [Mysteries of Auto Layout, Part 1](https://developer.apple.com/videos/wwdc/2015/?id=218)

 2. [What's New in Storyboards](https://developer.apple.com/videos/wwdc/2015/?id=215)

 3. [Implementing UI Designs in Interface Builder](https://developer.apple.com/videos/wwdc/2015/?id=407)

 4. [Getting Started with Multitasking on iPad in iOS 9](https://developer.apple.com/videos/wwdc/2015/?id=205)

 5. [Optimizing Your App for Multitasking on iPad in iOS](https://developer.apple.com/videos/wwdc/2015/?id=212)

## 7.字型間隙變大導致 UI 顯示異常

iOS8中，字型是Helvetica，中文的字型有點類似於“華文細黑”。只是蘋果手機自帶渲染，所以看上去可能比普通的華文細黑要美觀。iOS9中，中文系統字型變為了專為中國設計的“蘋方” 有點類似於一種word字型“幼圓”。字型有輕微的加粗效果，並且最關鍵的是字型間隙變大了！

所以很多原本寫死了width的label可能會出現“...”的情況：

情況 | 顯示 |解釋
-------------|------------- |-------------
XIB |將 label 的 width 寫死 | 下面這兩張圖也可以直觀的看出同一個介面，同一個label的變化。
iOS8 | ![enter image description here](http://images2015.cnblogs.com/blog/717809/201509/717809-20150919223903476-176844619.png) | 正常
iOS9 | ![enter image description here](http://images2015.cnblogs.com/blog/717809/201509/717809-20150919223918101-1917717144.png) | 最後四位數字、、、

如果不將 label 的 width 寫死，僅僅新增左端約束則右端的四個數字會越界

情況 | 顯示 |解釋
-------------|------------- |-------------
XIB | ![enter image description here](http://i60.tinypic.com/292r428.jpg) |如果僅僅新增左端約束
iOS8 | ![enter image description here](http://i58.tinypic.com/2vj92bn.jpg) | 正常
iOS9 | ![enter image description here](http://i62.tinypic.com/2czaq1v.jpg) | “3199”這四個數字越界了

所以為了在介面顯示上不出錯，就算是固定長度的文字也還是建議使用sizetofit 或者ios向上取整 ceilf() 或者提前計算：


 ```Objective-C
CGSize size = [title sizeWithAttributes:@{NSFontAttributeName: [UIFont systemFontOfSize:14.0f]}];
CGSize adjustedSize = CGSizeMake(ceilf(size.width), ceilf(size.height));
 ```


## 8.升級 Xcode7 後的崩潰與警告

### 舊版本新浪微博 SDK 在 iOS9 上會導致的 Crash

 ```Objective-C
 app was compiled with optimization - stepping may behave oddly; variables may not be available
 ```

列印出來這句話，然後崩潰。多是啟動的過程中程式就崩潰。

在iOS9下，新浪微博SDK裡面使用的 JSONKit 在部分機型可能導致崩潰。崩潰資訊如下圖。

![enter image description here](http://wiki.mob.com/wp-content/uploads/2015/09/4062130C-1138-4352-89AF-E518F189A851.png)

解決：更新新浪微博SDK，新浪的SDK最新版做了對iOS9相容。

### iOS9 下使用 Masonry 會引起崩潰的一種情況

在 iOS8（及以前）我們有這樣的經驗：

 >   `leading 與 left`  、 `trailing 與 right`  在正常情況下是等價的 但是當一些佈局是從右至左時(比如阿拉伯文?沒有類似的經驗) 則會對調，換句話說就是基本可以不理不用，用left和right就好了

（摘自 [《Masonry介紹與使用實踐(快速上手Autolayout)》](http://adad184.com/2014/09/28/use-masonry-to-quick-solve-autolayout/) ）


但在概念裡，還是一直將 leading 與 left 劃為等號，這樣做在 iOS8（及以前）上是正常的，但在 iOS9 上這樣的觀念可能會引起崩潰，比如：

 ```Objective-C
 make.left.equalTo(self.mas_leading).offset(15);
 ```

應該為：

 ```Objective-C
 make.left.equalTo(self.mas_left).offset(15);
 ```

同理 mas_training 也需要改為right

同時也有人反饋說也需要作如下調整否則也會崩潰：

toplayoutGuide 替換成 mas_toplayoutguide
bottomlayoutguide 替換成 mas_bottomlayoutguide

而且使用類似 `make.top.equalTo(topView.mas_baseline).with.offset(5);` 涉及 `mas_baseline` 的語句也會引起崩潰。

暫時的解決方案是

使用 `make.top.equalTo(self.mas_topLayoutGuide).with.offset(5);` 來替換原來的  `self.topLayoutGuide.mas_baseline`  反正效果是一樣的

原來的程式碼：

 ```Objective-C
[self.headerView mas_makeConstraints:^(MASConstraintMaker *make) {
    UIView *topView = (UIView *)self.topLayoutGuide;
    make.top.equalTo(topView.mas_baseline).with.offset(5);
    make.leading.equalTo(self.view.mas_leading).with.offset(10);
    make.right.equalTo(self.view.mas_right).with.offset(-10);
    make.height.equalTo(@34);
}];
 ```

修改後：

 ```Objective-C
[self.headerView mas_makeConstraints:^(MASConstraintMaker *make) {
    make.top.equalTo(self.mas_topLayoutGuide).with.offset(5);
    make.left.equalTo(self.view.mas_left).with.offset(10);
    make.right.equalTo(self.view.mas_right).with.offset(-10);
    make.height.equalTo(@34);
}];
 ```

### Xcode 升級後，舊的狀態列的樣式設定方式會引起警告

 ```Objective-C
<Error>: CGContextSaveGState: invalid context 0x0. If you want to see the backtrace, please set CG_CONTEXT_SHOW_BACKTRACE environmental variable.
<Error>: CGContextTranslateCTM: invalid context 0x0. If you want to see the backtrace, please set CG_CONTEXT_SHOW_BACKTRACE environmental variable.
<Error>: CGContextRestoreGState: invalid context 0x0. If you want to see the backtrace, please set CG_CONTEXT_SHOW_BACKTRACE environmental variable.
 ```

出錯原因：設定 app 的狀態列樣式的時候，使用了舊的方式，在 info.plist 裡面的 `View controller-based status bar appearance` 預設會為 YES，即使不設定也是 YES，但一般 iOS6 的時候為了設定狀態列樣式，需要將其設為NO，iOS7，8也相容，但是到了iOS9 就會報警告。

解決辦法：

刪除原先的設定程式碼，通常老的設定方式是這樣的：

 ```Objective-C
 //設定狀態列的白色
    [[UIApplication sharedApplication] setStatusBarStyle:UIStatusBarStyleLightContent];
 ```

刪除的原因見下：

 ```Objective-C
 // Setting the statusBarStyle does nothing if your application is using the default UIViewController-based status bar system.
@property(readwrite, nonatomic) UIStatusBarStyle statusBarStyle NS_DEPRECATED_IOS(2_0, 9_0, "Use -[UIViewController preferredStatusBarStyle]");
- (void)setStatusBarStyle:(UIStatusBarStyle)statusBarStyle animated:(BOOL)animated NS_DEPRECATED_IOS(2_0, 9_0, "Use -[UIViewController preferredStatusBarStyle]");
 ```


修改方式是在 `Info.plist` 檔案中做如下修改：

將 `View controller-based status bar appearance` 刪除（預設為 YES），或設定為YES：

對應的 plist 裡的 XML源碼：

 ```Objective-C
 <key>UIViewControllerBasedStatusBarAppearance</key>
	<true/>
 ```
看起來長這樣：

![enter image description here](http://i61.tinypic.com/jrsjnd.jpg)

然後使用新的方式來實現狀態列的樣式：


 ```Objective-C
- (UIStatusBarStyle)preferredStatusBarStyle;
- (UIViewController *)childViewControllerForStatusBarStyle;
- (void)setNeedsStatusBarAppearanceUpdate
 ```

比如，你想將狀態列設定為白色，就可以這樣寫：

 ```Objective-C
//設定狀態列的白色
 -(UIStatusBarStyle)preferredStatusBarStyle
{
    return UIStatusBarStyleLightContent;
}
 ```

記得要 clean 下或者刪除應用程式重新執行

參考連結： [**How to change Status Bar text color in iOS 7**]( http://stackoverflow.com/a/17768797/3395008 )

#### Demo4---navigationController狀態列樣式新的設定方法

如果你按照上面的方法設定了，但還是不行。八成是 rootViewController 設定的問題，你必須設定 rootViewController，編譯器才會去 rootViewController 中過載 preferredStatusBarStyle 方法。

另外當你在 appdelegate 中將 navigationController 設為 rootViewController 的時候：

 ```Objective-C
     self.window.rootViewController = self.navigationController;
 ```

因為 rootViewController 變為了 navigationController，你在 ViewController 裡重寫 preferredStatusBarStyle 方法是不會起作用的。所以最好的方法是：



 ```Objective-C
 - (void)viewDidLoad
{
    [super viewDidLoad];
    self.title = @"微博@iOS程式犭袁";
    self.navigationController.navigationBar.barStyle = UIBarStyleBlack;
}
 ```


如果你還是想重寫 preferredStatusBarStyle 方法來達到作用，那最好使用分類來解決：

第二種方法：

.h檔案：

 ```Objective-C
 //
//  UINavigationController+StatusBarStyle.h
//  微博@iOS程式犭袁
//
//  Created by  https://github.com/ChenYilong/iOS9AdaptationTips/ on 15/6/8.
//  Copyright (c) 2015年   http://weibo.com/luohanchenyilong/  . All rights reserved.
//

#import <UIKit/UIKit.h>

@interface UINavigationController (StatusBarStyle)

@end

 ```

.m檔案：


 ```Objective-C
 //
//  UINavigationController+StatusBarStyle.m
//  微博@iOS程式犭袁
//
//  Created by  https://github.com/ChenYilong/iOS9AdaptationTips/ on 15/6/8.
//  Copyright (c) 2015年   http://weibo.com/luohanchenyilong/  . All rights reserved.
//

#import "UINavigationController+StatusBarStyle.h"

@implementation UINavigationController (StatusBarStyle)

- (UIStatusBarStyle)preferredStatusBarStyle
{
    //also you may add any fancy condition-based code here
    return UIStatusBarStyleLightContent;
}

@end
 ```

但最好不要通過 Category 重寫 `preferredStatusBarStyle` 的方式來指定 status bar 樣式。按照蘋果官方的解釋：

 > If the name of a method declared in a category is the same as a method in the original class, or a method in another category on the same class (or even a superclass), the behavior is undefined as to which method implementation is used at runtime. This is less likely to be an issue if you’re using categories with your own classes, but can cause problems when using categories to add methods to standard Cocoa or Cocoa Touch classes.

所以推薦第一種的方法，不推薦第二種。

我在倉庫裡給出了 navigation 的兩種設定方法，見Demo4。


 第三種方法：

 ```Objective-C
 - (UIViewController *)childViewControllerForStatusBarStyle;
 ```

 按照蘋果官方的解釋：

 > If your container view controller derives its status bar style from one of its child view controllers, implement this method and return that child view controller. If you return nil or do not override this method, the status bar style for self is used. If the return value from this method changes, call the setNeedsStatusBarAppearanceUpdate method.

 呼叫 `setNeedsStatusBarAppearanceUpdate` 時，系統預設會去呼叫application.rootViewController的 `preferredStatusBarStyle` 方法，所以這時候當前自己的 viewController 的 `preferredStatusBarStyle` 方法根本不會被呼叫。

 這個介面很重要，這種情況下 `childViewControllerForStatusBarStyle` 就有用了。一般我們常用 navigationController 作為 rootViewController，利用此介面便可以很方便自訂各個 viewController 的 statusBarStyle。 子類化一個 navigationController，並且 override `childViewControllerForStatusBarStyle`

 ```Objective-C
 - (UIViewController * _Nullable)childViewControllerForStatusBarStyle {
     return self.topViewController;
 }
 ```

 意思就是說不要呼叫我自己 `application.rootViewController（navigationController）` 的 `preferredStatusBarStyle` 方法，去呼叫｀childViewControllerForStatusBarStyle｀ 回傳的 UIViewController 的 `preferredStatusBarStyle`。這裡回傳 self.topViewController 就可以保證當前顯示的 viewController 的 `preferredStatusBarStyle` 會被系統呼叫且正確的顯示。

參考連結：
 1.  [preferredStatusBarStyle isn't called--For anyone using a UINavigationController:](http://stackoverflow.com/a/19513714/3395008)
 2. [ ***How to hide iOS status bar*** ](http://stackoverflow.com/a/18980833/3395008)

### Xcode7 在 debug 狀態下也生成 .dSYM 檔案引起的警告

Xcode6 的工程升級到 Xcode7上來，會報警告：

![enter image description here](http://i57.tinypic.com/2a5zuia.jpg)

這是 debug 編譯時匯出符號檔案出現的告警，

然而新建的Xcode7工程不會有該問題。

解決方法是讓 debug 編譯的時候不生成符號檔案：

![enter image description here](http://i60.tinypic.com/2e23qyp.jpg)

### Xcode7 無法使用 8.x 系統的裝置偵錯，一執行就報錯 `there is an intenal API error`


![enter image description here](http://cdn.cocimg.com/bbs/attachment/Fid_21/21_296305_92094d6a71e587a.png)

`Xcode7` 偵錯  `iOS8.x` 的真機，需要確保項目名改為英文，中間含有中文會報錯  `there is an intenal API error`

按照下面的步驟檢查：

bulid settings  ->    packaging  -> product name

### 使用了 HTML 的 iframe 元素可能導致無法從 Safari 跳轉至 App

我們都知道，從網易新聞分享一條新聞到QQ，然後從QQ中開啟連結再用safari開啟連結，在iOS8上，這個時候會跳轉到網易新聞App。但是現在（2015年09月23日）版本的網易新聞在 iOS9 就不能正常跳轉，會跳轉到 App Store 頁面並提示要不要開啟 App Store。


這是很可能是因為使用了 HTML 的 iframe 元素，並將自定義的連結放進了該元素中

舉例說明：

![enter image description here](http://i61.tinypic.com/2wbvok8.jpg)


我之前寫的一個 Demo： [模仿 《簡書 App》 的效果:在html中跳轉到App中的對應頁面,並能從App跳轉到原來的網址](https://github.com/ChenYilong/CYLExternalURL)，在例子中直接呼叫自定義連結在 iOS9上是可以跳轉到 App 中的，然而，如果用 iframe 元素包起來就會變不可用。

參考連結：


 1.  [HTML 的iframe 標籤](http://www.w3school.com.cn/tags/tag_iframe.asp)
 2.  [iOS 9 safari iframe src with custom url scheme not working](http://stackoverflow.com/questions/31891777/ios-9-safari-iframe-src-with-custom-url-scheme-not-working)

### iOS9鎖屏控制檯會列印警告

加入執行如下示例程式碼：

 ```Objective-C
- (void)viewDidLoad {
    [super viewDidLoad];
    dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
    dispatch_async(queue, ^(void) {
        //在這個10秒內鎖屏
         NSLog(@"準備休眠");
        sleep(10);
        NSLog(@"列印成功");
    });
}
 ```

應用執行過程中鎖屏，總是會出現以下提示：


 ```Objective-C
** -[UIApplication _handleNonLaunchSpecificActions:forScene:withTransitionContext:completion:] ** unhandled action -> <FBSSceneSnapshotAction: 0x16da76c0> {
    handler = remote;
    info = <BSSettings: 0x16d80e50> {
        (1) = 5;
    };
}
 ```


當應用處於空閒狀態時（無網路請求）鎖屏對於使用者而言並無較大影響，


但是當應用在執行某個非同步任務時（比如下拉重新整理一下列表）鎖屏，重新解鎖進入就可能會發現非同步任務失敗，控制檯也會提示 Error 資訊：


 ```Objective-C
** -[UIApplication _handleNonLaunchSpecificActions:forScene:withTransitionContext:completion:] ** unhandled action -> <FBSSceneSnapshotAction: 0x16da76c0> {
    handler = remote;
    info = <BSSettings: 0x16d80e50> {
        (1) = 5;
    };
}
error in __connection_block_invoke_2: Connection interrupted
 ```

以上情況不易復現，但確有發生。

在 iOS8 系統下測試並未發現此問題。

對此並未找到合理的解釋和對應的解決辦法，如果你有解決方法，歡迎提 PR !

### 在`didFinishLaunchingWithOptions`結束後還沒有設定window的`rootViewController`會導致崩潰




 iOS9 不允許在 `didFinishLaunchingWithOptions` 結束了之後，還沒有設定 window 的 `rootViewController` 。 也許是 Xcode7 的編譯器本身就不支援。

崩潰時的控制檯日誌提示：

 ```Objective-C
*** Assertion failure in -[UIApplication _runWithMainScene:transitionContext:completion:], /BuildRoot/Library/Caches/com.apple.xbs/Sources/UIKit_Sim/UIKit-3505.16/UIApplication.m:3294

***  Terminating app due to uncaught exception 'NSInternalInconsistencyException', reason: 'Application windows are expected to have a root view controller at the end of application launch'

*** First throw call stack:
/*省略*/
libc++abi.dylib: terminating with uncaught exception of type NSException
(lldb)
 ```

解決的方法是先設初始化個值，之後再賦值替換掉：



 ```Objective-C
UIWindow *window = [[UIWindow alloc] initWithFrame:[UIScreenmainScreen].bounds];
window.rootViewController = [[UIViewController alloc] init];
 ```




尤其注意一種情況，在 iOS8以前，我們有時候會通過在 AppDelegate 中新增另一個 UIWindow ，並修改其 Level 來達到 addSubview 的效果，因而也不設定 window 的 `rootViewController` ，而是把它直接以檢視的形式展示了，則在 iOS8 上是警告，在 iOS9 上就崩潰了。

 ```Objective-C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    self.window.backgroundColor = [UIColor yellowColor];
    [self.window makeKeyAndVisible];

    UIWindow *normalWindow = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    normalWindow.backgroundColor = [UIColor blueColor];
    normalWindow.windowLevel = UIWindowLevelAlert;
    [normalWindow makeKeyAndVisible];

    return YES;
}
 ```


這種情況，在 `didFinishLaunchingWithOptions` 需要修改原來的策略，將第二個 window 類型改為其他類型，比如 viewController 類型、navigation 類型、tabbarController 類型等。


## 9.Demo5、Demo6--- 搜尋 API

匯入兩個 framework，

然後像設定tableView 的 cell 一樣設定下每一個“搜尋元素”，搜尋元素的組成如下：


![enter image description here](http://i57.tinypic.com/144b22w.jpg)


詳情見 Demo6 程式碼。


![enter image description here](http://image17-c.poco.cn/mypoco/myphoto/20150923/21/17338872420150923214730010.gif?370x686_110
)

既然剛才說了搜尋元素與 tableView 的 cell 非常相似：那麼我們就展示一下如何讓 tableView 與 CoreSpotlightSearch 進行結合：

詳見 Demo6，Demo6 與 Demo5 的主要差異在於：在點選搜尋結果跳轉到 App 後，還會進一步根據搜尋的內容 push 到相應的詳情頁中：

![enter image description here](http://image17-c.poco.cn/mypoco/myphoto/20150924/00/17338872420150924001340035.gif?306x572_110
)

## 10.iOS國際化問題：當前裝置語言字元串返回有變化。


```
NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
NSArray *allLanguage = [defaults objectForKey:@"AppleLanguages"];
NSString *currentLanguage = [allLanguage objectAtIndex:0];
NSLog(@"The current language is : %@", currentLanguage);
```

iOS 9 之前：以上返回結果：語言字元串程式碼。例如："zh-Hans"

iOS 9:以上返回結果：語言字元串程式碼 + 地區程式碼。例如："zh-Hans-US"

備註：
1.請注意判斷當前語言類型，不要用以下形式的程式碼了，不然在iOS9上就會遇到坑。

```
if ([currentLanguage isEqualToString:@"zh-Hans"])
```

可以使用：

```
if ([currentLanguage hasPrefix:@"zh-Hans"])
```

另外：對於中文，語言有：

+ 簡體中文:zh-Hans
+ 繁體中文:zh-Hant
+ 香港中文:zh-HK
+ 澳門中文:zh-MO
+ 臺灣中文:zh-TW
+ 新加坡中文:zh-SG

**備註：以上iOS9 當前語言字元串返回結果：語言字元串程式碼 + 地區程式碼。在某些情況下不是這樣，本人手機型號：大陸版電信iPhone5S/A1533/16GB測試結果：zh-HK/zh-TW，在地區為"中國"、"中國香港"、"中國臺灣"的時候，顯示的還是zh-HK/zh-TW，一旦切換到其它地區，裝置語言會自動的切換到中文繁體。請開發人員注意中文的問題！**



## 11.UITableView顯示異常

原本在 Xcode6 上完好的項目，在 Xcode7 上一編譯， `tableView` 出了兩個問題 ：


 1.  程式碼建立的 `tableView` 無法隱藏 cell 分割線
 2.  `reloadData` 重新整理失效；


### 程式碼建立的 `tableView` 無法隱藏 cell 分割線

iOS9 裡面用到 tableView 突然跑出來了很多 cell 的分割線， 但是在用xib建立的 tableview，就不存在這個問題

解決方法是將設定分割線隱藏的方法 `self.tableView.separatorStyle = UITableViewCellSeparatorStyleNone;` 寫在 `-layoutSubviews` 中：

 ```Objective-C
-(void)layoutSubviews{
    [super layoutSubviews];
    self.tableView.separatorStyle = UITableViewCellSeparatorStyleNone;
}
 ```

也有人發現另一種方法，就是每次 reloadData 之前都進行一次設定：設定分割線隱藏，這樣也可以解決：



 ```Objective-C
    self.tableView.separatorStyle = UITableViewCellSeparatorStyleNone;
   [self.tableView reloadData]
 ```

雖然也可以解決但是不推薦，這樣寫會給其他人造成困擾：不知所云。


### `reloadData` 重新整理失效

現象： `[tableView reloadData]` 無效，有一行 cell 明明改變了但是重新整理不出來。


 感覺可能是這個方法和某種新加的特性衝突了，猜測可能是 `reloadData` 的操作被推遲到下一個 `RunLoop` 執行最終失效。

解決的方法是，註釋 `[tableView reloadData]` ，改用局部重新整理：

 ```Objective-C
[self.tableView reloadSections:[NSIndexSet indexSetWithIndex:0] withRowAnimation:UITableViewRowAnimationNone];
 ```

這兩個推測均屬 Xcode7 的bug，將來 Apple 肯定會修復。

### 基於HTTP/2的全新APNs協議
文章較長，單獨成篇: [《基於HTTP/2的全新APNs協議》](https://github.com/ChenYilong/iOS9AdaptationTips/blob/master/基於HTTP2的全新APNs協議/基於HTTP2的全新APNs協議.md#如何建立-universal-push-notification-client-ssl-證書) 。

#結束語
如果你在開發中遇到什麼新的 iOS9 的坑，或者有什麼適配細節本文沒有提及，歡迎給本倉庫提 pull request。也歡迎在[微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/)  或在“iOS9開發學習交流群：515295083”中交流。

疏漏之處，可前往閱讀下[這個網站](http://asciiwwdc.com)，這裡有每年 WWDC 演講的英文記錄。

----------


Posted by [微博@iOS程式犭袁](http://weibo.com/luohanchenyilong/)
原創文章，版權聲明：自由轉載-非商用-非衍生-保持署名 | [Creative Commons BY-NC-ND 3.0](http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh)
<p align="center"><a href="http://weibo.com/u/1692391497?s=6uyXnP" target="_blank"><img border="0" src="http://service.t.sina.com.cn/widget/qmd/1692391497/b46c844b/1.png"/></a></a>
