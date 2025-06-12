# 🔧 Google Drive 連接問題診斷指南

## ❌ 錯誤：「Google API 尚未初始化」

### 🔍 可能原因與解決方案

#### 1. **Client ID 和 API Key 未設定**
**檢查方法：**
- 開啟 `whisper_web_app.html`
- 查看是否還有以下內容：
```javascript
const GOOGLE_CLIENT_ID = '1234567890-abcdefghijklmnopqrstuvwxyz123456.apps.googleusercontent.com';
const GOOGLE_API_KEY = 'AIzaSyABC123def456GHI789jkl012MNO345pqr';
```

**解決方案：**
1. 按照 `Google_Drive_設定指南.md` 建立 Google Cloud 專案
2. 取得真實的 Client ID 和 API Key
3. 替換程式碼中的佔位符

#### 2. **網路連線問題**
**檢查方法：**
- 開啟瀏覽器開發者工具 (F12)
- 查看 Console 是否有載入錯誤
- 檢查 Network 標籤是否有失敗的請求

**解決方案：**
- 確保網路連線正常
- 檢查防火牆是否阻擋 Google API 請求
- 嘗試刷新頁面

#### 3. **瀏覽器相容性問題**
**檢查方法：**
- 嘗試不同瀏覽器 (Chrome, Firefox, Edge)
- 檢查瀏覽器是否為最新版本

**解決方案：**
- 使用 Chrome 瀏覽器 (推薦)
- 更新瀏覽器到最新版本
- 清除瀏覽器快取

#### 4. **檔案載入順序問題**
**檢查方法：**
- 確認 HTML 檔案包含以下腳本載入：
```html
<script src="https://apis.google.com/js/api.js"></script>
<script src="https://accounts.google.com/gsi/client"></script>
```

**解決方案：**
- 確保腳本標籤在 `<head>` 區域
- 檢查網址是否正確

## 🛠️ 即時診斷步驟

### 步驟 1: 開啟開發者工具
1. 按 `F12` 或右鍵點擊頁面選擇「檢查」
2. 切換到 `Console` 標籤

### 步驟 2: 檢查載入狀態
輸入以下指令並按 Enter：
```javascript
console.log('gapi:', typeof gapi);
console.log('GOOGLE_CLIENT_ID:', GOOGLE_CLIENT_ID);
console.log('isGoogleAuthInitialized:', isGoogleAuthInitialized);
```

### 步驟 3: 解讀結果
- **gapi: "undefined"** → Google API 腳本未載入
- **GOOGLE_CLIENT_ID 包含 "1234567890"** → Client ID 未設定
- **isGoogleAuthInitialized: false** → 初始化失敗

### 步驟 4: 手動重試初始化
在 Console 輸入：
```javascript
initializeGoogleAPI();
```

## 📋 設定檢查清單

- [ ] ✅ Google Cloud 專案已建立
- [ ] ✅ Google Drive API 已啟用  
- [ ] ✅ OAuth 2.0 客戶端 ID 已建立
- [ ] ✅ API 金鑰已建立
- [ ] ✅ 程式碼中的 Client ID 和 API Key 已更新
- [ ] ✅ 瀏覽器網路連線正常
- [ ] ✅ 使用支援的瀏覽器 (Chrome 推薦)

## 🚨 常見錯誤訊息

### "Google API 腳本未載入"
- **原因：** 網路問題或腳本載入失敗
- **解決：** 檢查網路連線，重新整理頁面

### "請先設定正確的 Google Client ID"
- **原因：** Client ID 尚未替換為真實值
- **解決：** 完成 Google Cloud 設定

### "Google API 載入逾時"
- **原因：** 網路速度慢或 Google 服務暫時不可用
- **解決：** 稍後再試，或檢查網路連線

### "Google API 客戶端初始化失敗"
- **原因：** API Key 或 Client ID 不正確
- **解決：** 檢查 Google Cloud Console 中的憑證設定

## 🔄 快速修復方案

如果問題持續存在，請嘗試以下快速修復：

1. **重新整理頁面** (Ctrl+F5)
2. **清除瀏覽器快取**
3. **嘗試無痕/私人瀏覽模式**
4. **檢查是否有廣告攔截器干擾**
5. **暫時關閉瀏覽器擴充功能**

## 📞 尋求協助

如果以上方法都無法解決問題，請提供：
1. 瀏覽器類型和版本
2. Console 中的錯誤訊息截圖
3. 網路連線狀態
4. 是否完成 Google Cloud 設定

這樣可以更快找到解決方案！ 