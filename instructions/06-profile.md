# 個人頁面

## 目標
實作個人頁面、帳號等級顯示、貢獻紀錄、已收藏列表、其他用戶的公開頁面。

## 前置條件
- 05-vote.md 已完成

## 執行步驟

### 1. 建立個人頁面 src/screens/ProfileScreen.tsx
頂部區塊：
- 頭像（可點擊更換）
- 顯示名稱
- 身份標籤（社員、校友屆別、一般用戶）
- 帳號等級徽章（Lv1 到 Lv5，根據 context/design-system.md 色彩）
- 目前點數和距離下一等級所需點數的進度條
- Bio 簡介
- 加入日期

中間 Tab 切換：
- 我的發文：呼叫 GET /api/community/posts?userId=me
- 我的回覆：顯示曾回覆過的發文列表
- 已收藏：從本地儲存讀取收藏的發文

底部：
- 登出按鈕
- 設定按鈕（導向設定頁）

### 2. 建立編輯個人資料頁 src/screens/EditProfileScreen.tsx
可編輯欄位：
- 頭像（使用 expo-image-picker，上傳至 Supabase Storage）
- 顯示名稱
- Bio 簡介
- LinkedIn URL（選填）
- Instagram handle（選填）
儲存後呼叫 PATCH /api/community/users/me。

### 3. 建立他人公開頁面 src/screens/UserProfileScreen.tsx
顯示指定用戶的公開資料：
- 頭像、顯示名稱、身份標籤、帳號等級
- Bio 簡介
- 該用戶的發文列表
- 若用戶有填 LinkedIn 或 Instagram，顯示對應連結按鈕
- 不顯示私人資訊（email 等）

### 4. 實作帳號等級計算
每次載入個人頁面時呼叫 GET /api/community/users/me 取得最新點數。
根據 context/architecture.md 的等級門檻計算目前等級。
顯示等級進度條：目前點數 / 下一等級所需點數。

### 5. 建立設定頁 src/screens/SettingsScreen.tsx
- 通知設定（開關各類推播通知）
- 語言設定（繁體中文 / 英文）
- 隱私設定（是否允許其他人查看個人頁面）
- 帳號刪除（需輸入確認文字）

## 驗證方法
1. 確認個人頁面正確顯示所有資訊
2. 確認帳號等級和進度條正確計算
3. 確認編輯個人資料後正確更新
4. 確認頭像上傳後正確顯示
5. 確認他人公開頁面正確顯示
6. 確認 Tab 切換正確顯示對應內容
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
