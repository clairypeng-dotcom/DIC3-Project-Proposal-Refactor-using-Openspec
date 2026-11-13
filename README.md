<img width="3508" height="2481" alt="Food_Guardian_A4_Infographic_Refined" src="https://github.com/user-attachments/assets/9424547d-ea48-494a-89b1-84e330c69c0c" />
# Food Guardian

### Three Core Innovations｜三大核心創新

本研究提出 **Food Guardian：一套結合家庭食材庫存、食品保存知識與資料分析的智慧備餐系統**。使用者可以用自然語言詢問「冰箱裡的食材夠做兩人份晚餐嗎？」系統會查詢目前的庫存，回報可做的料理、缺少的份量，以及哪些食材值得優先處理。

**1. Inventory-Aware Meal Planning — 庫存感知的餐點規劃**

Gemini 透過 LangGraph 呼叫庫存與食譜工具，Python 依用餐人數換算食譜份量，再以 SQLite 的庫存數量計算缺額。例如，兩人份番茄炒蛋需要 4 顆蛋，現有庫存為 3 顆，系統會指出還缺 1 顆。使用者可以選擇優先查看「現有食材就能做」或「能先用掉接近標示日期的食材」的料理。

**2. Food Safety Screening and Source Retrieval — 食品安全初篩與來源檢索**

系統依日期標示與已知風險將食材分為可納入候選、需人工確認及排除，並說明原因。食品保存知識透過 JSON 與 ChromaDB 檢索，讓使用者能查閱建議來源。可納入候選表示該食材通過目前的初篩條件，實際保存狀況仍需確認。

**3. Usage and Waste Analytics — 食材使用與浪費分析**

使用者確認實際使用或丟棄後，系統同步更新庫存與事件紀錄。分析介面依期間、分類及可比較的單位彙整使用量與丟棄量，讓使用者看見哪些食材經常剩下，以及已記錄的丟棄原因。

**核心研究價值**　把「今天可以煮什麼？」轉成能核對的家庭備餐決策。使用者可以看出建議依據哪些庫存、還缺多少，以及食材為何被優先安排或排除，並透過後續紀錄觀察使用與丟棄情況。

### OpenSpec 與評估

本儲存庫收錄[修訂報告](Food_Guardian_Revised.docx)、[系統設計](DESIGN.md)與 [OpenSpec 驗收任務](openspec/changes/validate-food-guardian-workflow/tasks.md)。應用程式與原始評估紀錄請見 [Food Guardian 原始專案](https://github.com/Chen-Fanny/Food-Guardian)。

```bash
npm install -g @fission-ai/openspec@2.0.0
openspec status --change validate-food-guardian-workflow
openspec validate validate-food-guardian-workflow --strict
```

現有 40 項測試全數通過。30 組固定案例中，25 組通過離線檢查、5 組未執行。RAG 實際引用品質、一般 LLM 基準比較及家庭減浪成效仍待驗證。
