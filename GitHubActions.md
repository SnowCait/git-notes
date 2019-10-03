# GitHub Actions

## Official
- [Features • GitHub Actions](https://github.com/features/actions)
- [GitHub アクションでワークフローを自動化する - GitHub ヘルプ](https://help.github.com/ja/categories/automating-your-workflow-with-github-actions)
- [GitHub Marketplace · Actions to improve your workflow](https://github.com/marketplace?type=actions)
- blog
  - [GitHub Actions now supports CI/CD, free for public repositories](https://github.blog/2019-08-08-github-actions-now-supports-ci-cd/)
  - [New workflow editor for GitHub Actions - The GitHub Blog](https://github.blog/2019-10-01-new-workflow-editor-for-github-actions/?utm_campaign=1569944972&utm_medium=social&utm_source=twitter&utm_content=1569944972)
- [GitHub Actions - GitHub Community Forum](https://github.community/t5/GitHub-Actions/bd-p/actions)

## 便利 Actions
- Slack
  - [Slatify · Actions · GitHub Marketplace](https://github.com/marketplace/actions/slatify)
  - [GitHub Actions(beta)向けにslack通知プラグインを作った - 839の日記](https://839.hateblo.jp/entry/2019/08/16/104624)
- [WIP · Actions · GitHub Marketplace](https://github.com/marketplace/actions/wip)
- [Create Pull Request · Actions · GitHub Marketplace](https://github.com/marketplace/actions/create-pull-request)

## 参考
- [GitHub Actions(v2)ファーストインプレッション 〜v1との違い、導入方法、価格、良い点・悪い点〜 - Hack Your Design!](https://blog.toshimaru.net/github-actions-first-impression/)
- [新 GitHub Actions 入門 - 生産性向上ブログ](https://www.kaizenprogrammer.com/entry/2019/08/18/205010)

## Templates
自作する際のテンプレート。
- [actions/hello-world-docker-action: A template to demonstrate how to build a JavaScript action.](https://github.com/actions/hello-world-docker-action)
- [actions/javascript-action: Create a JavaScript Action with tests, linting, workflow, publishing, and versioning](https://github.com/actions/javascript-action)
- [actions/typescript-action](https://github.com/actions/typescript-action)

## 足りていないもの
- 手動トリガー
  - デプロイ等に使いたい
- ワークフロー途中での承認
- キャッシュ機構

## 巨大リポジトリを扱う方法
一般的なクラウド CI サービスはまず git clone を行う。しかし巨大リポジトリだとそこで数十分～数時間かかってしまい CI に支障をきたす。  
Jenkins の場合ワーキングディレクトリが使いまわされるので予め並列実行数分 git clone しておくなどの対策がとれるがクラウド CI サービスでは難しい。
- リポジトリを分割する
- git clone したディレクトリをキャッシュ
- Git LFS
- [VFS for Git](https://www.learning-diary.com/posts/20190321-try-vfs-for-git/)

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
- do-not-merge-labels
  - 特定のラベルが付いていたらマージボタンを非アクティブにする
    - `WIP`, `作業中`
  - [WIP · Actions · GitHub Marketplace](https://github.com/marketplace/actions/wip) のラベル版
- あるブランチにマージされたら別のブランチにもマージする
  - マージ終わったら削除走らせても良さそうだが削除専用の Action を組み合わせられるならそっちの方がいい
- マージ先ブランチに対応したラベルを付ける
  - 例
    - ブランチ名と同じラベルを付ける
    - デフォルトブランチ以外がマージ先のときにラベルを付ける
  - labeler と組み合わせられそうならそうする
- 編集禁止ディレクトリ/ファイル
  - Pull Request に含まれていたら Check のステータスを false にする
- 特定のコードが含まれていたらエラーにする
  - `var_dump` やデバッグコードなど
  - input で配列で指定したい
    - 単純な grep or 正規表現
- PHPUnit の並列実行
  - テストスイート単位で分割してマトリックスビルド
  - MySQL へアクセスする場合はコンテナの設定が必要
    - マトリックスビルドすればそれぞれに MySQL が立つので干渉はしないはず
