## import文で、iconsが見つからないエラー

Jetpack Compose の `Icons` は、Compose Material ライブラリに含まれています。

`app/build.gradle.kts`に以下を追加してください。

```kotlin
dependencies {
    implementation("androidx.compose.material:material-icons-core")
    implementation("androidx.compose.material:material-icons-extended")
}
```

## 動作確認用の画像がない

以下のURLの画像を使用してください

```url
https://raw.githubusercontent.com/KimiyukiYamauchi/android.kotlin/main/images/android-head_flat.png
```
