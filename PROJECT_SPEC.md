# FUJIFILM X-T5 Lightroom RAW Preset Project
## プロジェクト仕様（2026年10月22日版）

このプロジェクトは、FUJIFILM X-T5で撮影したRAW写真を対象として、FUJIFILMのフィルムシミュレーションやSIGMA BF、Kodakフィルムなどの写真表現を再現する、Lightroomプリセットライブラリを構築することを目的としています。

本書は、プリセットの設計・命名・プロファイル指定・検証に関する正式仕様です。

---

# 1. 使用環境

- カメラ：FUJIFILM X-T5
- RAW形式：RAF
- 編集ソフト：Adobe Lightroom
- プリセット形式：XMP（.xmp）
- 対応データ：RAW専用
- 配布方法：原則としてダウンロード可能なXMP、複数の場合はZIP

JPEG用のプリセットを別途作成する必要はありません。

### 重要な原則

ユーザーが参考写真や現像イメージを送った場合、画像生成や写真の直接編集は行わず、Lightroomで実際に使えるXMPプリセットを作成してください。

求められている成果物は画像ではなく、**RAW現像パラメータを持つXMPファイル**です。

---

# 2. 現像スタイルの方向性

プリセットの設計では以下の表現を重視します。

- フィルム写真特有の自然な色彩と階調
- ノスタルジーと透明感の両立
- 適度に色褪せた表現
- 自然で美しい肌色
- 落ち着いたグリーン
- 深みのあるブルーとターコイズ
- 柔らかくロールオフするハイライト
- ディテールを残したシャドウ
- 適度なフィルムグレイン
- 写真の空気感や光の質を大切にする表現
- 強すぎないコントラスト
- 自然な明暗の分離

過剰なHDR表現、過剰な彩度、人工的なシャープネス、極端なカラーグレーディングは避けます。

RAWデータ本来のダイナミックレンジを生かした現像を優先してください。

## 対象スタイル

### FUJIFILM
- Classic Neg.
- Nostalgic Neg.
- Classic Chrome
- REALA ACE
- ETERNA
- PRO Neg.
- PROVIA
- その他、X-T5で利用可能なCamera Matching

### SIGMA BF
- ミニマル
- クリーン
- 淡い色彩
- 自然で美しい階調
- 洗練されたニュートラルな表現

### Kodak Film Inspired
- Portra 160
- Portra 400
- Gold 200
- Ektar 100
- UltraMax 400
- VISION3 250D

Kodak系はオリジナルフィルムの特徴を参考にした近似再現です。実際のKodakフィルムを完全に再現できると主張しないでください。

---

# 3. カテゴリの正式命名規則

**カテゴリの先頭に数字を付けることは禁止です。**

過去には `01 Portrait / FUJIFILM` のようなナンバリングを使用していましたが、カテゴリを追加しづらいため廃止しました。

カテゴリは必ず以下の構造とします。

**撮影対象 / スタイル**

現在使用しているカテゴリ：

- `Portrait / FUJIFILM`
- `Landscape / FUJIFILM`
- `Landscape / SIGMA BF`
- `Street & Travel / FUJIFILM`
- `Street & Travel / SIGMA BF`
- `Daily & Cafe / FUJIFILM`
- `Night & Event / FUJIFILM`
- `Portrait / KODAK`
- `Landscape / KODAK`
- `Street & Travel / KODAK`
- `Daily & Cafe / KODAK`

今後、必要に応じて使用できるカテゴリ例：

- `Portrait / SIGMA BF`
- `Daily & Cafe / SIGMA BF`
- `Night & Event / SIGMA BF`
- `Night & Event / KODAK`

新たな撮影ジャンルが必要な場合は拡張して構いません。ただし、既存カテゴリで対応できる場合は新設しないでください。

### XMLでの注意

XMP内部の `crs:Group` は正式カテゴリ名と完全一致させます。

アンパサンドはXML内で `&amp;` とエスケープします。

例：

表示名：`Street & Travel / KODAK`

XML内部：`Street &amp; Travel / KODAK`

大文字小文字、スペース、スラッシュも統一してください。

---

# 4. プリセット名の命名規則

次の形式で統一します。

**フィルムシミュレーションまたはスタイル - 短い英語の特徴**

例：

- `Classic Neg - Clear Nostalgia`
- `Nostalgic Neg - Alpine Glow`
- `Classic Chrome - Soft Memories`
- `Kodak Portra 400 - Soft Skin`
- `SIGMA BF - Soft Minimal`

名前から仕上がりをイメージできることを優先します。

XMPファイル名には英数字とアンダースコアのみを使用し、拡張子は `.xmp` にしてください。

各プリセットは一意のUUIDを持ち、重複する名前と設定を無意味に増やさないでください。

---

# 5. Camera Matchingの絶対ルール

このセクションは最重要事項です。

**Adobe StandardやAdobe Colorを安易に使用しないでください。**

FUJIFILM X-T5のRAWでは、原則として写真表現に適したCamera Matchingプロファイルを使用します。

過去に、Classic Neg.を指定したXMPがAdobe Standardのままになる問題が発生しました。

原因の一つは、プロファイルによって必要な指定形式が異なることです。

以下は既存の実機検証に基づくプロファイル指定方式です。各プリセットの実機適用の検証状況とは区別します。

プロファイル名、UUID、Digestを推測で作成することは禁止です。

## 形式A：CameraProfile属性

以下のフィルムシミュレーションは `rdf:Description` の `crs:CameraProfile` 属性で指定します。

| シミュレーション | 正確な内部名 |
|---|---|
| PROVIA | `Camera PROVIA/Standard` |
| Velvia | `Camera Velvia/Vivid` |
| ASTIA | `Camera ASTIA/Soft` |
| Classic Chrome | `Camera CLASSIC CHROME` |
| PRO Neg. Hi | `Camera PRO Neg Hi` |
| PRO Neg. Std | `Camera PRO Neg Std` |
| ETERNA | `Camera ETERNA/Cinema` |
| ETERNA Bleach Bypass | `Camera ETERNA BLEACH BYPASS` |

これらは属性方式を使用します。

## 形式B：CameraProfile属性＋Lookスタブ

Classic Neg.とNostalgic Neg.は、必ず**二重指定**します。

属性のみ、またはLookスタブのみでは、環境によって正しく選択状態にならないことが確認されています。

### Classic Neg.

rdf:Descriptionの属性：

`crs:CameraProfile="Camera CLASSIC Neg"`

さらに子要素として以下を追加します。

```xml
<crs:Look>
  <rdf:Description
    crs:Name="Camera CLASSIC Neg"
    crs:Amount="1"
    crs:UUID="20BE890A36DB4DBD990DD984231D15DB"
    crs:SupportsAmount="false"
    crs:SupportsMonochrome="false"
    crs:SupportsOutputReferred="false"
    crs:CameraModelRestriction="Fujifilm X-T5"
    crs:Stubbed="true">
    <crs:Group>
      <rdf:Alt>
        <rdf:li xml:lang="x-default">Profiles</rdf:li>
      </rdf:Alt>
    </crs:Group>
  </rdf:Description>
</crs:Look>
```

### Nostalgic Neg.

rdf:Descriptionの属性：

`crs:CameraProfile="Camera NOSTALGIC Neg"`

LookスタブはClassic Neg.と同形式ですが、以下を変更します。

- `crs:Name="Camera NOSTALGIC Neg"`
- `crs:UUID="EB139FD741F44978B0F05060770DCBE0"`

さらにLook内のrdf:Descriptionに以下を追加します。

`crs:Copyright="Copyright 2022 Adobe Systems, Inc."`

これらのUUIDはFUJIFILM X-T5向けです。他機種に流用してはいけません。

## 形式C：CameraProfile属性＋Digest

REALA ACEでは、必ず以下の両方を指定してください。

`crs:CameraProfile="Camera REALA ACE v2"`

`crs:CameraProfileDigest="2C135ADB4A8CE98CDF000A063A877016"`

`v2` を省略してはいけません。

## プロファイルが反映されない場合

推測で内部名の綴りを変更してはいけません。

正しい検証手順：

1. LightroomでX-T5のRAWを開く
2. Camera Matchingから対象プロファイルを手動選択
3. プロファイルを含めてプリセットを作成する
4. LightroomからXMPとして書き出す
5. Adobeが出力した実際のプロファイル指定を確認する
6. その構造を新しいプリセットへ適用する

XMLの構造検証とLightroom実機での動作検証は区別してください。

---

# 6. XMPの構造仕様

全プリセットで以下を使用します。

- `crs:Version="15.0"`
- `crs:ProcessVersion="11.0"`
- `crs:PresetType="Normal"`
- `crs:HasSettings="True"`
- `crs:Name`
- `crs:SortName`
- `crs:Group`

Name・SortName・Groupは適切なXMP要素として記載します。

RAW用の編集項目には以下を使用できます。

- Exposure2012
- Contrast2012
- Highlights2012
- Shadows2012
- Whites2012
- Blacks2012
- Texture
- Clarity2012
- Dehaze
- Vibrance
- Saturation
- ToneCurvePV2012
- HSL Adjustment
- ColorGrade
- Grain
- PostCropVignette
- Calibration

現像上必要な範囲で値を設定してください。

### RAW現像の注意

- 露出を原則固定しない
- ホワイトバランスを原則固定しない
- 写真依存の調整を過度に固定しない
- 極端なシャドウ補正を避ける
- 白飛びや黒つぶれを抑えつつ自然な階調を維持する
- プリセット適用後の微調整を許容する
- プロファイル設定は各スタイルに合わせて指定する

---

# 7. 現在のプリセットライブラリ

2026年10月22日時点で、**合計23種類のRAWプリセットを管理する構成**になっています。

全23種類の名称・設定は、INDEX.csv と presets/ 内のXMPを参照してください。更新・統合・再生成では実ファイルを読み込み、未指定の設定とUUIDを維持します。実ファイルがない場合、本書だけから全設定を復元したと扱わないでください。

## Classic Neg.コレクション（4種類）

| プリセット | カテゴリ |
|---|---|
| Classic Neg - Clear Nostalgia | Portrait / FUJIFILM |
| Classic Neg - Clear Blue | Landscape / FUJIFILM |
| Classic Neg - Qinglv Fresh | Landscape / FUJIFILM |
| Classic Neg - Trail Film 400 | Street & Travel / FUJIFILM |

全て `Camera CLASSIC Neg` を使用。

## Nostalgic Neg.コレクション（4種類）

| プリセット | カテゴリ |
|---|---|
| Nostalgic Neg - Warm Portrait | Portrait / FUJIFILM |
| Nostalgic Neg - Alpine Glow | Landscape / FUJIFILM |
| Nostalgic Neg - Sunlit Journey | Street & Travel / FUJIFILM |
| Nostalgic Neg - Cafe Memories | Daily & Cafe / FUJIFILM |

全て `Camera NOSTALGIC Neg` を使用。

## Kodak Film Inspiredコレクション（6種類）

| プリセット | カテゴリ | ベースプロファイル |
|---|---|---|
| Kodak Portra 400 - Soft Skin | Portrait / KODAK | PRO Neg Std |
| Kodak Portra 160 - Fine Pastel | Portrait / KODAK | PRO Neg Std |
| Kodak Gold 200 - Golden Days | Street & Travel / KODAK | NOSTALGIC Neg |
| Kodak Ektar 100 - Vivid Nature | Landscape / KODAK | Velvia/Vivid |
| Kodak Ultramax 400 - Everyday Color | Daily & Cafe / KODAK | PROVIA/Standard |
| Kodak Vision3 250D - Cinema Daylight | Street & Travel / KODAK | ETERNA/Cinema |

残り9種類は既存のFUJIFILM / SIGMA BF系ライブラリ由来です。正確な名称と設定値はINDEX.csvおよびpresets/内のXMPを参照してください。

Kodakスタイルであっても、技術的なベースはFUJIFILM X-T5対応のCamera Matchingプロファイルです。

---

# 8. 参考写真・作風の分析

参考画像を受け取った場合、以下を分析してください。

1. 写真のジャンルと被写体
2. 主光源と光の方向
3. 露出とコントラスト
4. ハイライトとシャドウの傾向
5. 肌色の表現
6. 空・緑・水などの色調
7. 彩度・明度・色相
8. トーンカーブ
9. フィルム粒子
10. ノスタルジー・透明感・シネマティックな印象

その結果から、適切なCamera Matchingプロファイルと現像パラメータを決定します。

---

# 9. プロファイル・カテゴリ・配布の注意点

## 問題A：Adobe Standardが適用される

原因として、CameraProfileの指定形式や内部名が一致していないケースがありました。

対策：
- 検証済みのプロファイル指定方式を使用
- Classic Neg. / Nostalgic Neg.は属性＋Lookを両方記載
- REALA ACEは属性＋Digest
- Lightroomでの実機確認を最終基準とする

## 問題B：不要なカテゴリが増える

カテゴリの表記揺れやナンバリングが原因でした。

対策：
- カテゴリ番号は廃止
- `撮影対象 / スタイル` に統一
- Kodakも撮影対象別に分類する
- XMPのGroupを完全一致させる

## 問題C：配布リンクの確認

配布するファイルの存在と読み取りを確認してからリンクを提供してください。

## 問題D：重複したプリセットが増える

過去の旧版と最新版を同時インポートしてしまう可能性があります。

対策：
- インポート前に重複を整理する
- 現行設定を維持しながらバージョン管理する
- ZIPは最新版のみを基本にする
- ユーザーに旧プリセットの整理手順を必要に応じて案内する

---

# 10. 新しいプリセットを作る際のワークフロー

ユーザーが参考写真をアップロードするか、新しいスタイルを指定した場合：

1. 写真または参考スタイルを分析
2. 適切な撮影カテゴリを決定
3. FUJIFILM / SIGMA BF / KODAKなどのスタイルを決定
4. 検証済みのCamera Matchingプロファイルを選択
5. RAW現像用のパラメータを設計
6. XMPを生成
7. XMLとして正常に解析できるか検証
8. プロファイルの指定形式を検証
9. Name・SortName・Groupを検証
10. 既存プリセットと重複していないか確認
11. 必要に応じて複数XMPをZIPにまとめる
12. ダウンロード可能なファイルとして渡す

一括更新・統合・再生成では、リポジトリ内の現行XMPをベースに指定された変更を適用してください。

明示されていない現像パラメータは、原則として維持してください。

---

# 11. 納品時のルール

プリセットを作成した場合、回答には以下を含めます。

- プリセット名
- 正式カテゴリ名
- 使用Camera Matchingプロファイル
- 写真表現の特徴
- ダウンロードリンク
- 必要な注意点

複数プリセットではZIPにまとめ、可能ならREADMEとINDEX.csvを付けます。

INDEX.csvには以下を記録します。

- Preset Name
- Category
- Camera Profile
- Description
- File Name

ファイルを作成できる場合、XMLパースとZIPの読み取りテストを行ってください。

Lightroom実機で未検証の場合は、その事実を明記してください。

**ファイル生成が不可能な場合は、ダウンロードリンクを捏造せず、ファイル名と完全なXMPソースを提示してください。**

---

# 12. 今後の拡張方針

プリセットライブラリは今後も増やしていきます。

想定する拡張：

- Kodakフィルムのバリエーション
- FUJIFILMフィルムシミュレーション別の派生スタイル
- SIGMA BFライクなミニマル系
- 夜景・イベント撮影
- 屋内・カフェ撮影
- 旅行・ストリートスナップ
- 山岳・湖・森林のランドスケープ
- 自然光ポートレート

新しいカテゴリを増やす際には、既存の分類体系との一貫性を重視してください。

スタイル名と撮影ジャンルは別概念として扱います。

例えばKodak Portraのプリセットを作る際に、単に `KODAK` というカテゴリへまとめるのではなく、ポートレート向けなら `Portrait / KODAK` に入れます。
