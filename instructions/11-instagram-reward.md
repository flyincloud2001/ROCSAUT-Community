# Instagram 獎勵機制

## 目標
實作每月 Instagram 獎勵評選系統，激勵校友積極回覆。

## 前置條件
- 10-category.md 已完成

## 執行步驟

### 1. 資料庫統計邏輯
後端需要能夠統計每位校友用戶當月回覆的被按讚總數。
在 GET /api/community/admin/reward 回傳當月校友排行。
只統計身份為 alumni 的用戶。
只統計當月（每月 1 日重置）的回覆被按讚數。

### 2. 在通知系統中加入獎勵通知
管理員在 Admin 介面公布得獎名單後，系統自動推播通知給得獎者。
通知文字：「恭喜！你獲得本月 ROCSAUT Instagram [Story/貼文] 曝光獎勵！請聯絡管理員。」

### 3. 獎勵說明頁 src/screens/RewardInfoScreen.tsx
在個人頁面的設定或說明區塊中可以進入此頁面。
說明 Instagram 獎勵機制：
- 每月統計校友回覆被按讚總數
- 排名前 5 獲得 Story 曝光
- 排名第 1 獲得貼文曝光
- 只有校友身份的用戶才參與排行

## 驗證方法
1. 確認後端正確統計當月校友回覆按讚數
2. 確認得獎通知正確推播
3. 確認獎勵說明頁內容正確顯示
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
