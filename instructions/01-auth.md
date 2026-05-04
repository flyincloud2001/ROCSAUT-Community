# 認證系統

## 目標
實作 Gmail 邀請制登入流程，包含 Google OAuth、JWT 管理、登入狀態持久化。

## 前置條件
- 00-setup.md 已完成

## 執行步驟

### 1. 安裝認證相關依賴
```
npx expo install expo-auth-session expo-crypto expo-web-browser
```

### 2. 建立登入頁面 src/screens/LoginScreen.tsx
- 深色背景，中央顯示 ROCSAUT Community Logo（文字版）
- 標語：「ROCSAUT 社群，連結現在與未來」
- Google 登入按鈕
- 小字說明：「僅限受邀用戶加入」
- 登入失敗時顯示錯誤訊息（例如「此 Gmail 尚未受邀，請聯絡管理員」）

### 3. 實作 Google OAuth 流程
使用 expo-auth-session 實作 Google OAuth。
登入成功後將 Google ID Token 傳送至 POST /api/community/auth/token。
後端驗證 Google Token 並確認 email 在受邀名單中，回傳 JWT。
將 JWT 儲存至 expo-secure-store，key 為 "community_jwt"。

### 4. 建立 src/hooks/useAuth.ts
管理登入狀態：
- isLoggedIn：是否已登入
- user：目前登入用戶資料
- login()：執行 Google OAuth 流程
- logout()：清除 JWT 並導向登入頁

### 5. 實作登入狀態持久化
App 啟動時從 expo-secure-store 讀取 JWT。
若 JWT 存在，呼叫 GET /api/community/users/me 驗證是否仍有效。
若有效則直接進入主頁，若無效則清除並顯示登入頁。

### 6. 建立載入畫面 src/screens/SplashScreen.tsx
App 啟動時顯示，確認登入狀態後再導向對應頁面。
顯示 ROCSAUT Community Logo 和載入動畫。

## 驗證方法
1. 確認未登入時顯示登入頁
2. 確認點擊 Google 登入後可以完成 OAuth 流程
3. 確認已受邀的 Gmail 能成功登入並進入主頁
4. 確認未受邀的 Gmail 登入後顯示錯誤訊息
5. 確認關閉 App 重新開啟後登入狀態持久化
6. 確認登出後清除 JWT 並回到登入頁
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
