# java(Kotlin語法) 檔案讀寫、資料夾創建

### nio是non-blocking比io新速度也比較快，也不會需要等待暫停等待資料到達
使用nio的方式
> 關於使用`path.of` or `paths.get` [連結](https://stackoverflow.com/questions/58631724/paths-get-vs-path-of) [文件](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/nio/file/Paths.html)
```
API Note:
It is recommended to obtain a Path via the Path.of methods instead of via the get methods defined in this class as this class may be deprecated in a future release.
```
結論用`path.of`
可以用
``` kotlin
    val fileName =  Path.of("teww/a123/demo.txt");
    fileName.createDirectory()
```
但是Kotlin[警告](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io.path/-experimental-path-api/)
```
This annotation marks the extensions and top-level functions for working with java.nio.file.Path considered experimental.
```
等未來穩定在更新

---


 使用io的方式 [參考文件](https://www.w3schools.com/java/java_files_create.asp)
> 創立資料夾
  ``` kotlin
  var file = File("test/123")
  file.mkdirs()
  ```
> 在創立的資料夾內新增檔案
``` kotlin
var file = File("test/123/filename.txt")
file.createNewFile()
```
> 寫入檔案
``` kotlin
var myWriter =  FileWriter("filename.txt");
myWriter.write("Files in Java might be tricky, but it is fun enough!");
myWriter.close();
```
> 讀取檔案
``` kotlin
var file = File("test/123/filename.txt")
var myReader =  Scanner(file);
while (myReader.hasNextLine()) {
    var data = myReader.nextLine();
    println(data);
}
myReader.close();
```
> 刪除檔案

``` kotlin
var file = File("test/123/filename.txt")
file.delete()
```
   