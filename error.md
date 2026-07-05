## import文で、iconsが見つからないエラー

Jetpack Compose の `Icons` は、Compose Material ライブラリに含まれています。  

`app/build.gradle.kts`に以下を追加してください。
```kotlin
dependencies {
    implementation("androidx.compose.material:material-icons-core")
    implementation("androidx.compose.material:material-icons-extended")
}
```