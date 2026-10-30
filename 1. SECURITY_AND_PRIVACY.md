# Security, Privacy & Compliance Statement
# 資安、隱私與合規聲明

**(English below)**

本專案（Enterprise CSAT Data Consolidation）致力於遵循最高標準的資訊安全與隱私保護原則（Privacy by Design）。為協助企業使用者及稽核人員評估本工具之合規性，特此聲明本專案之架構設計與全球主要法規之適用關係。

## 1. 人工智慧規範之豁免聲明 (Exemption from AI Regulations)
本專案為**基於規則之確定性數據處理腳本（Deterministic Rule-based Script）**，**不包含**任何機器學習（Machine Learning）、深度學習、大型語言模型（LLM）或生成式人工智慧技術。
因此，本專案**不適用**且**無須遵循**以下人工智慧專屬規範：
*   **歐盟人工智慧法案 (EU AI Act)**
*   **ISO/IEC 42001:2023 (人工智慧管理系統)**
*   **中國國家網信辦《生成式人工智慧服務管理暫行辦法》**

## 2. 隱私與個人資料保護 (Privacy & Personal Data Protection)
本專案的架構設計原生符合**香港《個人資料（私隱）條例》（PDPO）**、**歐盟《一般資料保護規則》（GDPR）**及 **ISO/IEC 27701 (PIMS)** 的核心要求：
*   **本地化處理 (Local Processing / Data Sovereignty)**：本專案為純前端/純本機端應用。資料處理 100% 於使用者的本機記憶體或瀏覽器中進行，**絕對不會**將任何原始資料（RAW Data）傳輸至外部伺服器或雲端。
*   **去識別化與資料最小化 (De-identification & Data Minimization)**：開源版本的 `config.py` 採零個資（Zero-PII）設計。企業內部使用時，透過內建的映射字典（Mapping Dictionary）進行假名化（Pseudonymization），避免在報表中暴露真實個人聯絡資訊。
*   **生命週期安全 (Data Lifecycle Security)**：Python 引擎內建強制垃圾回收機制（`gc.collect()`），確保敏感資料在報表生成後即時從記憶體中銷毀（Right to be Forgotten / Erasure）。

## 3. 資訊安全管理 (Information Security - ISO/IEC 27001)
*   **機密性 (Confidentiality)**：支援在完全斷網（Air-gapped）的環境下獨立執行，杜絕外部網路攻擊或資料外洩風險。
*   **完整性與可用性 (Integrity & Availability)**：代碼完全開源透明，企業可隨時進行程式碼審查（Code Review）與弱點掃描，無第三方黑盒依賴。

---

**[English]**

This project (Enterprise CSAT Data Consolidation) is committed to adhering to the highest standards of Information Security and Privacy by Design. To assist enterprise users and auditors in evaluating compliance, we declare the architectural design and its applicability to global regulations.

## 1. Exemption from AI Regulations
This project is a **Deterministic Rule-based Script**. It **DOES NOT** contain any Machine Learning (ML), Deep Learning, Large Language Models (LLM), or Generative AI technologies. 
Therefore, this project is **NOT APPLICABLE** to and **EXEMPT** from the following AI-specific regulations:
*   **European Union Artificial Intelligence Act (EU AI Act)**
*   **ISO/IEC 42001:2023 (Artificial Intelligence Management System)**
*   **CAC Interim Measures for the Management of Generative AI Services**

## 2. Privacy & Personal Data Protection
The architecture is natively compliant with the **Hong Kong Personal Data (Privacy) Ordinance (PDPO)**, the **EU General Data Protection Regulation (GDPR)**, and **ISO/IEC 27701 (PIMS)** requirements:
*   **Local Processing & Data Sovereignty**: This is an offline-first/client-side application. 100% of data processing occurs within the user's local memory or browser. **ZERO** raw data is transmitted to any external servers or clouds.
*   **De-identification & Data Minimization**: The open-source `config.py` adopts a Zero-PII design. For internal enterprise usage, the built-in mapping dictionary functions as a pseudonymization layer, preventing the exposure of real contact details in reports.
*   **Data Lifecycle Security**: The Python engine strictly enforces garbage collection (`gc.collect()`), ensuring sensitive data is immediately purged from volatile memory upon report generation (Right to be Forgotten/Erasure).

## 3. Information Security (ISO/IEC 27001)
*   **Confidentiality**: Fully supports execution in air-gapped environments, eliminating risks of network-based exfiltration.
*   **Integrity & Availability**: 100% open-source and transparent. Enterprises can conduct independent code reviews and vulnerability scans without relying on third-party black-box dependencies.
