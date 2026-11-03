# AI SOC Analyst Agent

結合 **ML 告警分級**、**MITRE ATT&CK 領域知識** 與 **LLM 推理** 的資安維運中心（SOC）智慧代理人。
Agent 針對資安事件提供 TP / BP / FP 分級、ATT&CK 攻擊鏈對應與處置建議，每個結論都附上證據；信心不足時主動交由分析師複核。

> AIOT 課程期末專題 — 目前為 **Proposal 階段**。

## 專題文件

| 文件 | 內容 |
|---|---|
| [`docs/proposal.md`](docs/proposal.md) | Proposal：Abstract、Introduction、Related Work、Deep Research、Proposed Scheme、References |
| [`docs/AI_SOC_Analyst_Agent-Proposal.pdf`](docs/AI_SOC_Analyst_Agent-Proposal.pdf)（[PPTX](docs/AI_SOC_Analyst_Agent-Proposal.pptx)） | Proposal 簡報 |
| [`DESIGN.md`](DESIGN.md) | 系統設計：Architecture、Components、Data、Algorithm、Evaluation Plan |
| [`data/README.md`](data/README.md) | 資料集來源與下載方式 |

## 系統概觀

```
① 分析師 / 告警佇列 → ② 事件輸入 → ③ Planner & Reasoning Agent
   ↔ ④ 證據取得（事件資料、Log 查詢）
   ↔ ⑤ 分析引擎（分級模型、SHAP、相似事件）
   ↔ ⑥ 領域知識（MITRE ATT&CK、NIST SP 800-61、D3FEND）
→ ⑦ 決策融合與升級判斷 → ⑧ 事件報告 / Dashboard
```

完整架構圖、流程圖與 Pseudocode 見 [`DESIGN.md`](DESIGN.md)。

## 資料集

- **Microsoft GUIDE** — 真實 SOC 事件與分析師分級標籤（主資料集）
- **ExCyTIn-Bench** — LLM Agent 資安調查能力 benchmark
- **MITRE ATT&CK** — 領域知識庫

## 目錄結構

```
.
├── README.md
├── DESIGN.md
├── docs/
│   └── proposal.md
├── data/             # 資料集（不納入版本控制，見 data/README.md）
├── src/soc_agent/    # Agent 原始碼（規劃）
└── experiments/      # 實驗腳本（規劃）
```

## Installation

實作階段補上。

## How to Run

實作階段補上。

## Demo

實作階段補上。

## 組員

第 16 組

| 姓名 | 學號 |
|---|---|
| 蘇恩平 | |
| 周妤 | |
| 袁靖淇 | |
| 蕭宥瑄 | |
