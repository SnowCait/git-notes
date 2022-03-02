# GitHub API

## WebHook
- [GitHub webhook->hubotのテストをローカルで行う方法メモ - Qiita](https://qiita.com/nunulk/items/22c930dafe8c4afa7212)
- [jenkins - github api to compare commits, response status is diverged - Stack Overflow](https://stackoverflow.com/questions/23943855/github-api-to-compare-commits-response-status-is-diverged)
  - `compare` でブランチ比較時の status
    - "diverged" = commits were introduced on both the head and base branch since the common ancestor
    - "ahead" = commits were introduced on head after the common ancestor with base
    - "behind" = commits were introduced on base after the common ancestor with head
    - "identical" = branches point to same commit

## Branch
- [GitHub APIを使ってブランチを新規作成する - ぷらすのブログ](https://blog.p1ass.com/posts/create-branch-using-github-api/)

## 列挙型

||説明|
|---|---|
|`mergeable`|コンフリクトしていないか|
|`mergeStateStatus`|マージ可能か|
