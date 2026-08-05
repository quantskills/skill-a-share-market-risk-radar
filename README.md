# A股市场风险雷达

A股市场风险监测 Skill，从全球宏观、融资资金、指数估值、市场趋势、资金流向、板块轮动、个股事件和技术面进行综合扫描，并输出红、黄、绿风险等级。

本项目用于风险预警和市场研究，不构成投资建议，也不承诺任何投资收益。

## 功能

- 全球宏观环境扫描
- A股市场整体风险判断
- 资金流向与融资压力监测
- 行业及板块轮动分析
- 个股事件风险检查
- 股票技术面风险预警
- 限售股解禁压力检查
- 市场预期差分析
- 综合输出市场风险等级

## 文件结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── scripts/
    ├── full_scan.py
    ├── global_macro.py
    ├── market_radar.py
    ├── capital_flows.py
    ├── sector_rotation.py
    ├── stock_risk.py
    ├── tech_alert.py
    ├── margin_scan.py
    ├── unlock_calendar.py
    └── expectation_gap.py
```

各文件用途：

- `SKILL.md`：Skill 的触发条件、使用流程和风险说明
- `agents/openai.yaml`：Skill 展示名称和默认调用提示
- `scripts/full_scan.py`：执行完整市场风险扫描
- `scripts/global_macro.py`：扫描全球宏观环境
- `scripts/market_radar.py`：分析A股市场整体风险
- `scripts/capital_flows.py`：分析市场和个股资金流向
- `scripts/sector_rotation.py`：分析行业及板块轮动
- `scripts/stock_risk.py`：检查个股风险
- `scripts/tech_alert.py`：生成技术面风险预警
- `scripts/margin_scan.py`：扫描融资资金风险
- `scripts/unlock_calendar.py`：检查限售股解禁压力
- `scripts/expectation_gap.py`：分析市场预期差

## 环境要求

需要 Python 3，并安装以下依赖：

```bash
pip install pandas numpy
```

同时需要安装并配置 `panda_data`。

## 凭证配置

运行前设置 PandaData 环境变量：

```bash
export PANDADATA_USERNAME="你的账号"
export PANDADATA_PASSWORD="你的密码"
```

不要把账号、密码、Token 或其他敏感信息写入代码或上传到 GitHub。

## 快速运行

### 扫描整体市场风险

```bash
python3 scripts/full_scan.py \
  --out /tmp/a_share_market_risk.json
```

### 扫描市场并加入指定股票

```bash
python3 scripts/full_scan.py \
  --symbols 603501.SH 688808.SH \
  --out /tmp/a_share_market_risk.json
```

## 专项扫描

### 全球宏观环境

```bash
python3 scripts/global_macro.py
```

### A股市场风险

```bash
python3 scripts/market_radar.py
```

### 资金流向

```bash
python3 scripts/capital_flows.py \
  --symbols 603501.SH 688808.SH
```

### 板块轮动

```bash
python3 scripts/sector_rotation.py
```

### 个股风险

```bash
python3 scripts/stock_risk.py 603501.SH
```

### 技术面预警

```bash
python3 scripts/tech_alert.py 603501.SH 688808.SH
```

### 融资资金风险

```bash
python3 scripts/margin_scan.py \
  --symbols 603501.SH 688808.SH
```

### 限售股解禁

```bash
python3 scripts/unlock_calendar.py \
  --symbols 603501.SH 688808.SH
```

### 市场预期差

```bash
python3 scripts/expectation_gap.py \
  --symbols 603501.SH 688808.SH
```

## 风险等级

| 等级 | 含义 |
|---|---|
| `RED` | 多个风险维度出现共振，需要降低风险暴露并进一步核查 |
| `YELLOW` | 部分风险维度异常，需要控制仓位并持续观察 |
| `GREEN` | 当前覆盖维度未发现明显风险共振，但不代表未来没有风险 |
| `UNKNOWN` | 数据不足或接口调用失败，不能将其视为低风险 |

## 输出说明

报告通常包括：

- 扫描时间
- 市场总体风险等级
- 主要风险触发信号
- 指定股票的专项风险
- 数据缺口和接口异常
- 模型及方法限制

分析时应明确区分观测事实与推断结果。

## 使用限制

- 当前评分主要基于经验阈值和信号计数
- 数据接口权限、数据延迟和数据缺失可能影响结果
- 市场走势指标不等同于真实涨跌停家数
- 扫描结果不能替代历史回测、样本外检验和人工研究
- 不应根据单次扫描结果直接作出买卖决策
- 所有输出仅供研究参考，不构成投资建议
