<!-- TOC -->

# 目次

- [import文で、iconsが見つからないエラー](#import文でiconsが見つからないエラー)
- [動作確認用の画像がない](#動作確認用の画像がない)
- [`by`でエラー](#byでエラー)
- [compilerのバージョンでビルドに失敗する](#compilerのバージョンでビルドに失敗する)
- [WebViewの呼び出しでエラーとなる](#webviewの呼び出しでエラーとなる)
- [Serializerが見つからない](#serializerが見つからない)

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

```url
https://raw.githubusercontent.com/KimiyukiYamauchi/android.kotlin/main/images/android-head_3D.png
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
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.compose)
    id("com.google.devtools.ksp") version "2.2.10-2.0.2" // 追加
}

android {
    namespace = "com.example.mytodo"
//    compileSdk {
//        version = release(36) {
//            minorApiLevel = 1
//        }
//    }
    compileSdk = 37

    defaultConfig {
        applicationId = "com.example.mytodo"
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

dependencies {
    implementation("androidx.room:room-runtime:2.8.4") // 追加
    implementation("androidx.room:room-ktx:2.8.4") // 追加
    ksp("androidx.room:room-compiler:2.8.4") // 追加

    implementation(platform(libs.androidx.compose.bom))
    implementation(libs.androidx.activity.compose)
    implementation(libs.androidx.compose.material3)
    implementation(libs.androidx.compose.ui)
    implementation(libs.androidx.compose.ui.graphics)
    implementation(libs.androidx.compose.ui.tooling.preview)
    implementation(libs.androidx.core.ktx)
    implementation(libs.androidx.lifecycle.runtime.ktx)
    testImplementation(libs.junit)
    androidTestImplementation(platform(libs.androidx.compose.bom))
    androidTestImplementation(libs.androidx.compose.ui.test.junit4)
    androidTestImplementation(libs.androidx.espresso.core)
    androidTestImplementation(libs.androidx.junit)
    debugImplementation(libs.androidx.compose.ui.test.manifest)
    debugImplementation(libs.androidx.compose.ui.tooling)
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
