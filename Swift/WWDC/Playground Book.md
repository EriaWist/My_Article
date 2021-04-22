# Playground Book 簡易教學
### Playground Book : 是用來執行在 Swift Playgrounds 上的框架
目前主要用在參加 WWDC Swift Student Challenge 以及開發教學的Book，例如 Makeblock 公司開發的 mBot 除了本身的 APP 之外，也有在 Swift Playgrounds 有開發 Playground Book 提供更多樣的程式教學。

---
#### 1. 建立並運行 </br>
首先我們可以到[Creating and Running a Playground Book](https://developer.apple.com/documentation/swift_playgrounds/creating_and_running_a_playground_book)來了解如何運行最基本的 Playground </br>
首先前往[下載](https://developer.apple.com/download/more/?=Swift%20Playgrounds%20Author%20Template)預設的專案 (這篇文在是在 Xcode 12.2 的版本撰寫的 請參考目前最新版本下載)
完成之後點開啟dmg檔案將裡面的壓縮檔案拖出解壓縮
![v1點開壓縮之後的圖.png](https://github.com/EriaWist/My_Article/blob/main/Swift/WWDC/Resource/v1%E9%BB%9E%E9%96%8B%E5%A3%93%E7%B8%AE%E4%B9%8B%E5%BE%8C%E7%9A%84%E5%9C%96.png?raw=true)
我們點擊進入 PlaygroundBookTemplate ->Template->PlaygroundBook.xcodeproj 接下來 Xcode 應該就會將專案開啟

> 進入專案後的第一件事就是先編譯看看 如下圖選擇Playground Book
![v2設定為PlaygroundBook.jpg](https://github.com/EriaWist/My_Article/raw/main/Swift/WWDC/Resource/v2%E8%A8%AD%E5%AE%9A%E7%82%BAPlaygroundBook.jpg?raw=true)

> 確認左上角與下圖所示一致
![v3設定完成樣子.jpg](https://github.com/EriaWist/My_Article/raw/main/Swift/WWDC/Resource/v3%E8%A8%AD%E5%AE%9A%E5%AE%8C%E6%88%90%E6%A8%A3%E5%AD%90.jpg?raw=true)

接下來讓我們按下 command+b 進行編譯<br/>
>編譯完成之後我們可以開啟這個資料夾
![v4瀏覽.jpg](https://github.com/EriaWist/My_Article/blob/main/Swift/WWDC/Resource/v4%E7%80%8F%E8%A6%BD.jpg?raw=true)

對PlaygroundBook.playgroundbook按下右鍵 (注意不要選到Products)
![v5選取Show in Finder.jpg](https://github.com/EriaWist/My_Article/blob/main/Swift/WWDC/Resource/v5%E9%81%B8%E5%8F%96Show%20in%20Finder.jpg?raw=true)
選擇Show in Finder
![v6瀏覽檔案.jpg](https://github.com/EriaWist/My_Article/blob/main/Swift/WWDC/Resource/v6%E7%80%8F%E8%A6%BD%E6%AA%94%E6%A1%88.jpg?raw=true)
接下來我們我們把 Playground Book 拉到 Swift Playground 就可以打開檔案，可以在 mac 上安裝 [Swift Playground](https://apps.apple.com/tw/app/swift-playgrounds/id1496833156?mt=12) 或者在 iPad 上安裝 [Swift Playground](https://apps.apple.com/tw/app/swift-playgrounds/id908519492?l=en) <br/>
mac 的話將檔案丟入即可，iPad 則是把檔案 Air Drop 過去