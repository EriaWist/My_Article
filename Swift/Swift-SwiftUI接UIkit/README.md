
# Swift-SwiftUI接UIkit

在xcode11的時候正式開放SwiftUI框架，SwiftUI在快速建構APP上十分方便，但是在於一些功能上還沒支援到全部，以及自定義UI上並沒有非常方便
這時能接回UIkit就非常方便。

首先我們先開一個SwiftUI專案

![](https://cdn-images-1.medium.com/max/6032/1*FShgeanKZSk6Hn1UJqbfEg.png)

new一個UIkit的Group(資料夾)方便我們整理

![](https://cdn-images-1.medium.com/max/2000/1*i1Xc5uAZCwvSEquGT4Pw2w.png)

在資料夾裡面新增Storyboard以及Cocoa Touch

![](https://cdn-images-1.medium.com/max/5760/1*A0j_CSOwGljiD6Ielaiv-w.png)

![](https://cdn-images-1.medium.com/max/6208/1*RmEiZit8dSnNYo_bI36KvA.png)

![](https://cdn-images-1.medium.com/max/6208/1*3jA7ANHkG6CMLa_Tez6lOQ.png)

以及新增一個swift頁面

![](https://cdn-images-1.medium.com/max/6208/1*QStP4RqWJ0BIZMnow-if7Q.png)

接下來我們打開 apple 的 document 尋找 SwiftUI

![](https://cdn-images-1.medium.com/max/6208/1*KDDUphE2J0xlQsMHc59bVQ.png)

![](https://cdn-images-1.medium.com/max/6208/1*CZmZcBZspsr2IS3unmm86Q.png)

![](https://cdn-images-1.medium.com/max/6208/1*HXlgwk8X3Z1qKLfLCgAXeA.png)

進去後讓我們往下划到User Interface

![](https://cdn-images-1.medium.com/max/6208/1*aXGAMHnsoTB-CIehbm2Aew.png)

![](https://cdn-images-1.medium.com/max/6208/1*7Mlv3ocm60dbZzTC0Ijc2Q.png)

選擇框架整合 Framework Integration 並且移動到 UIKit Hosting 的部份

![](https://cdn-images-1.medium.com/max/6208/1*YBT0klFrkFgtXmUqb_3rww.png)

![](https://cdn-images-1.medium.com/max/6208/1*7inVB62FGW6ovxDPCV7KvA.png)

選擇 UIViewControllerRepresentable 這個 Protocol

![](https://cdn-images-1.medium.com/max/6208/1*CWRQdO1Ufeho8cbNpvyS1g.png)

我們接下來會使用這個 Protocol 
記得 我們在新開的頁面需要 **import SwiftUI**

將Protocol實作

![](https://cdn-images-1.medium.com/max/6208/1*yrvqFaOi8oElf2-Y90Jeaw.png)

    makeUIViewController

是進入頁面時創造頁面所需執行的內容

    updateUIViewController

是當刷新頁面所要執行的

我們先將創造頁面先實作出來，首先回到MyStoryboard

![](https://cdn-images-1.medium.com/max/6208/1*kLXIzQXvwxEv0iR0hkZAeQ.png)

![](https://cdn-images-1.medium.com/max/6208/1*qp-QfGSMZCU-1V24Ni_EgA.png)

拉一個 View Controller 並且與 MyViewController 綁定與 identity 設定

![](https://cdn-images-1.medium.com/max/6208/1*2S3-ls5TfjIs1oVNl8sl1A.png)

我們先取得 myStoryboard 並且將 myStoryboard 裡 MyView 的 myViewController 取出

![](https://cdn-images-1.medium.com/max/6208/1*b8uZmoHIRh41-ejO4rBZEw.png)

``` swift
let myStoryboard = UIStoryboard(name: "MyStoryboard", bundle: nil)
let myViewController = myStoryboard.instantiateViewController(withIdentifier: "MyView")
return myViewController as! MyViewController
```

到目前為止我們已經成功將UIkit頁面丟到SwiftUI，但是接下來要解決頁面溝通的部分

![](https://cdn-images-1.medium.com/max/6208/1*YvkRC7YrwYZgonJVPq7Rew.png)

![](https://cdn-images-1.medium.com/max/6208/1*B36tqR7XL0KFN61WE1k4wg.png)

![](https://cdn-images-1.medium.com/max/6208/1*3ZrtDomAW_VbvZREcvACqg.png)

![](https://cdn-images-1.medium.com/max/6208/1*HSsCIbgkyNRxoDiNFPx4iQ.png)
> 頁面溝通-SwiftUI到UIkit

從簡單的開始，將資料從SwiftUI往下傳以及刷新頁面，
首先在SwiftUI介面呼叫剛剛製作的UIkitToSwiftUI

![](https://cdn-images-1.medium.com/max/6208/1*aF4Nl5Ue2G7b7OUhBw9Crw.png)

並在myStoryboard的Label拉連結到myViewController

![](https://cdn-images-1.medium.com/max/6208/1*J_DaGH9c0ONYlVKVYDikTg.png)

在UIkitToSwiftUI綁定變數以及在updateUIViewController更新Storyboard

![](https://cdn-images-1.medium.com/max/6208/1*hs_Dmg0GBtROPfnNfwLYjw.png)

![](https://cdn-images-1.medium.com/max/6208/1*vVeqBg3UUKN6qxA0OpYDKA.png)

這時我們執行會發現，成功了

![](https://cdn-images-1.medium.com/max/2000/1*5KCxTItgv_N8JDeym7wCog.gif)

現在資料從SwiftUI上傳送到UIkit是沒問題的，但是相反的要把資料從UIkit傳回到SwiftUI

首先在Storyboard加上一些元件來顯示與操作

![](https://cdn-images-1.medium.com/max/6208/1*YgnOBfl61JpkYxmJyOi2dg.png)

![](https://cdn-images-1.medium.com/max/6208/1*n2iQJVKnHZYopx2Cj4C3RA.png)

新增Observer Class

![](https://cdn-images-1.medium.com/max/6208/1*hLexuIzv4rtzMIlokWDzcA.png)

``` swift
class Observer {
    static private var observer:Observer? = nil
    private var updateFunc:(()->())?=nil
    private init() {
    }
    static func createObsever() -> Observer {
        if Observer.observer==nil {
            Observer.observer = Observer()
        }
        return Observer.observer!
    }
    func addUpdate(update:@escaping ()->()) {
        self.updateFunc = update
    }
    func update() {
        (updateFunc ?? {print("Observer nil Error")})()
    }
}
```

在makeUIViewController添加Observer.createObsever().addUpdate

![](https://cdn-images-1.medium.com/max/6208/1*FaB0m678eGOdx1GJPGqSAw.png)

以及MyViewController的按鈕動作

![](https://cdn-images-1.medium.com/max/6208/1*vzZLNXSzTKFyBDeUOzDzDA.png)

最後你會發現成功了

![](https://cdn-images-1.medium.com/max/2000/1*LGG-4TgurQpxPru5RUsVJA.gif)
> 最後是Git
[**EriaWist/SwiftUIApplyUIkit**
*in SwiftUI use UIkit. Contribute to EriaWist/SwiftUIApplyUIkit development by creating an account on GitHub.*github.com](https://github.com/EriaWist/SwiftUIApplyUIkit)
