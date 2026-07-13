# 吉隆天曜 Landing Page

品牌型建案 Landing Page，架構參考「華雄音樂匯」範本，質感等級對齊、內容與素材為吉隆天曜專用。

## 檔案結構
```
index.html    ← 單一頁面（CSS/JS 內嵌）
images/       ← 所有圖（外部相對路徑，無 base64）
```

## 部署（GitHub Pages）
Settings → Pages → 選 `main` 分支、`/ (root)` 路徑即可。網址：
`https://normalsky315-jpg.github.io/sky-radianc/`

## 表單與後端
表單只留姓名 + 電話。`index.html` 內 `const ENDPOINT` 指向吉隆天曜 CRM 共用的 GAS Web App
（`gas-updates/jltx_v2_full.gs` 的 `submitPublicLead` action，位於 LONGDOM-CRM repo），
送出後直接寫進 Customer_Data，業務在 CRM 就看得到，不需要另外開一份表單試算表。

送出格式是 JSON payload（不是 urlencoded），因為要符合 CRM 共用後端的 `payload` 參數格式，
這點跟一般獨立 GAS 表單（urlencoded + `e.parameter.欄位名`）不同，是刻意的。

**GAS 有個地雷**：每次改完 GAS 程式碼，一定要「部署 → 管理部署作業 → 編輯 → 版本選新版本 → 部署」，
直接存檔不會生效。

## 已知缺口
- Hero / Architecture 區塊背景圖是官方 3D 外觀情境示意圖（738×563px 來源），不是原生高解析度建築 render，
  放大到很寬的桌機螢幕會略糊。如果有更高解析度版本，直接換 `images/jiulongtianyao-architecture-render.jpg` 即可。
- S6.5「關於吉隆建設」只用了已知的品牌文案，沒有編造得獎年份或時間軸（華雄範本有的timeline這裡故意留空），
  如果有實際得獎紀錄想放上去，可以比照 music-plaza 的 `.tl` timeline 元件加回來。
- 素材有限，S3 三大主張與 S6 生活風景牆共用同一批 7 張真實照片（大寮商圈4張＋學校3張），
  沒有額外的「純生活情境」照片可以區分兩區塊。

## 素材處理
照片皆已壓縮：長邊 ≤900px、JPEG quality 80-90，檔名皆為看得懂的英文 slug。
