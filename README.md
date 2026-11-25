# AIOT DIC4｜居家環境與外出建議代理人

國立中興大學資工系「物聯網應用與資料分析」課程的 IEEE 會議格式提案。

**英文題名**：An IoT Agent for Home and Outing Recommendations Using Indoor Sensing and Weather Forecasts

**作者**：KAO CHUN HSUAN、ZHONG YI XIAN、Xiao Cheng-Yun

## 專題概要

本提案規劃整合 ESP32 室內溫濕度量測、中央氣象署預報與使用者回饋，提供家電使用、外出安排及室內外曬衣建議。系統會記錄建議所依據的資料來源與時間，並在偵測到持續變化時詢問使用者是否有操作。提案包含系統架構、領域規則、事件監測偽程式碼及預定評估方法。

## 檔案

| 檔案 | 用途 |
| --- | --- |
| [`AIOT_DIC4.pdf`](./AIOT_DIC4.pdf) | 已編譯的 IEEE 雙欄提案 PDF |
| [`AIOT_DIC4.tex`](./AIOT_DIC4.tex) | LaTeX 主檔，包含正文、TikZ 圖、表格與參考文獻 |

## 在 Overleaf 編譯

1. 建立 Overleaf 專案並上傳 `AIOT_DIC4.tex`。
2. 將 `AIOT_DIC4.tex` 設為主文件，編譯器選擇 `pdfLaTeX`。
3. 按 **Recompile** 產生 PDF，確認標題、作者、圖表與參考文獻。

原始提案報告、簡報與設計文件見 [AIOT_FINAL_PROPOSAL](https://github.com/c2838/AIOT_FINAL_PROPOSAL)。
