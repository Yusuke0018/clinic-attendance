# ファイル共有システム

シンプルなファイル共有システムです。管理者がファイルをアップロードし、誰でも閲覧・ダウンロードできます。

## セットアップ手順

### 1. Firebaseプロジェクトの作成

1. [Firebase Console](https://console.firebase.google.com/) にアクセス
2. 「プロジェクトを作成」をクリック
3. プロジェクト名を入力（例: clinic-file-share）
4. Googleアナリティクスは「今は設定しない」を選択（シンプルにするため）

### 2. Firebase Storageの有効化

1. 左メニューから「Storage」を選択
2. 「始める」をクリック
3. セキュリティルールは「本番環境モード」を選択
4. ロケーションは「asia-northeast1（東京）」を選択

### 3. Storageルールの設定

Storage > ルール で以下を設定：

```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /files/{allPaths=**} {
      allow read: if true;
      allow write: if true;
    }
  }
}
```

※ これは簡易的なルールです。本番環境では認証を追加してください。

### 4. Firebase設定の取得

1. プロジェクト設定（歯車アイコン）をクリック
2. 「全般」タブの下部「マイアプリ」セクション
3. 「</> ウェブ」アイコンをクリック
4. アプリ名を入力（例: file-share-web）
5. 「Firebase Hostingも設定」のチェックは外す
6. 「アプリを登録」をクリック
7. 表示される設定値をコピー

### 5. index.htmlの設定

index.htmlの以下の部分を、取得した設定値に置き換えてください：

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

### 6. 管理者パスワードの変更

index.htmlの242行目：
```javascript
const ADMIN_PASSWORD = 'admin123';
```
を任意のパスワードに変更してください。

## 使い方

1. index.htmlをブラウザで開く
2. 管理者でログイン（設定したパスワード）
3. ファイルをドラッグ＆ドロップまたは選択してアップロード
4. アップロードされたファイルは自動的に一覧に表示される
5. 誰でもファイルをダウンロード可能

## 機能

- 管理者ログイン（簡易パスワード認証）
- ファイルアップロード（ドラッグ＆ドロップ対応）
- ファイル一覧表示
- ファイルダウンロード
- レスポンシブデザイン

## 注意事項

- 本番環境では適切な認証システムを実装してください
- 大容量ファイルのアップロードにはFirebaseの容量制限があります
- 無料プランでは1日あたりのダウンロード量に制限があります