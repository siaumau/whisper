# 🚀 Whisper 語音轉文字 Google Drive 整合設定指南

## 📋 前言
為了讓其他用戶能夠使用 Google Drive 雲端備份功能，你需要設定一個 Google Cloud 專案。設定完成後，任何人都可以直接使用你的應用程序！

## ⚡ 快速設定步驟

### 步驟 1：建立 Google Cloud 專案
1. 前往 [Google Cloud Console](https://console.cloud.google.com/)
2. 點擊「建立專案」或選擇現有專案
3. 輸入專案名稱，例如：`Whisper語音轉文字`

### 步驟 2：啟用 Google Drive API
1. 在 Google Cloud Console 中，前往「API 和服務」→「程式庫」
2. 搜尋「Google Drive API」
3. 點擊進入並按「啟用」

### 步驟 3：建立 OAuth 2.0 客戶端 ID
1. 前往「API 和服務」→「憑證」
2. 點擊「+ 建立憑證」→「OAuth 2.0 客戶端 ID」
3. 如果是首次使用，需要先設定「OAuth 同意畫面」：
   - 選擇「外部」用戶類型
   - 填寫應用程式名稱：`Whisper語音轉文字`
   - 填寫用戶支援電子郵件
   - 開發人員聯絡資訊填寫你的 email
   - 其他欄位可選填
4. 回到建立 OAuth 2.0 客戶端 ID：
   - 應用程式類型：選擇「網頁應用程式」
   - 名稱：`Whisper Web App`
   - 已授權的 JavaScript 來源：
     - `http://localhost:8000`
     - `http://127.0.0.1:8000`
     - （如果你有網域，也加入你的網域）

### 步驟 4：取得 API 金鑰
1. 在「憑證」頁面，點擊「+ 建立憑證」→「API 金鑰」
2. 複製產生的 API 金鑰
3. （建議）點擊「限制金鑰」，選擇「限制 API」，只選擇「Google Drive API」

### 步驟 5：更新程式碼
將取得的憑證更新到 `whisper_web_app.html` 檔案中：

```javascript
// 找到這段程式碼並替換
const GOOGLE_CLIENT_ID = '你的_CLIENT_ID.apps.googleusercontent.com';
const GOOGLE_API_KEY = '你的_API_金鑰';
```

## 🌐 部署給其他人使用

### 方案 1：簡單分享（推薦）
1. 完成上述設定後，直接分享 `whisper_web_app.html` 檔案
2. 用戶只需要：
   - 用瀏覽器開啟檔案
   - 輸入 OpenAI API Key
   - 點擊「連接 Google Drive」授權
   - 開始使用！

### 方案 2：架設網站
1. 將檔案上傳到網頁伺服器
2. 記得在 Google Cloud Console 的「已授權的 JavaScript 來源」加入你的網域
3. 用戶可以直接透過網址存取

## ✅ 測試步驟
1. 用瀏覽器開啟 `whisper_web_app.html`
2. 設定 OpenAI API Key
3. 點擊「連接 Google Drive」
4. 授權你的 Google 帳號
5. 進行語音轉錄測試
6. 點擊「立即備份」確認檔案能成功儲存到 Google Drive

## 🔒 安全性注意事項
- ✅ OAuth 2.0 是安全的授權機制
- ✅ 用戶只授權存取他們自己的 Google Drive
- ✅ API 金鑰只用於存取 Google Drive API
- ✅ OpenAI API Key 存在用戶本地瀏覽器，不會傳送給你

## 🎯 用戶使用流程
1. **開啟應用** → 用瀏覽器開啟 HTML 檔案
2. **設定 OpenAI** → 輸入自己的 OpenAI API Key
3. **連接雲端** → 點擊連接 Google Drive 並授權
4. **開始使用** → 語音轉錄自動備份到雲端
5. **無縫體驗** → 轉錄記錄永不遺失！

## 🆘 常見問題

**Q: 用戶看到「請先設定 Google Client ID」怎麼辦？**
A: 這表示你還沒有完成步驟 5，需要更新程式碼中的 Client ID 和 API Key。

**Q: 授權時出現「此應用程式未經驗證」？**
A: 這是正常的，點擊「進階」→「前往 Whisper語音轉文字（不安全）」即可。

**Q: 可以讓多少人使用？**
A: Google Drive API 有使用配額限制，一般個人使用綽綽有餘。如需大量使用，可能需要升級到付費方案。

**Q: 用戶的資料安全嗎？**
A: 完全安全！每個用戶只能存取自己的 Google Drive，且所有授權都是透過 Google 官方 OAuth 機制。

---

設定完成後，你就可以將 `whisper_web_app.html` 分享給任何人使用了！🎉 