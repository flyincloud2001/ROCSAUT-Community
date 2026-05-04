# 按讚與倒讚

## 目標
實作發文和留言的按讚、倒讚、收藏功能，並同步更新帳號等級點數。

## 前置條件
- 04-comment.md 已完成

## 執行步驟

### 1. 建立按讚元件 src/components/VoteButtons.tsx
- 上讚按鈕（向上箭頭）+ 數字
- 倒讚按鈕（向下箭頭）+ 數字
- 已按讚時上讚按鈕顯示綠色，已倒讚時倒讚按鈕顯示紅色
- 點擊已按讚的按鈕取消按讚
- 同一則內容不能同時按讚和倒讚
- 呼叫 POST /api/community/posts/:id/vote 或 POST /api/community/comments/:id/vote

### 2. 實作收藏功能
每篇發文右上角顯示書籤圖示。
點擊後收藏至個人頁面的「已收藏」列表。
收藏狀態儲存在本地（expo-secure-store）。

### 3. 實作樂觀更新
按讚後立即更新 UI，不等待 API 回應。
若 API 失敗則回滾 UI 並顯示錯誤提示。

## 驗證方法
1. 確認按讚後數字正確增加，按鈕變色
2. 確認再次點擊取消按讚，數字減少
3. 確認不能同時按讚和倒讚
4. 確認收藏後出現在個人頁面的已收藏列表
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
