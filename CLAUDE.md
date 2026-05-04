# ROCSAUT Community — Claude Code 執行手冊

## 這是什麼
ROCSAUT Community iPhone App，使用 React Native + Expo 開發。
這是大社團平台，開放給所有持有 Gmail 且受邀的人加入，包含現役社員、校友、以及對 ROCSAUT 有興趣的 UofT 台灣學生。
後端初期複用 https://rocsaut-club-platform.vercel.app，所有 Community API 使用 /api/community/ 前綴。

## 執行前必讀（按順序）
1. context/overview.md — 專案概覽、定位、帳號資訊、技術棧
2. context/backend-api.md — 後端 API 完整文件
3. context/architecture.md — App 架構決策
4. context/design-system.md — 設計系統、色彩、字體

## 執行前提
只有當所有 instructions/ 檔案的內容都不再是「待補充」時，才開始執行開發。若發現任何檔案仍為「待補充」，停止執行並回報哪些檔案尚未完成。

## 執行範圍
執行 instructions/ 內所有檔案，按編號從小到大順序執行。

## 執行規則
1. 每個功能完成後必須執行該檔案內指定的驗證步驟
2. 遇到錯誤自主修復，不要停下來等待指示
3. 所有程式碼變更必須 commit 並 push 至 flyincloud2001/ROCSAUT-Community
4. 每個功能完成並驗證通過後才進入下一個檔案
5. 不得修改 context/ 內的任何檔案
