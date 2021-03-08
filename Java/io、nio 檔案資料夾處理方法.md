# java(Kotlin語法) 檔案讀寫、資料夾創建

### nio比io新速度也比較快
使用nio的方式


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
   