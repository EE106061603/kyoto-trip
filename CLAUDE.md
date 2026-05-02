# 京都 9 天行程網頁 (Kyoto Trip Itinerary)

## 專案概述

這是一個個人京都旅遊行程網頁，8/7-8/15 與朋友群 9 天 8 夜的旅行。
目的是讓使用者和朋友可以一起查看完整行程。

## 旅行基本資訊

- **日期**：2026/08/07 - 08/15（9 天 8 夜）
- **同行者**：朋友群
- **氣候**：京都 8 月酷暑 30-37°C，行程設計需考慮避暑
- **住宿三段**：
  - Day 1-4：京都東九条（100-5 Higashikujō Matsudachō, Minami Ward）
  - Day 5-7：Hotel Legasta Kyoto Shirakawa Sanjo（東山三條）
  - Day 8：Hotel Odysis Suites Osaka Airport（臨空城，KIX 一站）
- **航班**：
  - 去程 8/7 15:37 桃園 → 18:27 關西
  - 回程 8/15 07:55 樂桃從 KIX T2 起飛（必須 5:10 接駁巴士到 T2）

## 日期對照（重要！）

```
8/7  五  Day 1  抵達日
8/8  六  Day 2  東山祇園+先斗町
8/9  日  Day 3  嵐山深度路線
8/10 一  Day 4  伏見+宇治+AEON
8/11 二  Day 5  鞍馬貴船+搬家
8/12 三  Day 6  銀閣寺+哲學之道
8/13 四  Day 7  上賀茂+二條城
8/14 五  Day 8  瑠璃光院+移動大阪
8/15 六  Day 9  樂桃 0755 起飛
```

⚠️ 之前曾誤判 8/11 為星期一，導致以為三栄（週一公休）會衝突。已確認 8/11 是星期二，三栄營業中。

## 檔案結構

```
kyoto-trip/
├── index.html           # 主頁：9 天行程（傳統格式，左到右排版）
├── map.html             # 互動式 Google Maps 版本（左行程右地圖）
├── CLAUDE.md            # 此檔案（給 Claude Code 看的）
└── README.md            # GitHub repo 說明
```

## 技術棧

- **單一 HTML 檔案**：純 HTML + CSS + Vanilla JS，無框架
- **字體**：Google Fonts（Shippori Mincho 日式 serif + Noto Sans TC + Klee One）
- **設計風格**：京都和風，配色為朱紅 (`#c8463c`) + 米白 (`#f5f0e6`) + 墨色 (`#2a2520`)
- **互動地圖**：Google Maps JavaScript API + Places API (New)
- **部署**：GitHub Pages，網址 `https://EE106061603.github.io/kyoto-trip/`

## Google Maps API Key

API key 已設定以下安全限制：

- HTTP 參照網址限制：`https://EE106061603.github.io/*`
- API 限制：只允許 Maps JavaScript API + Places API (New)

⚠️ **注意**：因為有網站限制，本機開啟 `file://` 無法載入地圖，必須部署到 GitHub Pages 才能看。
本機測試需暫時把網站限制改為「無」（測試完務必改回）。

map.html 內 `YOUR_GOOGLE_MAPS_API_KEY` 需替換為實際 key（commit 前要檢查不要把 key 塞到 public repo，建議用環境變數或在 GitHub Pages 上以 query string 注入）。

## 行程設計原則

1. **避暑優先**：8 月京都極熱，景點排早上 6-10 點 + 黃昏，正午安排室內/咖啡廳/商店
2. **餐廳挑台灣難吃到的**：鱧魚（夏季限定）、川床料理、京都老派咖啡、和菓子
3. **景點不重複**：補完朋友 chicTrip 排好的部分時務必避免重複
4. **尊重已預訂**：朋友已排好的部分（Day 1-4 大致完整）保留不動

## 已知問題與待辦

### 🔴 高優先

- [x] ~~8/11 三栄鱧魚店週一公休衝突~~ — **已澄清，8/11 是星期二，營業中**
- [ ] 瑠璃光院 8/14 預約：需要事前網路預約 + ¥2000 入山費，必須確認當日有開放
- [ ] 必訂位餐廳清單：
  - 三栄（鱧魚）— 8/11 二
  - ひろ文（川床流水素麵）— 8/11 二
  - 京都肉のひろ重 — 8/12 三
  - 富乃丞 三條 — 8/13 四
  - One Calbi 臨空城店 — 8/14 19:00

### 🟡 可優化

- [ ] 加上「已預約」勾選功能（目前是純展示）
- [ ] 加上預算追蹤（每人花費）
- [ ] 加上拍照打卡記錄
- [ ] 整合 Google Calendar 自動建立提醒

### 🟢 未來想做

- [ ] 多人即時協作（目前是單機 HTML，朋友改動不會同步）
  - 評估方案：Firebase Realtime Database 或 Supabase
- [ ] 餐廳預約狀態追蹤面板
- [ ] 行程結束後變成回憶相簿模式

## 設計重點與決策記錄

### 為什麼用 Google Maps API 而不是 Leaflet？

使用者要求最完整的互動體驗，且已申請 API key 並做好安全限制。

### 為什麼是單一 HTML 而不是 React/Vue？

- 單純行程展示，不需要框架
- 部署簡單（GitHub Pages 直接放）
- 朋友打開不需要任何環境

### 為什麼朋友的部分要保留不動？

朋友用 chicTrip APP 排好 Day 1-4，已經分工查資料、確認時間。
我（Claude）只負責補完空的部分（Day 5-9）和修正時間錯亂處。

## 與 Claude 對話歷史摘要

之前在 Claude.ai 對話中完成的事：

1. 分析朋友的 chicTrip 行程，找出 Day 5-9 缺漏
2. 推薦並加入新景點/餐廳（避免與朋友的重複）
3. 製作美觀的傳統 HTML 行程頁（`index.html`）
4. 製作 Google Maps 互動地圖版（`map.html`）
5. 加入 Day 4 AEON 蓋章免費明信片活動
6. 修正 Day 9 樂桃 0755 起飛 + 5:10 接駁巴士細節
7. 加入 Day 8 One Calbi 燒肉吃到飽（飯店旁邊走 2-3 分鐘）

## 開發指令

```bash
# 本機預覽（必須用 server，不能直接 open file://）
python3 -m http.server 8000
# 開啟 http://localhost:8000/

# 部署到 GitHub Pages
git add .
git commit -m "Update itinerary"
git push origin main
# 1-2 分鐘後 https://EE106061603.github.io/kyoto-trip/ 會更新
```

## 個人偏好

- 我是台灣使用者，習慣繁體中文
- 介面文字以中文為主，景點/餐廳名稱可保留日文原名
- 設計偏好：和風、簡約、京都氛圍（朱紅+米白）
- 不喜歡：過度花俏的動畫、AI 風 emoji 過多
- 利用 git 控管專案 https://github.com/EE106061603/kyoto-trip
