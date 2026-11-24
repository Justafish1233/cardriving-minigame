# 酒駕？別上路 — 公路安全小遊戲

純 HTML、CSS、JavaScript 的手機版小遊戲。GitHub Pages 可直接託管 `index.html`。

## 啟用跨裝置共用排行榜

排行榜需要一個可讓匿名訪客讀取與新增成績的資料庫。此專案使用 Supabase；尚未設定時，簽名成績只保存在目前瀏覽器的 localStorage，頁面會清楚標示為「本機排行榜」。

1. 建立一個 Supabase 專案。
2. 在 Supabase SQL Editor 執行 `leaderboard.sql`。
3. 從 Project Settings → API 複製 Project URL 與 anon/publishable key，填入 `leaderboard-config.js` 的 `url` 與 `anonKey`。
4. 將 `index.html`、`leaderboard-config.js`、`leaderboard.sql` 一起部署。

前端只使用可公開的 anon/publishable key。資料表的 RLS policy 僅允許任何訪客讀取排行榜、新增成績，不允許修改或刪除既有資料。玩家每次簽名後會新增一筆紀錄，排行榜依存活時間排序，金幣數作為平手排序。
