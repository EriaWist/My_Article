# Gradle相關指令
## [gradle建立Kotlin應用](https://docs.gradle.org/current/samples/sample_building_kotlin_libraries.html)
> [安裝](https://gradle.org/install/)
``` 
sdk install gradle 7.0
or
brew install gradle
and
sudo apt  install gradle
```
---
```
$ mkdir demo
$ cd demo
建議新增資料夾
$ gradle init
//為了配合大多數開發者習慣
Select build script DSL:
  1: Groovy
  2: Kotlin
Enter selection (default: Groovy) [1..2] 1
目前市面上選擇Groovy
```
專案的設定在app/build.gradle設定

---

下指令[打包](https://docs.gradle.org/current/userguide/application_plugin.html)
```
gradle distZip 打包成 ZIP
gradle distTar 打包成 TAR
```
檔案放在`/Kotlin_GUI_TornadoFX/app/build/distributions`