# 推播通知

## 目標
實作推播通知系統，在有人回覆、按讚、提及時通知用戶。

## 前置條件
- 07-member-directory.md 已完成

## 執行步驟

### 1. 設定 Expo Push Notifications
App 啟動後請求推播通知權限。
取得 Expo Push Token 後上傳至後端，儲存在用戶資料中。
呼叫 PATCH /api/community/users/me，帶入 expoPushToken 欄位。

### 2. 建立通知中心頁 src/screens/NotificationsScreen.tsx
此頁面是底部 Tab Bar 的第三個 tab。

通知類型與顯示文字：
- comment：「[用戶名] 回覆了你的發文：[發文標題前 20 字]」
- vote：「你的發文獲得 [N] 個讚」（累計，不是每次都通知）
- best：「你的回覆被標記為最佳回覆！」
- mention：「[用戶名] 在發文中提及了你」
- reward：「恭喜！你獲得本月 Instagram [Story/貼文] 曝光獎勵！」

每則通知：
- 左側圖示（依類型不同）
- 通知文字
- 時間戳記
- 未讀通知背景略亮
- 點擊後導向對應發文或個人頁面，並標記為已讀

頂部「全部標記已讀」按鈕。

### 3. 實作未讀數量徽章
底部 Tab Bar 的通知 tab 顯示未讀通知數量徽章。
App 進入前景時自動更新未讀數量。

### 4. 實作點擊通知跳轉
收到推播通知時，點擊通知直接跳轉至對應發文詳細頁。
App 在背景和前景狀態下都需要正確處理跳轉。

## 驗證方法
1. 確認 App 啟動後請求通知權限
2. 確認通知中心正確顯示所有通知
3. 確認未讀通知有視覺區別
4. 確認點擊通知能跳轉至對應頁面
5. 確認未讀數量徽章正確顯示
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
