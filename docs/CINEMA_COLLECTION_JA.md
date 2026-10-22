# X-T5 シネマ系プリセット4種類

富士フイルムのフィルムシミュレーションに対応するCamera Matchingを使用したLightroom XMP。対象はFUJIFILM X-T5のRAW（RAF）。他機種での互換性は未確認です。

| プリセット | 正式カテゴリ | Camera Matching | 方向性 |
|---|---|---|---|
| ETERNA - Cinema Daylight | Street & Travel / FUJIFILM | Camera ETERNA/Cinema | 柔らかな日中の映画調。穏やかな暖色の光、控えめな寒色の影、落ち着いた緑。旅・街・屋外の日常向け。 |
| ETERNA - Neon Afterglow | Night & Event / FUJIFILM | Camera ETERNA/Cinema | 夜の街。深い黒、シアン寄りの暗部、暖色の看板。ネオンの明部を抑え、夜の空気感を残す設計。 |
| ETERNA Bleach Bypass - Silver Horizon | Landscape / FUJIFILM | Camera ETERNA BLEACH BYPASS | 乾いた低彩度と銀色のような冷たい階調。山・岩・曇天・建築向け。ベースプロファイルのコントラストを少し和らげる。 |
| Nostalgic Neg - Cinema Reverie | Portrait / FUJIFILM | Camera NOSTALGIC Neg | 柔らかな人物の映画調。琥珀色のハイライト、落ち着いた緑、わずかに冷たい影。肌への強いオレンジ・ティールを避ける設計。 |

## 主な設計値

| 項目 | Cinema Daylight | Neon Afterglow | Silver Horizon | Cinema Reverie |
|---|---:|---:|---:|---:|
| Contrast2012 | 6 | 12 | -12 | -6 |
| Highlights2012 | -38 | -48 | -42 | -32 |
| Shadows2012 | 18 | 12 | 22 | 16 |
| Whites2012 | -16 | -22 | -18 | -12 |
| Blacks2012 | -8 | -16 | -4 | -7 |
| Vibrance | 8 | 10 | -4 | 2 |
| Saturation | -4 | -6 | -8 | -6 |
| GrainAmount | 12 | 16 | 14 | 12 |

全て弱いカラーグレーディングとカスタムトーンカーブを使用します。既存のKodak Vision3 250D、ETERNA Night Market、Nostalgic Neg Warm Portraitと同じ設定を複製せず、昼夜・低彩度・人物で調整を分けています。特定の映画やフィルムの完全再現を意図したものではありません。

## プロファイル構造

ETERNAとETERNA Bleach BypassはCameraProfile属性方式。Nostalgic Negは属性とLookスタブの二重指定で、既存XMPのLookを継承しています。

- Look Name：Camera NOSTALGIC Neg
- Look UUID：EB139FD741F44978B0F05060770DCBE0
- CameraModelRestriction：Fujifilm X-T5
- Copyright：Copyright 2022 Adobe Systems, Inc.

このLook UUIDはプリセット固有のUUIDではありません。新規4種類のプリセットUUIDはそれぞれ一意です。推測したプロファイル名・UUID・Digestは使用していません。

## 使い方と微調整

ZIPを展開し、4つのXMPをLightroomの「プリセットを読み込む」で追加してください。X-T5のRAFへ適用し、狙ったCamera Matchingがプロファイル欄に選択されることを確認してください。

露出・WB・ノイズ低減・レンズ補正はプリセットで固定しません。撮影条件に合わせて先に露出とWBを整えると選びやすくなります。アスペクト比やクロップも変更しません。

- Cinema Daylight：明部が灰色に沈む場合はWhitesを戻すか、露出を調整する。
- Neon Afterglow：暗部が沈みすぎる場合はBlacksやShadowsを上げる。高ISOのノイズ低減は写真ごとに調整する。色付き照明の光源そのものは別途WB調整が必要な場合がある。
- Silver Horizon：最も低彩度。人物中心より、風景・建築・岩肌向け。プロファイルの性格が強いため必要に応じてコントラストをさらに下げる。
- Cinema Reverie：肌が暖かすぎる場合はWBを寒色側へ微調整するか、ハイライトのグレーディング彩度を下げる。

撮影時の光・露出・被写体の色によって仕上がりは変わります。JPEGの完成見本やRAW比較画像はまだ作成していません。

## 検証

全28種類のXMLパース、INDEX・Name・SortName・Group・CameraProfileの一致、UUID・名称・設定の重複、プロファイル構造、チェックサム、既存24種類のファイル保持を検証。追加4種類のZIPは展開前提の全エントリー読み取りとXMPのバイト一致を検証しています。

Lightroom実機での読み込み・適用・仕上がりは未検証です。構造検証はLightroom実機検証を代替しません。
