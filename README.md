本次優化針對你貼上的版本進行了三項關鍵修正與升級：
 * 修復損壞的超連結與指令：移除 git clone 區塊內誤植的 Markdown 連結語法，並將指向 Google 搜尋的 SECURITY_AND_PRIVACY.md 與 LICENSE 修正為標準倉庫相對路徑。
 * 納入企業架構與稽核目錄（docs/、flows/、schemas/）：新增完整的專案目錄樹，讓稽核人員與訪客一目了然系統的契約規範與確定性流程。
 * 加入雙軌架構對照表：以結構化表格呈現網頁版與桌面版的安全邊界與適用場景，提升整體專業質感。
請直接複製以下完整代碼覆蓋 README.md：
# 📊 Enterprise CSAT Data Consolidation <br> (企業客戶滿意度問卷整合系統)

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![Frontend](https://img.shields.io/badge/frontend-HTML5%20%7C%20ExcelJS-orange)
![Security](https://img.shields.io/badge/security-Zero--PII%20%7C%20Offline--First-success)
![AI Governance](https://img.shields.io/badge/EU%20AI%20Act-Exempt%20(Deterministic)-lightgrey)
![License](https://img.shields.io/badge/license-MIT-green)

**(中文說明 | English below)**

這是一款開源、具備**「雙軌模式 (Dual-mode)」**的自動化數據處理工具，專為將 Microsoft Forms 匯出的原始客戶滿意度問卷資料（RAW Excel），自動轉換為標準化、排版精美，且帶有動態公式與條件格式的企業級管理層報表而設計。

本專案基於 **Privacy by Design（隱私始於設計）** 與 **Architecture-as-Code（架構即代碼）** 原則打造，確保所有敏感商業資料僅在操作者的本機環境或瀏覽器記憶體中處理，達到 **Zero-PII（零個資外洩）**，並內建完整的 JSON Schema 契約與合規聲明，滿足嚴格的企業資安與治理稽核要求。

### ✨ 核心功能
* **🌐 雙軌運作模式 (Dual-mode Execution)**：
  * **純前端網頁版 (Client-side Web App)**：透過瀏覽器本機運算（ExcelJS + FileSaver.js），受嚴格 CSP 安全策略保護，資料絕不上傳雲端。
  * **本機離線桌面版 (Offline Desktop CLI)**：透過 Python 搭配 `.bat` 批次檔，支援 Windows 一鍵拖曳（Drag-and-Drop）離線秒速生成。
* **🔄 智能名稱與群組標準化**：內建映射字典，自動將英文拼音、簡稱或別名轉換為標準客戶全名與企業群組排序。
* **🧮 全自動動態公式與條件預警**：自動套用標準企業字體、邊框、動態分母平均分公式（避免未作答題目拉低分數），並自動為**低於 7 分的項目標記粗體紅色警告**。
* **🔒 企業級資安與記憶體銷毀**：防呆 Schema 驗證（`validator.py`），並透過 `gc.collect()` 嚴格執行記憶體垃圾回收，即時銷毀殘留敏感資料。

---

**[English]**

An open-source, **Dual-mode** deterministic data automation tool designed to transform raw Microsoft Forms Customer Satisfaction (CSAT) survey exports into standardized, executive-ready Excel reports with dynamic formulas and conditional formatting.

Built upon **Privacy by Design** and **Architecture-as-Code** principles, this solution ensures 100% local processing within the user's browser or local RAM—achieving **Zero-PII (Zero Data Leakage)** alongside machine-readable JSON schemas and audit-ready compliance documentation.

### ✨ Key Features
* **🌐 Dual-mode Execution**:
  * **Client-side Web App**: Runs entirely in the browser (ExcelJS + FileSaver.js) under a strict Content Security Policy (`form-action 'none'`), ensuring zero server uploads.
  * **Offline Desktop CLI**: Python engine with Windows `.bat` drag-and-drop support for air-gapped environments.
* **🔄 Deterministic Normalization**: Built-in mapping dictionaries standardize respondent names, client aliases, and corporate group ordering.
* **🧮 Dynamic Formulas & Alerting**: Auto-formats fonts, borders, dynamic denominator averages, and applies **bold red highlighting (`#FF0000`) for scores < 7**.
* **🔒 Enterprise Security & Memory Purge**: Defensive schema validation (`validator.py`) paired with explicit volatile memory cleanup (`gc.collect()`).

---

## 🏗️ 雙軌架構對照 (Dual-Mode Architecture Comparison)

| 維度 / Dimension | 純前端網頁版 (Web App) | 本機離線桌面版 (Desktop CLI) |
| :--- | :--- | :--- |
| **核心引擎 / Engine** | HTML5 + ExcelJS + FileSaver.js | Python 3.8+ (`pandas` + `openpyxl`) |
| **運行環境 / Runtime** | 現代瀏覽器 (GitHub Pages / 本機開啟) | Windows / macOS / Linux 本機環境 |
| **資料駐留 / Data Residency** | 100% 瀏覽器本地記憶體 (Zero-Cloud) | 100% 本機 RAM，執行後 `gc.collect()` 銷毀 |
| **安全控制 / Security Control** | 嚴格 CSP 標頭隔離外部網路請求 | 支援完全斷網（Air-gapped）環境運行 |
| **適用對象 / Best For** | 業務與行政人員免安裝快速轉檔 | 定期批次處理與企業內網自動化腳本 |

---

## 📂 專案目錄結構 (Repository Structure)

```text
EnterpriseDemo-CustomerSurveyDataConsolidation/
├── docs/
│   └── architecture-and-data-flow.md    # 系統架構與 Mermaid 確定性資料流圖
├── flows/
│   └── csat_deterministic_pipeline.json # 6 階段確定性處理狀態機 (Machine-Readable Flow)
├── schemas/
│   ├── csat_raw_input_schema.json       # 輸入問卷 JSON Schema 驗證契約
│   └── csat_output_report_schema.json   # 輸出報表結構與 KPI 公式契約
├── index.html                           # 純前端離線網頁版入口 (含 CSP 與 SEO 優化)
├── main.py                              # Python 桌面版主程式入口
├── processor.py                         # 核心矩陣轉置、樣式渲染與記憶體銷毀引擎
├── validator.py                         # 輸入欄位防呆校驗模組
├── config.py                            # 脫敏展示版組態與映射字典 (Zero-PII)
├── generate_sample_data.py              # 合成測試數據生成器 (產出 RAW_SAMPLE.xlsx)
├── run_consolidation.bat                # Windows 一鍵拖曳執行批次檔
├── requirements.txt                     # Python 套件依賴清單
├── SECURITY_AND_PRIVACY.md              # 資安、隱私與 EU AI Act 豁免合規聲明
├── DISCLAIMER.md                        # 免責聲明與責任限制條款
└── LICENSE                              # MIT 開源授權條款

🚀 快速開始 (Quick Start)
模式一：純前端網頁版 (Web Application Mode)
無需安裝任何程式，點擊下方連結即可在瀏覽器本機離線處理：
👉 啟動線上網頁版 / Launch Web App
模式二：本機離線桌面版 (Offline Desktop Mode)
1. 安裝環境 (Installation)
請確保電腦已安裝 Python 3.8+ / Ensure Python 3.8+ is installed:
git clone [https://github.com/jackylawck/EnterpriseDemo-CustomerSurveyDataConsolidation.git](https://github.com/jackylawck/EnterpriseDemo-CustomerSurveyDataConsolidation.git)
cd EnterpriseDemo-CustomerSurveyDataConsolidation
pip install -r requirements.txt

2. 生成無害測試數據 (Generate Synthetic Mock Data)
為保護真實商業與個人資料，本專案內建虛擬數據生成器 / Generate a synthetic dataset for testing:
python generate_sample_data.py
# 將會在 sample_data/ 目錄下生成 RAW_SAMPLE.xlsx

3. 執行報表轉換 (Run Transformation)
將生成的 RAW_SAMPLE.xlsx 檔案，直接用滑鼠拖曳至 run_consolidation.bat 圖示上放開即可秒速產出整合報表（亦可在終端機執行 python main.py sample_data/RAW_SAMPLE.xlsx）。
⚙️ 企業內部部署配置 (Internal Enterprise Configuration)
本公開倉庫預設的 config.py 與 index.html 皆為開源脫敏展示版（Enterprise Demo），不含任何真實公司或個人姓名。若需於企業內部生產環境使用：
 * 編輯 config.py（桌面版）或 index.html 內的 CONFIG 物件（網頁版）。
 * 在 COMPANY_MAPPING 與 PERSON_NAME_MAPPING 中填入內部客戶別名與聯絡人對照表。
> ⚠️ 【資安警告 / Security Warning】
> 填入真實客戶名單或員工姓名的內部組態檔，以及原始問卷 RAW.xlsx，嚴禁上傳至 GitHub 或任何公開版本控制系統。本專案的 .gitignore 已預設排除所有 .xlsx 與 .csv 檔案。
> 
🛡️ 資安與合規聲明 (Security & Governance Compliance)
本專案嚴格遵循全球資訊安全與隱私保護框架：
 * AI 法規豁免 (EU AI Act / ISO 42001)：本工具為基於規則之確定性腳本（Deterministic Rule-based Script），不含任何機器學習或生成式 AI 模型，明確豁免相關 AI 監管要求。
 * 隱私與資安標準 (PDPO / GDPR / ISO 27001 & 27701)：落實本地化運算、資料最小化與即時記憶體清除。
詳細架構與合規文件請參閱：
 * 🏗️ docs/architecture-and-data-flow.md — 系統架構與確定性資料流說明
 * 📜 SECURITY_AND_PRIVACY.md — 資安、隱私與合規聲明
 * ⚖️ DISCLAIMER.md — 免責聲明與責任限制
📄 授權條款 (License)
本專案採用 MIT License 開源授權。 / This project is licensed under the MIT License.

