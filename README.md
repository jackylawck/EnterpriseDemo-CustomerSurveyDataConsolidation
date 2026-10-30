# 📊 Enterprise CSAT Data Consolidation <br> (企業客戶滿意度問卷整合系統)

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![Frontend](https://img.shields.io/badge/frontend-HTML5%20%7C%20ExcelJS-orange)
![Security](https://img.shields.io/badge/security-Zero--PII%20%7C%20Offline-success)
![License](https://img.shields.io/badge/license-MIT-green)

**(English below)**

這是一款開源、具備**「雙軌模式 (Dual-mode)」**的自動化數據處理工具，專為將 Microsoft Forms 匯出的原始滿意度問卷資料（RAW Excel），自動轉換為標準化、排版精美，且帶有動態公式與條件格式的企業級管理層報表而設計。

本專案基於 **Privacy by Design（隱私始於設計）** 原則打造，確保所有敏感商業資料僅在操作者的本機環境或瀏覽器記憶體中處理，達到 **Zero-PII（零個資外洩）**，完美符合嚴格的企業資安稽核要求。

### ✨ 核心功能
*   **🌐 雙軌運作模式 (Dual-mode Execution)**：
    *   **純前端網頁版 (Web App)**：打開瀏覽器即可拖曳執行，運算 100% 留存在本地端，不上傳任何伺服器。
    *   **本機離線桌面版 (Desktop CLI)**：透過 Python 搭配 `.bat` 批次檔，支援 Windows 一鍵拖曳 (Drag-and-Drop) 離線秒速生成。
*   **🔄 智能名稱標準化**：內建映射字典，自動將英文拼音、簡稱轉換為標準客戶全名與企業群組。
*   **🧮 全自動公式與排版**：自動套用標準企業字體、邊框、動態計算有效題數平均分，並自動為**低於 7 分的項目標記紅色警告**。
*   **🔒 企業級資安防護**：防呆 Schema 驗證，並透過 `gc.collect()` 嚴格執行記憶體回收，銷毀敏感資料。

---

**[English]**

An open-source, **Dual-mode** automation tool designed to convert raw Microsoft Forms Customer Satisfaction (CSAT) survey exports into standardized, beautifully formatted enterprise management reports with dynamic formulas and conditional formatting.

Built on the principle of **Privacy by Design**, this project ensures that all sensitive commercial data is processed exclusively within the operator's local environment or browser memory, achieving **Zero-PII (Zero Data Leakage)** and meeting strict enterprise security audit requirements.

### ✨ Key Features
*   **🌐 Dual-mode Execution**:
    *   **Client-side Web App**: Drag and drop files directly in the browser. 100% local computation with no server uploads.
    *   **Offline Desktop Mode**: Python backend with Windows `.bat` integration for zero-friction, drag-and-drop offline execution.
*   **🔄 Dynamic Normalization**: Built-in mapping dictionaries automatically convert English abbreviations or aliases into standardized corporate groups.
*   **🧮 Automated Formulas & Styling**: Auto-applies standard fonts, borders, dynamic denominator averages, and **conditional red formatting for scores < 7**.
*   **🔒 Enterprise-Grade Security**: Strict schema validation and explicit memory sanitization via `gc.collect()`.

---

## 🚀 快速開始 (Quick Start)

### 模式一：純前端網頁版 (Web Application Mode)
無需安裝任何環境，打開專屬網頁即可本機離線處理：
👉 **[Launch Web App](https://jackylawck.github.io/EnterpriseDemo-CustomerSurveyDataConsolidation/)**

### 模式二：本機離線桌面版 (Offline Desktop Mode)
**1. 安裝環境 (Installation)**
請確保您的電腦已安裝 Python 3.8+。 / Ensure Python 3.8+ is installed.
```bash
git clone [https://github.com/jackylawck/EnterpriseDemo-CustomerSurveyDataConsolidation.git](https://github.com/jackylawck/EnterpriseDemo-CustomerSurveyDataConsolidation.git)
cd EnterpriseDemo-CustomerSurveyDataConsolidation
pip install -r requirements.txt

```

**2. 生成測試數據 (Generate Mock Data)**
為保護真實個資，本專案提供虛擬數據生成器。 / Generate a synthetic mock dataset for testing:

```bash
python generate_sample_data.py
# 將會在 sample_data/ 內生成 RAW_SAMPLE.xlsx (Creates RAW_SAMPLE.xlsx)

```

**3. 執行轉換 (Run Transformation)**
將生成的 `RAW_SAMPLE.xlsx` 檔案，用滑鼠拖曳到 **`run_consolidation.bat`** 上放開即可秒速生成報表。 / Simply drag and drop the `.xlsx` file onto **`run_consolidation.bat`**.

---

## ⚙️ 內部部署與組態配置 (Internal Configuration)

本公開專案預設的 `config.py` 與 `index.html` 皆為**開源脫敏展示版（Enterprise Demo）**，不含任何真實姓名。
如果您要在企業內部生產環境中使用：

1. 編輯 `config.py` (針對桌面版) 或 `index.html` (針對網頁版)。
2. 在 `COMPANY_MAPPING` 與 `PERSON_NAME_MAPPING` 字典中填入貴司真實的客戶別名與員工姓名對照表。

> ⚠️ **【資安警告 / Security Warning】**
> 填入真實資料的組態檔與真實的問卷 `RAW.xlsx` **絕對不可**上傳至 GitHub 或任何公開網路。本專案的 `.gitignore` 已預設阻擋 Excel 檔案上傳。 / Do NOT commit your internal configurations or real `RAW.xlsx` to public repositories.

---

## 🛡️ 資安與合規聲明 (Security & Compliance)

本專案嚴格遵守全球資訊安全與隱私標準。我們明確宣告本專案為**確定性規則腳本（Deterministic Rule-based Script）**，不含任何 AI 模型，無須遵循 EU AI Act。同時，本架構設計原生符合 GDPR 與香港 PDPO 之要求。

詳細的資安架構與免責條款，請參閱以下文件：

* 📜 [SECURITY_AND_PRIVACY.md](https://www.google.com/search?q=SECURITY_AND_PRIVACY.md) (資安與隱私合規聲明)
* ⚖️ [DISCLAIMER.md](DISCLAIMER.md) (免責聲明)

## 📄 授權條款 (License)

本專案採用 [MIT License](https://www.google.com/search?q=LICENSE) 授權。 / This project is licensed under the MIT License.

