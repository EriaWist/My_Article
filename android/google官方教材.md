# google官方教材
### [官方總目錄](https://developer.android.com/courses/android-basics-kotlin/course)
</br>

>[hardcoded](https://developer.android.com/codelabs/basic-android-kotlin-training-birthday-card-app-image?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-three%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-birthday-card-app-image#3)
>
在 `res->values->strings.xml` 這個檔案會有key value的方式 
``` xml
<resources>
    <string name="app_name">My Application</string>
    <string name="roll">Roll</string>
</resources>
```
這樣在View的text部分可以使用 `@string/roll` 的方式用key `roll` 取得value `Roll`

---
> Common Attributes

在 Common Attributes 裡面有一個板手符號的 text 在裡面輸入文字能夠預覽文字狀態，並且在執行時不會顯示 [連結Style the TextView那一段](https://developer.android.com/codelabs/basic-android-kotlin-training-create-dice-roller-app-with-button#2)

---
 > Toast

``` kotlin
val toast = Toast.makeText(this, "內容", Toast.LENGTH_SHORT)
toast.show()
```           

---
> 自動排版

Windows `Control+A`+`Ctrl+Alt+L` 

Mac `Command+A`+`Command+Option+L`