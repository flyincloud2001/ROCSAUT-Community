# 專案初始化

## 目標
建立 React Native + Expo 專案基礎架構，設定所有必要的依賴和環境變數。

## 執行步驟

### 1. 初始化 Expo 專案
在 C:\Users\flyin\OneDrive\桌面\開源代碼\社團社群app 目錄下執行：
```
npx create-expo-app . --template blank-typescript
```

### 2. 安裝所有依賴
```
npx expo install expo-router expo-secure-store expo-image-picker expo-notifications expo-localization
npm install @react-navigation/native @react-navigation/bottom-tabs
npm install axios react-query @tanstack/react-query
npm install i18n-js
npm install date-fns
```

### 3. 設定 app.json
替換 app.json 內容：
```json
{
  "expo": {
    "name": "ROCSAUT Community",
    "slug": "rocsaut-community",
    "version": "1.0.0",
    "orientation": "portrait",
    "scheme": "rocsaut-community",
    "userInterfaceStyle": "dark",
    "ios": {
      "supportsTablet": false,
      "bundleIdentifier": "ca.rocsaut.community"
    },
    "plugins": [
      "expo-router",
      "expo-secure-store",
      [
        "expo-notifications",
        {
          "color": "#E31E24"
        }
      ]
    ]
  }
}
```

### 4. 建立環境變數檔案 .env.local
```
API_BASE_URL=https://rocsaut-club-platform.vercel.app
```

### 5. 建立基本資料夾結構
```
src/
  components/        # 共用元件
  screens/           # 頁面元件
  hooks/             # 自訂 hooks
  lib/               # 工具函式、API client
  constants/         # 常數、design tokens
  i18n/              # 多語言
  types/             # TypeScript 型別定義
```

### 6. 建立 src/constants/theme.ts
根據 context/design-system.md 的色彩和間距系統建立完整的 design token 檔案。

### 7. 建立 src/types/index.ts
根據 context/backend-api.md 的資料型別建立完整的 TypeScript 型別定義。

### 8. 建立 src/lib/api.ts
建立 axios instance，設定 base URL 和 JWT Bearer Token 攔截器。
Token 從 expo-secure-store 讀取，key 為 "community_jwt"。
若 API 回傳 401，清除 token 並導向登入頁。

### 9. 建立 src/i18n/ 多語言檔案
支援繁體中文和英文，跟隨裝置系統語言。
建立 src/i18n/zh.ts 和 src/i18n/en.ts，初始內容包含 App 名稱和基本 UI 文字。

## 驗證方法
1. 執行 npx expo start，確認專案能正常啟動
2. 確認 src/ 資料夾結構完整
3. 確認 TypeScript 編譯無錯誤
完成後 commit 並 push 至 flyincloud2001/ROCSAUT-Community。
