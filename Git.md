# Gitの基本

### ワークツリー
実際に作業をしているディレクトリ


### インデックス(index)
リポジトリに保存されている情報とワークツリー（作業している場所）との
差（変更箇所）を記録する場所

ワークツリーからの変更がインデックスに追加されると、Gitはその変更を次のコミットに含める準備ができたということ
インデックスに登録されていないファイルはコミットされない

### リポジトリ
ファイルやディレクトリの状態を記録する場所

### HEAD
現在使用しているブランチの先頭(最終コミット)を表す名前

### origin
リモートリポジトリのアクセス先に対してGitがデフォルトでつける名前

この行をコンフリクトさせる
コンフリクト解消完了！