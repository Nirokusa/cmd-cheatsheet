# glab コマンドまとめ（GitLab CLI）

`glab` は GitLab の公式CLI。Issue / MR / パイプライン / リリースなどを、ターミナルから操作できる。

## セットアップ

### インストール
- macOS: `brew install glab`
- Ubuntu/Debian: `sudo apt install glab`（古い場合あり）
- 公式: https://gitlab.com/gitlab-org/cli

### 認証（ログイン）
- 対話式: `glab auth login`
  - GitLab.com か self-hosted を選ぶ
  - トークン方式が確実（PAT: api スコープ等）
- 状態確認: `glab auth status`
- アカウント切替/追加: `glab auth login --hostname <gitlab.example.com>`

### 既定のホスト
- GitLab.com: `gitlab.com`
- Self-hosted は `--hostname` を付ける。

## リポジトリ（ローカルから扱う前提）
- いまのリポジトリをGitLabに関連付ける（基本は git remote で自動認識）
  - `git remote -v` で remote が GitLab を向いているか確認

## よく使うコマンド

### 1) Issue
- 一覧: `glab issue list`
  - フィルタ例: `glab issue list --assignee @me --state opened`
- 表示: `glab issue view <IID>`
- 作成: `glab issue create`
  - タイトルだけ: `glab issue create -t "title"`
- コメント: `glab issue comment <IID> -m "text"`
- クローズ: `glab issue close <IID>`

> **IID** はプロジェクト内の連番（#123 の 123）。グローバルIDとは別。

### 2) Merge Request（MR）
- 一覧: `glab mr list`
- 作成: `glab mr create`
  - よくある流れ: ブランチ切る → push → create
- 表示: `glab mr view <IID>`
  - 差分: `glab mr diff <IID>`
- チェックアウト: `glab mr checkout <IID>`
- レビュー（Approve）: `glab mr approve <IID>`
- マージ: `glab mr merge <IID>`
  - オプションは環境次第（squash/merge when pipeline succeeds等）

### 3) パイプライン / CI
- 直近パイプライン: `glab pipeline list`
- パイプライン詳細: `glab pipeline view <ID>`
- ジョブ一覧: `glab pipeline jobs <ID>`

### 4) リリース / タグ
- リリース一覧: `glab release list`
- リリース表示: `glab release view <tag>`
- リリース作成: `glab release create <tag> -n "notes"`

### 5) リポジトリ/プロジェクト情報
- プロジェクト表示: `glab repo view`
- ブラウザで開く: `glab repo view --web`

## 便利オプション
- JSON出力: `--json <fields>`（対応コマンドのみ）
- Webで開く: `--web`
- 1件だけ: `--limit 1`

## よくあるつまずき

- **認証が通らない**
  - `glab auth status` で確認
  - PAT のスコープ不足（api/read_api など）

- **どのプロジェクトを操作してるか分からない**
  - `git remote -v` を確認（GitLab remote か）
  - 明示したい場合は `-R <OWNER/REPO>` や `--repo` 系（バージョンで差あり）

- **IIDとIDの混同**
  - Issue/MRはだいたい IID（#番号）で操作することが多い

## まず覚える最小セット
- `glab auth login`
- `glab issue list`
- `glab issue create`
- `glab mr create`
- `glab pipeline list`

---

メモ更新の希望（コマンド例を増やす、特定用途：レビュー運用/リリース運用など）があれば言って。
