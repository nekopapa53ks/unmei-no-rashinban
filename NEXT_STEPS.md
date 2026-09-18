# 運命の羅針盤 iOSアプリ化 - 次にやること

このフォルダは Capacitor で作った iOSアプリのプロジェクトです（`www/` が実際のアプリ画面、`ios/` が Xcode プロジェクト）。
AdMob（バナー + リワード広告）はコード側の実装済みです。

## ① Apple Developer Program に登録する ✅ 完了
- チームID: `AN856756JR`（登録タイプ：個人、更新日 2027年9月19日）
- CodemagicでのiOS署名設定時にこのチームIDを使用する

## ② AdMob側の準備 ✅ 完了
- アプリID: `ca-app-pub-1027443362095260~1934400282`
- バナー広告ユニットID: `ca-app-pub-1027443362095260/5266693523`
- リワード広告ユニットID: `ca-app-pub-1027443362095260/1036251582`
- `ios/App/App/Info.plist`（`GADApplicationIdentifier`）と `www/index.html`（`ADMOB_IDS`）に反映済み

**⚠️ 実機でテストする前に必ずやること**
- `www/index.html` の `ADMOB_TEST_DEVICES` に、自分のテスト端末IDを追加してください
  （初回アプリ起動時、Xcodeのコンソールログに「To get test ads on this device...」という案内と一緒にIDが表示されます）
- ここに端末を登録しないまま、本番の広告ユニットIDのまま自分で広告をタップ・クリックすると、
  **無効なトラフィックとみなされAdMobアカウントが停止するリスクがあります**。テスト時は必ず端末登録を先に行ってください。

## ③ Macがないので、クラウドビルドサービスでビルドする
おすすめは **Codemagic**（Capacitor/iOSに対応、無料枠あり）
1. ~~このプロジェクトを GitHub 等のリポジトリにpushする~~ ✅ 完了（`https://github.com/nekopapa53ks/unmei-no-rashinban`）
2. https://codemagic.io/ でアカウント作成（未着手）
3. Codemagic側で「Capacitor」テンプレートを選び、iOSビルドを設定
4. Apple Developer のチーム情報（チームID `AN856756JR`）・証明書（Codemagicが自動生成も可能）を連携
5. TestFlight配信→動作確認→App Store提出、の順で進める

## ④ ビルド前にやっておくこと
- アプリアイコン・スプラッシュ画面の用意（現状はCapacitorのデフォルトのまま）
- スクリーンショット・アプリ説明文（App Store掲載用）
- プライバシーポリシーページ（広告・トラッキングを使うため必須。AdMob使用時はApp Storeの審査で必ず確認されます）

## 今後コードを変更したとき
`www/index.html` を編集したら、下記でネイティブ側に反映してから再ビルドしてください。
```
npx cap sync ios
```
