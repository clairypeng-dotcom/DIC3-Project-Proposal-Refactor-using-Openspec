## Why

現有 DESIGN.md 同時記載現況、提案與待驗收事項。將其轉成可逐項驗收的規格，讓後續整合能沿用固定的行為契約和測試證據。

## What Changes

- 建立五項能力的首版 OpenSpec 規格，涵蓋 FR-01 至 FR-10。
- 建立從固定測資到 RAG Live、人工審查及一般 LLM 基準比較的驗收工作。

## Capabilities

### New Capabilities

- `inventory-tracking`: 庫存、日期提醒及使用／丟棄紀錄。
- `meal-recommendation`: 依庫存、安全初篩與份量產生可解釋推薦。
- `food-knowledge`: 食品保存知識查詢及來源呈現。
- `usage-analytics`: 依事件紀錄呈現使用及丟棄情況。
- `workflow-evaluation`: 離線與 Live 評估、錯誤分類及重現證據。

### Modified Capabilities

## Impact

以 Streamlit、SQLite、Python services、Gemini/LangGraph、ChromaDB 與現有 evaluation 套件為驗收對象。本次文件變更建立驗收起點，待辦結果由後續實際執行填入。
