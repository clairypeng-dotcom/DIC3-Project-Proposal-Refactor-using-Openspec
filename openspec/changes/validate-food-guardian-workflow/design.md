## Context

以根目錄 DESIGN.md §1–11、目前原始碼及 evaluation/results 為依據。部署範圍為單一家庭的課程原型，庫存由使用者輸入，食譜使用示範 JSON。

## Goals / Non-Goals

以固定日期和測資驗收庫存一致性、推薦與引用行為。多家庭隔離、影像辨識、實際保存溫度及長期減浪效果超出本輪驗收範圍。

## Decisions

1. **寫入路徑**。Streamlit 操作透過 InventoryService 在同一 SQLite 交易更新庫存及新增事件。推薦路徑唯讀，使用者可另外確認並登錄實際用量。
2. **推薦路徑**。Gemini/LangGraph 理解意圖及選工具，Python 依安全初篩、相容單位和指定份數計算缺額；ready_now 與 expiry_first 服務不同需求。日期提醒與可用性初篩各自判斷。遇必要資訊不明，以追問或明確標記不確定處理，整合時驗證各入口的實際行為。
3. **知識路徑**。JSON／ChromaDB 提供檢索來源，顯示來源類別與可追溯證據。RAG 是否支援回答由人工檢查。API 不可用時可手動選本地規則模式。
4. **分析路徑**。依 consumption_waste_logs 分組，僅在可比較單位及分母大於零時計算丟棄量除以使用與丟棄總量。
5. **驗收路徑**。固定案例執行離線測試，再分別跑 Gemini 多工具與 RAG Live，記錄 API 成功率、有效回應的工具選擇率及人工內容品質。一般 LLM 比較使用同一情境與一致評分規則，並記錄兩組可取得的資料。

| DESIGN.md | OpenSpec 對應 |
|---|---|
| §1–2 問題與需求 | proposal 與五項能力規格 |
| §3–5 架構、元件、資料 | 本檔與 inventory-tracking、usage-analytics |
| §6–8 AI、領域知識、演算法 | meal-recommendation、food-knowledge、workflow-evaluation |
| §9–11 實作、執行、結果 | tasks、evaluation/results 與根目錄 DESIGN.md |

## Risks / Trade-offs

手動輸入有漏填風險，以缺資料情境驗收。Live 依賴 API 與索引，以有限重試及獨立結果分類保留證據。相容單位限制會縮小可推薦範圍，同時維持數量判定可解釋。
