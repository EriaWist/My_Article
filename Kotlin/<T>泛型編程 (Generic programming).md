# Kotlin-泛型<T>

[泛型的Wiki介紹](https://zh.wikipedia.org/wiki/%E6%B3%9B%E5%9E%8B%E7%BC%96%E7%A8%8B)

泛型簡單來說就是可以依照傳入的資料型態推斷回傳的資料型態，就是常常看到的<T>

比如
``` kotlin
class Box<T>(t : T) {
    val t = t
    fun getData():T
    {
        return t
    }
}
```
這時使用這個class時
``` kotlin
val box = Box<Int>(123) //這樣裡面的T型態就是Int，並且傳入整數123
val boxData = box.getData() //回傳的123也是T型態Int
```
or
``` kotlin
val box = Box<String>("Hi") //這樣裡面的T型態就是String，並且傳入整數"Hi"
val boxData = box.getData() //回傳的Hi也是T型態String
```
也能夠縮寫成這樣
``` kotlin
val box = Box("Hi")
val data = box.getData()
```
這個和
``` kotlin 
val box = Box<String>("Hi")
```
的結果一樣

---
順帶一提 泛型能夠透過加裝一些條件，來限制資料型態比如說
``` kotlin
class Box<T:Int>(t : T) {
    val t = t
    fun getData():T
    {
        return t
    }
}
```
這樣只能使用Int的"子類別"，注意並不是只能使用Int而是只能使用Int"子類別"

---
在Kotlin裡還有一種，不需要透過class，可以直接在fun裡使用泛型的方法，加上reified就能夠在呼叫fun時定義型態
``` kotlin
inline fun <reified T> getData(fileName: String):T{
    return Json.decodeFromString<T>(fileName)
}
```
在上面有個[inline]()之後再寫個文章說明

---
參考資料
* [泛型](https://medium.com/evan-android-note/kotlin-%E7%B7%9A%E4%B8%8A%E8%AE%80%E6%9B%B8%E6%9C%83-%E7%AD%86%E8%A8%98-%E5%8D%81%E4%B8%80-%E6%B3%9B%E5%9E%8B-generics-3080538b5b22)
* [reified](https://yongjhih.medium.com/reified-type-%E5%8F%AF%E5%BB%BA%E6%A7%8B%E5%9E%8B%E5%88%A5-kotlin-46a8b7e848dd)
* [inline](https://givemepass.blogspot.com/2020/01/inline.html) 
* [inline2](https://www.itread01.com/content/1544104699.html)