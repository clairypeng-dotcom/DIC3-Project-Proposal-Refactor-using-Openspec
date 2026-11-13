## ADDED Requirements

### Requirement: 可重現的評估與錯誤分類

評估 MUST 使用固定案例，保存離線與 Live 結果，並分別統計 API 成功率與有效回應的工具選擇率。

#### Scenario: API 暫時失敗

- **WHEN** API 在有限重試後仍回傳 503
- **THEN** 該案例記為 API_ERROR，計入 API 嘗試次數但排除於有效工具選擇率分母

### Requirement: 知識引用與基準比較

評估 MUST 以實際檢索驗證 RAG 引用支持度，並以配對情境計算基準比較指標。

#### Scenario: 離線案例未執行 Live 檢索

- **WHEN** 只通過靜態來源檢查
- **THEN** 結果僅記為靜態檢查，Live 引用支持度維持待評
