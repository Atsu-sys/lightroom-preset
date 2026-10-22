# FUJIFILM X-T5 Lightroom RAW Presets

富士フイルム（FUJIFILM）のカメラ向けに、フィルムシミュレーションをベースとして調整したAdobe Lightroom用プリセット集です。Camera Matchingプロファイルを使用し、色彩・階調・粒子感などを撮影対象やスタイルに合わせて整えています。

現在収録している24種類のXMPプリセットは、FUJIFILM X-T5で撮影したRAW（RAF）専用です。他機種での互換性は未確認です。FUJIFILM系のほか、同じCamera Matchingを土台にしたSIGMA BF風・Kodakフィルム風のスタイルを含み、11カテゴリで管理しています。

## フォルダー構成

```text
presets/
  Daily & Cafe/
    FUJIFILM/         3種類
    KODAK/            1種類
  Landscape/
    FUJIFILM/         5種類
    KODAK/            1種類
    SIGMA BF/         1種類
  Night & Event/
    FUJIFILM/         2種類
  Portrait/
    FUJIFILM/         4種類
    KODAK/            2種類
  Street & Travel/
    FUJIFILM/         2種類
    KODAK/            2種類
    SIGMA BF/         1種類
docs/
  README_JA.txt        受領時の説明書
INDEX.csv             名称・カテゴリ・プロファイル・説明・相対パス
SHA256SUMS.txt        各XMPのSHA-256と相対パス
PROJECT_SPEC.md       設計・プロファイル・検証の仕様
AGENTS.md             リポジトリの作業ルール
```

## 使用方法

`presets/` 内の必要なカテゴリのXMPを、Lightroomの「プリセットを読み込む」で選択してください。
X-T5のRAFに適用し、プロファイル欄で意図したCamera Matchingが選択されることを確認してください。
フォルダーは管理用です。Lightroom上のカテゴリはXMP内部のGroupによって決まります。
旧版を読み込み済みの場合は、必要に応じて重複を整理してください。
Kodak系はFUJIFILM Camera Matchingをベースにした近似表現です。

## 整理・検証記録（2026-10-22）

- 23種類のXMPを撮影対象／スタイル別に移動しました。
- 全23ファイルのSHA-256が受領時のSHA256SUMS.txtと一致し、移動後も一致することを確認しました。XMPの内容・ファイル名・UUIDは維持しています。
- 全XMPのXMLパース、UUIDの一意性、Name・SortName・Group・CameraProfileと受領時INDEXの一致を確認しました。
- Classic Neg.／Nostalgic Neg.のCameraProfile属性とLook内の名前・UUIDの一致を確認しました。
- INDEX.csvに説明と相対パスを記録し、SHA256SUMS.txtを新しい配置に合わせました。
- 今回の作業ではZIPは作成していません。Lightroom実機での適用は未検証です。

`docs/README_JA.txt` は受領時の説明を保持したものです。現在の配置・今回の検証範囲はこのREADMEを参照してください。

## 追加プリセット（2026-10-22）

- **Classic Chrome - Classic Moody**（Daily & Cafe / FUJIFILM）
- Camera Matching：`Camera CLASSIC CHROME`
- 暖かいテラコッタ色の光、わずかに青い暗部、深い黒。粒子は加えず、シャープネスを控えめにしています。
- 露出・ホワイトバランスは固定しません。木製家具、カフェ、日なたと日陰が分かれる場面に向いています。
- カメラ内レシピの直接変換ではなく、参考画像から設計した近似表現です。フラットな光を参考写真と同じ強い陰影に変えるものではありません。
- 新規XMPのXML・プロファイル・名称・カテゴリ・重複・チェックサムを検証。Lightroom実機での適用・見た目は未検証です。
- 設計と使用上の注意は `docs/CLASSIC_MOODY_JA.md` を参照してください。既存23種類は変更していません。
