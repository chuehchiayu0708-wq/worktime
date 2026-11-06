# 打卡網頁

單一 `index.html`，不需要 build。沒填 Firebase 設定時會自動用「本機模式」（存在瀏覽器），可先試用。

## 一、設定 Firebase（約 5 分鐘）
1. 到 https://console.firebase.google.com 建立專案
2. **Build → Authentication → Sign-in method** → 啟用 **Google**
3. **Build → Firestore Database** → 建立資料庫（正式模式即可）
4. Firestore 的 **規則** 分頁 → 貼上 `firestore.rules` 的內容 → 發布
5. **專案設定 → 你的應用程式 → 新增網頁應用程式（</>）**，複製 `firebaseConfig`
6. 貼到 `index.html` 最上方的 `firebaseConfig`（apiKey、authDomain、projectId、appId）

## 二、部署到 Vercel
- 方法 A（推薦）：把資料夾推到 GitHub → vercel.com → Add New Project → 匯入 → Deploy（Framework 選 Other，不需任何指令）
- 方法 B：資料夾內執行 `npx vercel --prod`

## 三、最後一步（很重要）
Firebase → Authentication → **Settings → Authorized domains** → 加入你的 Vercel 網域（例如 `xxx.vercel.app`），否則 Google 登入會失敗。

## 使用
- 先在「我的工作」新增每份工作（名稱、時薪、顏色）
- 上班前點選工作，再按大按鈕：綠色「上班」/ 紅色「下班」
- 上班中不能切換工作，要先下班
- 上方切換月份，看總工時、出勤天數、總預估薪資，以及每份工作各自的工時與薪資
- 修改時薪會連同該工作的歷史紀錄一起重新計算
- 點 🗑 可刪除錯誤紀錄
- 手機瀏覽器可「加入主畫面」當 App 用
