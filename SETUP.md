# 番茄園讀書社・架設步驟（約 15 分鐘）

整個網站有四個檔案：

| 檔案 | 用途 |
| --- | --- |
| `index.html` | 網站本體（不用改） |
| `config.js` | 貼上你的 Firebase 設定（第 2 步） |
| `firestore.rules` | 資料庫安全規則（第 4 步貼到 Firebase） |
| `SETUP.md` | 就是這份說明 |

還沒設定 Firebase 之前，打開 `index.html` 會進入**示範模式**：可以先玩看看，但資料只存在那支手機。

---

## 1. 建立 Firebase 專案

1. 用你的 Google 帳號到 <https://console.firebase.google.com>
2. 按「建立專案」（或「新增專案」），名稱例如 `tomato-garden`
3. Google Analytics 可以關掉，按「建立專案」

## 2. 新增網頁應用程式，拿到設定

1. 專案首頁按 `</>`（網頁）圖示
2. 暱稱填 `番茄園`，**不用**勾 Firebase Hosting，按「註冊應用程式」
3. 畫面會出現一段 `const firebaseConfig = { ... }`
4. 打開 `config.js`，把 `window.FIREBASE_CONFIG = null;` 改成：

```js
window.FIREBASE_CONFIG = {
  apiKey: "……",
  authDomain: "……firebaseapp.com",
  projectId: "……",
  storageBucket: "……",
  messagingSenderId: "……",
  appId: "……"
};
```

（就是把 Firebase 給你的大括號整段貼過來。這組 apiKey 本來就會公開在網頁上，安全靠第 4 步的規則。）

## 3. 開啟 Google 登入

1. 左邊選單「建構 → Authentication」→「開始使用」
2. 「登入方式」分頁 →「Google」→ 啟用 →「專案支援電子郵件」選你的信箱 → 儲存

網站只讓 Google 帳號使用（規則會擋掉其他帳號），這樣團長在「成員管理」看得到每個人的 Google 信箱，也能封鎖不認識的帳號。
以前開過的「電子郵件/密碼」和「匿名」可以留著不動：舊帳號登入後，網站會請他們綁定 Google 帳號，紀錄會保留。

## 4. 建立資料庫並貼上規則

1. 左邊選單「建構 → Firestore Database」→「建立資料庫」
2. 位置選 `asia-east1 (Taiwan)`
3. 選「以正式版模式啟動」→ 建立
4. 上方「規則」分頁：把裡面的內容全部刪掉，貼上 `firestore.rules` 的整份內容 →「發布」

## 5. 放到 GitHub Pages

1. 在 GitHub 新增一個 repository，例如 `tomato-garden`（Public）
2. 「Add file → Upload files」，上傳 `index.html` 和 `config.js`（`firestore.rules`、`SETUP.md` 也可以一起放，不影響）
3. Repository 的「Settings → Pages」：Source 選「Deploy from a branch」，Branch 選 `main`、資料夾 `/ (root)` → Save
4. 等 1–2 分鐘，網址會是 `https://你的帳號.github.io/tomato-garden/`

## 6. 把網址加進 Firebase 授權網域

1. Firebase「Authentication → 設定 → 已授權網域」
2. 「新增網域」：`你的帳號.github.io`（只要網域，不用 `https://` 也不用 `/tomato-garden`）

少了這一步，登入會出現「unauthorized-domain」。

## 7. 開始使用

1. 用手機的 **Safari 或 Chrome** 打開網址 → 用 Google 登入
2. 建立群組（例如「302 番茄小隊」），考試日期填 12/2
3. 到「任務」頁 →「整批貼上」→「載入『國一第二次段考』衝刺表（80 項）」
4. 到「朋友」頁 → 複製邀請連結，用 LINE 傳給好朋友
5. iPhone：Safari 分享 →「加入主畫面」；Android：Chrome 選單 →「加到主畫面」，就像 App 一樣

---

## 常見問題

**從 LINE 點連結登入失敗？**
LINE、FB 內建的瀏覽器常會擋 Google 登入。請按右上角「⋯」→「用瀏覽器開啟」。

**孩子沒有 Google 帳號，或學校帳號登入被擋？**
可以用家長的 Google 帳號登入。為了擋掉一直換瀏覽器註冊的假帳號，現在只開放 Google 帳號。

**以前用「免帳號登入」或 Email 的人怎麼辦？**
照原本的方式打開網站，會看到「請綁定 Google 帳號」，按下去選一個 Google 帳號就好，番茄兵和讀書紀錄都會保留。
如果那個 Google 帳號以前已經登入過番茄園，就不能再綁定，只能改登入那個帳號（免帳號的紀錄不會帶過去）。

**團長怎麼封鎖人？**
「設定 → 讀書社 → 成員管理」裡，每個人名字下面有他的 Google 信箱（只有團長看得到）。按「封鎖」會把他移出，而且同一個帳號不能再加入；在「已封鎖」可以解除。

**手機鎖螢幕，計時會停嗎？**
不會。計時是用開始時間計算的，回到網頁就會自動「收成」番茄。但鎖螢幕時不會響鈴，所以讀書時讓網頁開著比較好（網頁會盡量讓螢幕不自動關閉）。

**要錢嗎？**
Firebase 免費方案（Spark）的額度，幾個同學一起用遠遠用不完，也不需要綁信用卡。

**誰看得到資料？**
只有輸入同一個邀請碼的群組成員看得到彼此的讀書時間、完成度和熟練度。不知道邀請碼的人看不到。

**之後要改內容？**
任務、群組名稱、考試日期都在網站裡面改。下次段考只要在「設定」改考試日期，再到「任務」頁貼新範圍。
