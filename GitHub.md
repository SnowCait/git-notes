# GitHub

## 設定
- Branch protection
  - 設定すると force push 禁止になる
  - レビュー必須にできる `Require pull request reviews before merging`
  - status check に通っていることを必須にできる `Require status checks to pass before merging`

## Authentication
### OAuth (Personal Access Token)
- [Dockerfileのbuildで簡単にGithubのプライベートリポジトリをクローンする方法 - Qiita](https://qiita.com/Jah524/items/fa68f99c8b787f94b884)

## Marketplace
- [dependabot](https://github.com/marketplace/dependabot-preview)
- [Renovate | Automated Dependency Updates](https://renovatebot.com/)
- [delete-merged-branch](https://github.com/apps/delete-merged-branch/)

## Issue / Pull request
- [Issue およびプルリクエストを検索する - GitHub ヘルプ](https://help.github.com/ja/github/searching-for-information-on-github/searching-issues-and-pull-requests)

## ZenHub
GitHub を拡張できる。
- [ZenHub - Agile Project Management for GitHub](https://www.zenhub.com/)
- [ZenHub2.0について](https://qiita.com/GeckoTang/items/1402c48181c4663e68c5)
- [GitHubを中心とした開発プロセス ZenHub - Qiita](https://qiita.com/suzuki-hoge/items/f02b6752d8876ba6e114)

## Zube.io
- [スクラム向けプロジェクトマネジメントツールを比較した結果 Zube.io を推してみる - Witch on the Other Shore](https://iktakahiro.hatenablog.com/entry/2018/07/12/192213)

## Slack
- [GitHub | Slack App ディレクトリ](https://by-black.slack.com/apps/A8GBNUWU8-github)
  - [GitHub Enterprise Server | Slack App ディレクトリ](https://by-black.slack.com/apps/A0F7YS2SX-github-enterprise-server)
- [無料になった Pull Panda を GitHub に導入すると、Pull Requestのやり取りが自動化されて便利に！！ ｜ DevelopersIO](https://dev.classmethod.jp/tool/github/happy-pull-panda/)

## GitHub Enterprise
### メリット
- 社内ネットワークに置ける
- マネジメントコンソールで設定をいじれる
  - LDAP, SAML, CAS
  - Repository upload limit `100MB -> 1GB`

### デメリット
- メンテナンスコストがかかる
- 機能追加がとても遅いので最新機能を使えない
  - Suggestion
  - Re-request review
  - Viewed
 
