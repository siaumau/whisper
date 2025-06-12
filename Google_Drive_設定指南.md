# 🚀 Whisper 語音轉文字 Google Drive 整合設定指南

## 📋 前言
根據 [Google Identity 官方文檔](https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid?hl=zh-tw)，我們提供最簡化的設定流程，讓其他用戶能夠輕鬆使用 Google Drive 雲端備份功能！

## ⚡ 5分鐘快速設定

### 步驟 1：開啟 Google API Console
1. 前往 [Google API Console](https://console.developers.google.com/)
2. **建立新專案**或選擇現有專案
3. 專案名稱建議：`Whisper語音轉文字`

### 步驟 2：啟用 Google Drive API
1. 在左側選單點擊「**程式庫**」
2. 搜尋「**Google Drive API**」
3. 點擊進入並按「**啟用**」

### 步驟 3：設定 OAuth 同意畫面（首次必做）
1. 左側選單點擊「**OAuth 同意畫面**」
2. 選擇「**外部**」→ 建立
3. **基本資訊**填寫：
   - 應用程式名稱：`Whisper 語音轉文字`
   - 用戶支援電子郵件：你的 Gmail
   - 開發人員聯絡資訊：你的 Gmail
4. 其他欄位跳過，點擊「**儲存並繼續**」→「**儲存並繼續**」→「**返回控制台**」

### 步驟 4：建立 OAuth 2.0 客戶端 ID
1. 左側選單點擊「**憑證**」
2. 點擊「**+ 建立憑證**」→「**OAuth 2.0 客戶端 ID**」
3. 應用程式類型：選擇「**網頁應用程式**」
4. 名稱：`Whisper Web App`
5. **已授權的 JavaScript 來源**，依序新增：
   ```
   http://localhost
   http://localhost:3000
   http://localhost:8000
   http://127.0.0.1
   file://
   ```
   > 💡 這樣設定後可以在任何本機環境使用

### 步驟 5：複製 Client ID
1. 建立完成後，會顯示客戶端 ID
2. **複製**這個 Client ID（格式像：`1234567890-abc123def456.apps.googleusercontent.com`）

### 步驟 6：更新程式碼（只需要 Client ID！）
根據 Google 官方文檔，我們**不需要 API Key**，只需要 Client ID：

1. 開啟 `whisper_web_app.html`
2. 找到這行：
```javascript
const GOOGLE_CLIENT_ID = '1234567890-abcdefghijklmnopqrstuvwxyz123456.apps.googleusercontent.com';
```
3. **替換為你的真實 Client ID**

### 步驟 7：移除 API Key 依賴
由於使用 Google Identity Services，我們不需要 API Key，移除相關檢查：

```javascript
// 移除這行，因為不需要 API Key
// const GOOGLE_API_KEY = 'AIzaSyABC123def456GHI789jkl012MNO345pqr';
```

## 🌐 部署方式（超簡單）

### 方案 1：本機使用（推薦）
1. 設定好 Client ID 後
2. 雙擊開啟 `whisper_web_app.html`
3. 用戶直接在瀏覽器中使用！

### 方案 2：網站部署
1. 上傳到任何網頁伺服器
2. 在 Google Console 添加你的網域到「已授權的 JavaScript 來源」
3. 用戶透過網址存取

## ✅ 一分鐘測試
1. **開啟檔案**：用瀏覽器開啟 `whisper_web_app.html`
2. **輸入 OpenAI Key**：設定你的 OpenAI API Key
3. **連接雲端**：點擊「🔑 連接 Google Drive」
4. **Google 授權**：會彈出 Google 登入視窗，選擇帳號授權
5. **開始轉錄**：語音轉錄會自動分區顯示
6. **備份測試**：點擊「💾 立即備份」，檔案會儲存到你的 Google Drive

## 🔒 安全性保證
- ✅ **OAuth 2.0 標準**：使用 Google 官方安全授權機制
- ✅ **個人權限**：每個用戶只能存取自己的 Google Drive
- ✅ **無需 API Key**：根據官方文檔，只需要 Client ID
- ✅ **本地儲存**：OpenAI API Key 只存在用戶本地瀏覽器

## 🎯 用戶使用流程
1. **開啟應用** → 用瀏覽器開啟 HTML 檔案
2. **設定 OpenAI** → 輸入自己的 OpenAI API Key
3. **連接雲端** → 點擊連接 Google Drive 並授權
4. **開始使用** → 語音轉錄自動備份到雲端
5. **無縫體驗** → 轉錄記錄永不遺失！

## 🆘 常見問題

**Q: 看到「請先設定正確的 Google Client ID」怎麼辦？**
A: 請完成步驟 6，將程式碼中的 `你的_CLIENT_ID.apps.googleusercontent.com` 替換為你的真實 Client ID。

**Q: 授權時出現「此應用程式未經驗證」？**
A: 正常現象！點擊「進階」→「前往 Whisper 語音轉文字（不安全）」即可使用。

**Q: 為什麼不需要 API Key？**
A: 根據 [Google Identity 官方文檔](https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid?hl=zh-tw)，使用 Google Identity Services 只需要 Client ID，比傳統方式更簡單！

**Q: 本機開啟檔案可以連接 Google Drive 嗎？**
A: 可以！我們已經設定好 `file://` 協議支援，直接雙擊 HTML 檔案就能使用。

**Q: 可以給多少人使用？**
A: Google Drive API 免費配額很充裕，個人使用完全夠用。商業用途可考慮升級方案。

---

設定完成後，你就可以將 `whisper_web_app.html` 分享給任何人使用了！🎉 