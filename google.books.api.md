## 認証情報の作成

- [Google Cloud Console](https://console.cloud.google.com/)

### Google Cloud Console

### → 有効なAPIとサービス

#### APIとサービスを有効にする

#### Books APIを選択


#### → APIとサービス

#### → 認証情報

#### → 認証情報を作成

#### → APIキー

- 名前 => 例： BooksAPI
- APIの制限の選択 => Books API
- アプリケーションの制限 => なし

## Webでのアクセス

```
https://www.googleapis.com/books/v1/volumes?q=inauthor:%E8%8A%A5%E5%B7%9D%E9%BE%8D%E4%B9%8B%E4%BB%8B&key=YOUR_API_KEY
```
