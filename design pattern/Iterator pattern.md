# Iterator pattern 
Iterator 我個人的理解感覺比較像是要處理不同型態組合成的資料</br>
在這些資料間建立抽象層讓後續使用時只需要使用固定的方法就能夠走訪所有資料，而不用為每一種資料型撰寫多次走訪方法

---
我在一篇[反覆器模式 (Iterator Pattern)](http://corrupt003-design-pattern.blogspot.com/2016/07/iterator-pattern.html)看到的比喻方式我覺得很棒，在文章中使用餐廳的菜單來做比喻，今天有兩家餐廳分別使用不同的資料型態儲存，一家使用 Array、一家使用 List </br>
今天突然需要將兩家菜單輸出，正常的方法可能要依照不同的形態撰寫不同的走訪方式，但是假如我們讓菜單上開一個能夠回傳Iterator，</br>
Iterator內有往下一個元素的走訪的方法，這樣我們後續使用只需要呼叫 Iterator的next就好

---
> 下列code是取自[疊代器模式Wiki](https://zh.wikipedia.org/wiki/%E8%BF%AD%E4%BB%A3%E5%99%A8%E6%A8%A1%E5%BC%8F)</br>
``` java
interface Iterator{
    Object First();
    Object Next();
    boolean IsDone();
    Object CurrentItem();
}

abstract class Aggregate{
    abstract Iterator CreateIterator();
}

class ConcreteIterator implements Iterator{
    private List<Object> list = new ArrayList<Object>();
    private int curr=0;
    public ConcreteIterator(List<Object> list){
        this.list = list;
    }

    public Object First(){
        return list.get(0);
    }

    public Object Next(){
        Object ret = null;
        curr++;
        if(curr < list.size()){
            ret = list.get(curr);
        }
        return ret;
    }

    public boolean IsDone(){
        return curr>=list.size()?true:false;
    }

    public Object CurrentItem(){
        return list.get(curr);
    }
}

class ConcreteAggregate extends Aggregate{
    private List<Object> list = new ArrayList<Object>();
    public ConcreteAggregate(List<Object> list){
        this.list = list;
    }
    public Iterator CreateIterator(){
        return new ConcreteIterator(list);
    }
}
```
這樣改變資料型態時While部分也不需要更改
``` java
class client{
    public static void main(String[] args){
    List<Object> list = new ArrayList<Object>();
    list.add("miner");
    list.add("any");
    Aggregate agg = new ConcreteAggregate(list);
    Iterator iterator = agg.CreateIterator();
    iterator.First();
    while(!iterator.IsDone()){
        System.out.println(iterator.CurrentItem());
        iterator.Next();
        }
    }
}
```
假如在加入一個資料型態為Array</br>
首先幫他設定Iterator
``` java
class ArrayIterator implements Iterator{
    private Object[] arrayData;
    private int curr=0;
    public ArrayIterator(Object[] arrayData){
        this.arrayData = arrayData;
    }

    public Object First(){
        return arrayData[0];
    }

    public Object Next(){
        Object ret = null;
        curr++;
        if(curr < arrayData.length){
            ret = arrayData[curr];
        }
        return ret;
    }

    public boolean IsDone(){
        return curr>=arrayData.length?true:false;
    }

    public Object CurrentItem(){
        return arrayData[curr];
    }
}
```
以及Aggregate
``` java
class ArrayAggregate extends Aggregate{
    private Object[] data;
    public ArrayAggregate(Object[] data){
        this.data = data;
    }
    public Iterator CreateIterator(){
        return new ArrayIterator(data);
    }
}
```
最後要使用的話只需要改這兩行
``` java
class client{
    public static void main(String[] args){
        Object[] arrayData = new Object[10];//只需要改這兩行
        Aggregate agg = new ArrayAggregate(arrayData);//只需要改這兩行
        Iterator iterator = agg.CreateIterator();
        iterator.First();
        while(!iterator.IsDone()){
            System.out.println(iterator.CurrentItem());
            iterator.Next();
        }
    }
}
```
在很多現代語言都有使用 Iterator pattern 像是 for in 其實就有使用到

---
### 參考資料: </br>
* [反覆器模式 (Iterator Pattern)](http://corrupt003-design-pattern.blogspot.com/2016/07/iterator-pattern.html)</br> 
* [疊代器模式Wiki](https://zh.wikipedia.org/wiki/%E8%BF%AD%E4%BB%A3%E5%99%A8%E6%A8%A1%E5%BC%8F)