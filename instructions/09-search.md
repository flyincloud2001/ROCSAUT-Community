# 搜尋功能

## 目標
實作全站搜尋，支援搜尋發文和成員。

## 前置條件
- 08-notification.md 已完成

## 執行步驟

### 1. 建立探索頁 src/screens/ExploreScreen.tsx
此頁面是底部 Tab Bar 的第二個 tab。

頂部搜尋欄：點擊後進入搜尋模式。

未搜尋時顯示：
- 熱門分類列表（呼叫 GET /api/community/categories）
- 熱門發文（按讚數最高的 10 篇）
- 活躍用戶（本週發文或回覆最多的 5 位）

### 2. 建立搜尋結果頁 src/screens/SearchResultScreen.tsx
搜尋時呼叫 GET /api/community/search?q=關鍵字。

結果分兩個 Tab 顯示：
- 發文：顯示符合關鍵字的發文列表（使用 PostCard 元件）
- 成員：顯示符合關鍵字的用戶列表

關鍵字在結果中高亮顯示。
搜尋歷史儲存在本地，最多保留 10 筆，可個別刪除或清除全部。

### 3. 實作分類瀏覽頁 src/screens/CategoryScreen.tsx
點擊分類後顯示該分類下的所有發文。
支援排序切換（熱門、最新、最高讚）。

## 驗證方法
1. 確認探索頁正確顯示熱門分類和發文
2. 確認搜尋結果正確顯示
3. 確認關鍵字高亮正確運作
4. 確認搜尋歷史正確儲存和顯示
5. 確認分類瀏覽正確過濾發文
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
