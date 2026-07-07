## import文で、iconsが見つからないエラー

Jetpack Compose の `Icons` は、Compose Material ライブラリに含まれています。  

`app/build.gradle.kts`に以下を追加してください。
```kotlin
dependencies {
    implementation("androidx.compose.material:material-icons-core")
    implementation("androidx.compose.material:material-icons-extended")
}
```

## `by`でエラー

以下のimport文を追加

```kotlin
import androidx.compose.runtime.getValue
import androidx.compose.runtime.setValue
```

## compilerのバージョンでビルドに失敗する

`app/build.gradle.kts`の以下の修正。
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
