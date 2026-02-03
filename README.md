# cmd-cheatsheet

忘れたコマンドを、忘れた日に追記するだけのメモ。

## Index
- [PowerShell](./cheatsheets/powershell.md)
- [WSL](./cheatsheets/wsl.md)

## Format
### やりたいこと
- コマンド:
- 何が起きる:
- 注意:
- 例:

## Discordから追記する運用（メモ投げ→自動コミット）

このリポは「忘れたコマンド」をチャットに投げて、後で検索できる形に整形して蓄積するためのもの。

### 投稿のしかた（ラフでOK）
メッセージ先頭に対象だけ付ける：
- `wsl` … WSL / Git Bash / bash系のコマンド（まとめ枠）→ `cheatsheets/wsl.md`
- `pwsh` … PowerShell → `cheatsheets/powershell.md`

例：
- `wsl 複数の作業ディレクトリを作成できる: git worktree`
- `pwsh このコマンドメモっといて: Get-ChildItem -Recurse -Filter "*.log"`

### 整形ルール
- 見出し（やりたいこと）＋ コマンド＋注意＋例、の形に整形して追記する
- 情報が足りない場合は、最低限「見出し＋コマンド」だけでも追記する
