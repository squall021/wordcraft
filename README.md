# WordCraft Web — GitHub Pages

部署網址（Pages 啟用後）：https://squall021.github.io/wordcraft/

本 Repository 用 GitHub Actions 下載並部署官方 [WordCraft](https://github.com/storytold/wordcraft) WebAssembly 版，固定使用 `v0.5.0`。專案本身不需要 Rust 編譯環境，也沒有雲端文件儲存／協同編輯功能。

## 第一次啟用 Pages（必須由 Repo 管理員操作）

1. 登入 GitHub，開啟 <https://github.com/squall021/wordcraft/settings/pages>。
2. 在 **Build and deployment → Source** 選擇 **GitHub Actions**。
3. 前往 <https://github.com/squall021/wordcraft/actions/workflows/deploy.yml>，按 **Run workflow** → **Run workflow**。
4. 等待 Actions 部署成功後，開啟 <https://squall021.github.io/wordcraft/> 檢查文件編輯器。

若未先手動啟用 GitHub Pages，`actions/configure-pages@v5` 可能因 `Resource not accessible by integration` 而失敗；GitHub Actions 的預設 `GITHUB_TOKEN` 無法替管理員完成第一次 Pages 啟用。

## 更新與回復

- 發布檔由 GitHub Actions 自動下載官方 `wordcraft-web-0.5.0.zip` 和 `SHA256SUMS.txt`，進行 SHA256 比對後部署。
- 更新版本時修改 `.github/workflows/deploy.yml` 內的 `VERSION`。修改檔案並 Push 到 `main` 會自動觸發部署。
- 先保留可回復點；初始備份分支是 `backup/before-pages-deploy-20261011`。
- 如需回復，將 `VERSION` 及部署工作流程還原到先前可用的 Commit。

## 測試與注意事項

檢查畫面沒有停在 Loading WordCraft，並以測試用 .docx 驗證繁體中文輸入、開啟、編輯與下載功能。WordCraft 目前是 Alpha 軟體，請勿將敏感文件提交至公開儲存庫，也不應假定 GitHub Pages 會保存使用者的文件。
