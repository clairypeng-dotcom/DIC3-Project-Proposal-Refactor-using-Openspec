## ADDED Requirements

### Requirement: 庫存導向的份量與排序

系統 MUST 以有效庫存與指定份數計算候選食譜的需求及缺額，使用相容單位換算，並明示未知單位、排序理由與缺料。推薦 MUST 採唯讀查詢。

#### Scenario: 兩人份有缺料

- **WHEN** 兩人份番茄炒蛋需要 4 顆雞蛋但只有 3 顆可用
- **THEN** 回報缺 1 顆，ready_now 優先完整候選，expiry_first 可優先接近標示日期的候選並保留缺料提示
- **AND** 庫存及異動紀錄不變

### Requirement: 食品安全前置篩選

系統 MUST 將 blocked 和 review 批次排除於自動選用，並呈現原因。eligible 僅代表通過已知篩選條件。

#### Scenario: 日期類型的處置

- **WHEN** 有效庫存分別超過 Use By 與 Best Before
- **THEN** 前者列 blocked，後者列 review，兩者皆不作為自動推薦的可用量
