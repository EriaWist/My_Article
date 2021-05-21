# Exposed
[Getting Started](https://github.com/JetBrains/Exposed/wiki/Getting-Started)
首先設定`build.gradle`
```  groovy
dependencies {
    implementation("org.jetbrains.exposed:exposed-core:$exposedVersion")
    implementation("org.jetbrains.exposed:exposed-dao:$exposedVersion")
    implementation("org.jetbrains.exposed:exposed-jdbc:$exposedVersion")
}
```
`$exposedVersion`的部分替換成當前版本

---
### connection連接
> 連接SQLite

Step
1. 將`org.sqlite.JDBC`導入
``` groovy
dependencies {
    //導入sqllite
    implementation 'org.xerial:sqlite-jdbc:3.34.0'
}
```
2. import Database
``` kotlin
import org.jetbrains.exposed.sql.Database
```

3. 連接sqlite
``` Kotlin
Database.connect("jdbc:sqlite:./data.db", "org.sqlite.JDBC")
```
