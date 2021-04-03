# design pattern - 單例模式 Singleton
### Singleton 要解決的問題 : 在有些時候我們希望這個class只會有一個實體、實例 
EX.比如今天需要打開 DataBase 在不同的class開啟時，我們可能會希望全部開啟的 DataBase 都是同一個物件而不是在不同地方重複開啟。

---
``` java
class Singleton {
    static private Singleton instance = null;
    static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
    private Singleton(){}
}

```
這樣在需要使用Singleton只需要
``` java
Singleton singleton = Singleton.getInstance();
```
並且我們能夠確保不管在哪裡的Singleton的實例都是同個

----
在單線程的部分不會出問題但是在多線程可能會應為Singleton建構時間很長 導致在建構的時候又發出請求Singleton導致建構了兩個不同的Singleton這時候要使用Synchronized同步標籤在new的區塊確保在建構時資料會被lock鎖住
``` java
class Singleton {
    static private Singleton instance =null;
    static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
    int id = 0;
    private Singleton(){
        id = new Random().nextInt(100);
    }

    public static void main(String[] args) {
        SingletonThread singletonThread1 = new SingletonThread(1);
        SingletonThread singletonThread2 = new SingletonThread(2);
        singletonThread1.start();
        singletonThread2.start();
        try
        {
            Thread.sleep(1000);
        }
        catch(InterruptedException e){}
        System.out.println("now Singleton id : "+Singleton.getInstance().id);
    }
}
class SingletonThread extends Thread {
    int threadId;
    SingletonThread(int threadId){
        this.threadId=threadId;
    }
    @Override
    public void run() {
        super.run();
        Singleton singleton = Singleton.getInstance();
        System.out.println(threadId+":"+singleton.id);
    }
}
```
執行我們可以看到 id 的結果
```
2:83
1:47
now Singleton id : 83
```
可以發現他並不是單一的，這樣在多線程時無法解決我們的需求，這時可以加上 synchronized 使資料同步，當有人在用資料時 lock 這樣就能避免再多線程開到多個實例
``` java
static synchronized Singleton getInstance() {
    if (instance == null) {
        instance = new Singleton();
    }
    return instance;
}
``` 
在執行一次我們會發現
```
2:18
1:18
now Singleton id : 18
``` 
成功為只一個實例了，但是可以實際上我們只需要在 new 時 lock 資料
可以再修改一下
``` java
    static synchronized Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
```
這樣只要不是第一次呼叫就都不會鎖住了

----
> 參考文章
* [單例模式 Singleton](https://skyyen999.gitbooks.io/-study-design-pattern-in-java/content/singleton.html)
* [同步處理 synchronized](https://ithelp.ithome.com.tw/articles/10187884)