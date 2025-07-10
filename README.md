# ファイル共有システム（GitHub版）

GitHubを使用した完全無料のファイル共有システムです。

## 特徴

- 完全無料（GitHubの無料枠を使用）
- Firebase不要
- 管理者のみファイルアップロード可能
- 誰でもファイルを閲覧・ダウンロード可能
- GitHub Pagesでホスティング可能

## セットアップ手順

### 1. GitHub Personal Access Tokenの取得

1. [GitHub](https://github.com) にログイン
2. 右上のプロフィールアイコン → Settings
3. 左メニューの一番下「Developer settings」
4. 「Personal access tokens」→「Tokens (classic)」
5. 「Generate new token (classic)」をクリック
6. Note欄に「File Share System」など任意の名前を入力
7. Expiration（有効期限）を選択（90日推奨）
8. Select scopesで「repo」にチェック
9. 「Generate token」をクリック
10. 生成されたトークン（ghp_で始まる文字列）をコピー

**重要**: トークンは一度しか表示されません。必ずコピーして保存してください。

### 2. GitHub Pagesの有効化

1. リポジトリの「Settings」タブを開く
2. 左メニューの「Pages」をクリック
3. Source: Deploy from a branch
4. Branch: main、/(root)を選択
5. 「Save」をクリック

数分後、`https://yusuke0018.github.io/clinic-attendance/` でアクセス可能になります。

### 3. システムの初期設定

1. ブラウザでindex.htmlを開く（またはGitHub PagesのURL）
2. 初期設定画面で以下を入力：
   - GitHub Personal Access Token（先ほどコピーしたもの）
   - 管理者パスワード（任意に設定）
3. 「設定を保存」をクリック

## 使い方

### 管理者（ファイルアップロード）

1. 管理者パスワードでログイン
2. ファイルをドラッグ＆ドロップまたは選択してアップロード
3. アップロードされたファイルは自動的にGitHubリポジトリの`files`フォルダに保存

### 一般ユーザー（ファイル閲覧）

1. ページを開くとファイル一覧が表示される
2. 「ダウンロード」ボタンでファイルをダウンロード

## 制限事項

- ファイルサイズ: 1ファイル最大100MB（GitHubの制限）
- リポジトリ容量: 最大1GB推奨（GitHubの推奨値）
- API制限: 1時間あたり5000リクエスト（認証あり）

## セキュリティ注意事項

- Personal Access Tokenは他人に教えないでください
- パブリックリポジトリの場合、アップロードしたファイルは誰でも閲覧可能です
- 機密情報を含むファイルはアップロードしないでください

## トラブルシューティング

### ファイル一覧が表示されない
- Personal Access Tokenが正しく設定されているか確認
- トークンの有効期限が切れていないか確認

### アップロードエラーが発生する
- ファイルサイズが100MBを超えていないか確認
- インターネット接続を確認

### ログインできない
- 設定した管理者パスワードが正しいか確認
- ブラウザのキャッシュをクリアして再試行