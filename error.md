<!-- TOC -->

# 目次

- [import文で、iconsが見つからないエラー](#import文でiconsが見つからないエラー)
- [動作確認用の画像がない](#動作確認用の画像がない)
- [`by`でエラー](#byでエラー)
- [compilerのバージョンでビルドに失敗する](#compilerのバージョンでビルドに失敗する)

<!-- /TOC -->

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

## `by`でエラー

以下のimport文を追加

```kotlin
import androidx.compose.runtime.getValue
import androidx.compose.runtime.setValue
```

## compilerのバージョンでビルドに失敗する

`app/build.gradle.kts`の「compileSdk」の修正。

```kotlin
android {
    namespace = "com.example.order"
    compileSdk = 37

    defaultConfig {
        applicationId = "com.example.order"
        minSdk = 30
        targetSdk = 36
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            optimization {
                enable = false
            }
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_11
        targetCompatibility = JavaVersion.VERSION_11
    }
    buildFeatures {
        compose = true
    }
}
```

## WebViewの呼び出しでエラーとなる

Jetpack Composeで従来のAndroid ViewであるWebViewを表示する場合は、AndroidViewを使用します。

```kotlin
package com.example.webpageapp

import androidx.compose.runtime.Composable
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.viewinterop.AndroidView

@Composable
fun WebView(url: String) {
    AndroidView(
        factory = { context ->
            android.webkit.WebView(context).apply {
                webChromeClient = android.webkit.WebChromeClient()
                webViewClient = android.webkit.WebViewClient()
                settings.javaScriptEnabled = true
                loadUrl(url)
            }
        }
    )
}

@Preview
@Composable
fun WebViewPreview() {
    WebView(url = "https://www.google.com/")
}
```

## Serializerが見つからない

以下を追加

- build.gradle.kts

```kotlin
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.android)

    // これが必要
    alias(libs.plugins.kotlin.serialization)
}
```

- libs.version.toml

```kotlin
[plugins]
kotlin-serialization = { id = "org.jetbrains.kotlin.plugin.serialization", version.ref = "kotlin" }
```
