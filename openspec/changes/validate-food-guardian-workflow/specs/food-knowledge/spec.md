## ADDED Requirements

### Requirement: 可追溯的食品保存查詢

系統 MUST 區分示範資料與有來源的資料，並在食品知識不足時呈現不確定性。

#### Scenario: 只有未核實示範資訊

- **WHEN** 知識工具只取得 project_sample 資料
- **THEN** 顯示其未核實狀態，不以該內容支持確定的安全結論
