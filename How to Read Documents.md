# How to Read Documents
該如何閱讀開發文件呢，我們以 JavaFx 為例，首先我們可以閱讀社群文件，或者是官方的文件，這裡以官方文件為例，因為不一定每個開發軟體都有社群文件

---

## 1. Step 1 : life-cycle </br>
在找到生命週期後就能夠了解要讓JavaFx跑起來，所需要的動作，所以讓我們再介紹找到有關life-cycle的路徑</br>
Module javafx.graphics ->Package javafx.application ->Class Application</br>
在 application 裡可以看到生命週期的步驟</br>
```
    1. Starts the JavaFX runtime, if not already started (see Platform.startup(Runnable) for more information)
    2. Constructs an instance of the specified Application class
    3. Calls the init() method
    4. Calls the start(javafx.stage.Stage) method
    5. Waits for the application to finish, which happens when either of the following occur:
       * the application calls Platform.exit()
       * the last window has been closed and the implicitExit attribute on Platform is true
    6. Calls the stop() method</br>
```    
由此得知需要他跑起來會 call 一個叫做 start(javafx.stage.Stage) 的 method

在來我們看到 Start的文件</br>
 ```  
Parameters:
primaryStage - the primary stage for this application, onto which the application scene can be set. Applications may create other stages, if needed, but they will not be primary stages.
```
他的介紹說到我們可以透過設定參數來改變View的樣子

---
## 2. 設定View
