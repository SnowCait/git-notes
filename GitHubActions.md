# GitHub Actions

## Official
- [Features • GitHub Actions](https://github.com/features/actions)
- [GitHub アクションでワークフローを自動化する - GitHub ヘルプ](https://help.github.com/ja/categories/automating-your-workflow-with-github-actions)
- [GitHub Marketplace · Actions to improve your workflow](https://github.com/marketplace?type=actions)
- blog
  - [GitHub Actions now supports CI/CD, free for public repositories](https://github.blog/2019-08-08-github-actions-now-supports-ci-cd/)
  - [New workflow editor for GitHub Actions - The GitHub Blog](https://github.blog/2019-10-01-new-workflow-editor-for-github-actions/?utm_campaign=1569944972&utm_medium=social&utm_source=twitter&utm_content=1569944972)
  - [GitHub Actions - new workflow syntax features - The GitHub Blog](https://github.blog/changelog/2019-10-01-github-actions-new-workflow-syntax-features/)
  - [Working with GitHub Actions | Jeff Rafter](https://jeffrafter.com/working-with-github-actions/)
  - [GitHub Actions: Manual triggers with workflow_dispatch The GitHub Blog](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch/)
- [GitHub Actions - GitHub Community Forum](https://github.community/t5/GitHub-Actions/bd-p/actions)
- [microsoft/azure-pipelines-image-generation: Azure Pipelines VM image generation for Microsoft-hosted CI/CD](https://github.com/microsoft/azure-pipelines-image-generation)

## 便利 Actions
- [GitHub API Request · Actions · GitHub Marketplace](https://github.com/marketplace/actions/github-api-request)
- [AWS for GitHub Actions](https://github.com/aws-actions)
- [Azure/k8s-deploy: GitHub Action for deploying to Kubernetes clusters](https://github.com/Azure/k8s-deploy)
- Slack
  - [Slatify · Actions · GitHub Marketplace](https://github.com/marketplace/actions/slatify)
  - [GitHub Actions(beta)向けにslack通知プラグインを作った - 839の日記](https://839.hateblo.jp/entry/2019/08/16/104624)
- [WIP · Actions · GitHub Marketplace](https://github.com/marketplace/actions/wip)
- Pull Request
  - [Github Hub · Actions · GitHub Marketplace](https://github.com/marketplace/actions/github-hub)
  - [Create Pull Request · Actions · GitHub Marketplace](https://github.com/marketplace/actions/create-pull-request)
- [Run Laravel test suite on GitHub Actions with laravel-docker • stefanzweifel.io](https://stefanzweifel.io/posts/run-laravel-test-suite-on-github-actions-with-laravel-docker/)
- [warrenbuckley/Setup-Nuget: Set up your GitHub Actions workflow with the latest version of Nuget.exe CLI tool](https://github.com/warrenbuckley/Setup-Nuget)

## 参考
- [GitHub Actions(v2)ファーストインプレッション 〜v1との違い、導入方法、価格、良い点・悪い点〜 - Hack Your Design!](https://blog.toshimaru.net/github-actions-first-impression/)
- [新 GitHub Actions 入門 - 生産性向上ブログ](https://www.kaizenprogrammer.com/entry/2019/08/18/205010)
- [GitHub Actionsの使い方 | 純規の暇人趣味ブログ](https://jyn.jp/github-actions-usage/)
- [GitHub Actionsで.NET CoreアプリをAzureにデプロイする - Qiita](https://qiita.com//ikuosaito1989/items/1baf18c739d332f41411)

## Action の作り方
- [GitHub Actions の JavaScript Action を TypeScript で書いた - はやくプログラムになりたい](https://rhysd.hatenablog.com/entry/2019/11/15/212713)
- [TypeScriptの型エラーをPR上に表示するGitHub Actionsを作成してみた | Studio Andy](https://blog.andoshin11.me/posts/typescript-error-reporter-action)

### Templates
自作する際のテンプレート。
- [actions/hello-world-docker-action: A template to demonstrate how to build a JavaScript action.](https://github.com/actions/hello-world-docker-action)
- [actions/javascript-action: Create a JavaScript Action with tests, linting, workflow, publishing, and versioning](https://github.com/actions/javascript-action)
- [actions/typescript-action](https://github.com/actions/typescript-action)

## セルフホストランナー
- [自分のランナーをホストする - GitHub ヘルプ](https://help.github.com/ja/actions/hosting-your-own-runners)
- [[GitHub]ActionsのホストランナーをEC2でやってみた | Developers.IO](https://dev.classmethod.jp/articles/hosted-runner-on-ec2/)
- [GitHub Actionsでself-hosted runnersを試す - Qiita](https://qiita.com/hanaokatomoki/items/af47da39a61948fb123f)

## Azure Pipelines
- [GitHub Actionsを利用したAzure Pipelines連携を試してみた - kokoni](https://blog.kokoni.jp/entry/20191222)

## Skip
- [ブログズミ: GitHub Actions で [ci skip] できるようにしました](https://srz-zumix.blogspot.com/2019/10/github-actions-ci-skip.html)
- [GitHub Actions で Skip CI を実現する - Qiita](https://qiita.com/peaceiris/items/28e302996ccf04551434)
- [GitHub Actions does not respect [skip ci] #9](https://github.community/t/github-actions-does-not-respect-skip-ci/17325/9)

## 足りていないもの
- ~手動トリガー~
  - ~デプロイ等に使いたい~
- ワークフロー途中での承認
- ~キャッシュ機構~
- ~セルフホスト~
- エラーハンドリング（失敗を許容する）

## 巨大リポジトリを扱う方法
一般的なクラウド CI サービスはまず git clone を行う。しかし巨大リポジトリだとそこで数十分～数時間かかってしまい CI に支障をきたす。  
Jenkins の場合ワーキングディレクトリが使いまわされるので予め並列実行数分 git clone しておくなどの対策がとれるがクラウド CI サービスでは難しい。
- リポジトリを分割する
- git clone したディレクトリをキャッシュ
- Git LFS
- [VFS for Git](https://www.learning-diary.com/posts/20190321-try-vfs-for-git/)
- セルフホストランナー
  - Jenkins のようにできる？
