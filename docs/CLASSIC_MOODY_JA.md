# Classic Chrome - Classic Moody

- 対象：FUJIFILM X-T5のRAW（RAF）
- カテゴリ：Daily & Cafe / FUJIFILM
- プロファイル：Camera CLASSIC CHROME（属性方式。Lookスタブや推測したDigestは追加しない）
- XMP：presets/Daily & Cafe/FUJIFILM/Classic_Chrome_Classic_Moody.xmp

## 参考と設計

参考：KIUWFUJIの「Classic Moody」レシピ画像。
投稿URL：https://www.threads.com/@kiuwfuji__/post/Ddo3k-vnwuM
投稿本文は取得できなかったため、提供された画像の記載と写真から設計した。参考画像自体はリポジトリに含めていない。投稿者の公式XMPではない。

画像の記載：Classic Chrome、DR Auto、Highlight -1.5、Shadow -1.0、Color +3、Sharpening -2、Clarity 0、Grain Off、Color Chrome Off、Color Chrome FX Blue Off、WB Auto Ambience Priority（R -1 / B -2）。

カメラ内JPEG処理とLightroom RAW現像では、同じ数値・設定でも結果は一致しない。DR Auto、Color Chrome、Auto Ambience PriorityやWBシフトは直接換算していない。WBは固定せず、暖色と寒色の分離を弱いカラーグレーディングで近似した。

- 明るい木・テラコッタ色を残し、黄緑・青の彩度を抑える。
- ハイライトはHighlights -35 / Whites -15で柔らかくする。
- Shadows +10で暗部の階調を少し保ち、Blacks -20と低域を下げるカーブで黒を締める。Shadow -1.0の直接換算ではない。
- Vibrance +18 / Saturation +4で、Classic Chromeの落ち着きと温かい色の存在感を両立する。
- 暗部は青系215度・彩度6、明部は暖色40度・彩度6。中間調の暖色は彩度3に留める。
- GrainAmount 0、Clarity 0、Texture 0、Sharpness 25。人工的な周辺減光は加えない。

## 使用方法

XMPをLightroomの「プリセットを読み込む」で追加し、X-T5のRAFに適用する。プロファイルがCamera CLASSIC CHROMEになることを確認する。

日なたと日陰が分かれたカフェ、木製家具、レンガ、路地などに向く。参考写真の深い影には撮影時の光の方向と明暗差も影響する。均一な曇天や拡散光では同じ陰影にはならない。

露出・WBは元の写真の設定を維持する。最初に白飛びを見ながら露出を整え、必要に応じてWBを微調整する。肌がオレンジに寄る場合はWBを少し寒色側へ、影が沈みすぎる場合はBlacksを上げるかShadowsを追加する。WBシフトの数値をLightroomのTint値にそのまま転記しない。

## 検証範囲

XML構造、プロファイル属性、Name・SortName・Group、UUIDと設定の重複、INDEXとチェックサムの整合性をプログラムで検証。既存23種類のXMPの内容・UUIDは維持している。

Lightroom実機での読み込み・適用・色の一致は未検証。レシピと同一の出力を保証するものではない。
