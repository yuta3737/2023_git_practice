# gitコマンド集その2

## ブランチ間で特定のコミットをマージしたいが、全部はマージしたくない場合

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
