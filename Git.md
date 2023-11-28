## リモートリポジトリで自分が作業したブランチをマージした後に、マージを取り消したい時
1. ローカルリポジトリのDevelopブランチにて

```
git reset --hard HEAD^
```

2. developブランチのマージしたコミットの一つ前にコミットに戻っていることを確認する

```
git log
```

3.  ローカルからリモートに反映

```
git push -f origin develop
```

これでdevelopブランチがマージする前に戻る


## プルリクしてるものがコンフリクトした時
ローカルでコンフリクトを解消したいので、
1. リモートのdevelopブランチの内容をローカルに一時反映

```
git fetch origin develop
```

2. 作業ブランチにcheckoutして、developブランチの内容を作業ブランチに反映

```
git merge origin/develop
```

3. コンフリクトを起こしているファイルを修正して、コミット&プッシュで完了


