# Strategy

這個專案用來開發、紀錄與管理交易策略。現階段以策略發想、研究筆記、評估方法、上下架管理與基礎知識整理為主；程式碼尚未建立，後續可逐步加入回測、資料處理、策略執行與狀態管理工具。

## 專案目的

本專案的核心目標是建立一套可追蹤、可評估、可管理的策略工作流程：

- 紀錄策略發想與假設。
- 保存研究過程、回測結果與評估依據。
- 管理策略從發想到上架、暫停、下架的狀態。
- 依市場型態與交易方向整理策略。
- 累積程式交易、風控、績效評估與術語知識。

## 目前目錄結構

```text
strategy/
├─ consolidation/
│  ├─ long/
│  ├─ short/
│  └─ strategic_planning.md
├─ trend/
│  ├─ long/
│  └─ short/
├─ knowledge_base/
│  └─ docs/
│     ├─ program_trading_terms.md
│     └─ program_trading_glossary.md
└─ README.md
```

## 策略分類

策略先用市場型態做第一層分類，再用交易方向做第二層分類。

| 路徑 | 用途 |
| --- | --- |
| `consolidation/long/` | 盤整市場中的偏多策略。 |
| `consolidation/short/` | 盤整市場中的偏空策略。 |
| `trend/long/` | 趨勢市場中的偏多策略。 |
| `trend/short/` | 趨勢市場中的偏空策略。 |
| `knowledge_base/docs/` | 基礎知識、術語、評估方法與策略管理筆記。 |

後續單一策略可放在對應分類底下，例如：

```text
consolidation/
└─ long/
   └─ example_strategy/
      ├─ README.md
      ├─ research.md
      ├─ backtest.md
      ├─ status.md
      └─ src/
```

## 策略生命週期

策略狀態建議使用固定生命週期，方便追蹤與上下架管理。

| 狀態 | 涵義 |
| --- | --- |
| `idea` | 初步想法，尚未完成明確規則。 |
| `research` | 研究中，正在驗證市場假設、資料來源與策略邏輯。 |
| `backtest` | 回測中，已有初步規則並可用歷史資料檢驗。 |
| `paper` | 模擬交易中，正在驗證實盤資料、訊號與下單流程。 |
| `live` | 已上架，使用真實資金或正式交易流程運行。 |
| `paused` | 暫停，策略暫時不上架但尚未淘汰。 |
| `retired` | 已下架，策略不再使用或僅保留歷史紀錄。 |

## 上架管理原則

策略進入 `live` 前，至少應留下下列資訊：

- 策略邏輯：進場、出場、停損、停利、加減碼與部位規則。
- 適用市場：盤整或趨勢、多方或空方、標的與時間週期。
- 回測結果：期間、資料來源、交易成本、滑價假設與主要績效。
- 風險評估：最大回撤、波動、槓桿、曝險、單筆風險與容量限制。
- 樣本外驗證：out-of-sample、walk-forward 或不同市場期間測試。
- 實盤條件：資料更新、訊號產生、下單方式、監控與異常處理。
- 狀態紀錄：目前生命週期、上架日期、暫停原因或下架原因。

## 下架與暫停原則

策略不應只因短期虧損就立即下架，也不應在條件失效後繼續運行。可考慮暫停或下架的情境包括：

- 實盤表現明顯偏離回測或模擬交易。
- 最大回撤超過原本可承受範圍。
- 交易成本、滑價或流動性惡化，導致優勢消失。
- 市場結構改變，使原本策略假設不再成立。
- 樣本外表現持續退化。
- 資料來源、下單流程或風控條件無法穩定維持。

## 策略評估重點

策略評估不應只看總報酬或勝率，至少要同時觀察：

| 面向 | 常用指標 |
| --- | --- |
| 報酬能力 | Total Return、CAGR、Alpha |
| 風險控制 | Max Drawdown、Volatility、Exposure |
| 風險調整後報酬 | Sharpe Ratio、Sortino Ratio、Calmar Ratio |
| 交易優勢 | Profit Factor、Expectancy、Payoff Ratio |
| 穩定性 | Out-of-sample、Walk-forward、不同市場期間表現 |
| 成本敏感度 | Commission、Slippage、Spread、Turnover |
| 實盤可行性 | Liquidity、Capacity、Latency、Order Rejection |

簡化原則：

```text
好策略 = 正期望值
       + 可承受最大回撤
       + 穩定風險調整後報酬
       + 合理交易成本
       + 樣本外仍有效
       + 實盤可執行
```

## 知識文件

- [程式交易常用術語與策略評估指標](knowledge_base/docs/program_trading_terms.md)
- [程式交易詳細術語表](knowledge_base/docs/program_trading_glossary.md)

## 後續可擴充方向

程式碼與工具尚未建立，後續可依需求逐步加入：

- 策略模板與單一策略文件格式。
- 回測資料與結果輸出規範。
- 策略狀態登錄表或 metadata。
- 上架、暫停、下架紀錄。
- 自動化回測、績效彙整與報表工具。
- 實盤監控、異常通知與風控檢查。

## 注意事項

本專案內容用於策略研究、紀錄與管理，不構成投資建議。任何策略在實盤使用前，都應納入交易成本、滑價、流動性、資料品質、樣本外表現與風險承受能力評估。

