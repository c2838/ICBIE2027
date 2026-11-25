# AIOT DIC4｜居家環境與外出建議代理人

國立中興大學資工系「物聯網應用與資料分析」課程的 IEEE 會議格式提案。

**英文題名**：An IoT Agent for Home and Outing Recommendations Using Indoor Sensing and Weather Forecasts

**作者**：KAO CHUN HSUAN、ZHONG YI XIAN、Xiao Cheng-Yun

## 專題概要

本提案規劃整合 ESP32 室內溫濕度量測、中央氣象署預報與使用者回饋，提供家電使用、外出安排及室內外曬衣建議。系統會記錄建議所依據的資料來源與時間，並在偵測到持續變化時詢問使用者是否有操作。提案包含系統架構、領域規則、事件監測偽程式碼及預定評估方法。

## 檔案結構

| 路徑 | 用途 |
| --- | --- |
| [`ICEIB2027-IEEE/main.tex`](./ICEIB2027-IEEE/main.tex) | 新版 LaTeX 主檔，負責套件設定與載入各子檔 |
| [`ICEIB2027-IEEE/sections/`](./ICEIB2027-IEEE/sections/) | 摘要、正文和結論 |
| [`ICEIB2027-IEEE/figures/`](./ICEIB2027-IEEE/figures/) | TikZ 圖，包含事件時間線 |
| [`ICEIB2027-IEEE/tables/`](./ICEIB2027-IEEE/tables/) | 七欄文獻摘要表、研究問題與評估對照表及其他表格 |
| [`ICEIB2027-IEEE/references.bib`](./ICEIB2027-IEEE/references.bib) | 由 IEEEtran BibTeX 樣式排版的參考文獻 |
| [`.mcp.json`](./.mcp.json) | Overleaf MCP 伺服器啟動設定 |

拆檔前的 `AIOT_DIC4.tex` 與 `AIOT_DIC4.pdf` 可從 Git 歷史查閱。

## 編譯

- **本機**。進入 `ICEIB2027-IEEE/`，執行 `tectonic main.tex`，產生 `main.pdf`。
- **Overleaf**。將 `ICEIB2027-IEEE/` 內的檔案與子目錄放在 Overleaf 專案根目錄，將 `main.tex` 設為主文件，編譯器選擇 `pdfLaTeX`，再按 **Recompile**。主檔的章節、圖表與文獻路徑都以這個目錄結構為準。

## 在 Antigravity 安裝 Overleaf MCP

準備 Node.js 20 以上、Chrome 系列瀏覽器，以及有專案存取權的 Overleaf 帳號。可用 `node --version` 確認 Node.js 版本。

1. 在 Antigravity IDE 的指令面板選擇 **Antigravity IDE: Manage MCP Servers**，再點 **View raw config**。本次驗證使用的全域設定檔是 `~/.gemini/config/mcp_config.json`。
2. 將下方的 `overleaf` 項目合併到既有的 `mcpServers`。設定檔若為空，可貼上完整 JSON。

   ```json
   {
     "mcpServers": {
       "overleaf": {
         "command": "npx",
         "args": ["-y", "overleaf-web-mcp", "serve"]
       }
     }
   }
   ```

   如果 IDE 顯示找不到 `npx`，在 macOS 或 Linux 的終端機執行 `command -v npx`，用它回傳的絕對路徑替換 `command` 的值。本次在 macOS 使用 Volta 管理的 `npx`。

3. 儲存設定後回到 **Manage MCPs**，按 **Refresh**，確認清單列出 `overleaf` 和可用工具。
4. 在終端機執行 `npx -y overleaf-web-mcp login`，在開啟的專用瀏覽器視窗完成 Overleaf 登入。
5. 在 Antigravity 呼叫 `auth_status`。回傳 `authenticated: true` 表示 MCP 能使用已登入的 Overleaf 工作階段。

[Overleaf Web MCP 安裝文件](https://mhmdaskari.github.io/overleaf-web-mcp/install/)

## Overleaf MCP 同步與驗證

1. 在已載入 `overleaf` 伺服器的 MCP 客戶端執行 `auth_status`，確認 Overleaf 登入有效。
2. 用 `plan_sync` 比對本機 `ICEIB2027-IEEE/` 與 Overleaf 專案根目錄，確認待上傳路徑。
3. 用 `sync_directory` 的 `additive` 模式和該計畫的 `planToken` 同步。同步後再用 `plan_sync` 核對檔案內容，並用 `compile_project` 編譯。

2026-11-25 驗證時，Antigravity 顯示 Overleaf MCP 已載入 41 個工具，`auth_status` 確認登入成功。首次同步新增 18 個檔案、覆寫 0 個，同步後逐檔比對均一致。切換預設主檔後，在實際 Overleaf 服務用 `pdfLaTeX` 預設編譯，產出 6 頁 PDF。MCP 回報 0 個錯誤、0 個警告，引用和交叉參照均已解析。

原始提案報告、簡報與設計文件見 [AIOT_FINAL_PROPOSAL](https://github.com/c2838/AIOT_FINAL_PROPOSAL)。
