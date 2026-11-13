# 英文逐句默寫 App：Google Drive 一鍵備份設定

網站：https://stacy0908.github.io/english-practice/

## 設定一次
1. 使用要放備份的 Google 帳號登入 https://console.cloud.google.com/ ，選擇或建立專案。
2. 前往 https://console.cloud.google.com/apis/library/drive.googleapis.com 啟用 Google Drive API。
3. 前往 https://console.cloud.google.com/auth/overview 完成 Google Auth Platform 的 Branding 與 Audience。個人使用可以設定為 External / Testing，並將要使用的 Gmail 加入 Test users。
4. 前往 https://console.cloud.google.com/auth/clients ，建立 OAuth Client ID；Application type 選 **Web application**。
5. **Authorized JavaScript origins** 加入 `https://stacy0908.github.io`（只有網域，不要加 /english-practice/）；這個瀏覽器 token flow 不需要 Redirect URI。
6. 複製 OAuth Client ID（格式：數字-字串.apps.googleusercontent.com），不要提供或上傳 Client secret。
7. 開啟 App 的「④ 一鍵儲存 Google Drive」→ 展開「第一次使用：Google 雲端授權設定」→ 貼入 Client ID →「儲存授權設定」。
8. 點選「直接存到 Google Drive」，於 Google 的授權視窗選擇備份所用帳號並核准 `drive.file` 權限。僅授權你自己建立及信任的 Cloud 專案。
9. 必須看到 App 顯示「Google Drive 已新增／更新備份」才代表成功。可使用資料夾連結核對。

## 備份規則
- 每次按「直接存到 Google Drive」會上傳當前所有文章、中文、默寫與批改紀錄，檔名為「目前文章名稱_當天日期.json」。
- 同名、同日的 App 建立檔案會更新，而不是一直增加重複檔案。
- 第一次會嘗試使用先前建立的備份資料夾。若 `drive.file` 無權存取，會在 Google Drive 根目錄建立「英文默寫練習 App 自動備份」並明確顯示。你可以之後在 Google Drive 手動移動此 App 建立的資料夾。
- App 不會持續自動同步：每次要更新雲端備份，請按一次「直接存到 Google Drive」。
- 「從 Google Drive 還原最新備份」會合併相同文章 ID；更新時間較新的文章優先。還原前建議先下載一份本機 JSON。
- 網頁是公開的，但 Google Drive 存檔仍由你的 Google 授權控制，App 的 OAuth access token 只留在頁面執行期間，不會寫進 GitHub。
- 目前不需要 Google Drive 全部檔案權限；使用 Google 建議的有限 `drive.file`。
- 請勿將個人 JSON 備份提交到公開 GitHub repository。

官方說明：
- https://developers.google.com/identity/oauth2/web/guides/use-token-model
- https://developers.google.com/workspace/drive/api/guides/api-specific-auth
- https://developers.google.com/workspace/drive/api/guides/manage-uploads
