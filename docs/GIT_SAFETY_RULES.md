# 🚨 Git操作安全規則 - REBASE絶対禁止令

## 📋 目的
Git rebase操作による全データ消失事故の完全再発防止

## 🚫 絶対禁止操作

### ❌ LEVEL 5: 即座データ消失危険
```bash
# これらのコマンドは絶対に実行禁止
git rebase
git pull --rebase
git pull origin main --rebase
git reset --hard origin/main
git checkout origin/main
```

### ❌ LEVEL 4: 高危険操作
```bash
# 慎重な確認なしに実行禁止
git pull origin main
git merge origin/main
git reset --hard
```

## ✅ 安全な操作のみ許可

### 🟢 LEVEL 1: 完全安全操作
```bash
# ローカル確認系（常に安全）
git status
git log --oneline -10
git diff HEAD~1
git show HEAD
ls -la
wc -l app.py
```

### 🟡 LEVEL 2: 条件付き安全操作
```bash
# Force Push（ローカルが最新の場合のみ）
git push --force-with-lease origin main

# 新ブランチ作成（常に安全）
git checkout -b production-deploy
git push origin production-deploy
```

## 🛡️ 強制安全手順

### Streamlit Cloud デプロイ手順
```bash
# ステップ1: 現在状態の確認
git status
git log --oneline -5
wc -l app.py
ls docs/ | wc -l  # 28個のMDファイル確認

# ステップ2: 新ブランチでの安全デプロイ
git checkout -b streamlit-cloud-deploy-$(date +%Y%m%d)
git push origin streamlit-cloud-deploy-$(date +%Y%m%d)

# ステップ3: Streamlit Cloud で新ブランチを指定
# GitHub連携時に main ではなく新ブランチを選択
```

### 緊急時の安全確認
```bash
# 任意のGit操作前に実行必須
echo "=== 安全確認チェックリスト ==="
echo "✅ app.pyの行数: $(wc -l app.py)"
echo "✅ docsファイル数: $(ls docs/ | wc -l)"
echo "✅ 認証システム: $(ls auth_system.py 2>/dev/null && echo '存在' || echo '⚠️消失')"
echo "✅ 最新コミット: $(git log --oneline -1)"
echo "=========================="
```

## 🔥 事故パターン分析

### 過去の事故事例
1. **MCF DEATH GUARD事故**: GitHub Security Scanningによるpush拒否
2. **今回の事故**: git pull --rebase による古い状態への巻き戻し

### 共通原因
- **リモートの古い状態を「正解」として扱うGit操作**
- **ローカルの最新開発成果を軽視する操作**

## 📋 必須確認事項

### デプロイ前チェックリスト
- [ ] app.py行数: 6,377行以上
- [ ] docsフォルダ: 28個以上のMDファイル
- [ ] auth_system.py: 存在確認
- [ ] casting_office.db: 400KB以上
- [ ] .gitignore: 認証ファイル除外確認

### 操作前必須質問
1. 「この操作でローカルファイルが変更される可能性はありますか？」
2. 「リモートの古いデータでローカルが上書きされる可能性はありますか？」
3. 「rebase/reset/mergeなどの危険操作が含まれていませんか？」

## 🚀 安全なデプロイ戦略

### Option A: 新ブランチ戦略（推奨）
```bash
# 1. 新ブランチ作成
git checkout -b production-ready-$(date +%Y%m%d-%H%M)

# 2. 即座にプッシュ
git push origin production-ready-$(date +%Y%m%d-%H%M)

# 3. Streamlit Cloudで新ブランチ指定
```

### Option B: Force Push戦略
```bash
# 事前確認必須
git status
wc -l app.py
ls docs/ | wc -l

# ローカルが最新の場合のみ実行
git push --force-with-lease origin main
```

## 🆘 緊急復旧手順

### データ消失事故発生時
```bash
# 1. 即座に操作停止
git status

# 2. Google Drive バックアップから復旧
python3 google_drive_complete_backup.py --restore

# 3. 復旧確認
wc -l app.py
ls docs/ | wc -l
```

## 📞 エスカレーション

### 危険操作検出時
1. **即座停止**: 任意のGit操作を中断
2. **状況報告**: 現在のファイル状態を報告
3. **安全確認**: バックアップ状況の確認
4. **代替手段**: 新ブランチ戦略への変更

## 🔒 最終防衛線

### Google Drive自動バックアップ
- 1時間毎の自動バックアップ実行
- 重要ファイルの物理コピー保持
- Git操作とは独立したデータ保護

---

**⚠️ この規則に従わない場合、全ての開発成果が瞬時に消失する可能性があります。**

**✅ 疑問がある場合は、必ず操作前に確認してください。**