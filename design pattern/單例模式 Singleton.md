# design pattern - 單例模式 Singleton
### Singleton 要解決的問題 : 在有些時候我們希望這個class只會有一個實體、實例 
EX.比如今天需要打開 DataBase 在不同的class開啟時，我們可能會希望全部開啟的 DataBase 都是同一個物件而不是在不同地方重複開啟。

---
``` java
class HttpServer{
    static private HttpServer instance = null;
    static HttpServer getInstance() {
        if (instance == null) {
            instance = new HttpServer();
        }
        return instance;
    }
    private HttpServer(){}

}
```
這樣在需要使用HttServer只需要
``` java
 HttpServer httpServer = HttpServer.getInstance();
```
並且我們能夠確保不管在哪裡的HttpServer的實例都是同個