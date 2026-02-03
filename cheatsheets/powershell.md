# PowerShell

## いまいる場所のファイルを再帰で探す
- コマンド: `Get-ChildItem -Recurse -Filter "*.log"`
- 何が起きる: カレント配下から指定パターンを列挙
- 注意: ディレクトリが巨大だと遅い
- 例: `Get-ChildItem -Recurse -Filter "*.json" | Select-Object FullName`

## コマンドのヘルプを見る
- コマンド: `Get-Help <cmd> -Full`
- 何が起きる: 詳細ヘルプ
- 注意: 必要なら `Update-Help`（権限/ネットワーク次第）
- 例: `Get-Help Get-ChildItem -Examples`

## 文字列検索（grep相当）
- コマンド: `Select-String -Path .\**\*.txt -Pattern "ERROR"`
- 何が起きる: パターン一致行を探す
- 注意: `**` は環境によって挙動差あり。だめなら `Get-ChildItem -Recurse` と組み合わせる
- 例: `Get-ChildItem -Recurse -Filter "*.log" | Select-String -Pattern "ERROR"`
\n# setup note
