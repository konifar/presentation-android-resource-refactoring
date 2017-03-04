<!--
Android resources are in values directory.
styles, colors, dimens, strings.
In fact, we can define them in any xml files.
So I think it's better to divide some files. Like this.
-->

# res/values

## <color>
- colors_base.xml
- colors.xml
## <dimen>
- dimens_base.xml
- dimens.xml
## <string>
- strings.xml
- paths.xml
- fonts.xml
## <style>
- themes.xml
- styles_base.xml
- styles_messages.xml
- styles_settings.xml
- ...


# Problems
- Direct written colors & dimens
- Many styles
-

- 当時の状況
  - 直書きの色、大きさ
  - 統一感のない文字サイズ
  -

- 修正の順番
  - コンフリクトを避ける
  - リソースの依存関係
  - リリースはステップbyステップ
  - 心持ち
    - 何かあったら速攻で直すぞ
    - インスタバグ
  - アイコン


- colors.xml
  - Why did I modify colors at first?
  - colors.xml & colors_palette.xml
  -

- colorsの修正
  - colors.xmlの指針
    - ファイル分割規則
    - 命名規則
  - 新しいファイルを作る
  - greyscaleから
  - 直書き箇所の修正
  - colors.xmlの修正

- dimensの修正
  - dimensの指針
    - ファイル分割規則
    - 命名規則
  - 直書き箇所の修正

- stylesからthemesを剥がす
  - themes.xml
  - バージョンに依存するのでちゃんとPRに記載
  - PRテンプレート
  - 背景の統一

- styleの指針
  - 先にstyleを揃えてから適用していくスタイル
- ツールバーの統一
- ボーダーの統一
- テキストの統一
- ボタンの統一
  - ボタンの影を取った話
  - width、heightもstyleに入れるべきか？
- リストの統一
  - リファクタリングしたくなったら？するんだよ！
- アイコンの統一
  - 命名規則
    - 形をそのまま入れる
  - DataBinding BindingAdapterの話
  - tintの話
  - スタイルの利用
  - ローディング中の表示
- styleが揃ってきたら画面ごとにPRを出す

- インスタバグの話
