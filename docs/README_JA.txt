FUJIFILM X-T5 RAW (RAF) — Lightroom XMP プリセット統合版
更新日: 2026-10-22
プリセット数: 23種類
カテゴリ数: 11種類

使い方：
1. ZIPを展開します。
2. Lightroomの「プリセット」→「プリセットを読み込む」でXMPを選択します。
3. X-T5のRAW（.RAF）写真で使用してください。
4. プロファイル欄が意図したCamera Matchingに切り替わることを確認してください。

命名方針：
- カテゴリは「撮影対象 / スタイル」、番号は付けない
- KODAKも「Portrait / KODAK」など撮影対象別
- Kodak系はKodak純正プロファイルではなくFUJIFILM Camera Matchingを使用
- XMPファイル名は半角英数字とアンダースコアのみ

Camera Matching指定：
- Classic Neg. / Nostalgic Neg.：CameraProfile属性＋Lookスタブ（二重指定）
- その他：検証済みCameraProfile属性
- X-T5専用の確認済みLook UUIDを使用（推測したUUIDやDigestは使用しない）

ファイル形式：
- crs:Version=15.0 / crs:ProcessVersion=11.0
- Name、SortName、Groupを設定
- 露出とホワイトバランスはプリセットで固定しない
- 既存23種類の現像パラメータとプリセットUUIDを保持

カテゴリ別件数：
- Daily & Cafe / FUJIFILM: 2
- Daily & Cafe / KODAK: 1
- Landscape / FUJIFILM: 5
- Landscape / KODAK: 1
- Landscape / SIGMA BF: 1
- Night & Event / FUJIFILM: 2
- Portrait / FUJIFILM: 4
- Portrait / KODAK: 2
- Street & Travel / FUJIFILM: 2
- Street & Travel / KODAK: 2
- Street & Travel / SIGMA BF: 1

検証範囲：
全XMPのXMLパース、プロファイル指定方式、UUID、カテゴリ、ファイル名、
設定パラメータ保持、ZIPの整合性をプログラムで検証しました。
Lightroomモバイル／デスクトップでの実機適用は未検証です。

既存の旧版を読み込んでいる場合、カテゴリ重複・プリセット重複を防ぐため、
旧版を整理してからインポートしてください。

INDEX.csvにプリセット名・カテゴリ・Camera Matching・ファイル名が記載されています。
