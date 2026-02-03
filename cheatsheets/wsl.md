# WSL

## 文字列検索（ripgrep）
- コマンド: `rg "ERROR" .`
- 何が起きる: 高速全文検索
- 注意: 未インストールなら `sudo apt install ripgrep`
- 例: `rg -n "TODO" src/`

## ファイルを探す
- コマンド: `find . -type f -name "*.log"`
- 何が起きる: 再帰検索
- 注意: 大量ファイルで遅いときは絞る
- 例: `find . -maxdepth 3 -type f -name "*.json"`

## 圧縮・解凍（tar.gz）
- コマンド: `tar -czf out.tgz dir/`
- 何が起きる: 圧縮
- 注意: パスに注意
- 例: `tar -xzf out.tgz -C ./dest`

## 複数の作業ディレクトリを作成できる（git worktree）
- コマンド: `git worktree add <path> <branch-or-commit>`
- 何が起きる: 1つのリポジトリから複数の作業ツリー（別ディレクトリ）を同時に扱える
- 注意: worktreeでチェックアウト中のブランチは通常の `git branch -d` で消せないことがある（先に `git worktree remove` / `prune` を検討）
- 例: `git worktree add ../wt-feature feature/foo`
