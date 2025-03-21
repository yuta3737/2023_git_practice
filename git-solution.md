# gitコマンド集

## リモートリポジトリで自分が作業したブランチをマージした後に、マージを取り消したい時

1. ローカルリポジトリのDevelopブランチにて

```bash
git reset --hard HEAD^
```

2. developブランチのマージしたコミットの一つ前にコミットに戻っていることを確認する

```bash
git log
```

3. ローカルからリモートに反映

```bash
git push -f origin develop
```

これでdevelopブランチがマージする前に戻る

## プルリクしてるものがコンフリクトした時

ローカルでコンフリクトを解消したいので、

1. リモートのdevelopブランチの内容をローカルに一時反映

```bash
git fetch origin develop
```

2. 作業ブランチにcheckoutして、developブランチの内容を作業ブランチに反映

```bash
git merge origin/develop
```

3. コンフリクトを起こしているファイルを修正して、コミット&プッシュで完了

## コードレビューを頼まれて、ローカルでそのコードをみたい時

1. コードレビューしたいリモートリポジトリの最新コミットを取得

```bash
git fetch origin [ブランチ名]
```

2. 取得したブランチにチェックアウトする。または、リモートと同じブランチをローカルに作成する

```bash
git checkout origin/[ブランチ名]
```

```bash
git checkout -b [新規ブランチ名] origin/[元にするブランチ名]

```

## 編集内容を取り消したい時

### 編集内容を取り消したい(addする前)

```bash
git checkout [ファイル名]
```

[ファイル名]のところを.にすると、ステージング前の全ての変更内容がなくなる。

### ステージングを取り消したい

```bash
git checkout HEAD -- [ファイル名]
```

ステージしたファイルを最後にコミットした状態に戻す
つまり編集内容は残らない。

## コミットせずに変更を保存し他（のブランチ）で作業をしたいとき

1. まず変更を退避する

```bash
git stash -u
```

-u オプションは新規作成ファイル(gitが反応してくれないファイル)も退避することができる

2. 退避した変更の一覧を見る

```bash
git stash list
```

退避した作業の一覧を見ることができる

3. 退避していた変更を戻す

```bash
git stash apply [stash名]
```

例）　`git stash apply stash@{0}`

現在いるブランチに変更が反映される

4. 退避した作業を消す

```bash
git stash drop [stash名]
```

例）`git stash drop stash@{0}`

stash名がstashのリストから削除される

5. 3と4を一気に片付けるコマンド

```bash
git stash pop [stash名]
```

例）　`git stash pop stash@{0}`

変更を現在いるブランチに反映すると同時に、退避した変更の一覧の中から削除する
