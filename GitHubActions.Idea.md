# GitHub Actions のアイデア

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
    - このパターンも含める？併用した方がいいかも。
  - parameters
    - labels (string[]): 定義されていたら有効。対象ラベルのリスト。
    - title (string): 定義されていたら有効。正規表現を指定する。
    - todo (bool): true なら有効。 `- [x]` のリストが全部埋まっているかチェックする。
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
- LGTM Approve
  - コメントに `LGTM` と書いたら Approve する