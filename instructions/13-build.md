# 打包上架

## 目標
將 App 打包並上架至 Apple App Store。

## 前置條件
- 所有 instructions/ 檔案已完成並驗證通過
- Apple Developer 帳號已申請（developer.apple.com，$99/年）
- App Store Connect 已建立 App 條目
- Expo 帳號已登入

## 執行步驟

### 1. 確認 app.json 設定正確
- name：ROCSAUT Community
- bundleIdentifier：ca.rocsaut.community
- version：1.0.0

### 2. 執行 EAS Build 打包
```
eas build --platform ios --profile production
```

### 3. 等待 EAS 雲端打包完成

### 4. 執行 EAS Submit 上傳至 App Store Connect
```
eas submit --platform ios
```

### 5. 登入 App Store Connect，填寫以下資料
- App 描述（中英文）
- 截圖（至少一張）
- 隱私政策 URL
- 年齡分級問卷

### 6. 提交 App Review

## 驗證方法
1. 確認 EAS Build 打包成功，沒有任何錯誤
2. 確認 App 成功上傳至 App Store Connect
3. 確認 App Store Connect 上的資料填寫完整
4. 確認成功提交 App Review
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
