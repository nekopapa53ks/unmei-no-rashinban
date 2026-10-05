# App Review 返信用テキスト（Guideline 2.1 - Information Needed 対応）

## 使い方
1. 下の「英語本文」をそのままコピーして、App Store Connect の「App Review に返信」に貼り付ける
2. 同じ本文を「App Review に関する情報」の「メモ」欄にも貼り付けて保存する（Appleから指示あり）
3. 実機での画面録画を返信に添付する（録画のやり方は一番下）
4. 返信後、ページ上部の「App Review に再提出」を押す（新しいビルドは不要）

---

## 英語本文（コピペ用）

Hello App Review Team,

Thank you for your review. Below is the information you requested.

1. Screen recording
A recording captured on a physical iPhone (latest iOS), starting from app launch, is attached. The app has no account registration, login or account deletion, no user-generated content, and no paid content or In-App Purchases, so those flows do not exist in the app.

2. Purpose and target audience
"運命の羅針盤" (Compass of Destiny) is a free, entertainment-only fortune-telling app (Japanese UI, age rating 13+). It combines tarot (22 Major Arcana cards), a simplified Four Pillars of Destiny (Bazi) calculation based on the user's birth date, and biorhythm to offer (a) quick daily readings (today's fortune, omikuji, lucky outfit, lucky meals, event-day fortune, compatibility) and (b) a deeper 3-card tarot reading (past / present / future) with a combined conclusion. It gives users a fun daily ritual and a prompt for reflecting on their decisions. An in-app disclaimer states that results are for entertainment purposes only.

3. How to access the main features (no login or sample files needed)
a) Launch the app. iOS may show the App Tracking Transparency prompt (for ads); either choice works.
b) On the opening screen, tap "占いを始める" (Start).
c) Select any birth date (year / month / day dropdowns) and a gender, then tap "占いメニューへ →" (Go to fortune menu). The partner section is optional.
d) Quick reading: tap "今日の運勢" (Today's fortune) -> tap the face-down card to flip it -> tap "結果を見る" (See result). The other menu buttons (開運おみくじ, 開運コーデ, 今日の開運ごはん, イベント参加の開運) work the same way. "簡易相性" (compatibility) requires the optional partner birth date.
e) Full reading: tap "真剣タロット占い" at the bottom of the menu -> choose a topic under "何を占いますか？" -> tap "占いを始める" -> tap each of the three cards -> tap the buttons that appear in order ("タロット鑑定結果を見る", "四柱推命の鑑定を見る", "バイオリズムの鑑定を見る", "総合鑑定を見る") to reach the final conclusion.
Note: a rewarded video ad (Google AdMob) may appear when tapping "結果を見る", "タロット鑑定結果を見る" and "総合鑑定を見る". If no ad is available, the content is shown immediately.

4. External services
- Google AdMob (Google Mobile Ads SDK): banner and rewarded video ads. Apple's App Tracking Transparency framework is used for the ad tracking prompt.
- iOS built-in speech synthesis for the optional read-aloud button.
- No backend servers, no authentication services, no payment processors, no AI services and no external data providers. All fortune calculations run on the device.

5. Regional differences
None. The app functions the same in all regions (the UI is Japanese only). Only the ads served by AdMob may vary by region.

6. Regulated industry / protected material
The app is not in a regulated industry. The tarot card illustrations are the classic Rider-Waite-Smith Major Arcana artwork (1909), which is in the public domain.

Thank you.

---

## 実機での画面録画のやり方（iPhone）
1. 設定 > コントロールセンター で「画面収録」が追加されているか確認（なければ追加）
2. ホーム画面からコントロールセンターを開き、画面収録ボタンを押す（3秒カウント後に開始）
3. **アプリのアイコンをタップして起動するところから**録画する（Appleの指定：起動から始めること）
4. 以下の流れを順番に操作する（1〜3分程度）
   - オープニング →「占いを始める」
   - 生年月日・性別を選択 →「占いメニューへ」
   - 「今日の運勢」→ カードをタップ →「結果を見る」→ 結果表示
   - 「占いメニューに戻る」→「真剣タロット占い」→ テーマ選択 →「占いを始める」
   - 3枚のカードをタップ →「タロット鑑定結果を見る」→「四柱推命の鑑定を見る」→「バイオリズムの鑑定を見る」→「総合鑑定を見る」
5. 画面収録ボタン（赤い表示）をもう一度押して停止 → 写真アプリに動画が保存される
6. App Store Connect の返信画面に、その動画を添付する
