# GitHub Actions

## Official
- [GitHub アクションでワークフローを自動化する - GitHub ヘルプ](https://help.github.com/ja/categories/automating-your-workflow-with-github-actions)
- [GitHub Marketplace · Actions to improve your workflow](https://github.com/marketplace?type=actions)

## 便利 Actions
- [GitHub Actions(beta)向けにslack通知プラグインを作った - 839の日記](https://839.hateblo.jp/entry/2019/08/16/104624)
- [WIP · Actions · GitHub Marketplace](https://github.com/marketplace/actions/wip)
- [Create Pull Request · Actions · GitHub Marketplace](https://github.com/marketplace/actions/create-pull-request)

## 参考
- [GitHub Actions(v2)ファーストインプレッション 〜v1との違い、導入方法、価格、良い点・悪い点〜 - Hack Your Design!](https://blog.toshimaru.net/github-actions-first-impression/)
- [新 GitHub Actions 入門 - 生産性向上ブログ](https://www.kaizenprogrammer.com/entry/2019/08/18/205010)

## Idea
- 全員または一定数が Approve したらマージ
  - 全員
    - マージしたくないケースもあると思うので input で指定されるアカウントが assign されている場合に限定する
    - 指定されなかったら常にマージ
  - 一定数
    - 特定の人のレビューを必須にしたい場合は assign にも設定してレビューが終わっていることを確認する
  - input
    - account: @SnowCait
    - min: 0 `auto merge`, null `all approved`
