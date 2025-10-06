# 🎭 AIcast Room - キャスト管理・対話アプリ

AIcast Roomは、Google Cloud Vertex AIとStreamlitを活用したキャスト管理・対話アプリケーションです。複数のキャストとの対話、X(Twitter)投稿、スケジュール管理など、包括的なキャスト運営機能を提供します。

## ✨ 主要機能

### 🎪 コア機能
- **ダッシュボード**: キャスト統計、投稿管理、システム状況の一覧表示
- **キャスト管理**: プロフィール設定、個性調整、AI設定の詳細管理
- **AI対話**: Vertex AI Gemini-1.5-proを活用した自然な対話生成
- **投稿管理**: X(Twitter)投稿の作成、編集、スケジュール管理

### 🔐 認証・セキュリティ
- **パスワード認証**: SHA256ハッシュ化による安全な認証システム
- **セッション管理**: 8時間有効な自動ログアウト機能
- **2名運用対応**: 複数ユーザーでの安全な共同運用

### 🚀 X(Twitter) API統合
- **リアルタイム投稿**: 即座の投稿機能
- **予約投稿**: 時間指定での自動投稿
- **マルチアカウント**: 複数キャストの個別アカウント管理
- **リツイート機能**: 自動リツイートスケジューリング

### 📊 管理機能
- **投稿履歴**: 全投稿の詳細管理と検索
- **統計表示**: キャスト別パフォーマンス分析
- **バックアップ**: Google Drive自動バックアップ
- **ログ管理**: システム動作の詳細記録

## 🛠️ 技術仕様

### システム要件
- **言語**: Python 3.12+
- **フレームワーク**: Streamlit
- **AI**: Google Cloud Vertex AI (Gemini-1.5-pro)
- **データベース**: SQLite
- **認証**: Google Cloud ADC

### 主要依存関係
```txt
streamlit
pandas
google-cloud-aiplatform
gspread
google-auth
requests
python-dateutil
```

## 🚀 デプロイ手順

### Streamlit Cloud デプロイ

1. **リポジトリ連携**
   ```bash
   # GitHubリポジトリをStreamlit Cloudに接続
   ```

2. **Secrets設定**
   ```toml
   # Streamlit Cloud Secrets管理で設定
   [auth]
   password_hash = "your_password_hash_here"
   
   [development]
   debug_mode = false
   ```

3. **環境変数**
   - `GCP_PROJECT`: Google CloudプロジェクトID
   - `GOOGLE_APPLICATION_CREDENTIALS`: 認証情報（Streamlit Cloud Secrets推奨）

### ローカル開発

1. **認証設定**
   ```bash
   gcloud auth application-default login --no-launch-browser
   ```

2. **依存関係インストール**
   ```bash
   pip3 install -r requirements.txt
   ```

3. **アプリケーション起動**
   ```bash
   python3 run.py
   ```

## 🔐 セキュリティ

### 認証システム
- SHA256ハッシュ化パスワード
- セッションベース認証（8時間有効）
- 認証失敗時の自動ログアウト

### データ保護
- 認証情報の.gitignore除外
- Google Drive自動バックアップ
- SQLiteデータベース暗号化対応

## 📁 プロジェクト構造

```
aicast-room/
├── app.py                          # メインアプリケーション
├── auth_system.py                  # 認証システム
├── run.py                         # 起動スクリプト
├── requirements.txt               # 依存関係
├── style.css                     # UI スタイル
├── casting_office.db              # SQLite データベース
├── streamlit_secrets_template.toml # Secrets テンプレート
├── docs/                          # ドキュメント
│   ├── GIT_SAFETY_RULES.md       # Git操作安全規則
│   ├── FEATURES_LIST_LATEST.md   # 機能一覧
│   └── ...                       # その他ドキュメント
└── .streamlit/
    └── secrets.toml.template      # ローカル開発用設定
```

## 🏆 主要実装機能

### ✅ 完了機能
- [x] ダッシュボード & 統計表示
- [x] キャスト管理システム
- [x] AI対話生成（Vertex AI）
- [x] X API投稿機能
- [x] パスワード認証システム
- [x] 予約投稿システム
- [x] リツイート自動化
- [x] Google Drive バックアップ
- [x] マルチアカウント対応
- [x] Streamlit Cloud対応

### 🚀 技術的特徴
- **6,386行** の包括的実装
- **30個** の詳細ドキュメント
- **Git安全規則** による開発保護
- **三重バックアップ** システム

## 📞 サポート・問い合わせ

- **ドキュメント**: `docs/` フォルダ内の詳細ガイド
- **トラブルシューティング**: `docs/TROUBLESHOOTING_*.md`
- **開発者ガイド**: `docs/DEVELOPMENT_RULES.md`

## 📝 ライセンス

このプロジェクトは開発中のプライベートアプリケーションです。

---

**🎭 AIcast Room** - Powered by Google Cloud Vertex AI & Streamlit