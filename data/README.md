# Data

原始資料檔案體積大，**不納入版本控制**（見 `.gitignore`）。請依下列方式下載並放到對應目錄。

| 資料集 | 放置位置 | 來源 | 授權 |
|---|---|---|---|
| Microsoft GUIDE | `data/raw/guide/` | Kaggle：*Microsoft Security Incident Prediction*；論文 [arXiv:2407.09017](https://arxiv.org/abs/2407.09017) | CDLA-2.0 |
| ExCyTIn-Bench | `data/raw/excytin/` | 論文 [arXiv:2507.14201](https://arxiv.org/abs/2507.14201)（官方 repo 待確認） | 依官方 repo |
| MITRE ATT&CK（STIX 2.1） | `data/raw/attack/` | MITRE ATT&CK 官方 STIX 資料 | MITRE Terms of Use |
| Splunk BOTS v3（選用） | `data/raw/bots/` | [Splunk BOTS v3](https://www.splunk.com/en_us/blog/security/botsv3-dataset-released.html) | CC0 |

## GUIDE 資料說明（依原始論文 arXiv:2407.09017 附錄 B、C）

- **檔案**：train（70%）與 test（30%）兩個 CSV，皆放在 Kaggle。實際檔名與大小待下載後確認。
- **欄位**：共 45 欄，包含特徵、標籤與識別碼。
  - 識別碼：`Id`、`OrgId`、`IncidentId`、`AlertId`、`Timestamp`
  - 告警：`DetectorId`、`AlertTitle`、`Category`、`MitreTechniques`
  - 標籤：`IncidentGrade`（TP / BP / FP）、`ActionGrouped`、`ActionGranular`
  - 證據實體：`EntityType`、`EvidenceRole`、`Roles`、`DeviceId`、`DeviceName`、`Sha256`、`IpAddress`、`Url`、`AccountSid`、`AccountUpn`、`AccountObjectId`、`AccountName`、`NetworkMessageId`、`EmailClusterId`、`RegistryKey`、`RegistryValueName`、`RegistryValueData`、`ApplicationId`、`ApplicationName`、`OAuthApplicationId`、`ThreatFamily`、`FileName`、`FolderPath`、`ResourceIdName`、`ResourceType`
  - 環境：`OSFamily`、`OSVersion`、`AntispamDirection`、`SuspicionLevel`、`LastVerdict`、`CountryCode`、`State`、`City`
- **匿名化**：敏感值先以 SHA1 雜湊，再替換成隨機產生的 ID；時間戳記加入雜訊。論文沒有列出哪些欄位被匿名化，需下載後檢查。

## 待確認事項

- [x] GUIDE 是否包含 `MitreTechniques`、`IncidentGrade` 等欄位（論文 Table 4 確認有）
- [x] GUIDE 各欄位實際的匿名化程度：`AlertTitle` 與實體欄位為數字 ID；`Category`、`MitreTechniques` 等為可讀文字（詳見 `DESIGN.md` §5）
- [x] GUIDE 檔案大小：`GUIDE_Train.csv` 2.4 GB、`GUIDE_Test.csv` 1.1 GB
- [ ] 實體欄位中代表「無此實體」的固定 ID
- [ ] 同一事件內各列的 `IncidentGrade` 是否一致

## 目前的實際放置位置

Kaggle 下載的檔案目前放在 `data/archive/`（已加入 `.gitignore`）：

| 檔案 | 大小 | 內容 |
|---|---|---|
| `GUIDE_Train.csv` | 2.4 GB | 訓練集 |
| `GUIDE_Test.csv` | 1.1 GB | 測試集，多一欄 `Usage`（Public / Private） |
| `GUIDE_Test_Queue_Rankings.csv` | 136 KB | 9,980 起測試事件、499 個組織的佇列優先順序（1–20），來自 AIP 論文 [arXiv:2607.16963](https://arxiv.org/abs/2607.16963) |
- [ ] GUIDE train / test 檔案大小與記憶體需求
- [ ] ExCyTIn-Bench 官方 repo 位置、環境需求與授權
- [ ] 鎖定使用的 ATT&CK 版本
