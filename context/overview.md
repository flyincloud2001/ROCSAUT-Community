# 專案概覽

## 定位
ROCSAUT Community 是大社團平台，定位為 ROCSAUT 社群的開放論壇。
有別於小社團平台（club-platform-app）只服務現役社員，本平台開放給所有受邀的 Gmail 用戶，包含現役社員、校友、以及對 ROCSAUT 有興趣的 UofT 台灣學生。
功能形式參考 Reddit 和 X（Twitter），以發文、回覆、按讚為核心互動方式。

## 帳號資訊
- GitHub repo：flyincloud2001/ROCSAUT-Community
- Super Admin email：flyincloud2001@gmail.com
- 本地路徑：C:\Users\flyin\OneDrive\桌面\開源代碼\社團社群app

## 技術棧
- Framework：React Native + Expo
- 語言：TypeScript
- 導航：Expo Router
- 樣式：StyleSheet + 統一 design token
- 認證：Google OAuth（Gmail 邀請制）+ JWT Bearer Token
- 後端：Next.js API Routes（初期複用小社團平台後端，後續獨立）
- 資料庫：Supabase（PostgreSQL）
- 推播通知：Expo Push Notifications
- 打包：EAS Build
- 部署：App Store（iOS）

## 與小社團平台的關係
- 兩者是完全獨立的 App，不共用程式碼
- 初期共用後端 API，長期目標是獨立後端
- 用戶帳號系統獨立，小社團平台的社員不會自動成為大社團平台的成員
- 小社團平台 repo：flyincloud2001/club-platform-app
- 小社團平台後端 repo：flyincloud2001/club-platform

## 平台成員來源
- 現役 ROCSAUT 社員
- ROCSAUT 校友
- 對 ROCSAUT 有興趣的 UofT 台灣學生
- 所有人都需要持有 Gmail 並受邀才能加入

## 開發時間線
- 現在到 2026 年 10 月：完成平台開發
- 2026 年 10 月：開發者赴台灣服義務役
- 2027 年後：回加拿大後繼續維護和擴展
