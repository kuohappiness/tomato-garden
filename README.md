# 番茄園讀書社 🍅

和朋友一起專心讀書的番茄鐘網站。專心 25 分鐘，土裡就會長出一隻番茄兵；中途放棄，它會被榨成番茄醬。

**網站：** https://kuohappiness.github.io/tomato-garden/

## 功能

- 番茄鐘（切到別的 App 不會中斷）、考試範圍任務、完成度與熟練度
- 讀書社：用 6 碼邀請碼加入，看得到彼此的讀書時間和進度
- 番茄兵／珍珠收集、圖鑑、成就、每週遠征、67 彩蛋
- 空投寶物，可以送給隊友（一天一個，附一句話）
- 意外狀況：番茄兵偶爾會突變成玉米、榴槤……
- 訪客參觀：給家長看全團合計，不顯示個人資料

## 檔案

| 檔案 | 用途 |
| --- | --- |
| `index.html` | 整個網站 |
| `config.js` | Firebase 設定（公開金鑰，資料安全靠規則保護） |
| `firestore.rules` | Firestore 安全規則（改了要到 Firebase 主控台發布） |
| `SETUP.md` | 從零開始的架設步驟 |

資料存在 Firebase 專案 `tomato-garden-study`（Firestore，asia-east1）。
