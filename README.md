# 高速OCR 照明器具紹介記号チェッカー

反応が遅い・読み取りできない問題を改善した版です。

## 改善内容

- カメラ画像全体ではなく、型番枠だけをOCR
- 画像を小さくして高速化
- 白黒補正・コントラスト補正
- OCR対象文字を英数字とハイフンに限定
- 1行型番としてOCR
- 型番リストとの辞書照合
- OCR誤読を補正
  - O → 0
  - I / L → 1
  - S → 5
- リアルタイム時は連続一致で確定し、誤表示を減らす

## 登録済み

- NNFB84665 → A1
- NNFB84695 → A2
- XLX450NENP LE9 → A-12

## Netlify

1. ZIPを解凍
2. GitHubにアップロード、またはNetlifyにアップロード
3. Build command: `npm run build`
4. Publish directory: `dist`

## Vercel

1. GitHubにアップロード
2. VercelでImport
3. Build command: `npm run build`
4. Output directory: `dist`

## 使い方

1. HTTPSのURLをスマホで開く
2. カメラ起動
3. 型番を緑枠いっぱいに入れる
4. リアルタイム開始
5. A1/A2を表示

## 調整

`index.html` 内の以下を調整できます。

- `OCR_INTERVAL_MS = 1200`
  - 小さいほど速いが重い
  - 1500〜2000にすると安定

- `REQUIRED_STABLE = 2`
  - 2回連続一致で確定
  - 誤表示が多いなら3

- `TARGET_WIDTH = 900`
  - 大きいほど精度寄り
  - 小さいほど速度寄り
