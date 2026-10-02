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

## ③ Macがないので、クラウドビルドサービスでビルドする ✅ 完了（2026-09-22 初回ビルド成功）
**Codemagic**（`unmei-no-rashinban`アプリ、ワークフロー`ios-release`）でビルド・署名・TestFlight自動提出まで動作確認済み。
- リポジトリ: `https://github.com/nekopapa53ks/unmei-no-rashinban`
- 設定ファイル: `codemagic.yaml`（App Store Connect統合名`codemagic`、環境変数グループ`signing`に`CERTIFICATE_PRIVATE_KEY_B64`を保存）
- 署名は自動発行方式（`app-store-connect fetch-signing-files --create`）。証明書の秘密鍵はBase64エンコードしてCodemagicの環境変数に保存し、ビルド時にデコードしてファイル化してから使用している（Codemagicの変数入力欄に生PEMを貼ると改行が壊れるため）
- 次回以降、`main`ブランチにpushすると自動でビルド＆TestFlight提出される設定（`triggering.events: push`）

**次にやること**: App Store ConnectのTestFlightタブでビルドが処理完了（プロセッシング）するのを待ち、テスターとして自分を追加してTestFlightアプリで実機インストール・動作確認する。

## ⚠️ 本番リリース前に必ず戻すこと（2026-09-28〜、動作確認のため一時変更中）
AdMobの審査中は広告配信が制限されていて実機で全く広告が出なかったため、実装自体が正しいか切り分ける目的で
`www/index.html` の `ADMOB_USE_TEST_ADS` を `true` にして、Google公式のテスト広告ID（審査状況に関係なく必ず表示される）に一時的に切り替えている。
**本番の広告ユニットIDに戻すには、`ADMOB_USE_TEST_ADS` を `false` に書き換えてから `npx cap sync ios` → コミット→pushすること。この作業を忘れたままApp Storeに提出しないよう注意。**

## ④ ビルド前にやっておくこと
- アプリアイコン・スプラッシュ画面の用意 ✅ 完了（2026-09-30、羅針盤モチーフのブランドデザインに差し替え済み）
- スクリーンショット・アプリ説明文（App Store掲載用）✅ 完了（2026-10-02、6.5インチ・6.9インチの2サイズで入稿。素材は`app_store_screenshots/`、文章は`app_store_description.md`参照）
- プライバシーポリシーページ ✅ 完了（`privacy-policy.html`、GitHub Pagesで公開中: `https://nekopapa53ks.github.io/unmei-no-rashinban/privacy-policy.html`、App Store ConnectのApp情報にも登録済み）
- App Store Connectの「アプリのプライバシー」データ収集アンケート ✅ 完了（2026-10-01、位置情報/デバイスID/広告データ→サードパーティ広告・トラッキング目的、クラッシュ/パフォーマンスデータ→アプリの機能、で回答・公開済み）

## 今後コードを変更したとき
`www/index.html` を編集したら、下記でネイティブ側に反映してから再ビルドしてください。
```
npx cap sync ios
```
