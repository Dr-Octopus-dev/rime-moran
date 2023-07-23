# 魔改自然碼 Rime 方案

配方： ℞ ksqsf/rime-moran

![截圖](etc/screenshot-bql.png)

個人自用魔改自然碼的 Rime 方案，簡稱「魔然」。

⚠️ 方案目前已達到「適合日常使用」的狀態，但仍有一定量的瑕疵、需要長期的優化。歡迎[試用](#免安裝試用方法)並參與建設！

本方案的主要特徵：

+ 基於自然碼雙拼和輔碼
+ 收 2 萬不同簡繁漢字，優先支持傳承字（繁體字）
+ 支持三種輸入模式，用戶可依自己的愛好和心情隨意選用
  - 主模式（魔然）：固頂字詞 + 整句輔助，輕鬆寫意、高效精準，適合作爲主方案使用
  - 整句模式（魔然·整句）：無固頂字詞，適合新手和輕度輔碼用戶使用
  - 字詞模式（魔然·字詞）：完全固定的碼表輸入模式，適合少部分追求速度、精準度的高級用戶使用
+ 重新設計固頂一二級簡碼與簡詞
+ 內置 20 萬大詞庫供用戶選用

其他自定義功能：

+ 分號次選
  - 字詞模式還支持引號三選
+ 自定義短語
  - `moran.custom.txt`
+ 簡繁快速切換
  - Ctrl+S (S 意爲 simplified)
+ 反查
  - `` ` `` 爲萬能通配鍵
  - 虎碼反查用 `` ` `` 引導
+ 繪文字（Emoji）支持
  - 用 Ctrl+E 開關
+ Unicode 編碼和區位顯示
  - 用 Ctrl+U 開關
+ 時間快速查詢與輸入
  - 日期 orq
  - 星期 oxq
  - 節氣 ojq
  - 週數 ow
+ 大寫數字/金額轉換
  - 用 `S` 引導，如輸入 `S123`
+ 日語和英語詞庫（默認禁用）

## 輔助碼輸入方式修改

設一個字的音碼爲 YY，輔碼爲 XX，則該字可以使用以下方式輸入：

- Y     只輸入聲母
- YY    不輸入輔碼
- YYX   只輸入第一個輔碼
- YYXXo 全碼
- YYXX  全碼，但優先級低於同碼的詞語

增加 o 主要是爲了避讓字詞重碼，如版本 bjbf != 半 bjbfo。注：固頂詞庫中仍然可能有四碼單字。

詞語輔助碼的輸入方式與原版自然碼不同（這也是爲什麼這個方案叫做「魔改自然碼」）。原版自然碼中，所有輔碼均在詞語輸入完畢後給出。例如：

| 他們   | 她們   | 它們   |
|--------|--------|--------|
| ta'mfr | ta'mfn | ta'mfb |

注意到輔助碼與輔助的字其實是分離的，r n b 並不作用在「們」這個字上。魔然中字和它的輔助碼不會分開，也就是：

| 他們   | 她們   | 它們   |
|--------|--------|--------|
| tar'mf | tan'mf | tab'mf |

魔然方案依賴於 Rime 根據詞庫切分輸入消歧義。這種設計的優勢在於用戶可以在打詞的過程中也加強對單字編碼的條件反射，從而提高未來的單字輸入能力和組詞能力。相比之下，傳統的自然碼詞輔方案只能加強這個詞本身的編碼的條反。

實際體驗表明這種方式造成的干擾不多，是可行的輸入方案，並且比純音碼輸入方式更舒適。但是 Rime 僅對三碼切分支持較好（每個字最多只有一個輔助碼），如果一個字需要輸入兩個輔助碼，就必須手動使用 `'` 切分輸入，否則會被 Rime 切分成兩個音節。

## 注意事項

由于雙拼輔碼的特殊性，Rime 在首次部署時會耗費大量時間和內存，這是正常現象。請在部署時保證設備上空閒內存多于 3 GB。

## 免安裝試用方法

使用 [My RIME](https://my-rime.vercel.app/) 可以在瀏覽器中部署並試用魔然方案。

1. 打開 [My RIME](https://my-rime.vercel.app/)
2. 點擊 `Micro Plum` 按鈕
3. （默認即此，無須特別操作）選擇 Source 爲 GitHub
4. 選擇 Mode 爲 Plum，在 Target 中輸入 `ksqsf/rime-moran`
5. Schemas 中依次添加 `moran` （魔然）, `moran_fixed` （魔然·字詞）, `moran_sentence` （魔然·整句）
5. 點擊 Install

部署完成後，即可在文本框中使用魔然方案。

## 鳴謝

+ 自然碼原始碼表來自 [rime-zrm](https://github.com/bigshans/rime-zrm)
+ 部分功能設計得到[小鶴音形](https://flypy.com)的啓發
+ Lua 腳本和繪文字來自 [秃版虎碼 Rime 方案](https://tiger-code.com/)
+ 皮膚收集自 [ssnhd/Rime](https://github.com/ssnhd/rime/)、[KyleBing/rime-wubi86-jidian](https://github.com/KyleBing/rime-wubi86-jidian/) 和秃版虎码方案
+ [清華大學開放中文詞庫](http://thuocl.thunlp.org/)

大部分詞庫收集自其他 Rime 方案，出處均在相應詞典文件頭標出。

本方案的製作得到了铁圈、䑝曻、la sfuki'e的幫助，在此表示感謝。
