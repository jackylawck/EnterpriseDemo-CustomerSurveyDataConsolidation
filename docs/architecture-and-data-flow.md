# System Architecture & Deterministic Data Flow
# 系統架構與確定性資料流說明

**(English below)**

本文件說明 **Enterprise CSAT Data Consolidation** 的雙軌運作架構、資料結構契約（`schemas/`）與自動化處理管線（`flows/`），供企業 IT 團隊與資訊安全稽核人員檢視。

## 1. 確定性處理管線 (Deterministic ETL Flow)

本系統完全基於確定性規則（Deterministic Rules）運作，**不含任何 AI 或機器學習推論**，所有運算皆鎖定於使用者本機記憶體中：

```mermaid
flowchart LR
    A[Microsoft Forms<br>RAW Excel .xlsx] -->|本機讀取 / Local RAM| B{Schema 驗證<br>validator.py}
    B -->|缺少必要欄位| C[中止並提示錯誤<br>ValidationError]
    B -->|通過驗證| D[字典標準化與排序<br>config.py / CONFIG]
    D --> E[矩陣轉置與公式注入<br>動態分母 & <7分標紅]
    E --> F[本機匯出標準報表<br>Consolidated .xlsx]
    F --> G[強制記憶體回收<br>gc.collect / Zero-Retention]

2. 目錄與治理對照 (Repository Governance Mapping)
 * schemas/：定義輸入與輸出的 JSON Schema 契約，確保跨年度問卷欄位變動時具備自動防呆能力。
 * flows/：以機器可讀的 JSON 狀態機記錄 6 個處理階段與資安控制點，方便納入企業架構審查（Enterprise Architecture Review）。
 * SECURITY_AND_PRIVACY.md：聲明本工具豁免 EU AI Act，並符合香港 PDPO、GDPR 及 ISO/IEC 27001 / 27701 隱私設計原則。
[English]
This document outlines the dual-mode architecture, data contracts (schemas/), and deterministic processing pipeline (flows/) of Enterprise CSAT Data Consolidation for enterprise IT and security audit review.
 * Zero-Cloud Data Sovereignty: Whether executed via the browser (index.html with strict Content Security Policy) or desktop CLI (main.py), raw survey files never leave the local machine.
 * Auditability: Every transformation rule, formula denominator, and < 7 threshold alert is explicitly defined in flows/csat_deterministic_pipeline.json and schemas/.
