# 管理介面

## 目標
實作管理員專用的後台功能，包含邀請成員、審核違規、執行月度獎勵評選。

## 前置條件
- 11-instagram-reward.md 已完成

## 執行步驟

### 1. 管理員入口
個人頁面底部，只有 role 為 admin 的用戶才能看到「管理員後台」按鈕。
點擊後進入管理介面。

### 2. 建立管理介面主頁 src/screens/admin/AdminScreen.tsx
選單項目：
- 邀請成員
- 成員管理
- 違規內容審核
- 月度獎勵評選
- 分類管理

### 3. 邀請成員頁 src/screens/admin/InviteScreen.tsx
輸入 Gmail 地址和身份（現役社員、校友、一般用戶）。
校友需額外填入畢業屆別。
點擊邀請後呼叫 POST /api/community/auth/invite。
顯示已邀請的 email 列表。

### 4. 成員管理頁 src/screens/admin/MemberManageScreen.tsx
顯示所有用戶列表，可搜尋。
點進任一用戶可：
- 修改身份標籤（社員、校友、一般用戶）
- 修改畢業屆別（校友限定）
- 停權（banned）：停權後用戶無法登入
- 解除停權

### 5. 違規內容審核頁 src/screens/admin/ModerationScreen.tsx
顯示被用戶檢舉的發文和留言。
每則檢舉顯示：被檢舉內容、檢舉原因、檢舉者。
管理員可選擇：忽略檢舉、刪除內容、停權發文者。

### 6. 月度獎勵評選頁 src/screens/admin/RewardScreen.tsx
呼叫 GET /api/community/admin/reward 顯示當月校友回覆按讚排行。
顯示排名、用戶名、被按讚總數。
確認得獎名單後點擊「公布得獎名單」，系統推播通知給排名前 5 的校友。

### 7. 分類管理頁 src/screens/admin/CategoryManageScreen.tsx
顯示所有分類列表。
可新增、編輯、刪除分類。
可設定某分類為「只有管理員可發文」。

## 驗證方法
1. 確認只有管理員能看到管理員後台入口
2. 確認邀請成員後對方能成功登入
3. 確認停權後用戶無法登入
4. 確認月度排行正確顯示
5. 確認公布得獎後推播通知正確送出
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
