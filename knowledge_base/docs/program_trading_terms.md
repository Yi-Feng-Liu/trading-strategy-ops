# 程式交易常用術語與策略評估指標

這份筆記用 **5W1H** 整理程式交易中常見的術語、涵義，以及常用來定義策略好壞的指標。重點不是只看策略是否賺錢，而是同時理解報酬、風險、穩定性、交易成本與實盤可執行性。

## Who：誰會使用程式交易？

程式交易通常涉及下列角色或系統：

| 術語 | 涵義 |
| --- | --- |
| Quant | 量化研究員，用數據、統計與模型設計交易策略。 |
| Trader | 交易者，負責交易決策、執行或監控策略。 |
| Strategy Developer | 策略開發者，將交易邏輯轉成可回測、可執行的程式。 |
| Backtest Engine | 回測系統，用歷史資料模擬策略表現。 |
| Execution System | 交易執行系統，負責依照策略訊號下單。 |
| Broker API | 券商 API，提供下單、查詢成交、查詢部位等功能。 |
| Exchange | 交易所，撮合買賣委託。 |
| Market Maker | 做市商，提供買賣報價並維持市場流動性。 |
| Liquidity Provider | 流動性提供者，提供可成交的買賣量。 |
| Retail Investor | 散戶投資人。 |
| Institutional Investor | 機構投資人，例如基金、投信、避險基金。 |

## What：常見術語與涵義

### 策略與部位

| 術語 | 涵義 |
| --- | --- |
| Strategy | 交易策略，定義何時進場、出場、停損、停利與調整部位。 |
| Signal | 交易訊號，例如買進、賣出、加碼、減碼或空手。 |
| Entry | 進場條件。 |
| Exit | 出場條件。 |
| Long | 做多，買進後期待價格上漲。 |
| Short | 放空，賣出後期待價格下跌。 |
| Position | 持倉或部位。 |
| Exposure | 曝險程度，代表資金暴露在某市場、標的或風險因子上的比例。 |
| Leverage | 槓桿，用較少本金控制較大部位。 |
| Position Sizing | 部位 sizing，決定每次交易投入多少資金或口數。 |
| Rebalancing | 再平衡，依固定週期或條件調整資產配置或部位比例。 |

### 常見策略類型

| 術語 | 涵義 |
| --- | --- |
| Trend Following | 趨勢追蹤，順著既有趨勢交易。 |
| Momentum | 動能策略，買進近期相對強勢標的或放空相對弱勢標的。 |
| Mean Reversion | 均值回歸，假設價格偏離合理區間後會回到平均水準。 |
| Breakout | 突破策略，價格突破區間、壓力或支撐時進場。 |
| Arbitrage | 套利，利用市場間價格差異獲利。 |
| Statistical Arbitrage | 統計套利，用統計關係尋找相對錯價。 |
| Pairs Trading | 配對交易，交易兩個高度相關標的之間的價差。 |
| Market Neutral | 市場中性，降低整體市場漲跌對策略的影響。 |

### 訂單與成交

| 術語 | 涵義 |
| --- | --- |
| Market Order | 市價單，以市場可成交價格立即執行，但成交價可能不如預期。 |
| Limit Order | 限價單，指定可接受價格，可能不會成交。 |
| Stop Order | 停損或停利觸發單，價格到達條件後送出委託。 |
| Fill | 成交。 |
| Partial Fill | 部分成交。 |
| Slippage | 滑價，理論成交價與實際成交價的差距。 |
| Commission | 手續費。 |
| Spread | 買賣價差，最佳買價與最佳賣價之間的差距。 |
| Liquidity | 流動性，代表能否快速成交且不造成明顯價格衝擊。 |
| Latency | 延遲，訊號產生、送單與成交回報之間的時間差。 |
| Order Rejection | 委託被拒，例如資金不足、價格超限、商品不可交易。 |

### 回測與資料

| 術語 | 涵義 |
| --- | --- |
| Backtest | 回測，用歷史資料測試策略表現。 |
| Forward Test | 前向測試，用策略開發後的新資料驗證表現。 |
| Paper Trading | 模擬交易，不使用真實資金。 |
| Live Trading | 實盤交易。 |
| In-sample | 樣本內資料，通常用於策略開發與參數調整。 |
| Out-of-sample | 樣本外資料，通常用於驗證策略是否具備泛化能力。 |
| Walk-forward Analysis | 滾動式驗證，反覆用前段資料訓練、後段資料驗證。 |
| OHLCV | 開盤價、最高價、最低價、收盤價、成交量。 |
| Tick Data | 逐筆資料，記錄每一筆成交或報價變化。 |
| Adjusted Price | 還原價格，通常調整除權息、拆股等事件。 |
| Overfitting | 過度擬合，策略太貼合歷史資料，導致未來表現不佳。 |
| Look-ahead Bias | 偷看未來資料，回測中使用了當時不可能知道的資訊。 |
| Survivorship Bias | 存活者偏差，只使用仍存在的標的，忽略下市或失敗樣本。 |
| Data Snooping | 反覆測試大量規則後，只挑表現最好的結果，容易產生假優勢。 |

## When：術語會在什麼階段使用？

| 階段 | 常見術語 | 重點 |
| --- | --- | --- |
| 策略發想 | Signal、Entry、Exit、Long、Short | 定義交易邏輯與市場假設。 |
| 資料準備 | OHLCV、Tick Data、Adjusted Price、Survivorship Bias | 確認資料品質，避免偏差。 |
| 回測 | Backtest、Commission、Slippage、Drawdown | 模擬歷史表現，加入合理成本。 |
| 驗證 | Out-of-sample、Walk-forward、Overfitting | 檢查策略是否只適合歷史資料。 |
| 模擬交易 | Paper Trading、Fill、Latency、Order Rejection | 驗證訊號與下單流程是否可運作。 |
| 實盤交易 | Live Trading、Exposure、Position Sizing、Risk Control | 控制風險並監控實際執行差異。 |

## Where：適用市場

程式交易可應用在多種市場，但每個市場的主要風險與成本結構不同。

| 市場 | 常見重點 |
| --- | --- |
| 股票 | 選股、產業輪動、財報因子、除權息調整。 |
| 期貨 | 槓桿、保證金、轉倉、到期日。 |
| 選擇權 | 波動率、履約價、到期日、希臘字母。 |
| 外匯 | 點差、隔夜利息、槓桿、流動性時段。 |
| 加密貨幣 | 24 小時交易、資金費率、交易所風險、流動性分散。 |
| ETF | 資產配置、再平衡、輪動策略、追蹤誤差。 |

## Why：為什麼不能只看報酬？

策略評估不能只看「賺不賺錢」或「勝率高不高」，原因包括：

- 總報酬高的策略，可能伴隨極大的最大回撤。
- 勝率高的策略，可能每次賺很少，但一次虧損就吃掉多數獲利。
- 回測漂亮的策略，可能來自過度擬合或資料偏差。
- 交易次數太多的策略，可能被手續費、滑價與價差侵蝕。
- 策略在小資金有效，不代表資金變大後仍有足夠流動性。
- 策略需要能被穩定執行，否則理論績效無法轉成實盤績效。

因此，好的策略應同時評估：

- 報酬能力
- 風險大小
- 回撤程度
- 報酬穩定性
- 交易成本敏感度
- 樣本外表現
- 實盤可執行性

## How：如何定義策略好壞？

### 常用績效與風險指標

| 指標 | 定義 | 解讀方式 |
| --- | --- | --- |
| Total Return | 總報酬率。 | 越高越好，但不能單獨判斷策略品質。 |
| CAGR | 年化複合成長率。 | 衡量長期複利能力。 |
| Volatility | 報酬波動率。 | 越高代表資金曲線起伏越大。 |
| Max Drawdown, MDD | 最大回撤，從資金高點跌到後續低點的最大跌幅。 | 越低越好，代表最痛虧損較小。 |
| Sharpe Ratio | 單位總波動承擔下的超額報酬。 | 越高越好，常用於比較不同策略。 |
| Sortino Ratio | 只用下行波動衡量風險調整後報酬。 | 比 Sharpe 更重視虧損波動。 |
| Calmar Ratio | 年化報酬率除以最大回撤。 | 衡量報酬與最壞回撤的比例。 |
| Win Rate | 勝率，獲利交易次數占總交易次數比例。 | 不能單獨看，需搭配賺賠比。 |
| Profit Factor | 總獲利除以總虧損。 | 大於 1 代表總獲利大於總虧損。 |
| Expectancy | 每筆交易期望值。 | 大於 0 代表長期平均每筆交易有正期望。 |
| Payoff Ratio | 平均獲利除以平均虧損。 | 衡量平均賺賠比。 |
| Alpha | 相對基準的超額報酬。 | 越高代表策略相對基準越有價值。 |
| Beta | 策略對市場波動的敏感度。 | Beta 越高，通常越受市場漲跌影響。 |
| Turnover | 換手率。 | 越高通常交易成本越高。 |
| Capacity | 策略容量。 | 衡量資金規模變大後策略是否仍可執行。 |

### 常見公式

```text
Total Return = 期末資金 / 期初資金 - 1
```

```text
CAGR = (期末資金 / 期初資金) ^ (1 / 年數) - 1
```

```text
Max Drawdown = (資金曲線低點 / 先前資金曲線高點) - 1
```

```text
Profit Factor = 總獲利 / 總虧損
```

```text
Expectancy = 勝率 * 平均獲利 - 敗率 * 平均虧損
```

```text
Payoff Ratio = 平均獲利 / 平均虧損
```

```text
Calmar Ratio = 年化報酬率 / 最大回撤
```

### 期望值範例

假設某策略：

```text
勝率 = 40%
平均獲利 = 3000
敗率 = 60%
平均虧損 = 1000

Expectancy = 0.4 * 3000 - 0.6 * 1000
           = 1200 - 600
           = 600
```

這代表策略平均每筆交易期望獲利 600。即使勝率只有 40%，只要平均獲利足夠大，策略仍可能是正期望策略。

### 判斷策略好壞的實務框架

一個策略不能只用單一指標判斷，較完整的判斷方式如下：

```text
好策略 = 正期望值
       + 可承受最大回撤
       + 穩定風險調整後報酬
       + 合理交易成本
       + 樣本外仍有效
       + 實盤可執行
```

實務上可優先觀察：

| 面向 | 建議觀察指標 |
| --- | --- |
| 報酬能力 | Total Return、CAGR、Alpha |
| 風險控制 | Max Drawdown、Volatility、Exposure |
| 風險調整後報酬 | Sharpe Ratio、Sortino Ratio、Calmar Ratio |
| 交易優勢 | Profit Factor、Expectancy、Payoff Ratio |
| 穩定性 | Out-of-sample、Walk-forward、不同市場期間表現 |
| 成本敏感度 | Commission、Slippage、Spread、Turnover |
| 實盤可行性 | Liquidity、Capacity、Latency、Order Rejection |

## 核心結論

程式交易的重點不是寫出看起來很複雜的策略，而是建立一套能被驗證、能控制風險、能承受交易成本、能在實盤穩定執行的決策流程。

簡化來說：

```text
不要只看勝率。
不要只看總報酬。
不要只相信樣本內回測。

應該同時看：
CAGR、Max Drawdown、Sharpe、Sortino、Calmar、
Profit Factor、Expectancy、交易成本、樣本外表現與實盤可執行性。
```

## 延伸閱讀

更多術語分類與指標好壞簡易判斷，可參考 [程式交易詳細術語表](program_trading_glossary.md)。
