直接解析 通达信行情服务器协议

## test 202605

PS D:\Thirdprogram\newtdxtqv772\PYPlugins\user> tdxdata_test opentdx.py


~~~
 # 股票列表（带排序过滤）
    print(pd.DataFrame(client.stock_quotes_list(CATEGORY.A, sort_type=SORT_TYPE.TOTAL_AMOUNT)))
~~~

output

~~~
       market    code    close     open     high      low  pre_close  ... short_turnover  min2_amount  opening_rush  vol_rise_speed    depth  active   turnover0
MARKET.SZ  300308  1049.87  1068.99  1099.87  1034.00    1078.00  ...          0.06%  294744064.0         0.00%           0.86%  -16.02%    4756   24925.611
MARKET.SH  688008   247.98   265.00   272.00   242.63     265.08  ...          0.18%  178872320.0         0.00%           0.80%  -55.36%    4755   99900.522

MARKET.SZ  300394   399.99   401.00   414.08   381.91     392.00  ...          0.36%  346271744.0        -0.46%           1.11%  -69.18%    4765   86946.683
MARKET.SZ  300274   152.95   136.00   155.99   131.02     135.03  ...          0.21%  237209600.0         0.00%           0.85%  -79.84%    4778  109094.284
MARKET.SH  601138    67.62    69.50    71.76    67.37      68.60  ...          0.17%  155734016.0         0.00%           0.77%   43.83%    4744   17262.97..
 ...     ...      ...      ...      ...      ...        ...  ...            ...          ...           ...             ...      ...     ...        ...75
MARKET.SZ  300124    77.32    74.49    79.88    74.49      74.42  ...          0.05%   26427904.0         0.00%           0.62%   -7.02%    4747   29836.0776
MARKET.SZ  002015    21.71    23.11    23.60    21.20      23.50  ...          0.55%   36787200.0         2.53%           0.89%  -66.83%    4743  154027.7277
MARKET.SH  688072   529.94   493.00   565.00   472.06     493.00  ...          0.07%   21304832.0         0.00%           0.59%  -54.67%    4386   37391.4478
MARKET.SZ  000063    36.71    37.64    38.29    36.58      37.56  ...          0.09%   51426816.0         0.21%           0.91%   73.82%    4742   36489.8579
MARKET.SZ  300757   589.98   605.00   620.00   580.79     589.00  ...          0.19%   57696256.0        -0.15%           1.01%  -56.29%    4390   60693.20

~~~



~~~
from datetime import date

import pandas as pd
from opentdx.tdxClient import TdxClient
from opentdx.const import MARKET, CATEGORY, EX_MARKET, PERIOD, SORT_TYPE

if __name__ == "__main__":
  with TdxClient() as client:
 
    # 历史成交
    print(pd.DataFrame(client.stock_transaction(MARKET.SZ, '301487', date(2026, 4, 28))))    
~~~

output

~~~
          time  price   vol   action  unknown
0     09:25:00  23.00   163  NEUTRAL        0
1     09:30:00  23.11   155      BUY        0
2     09:30:00  23.11    62      BUY        0
3     09:30:00  23.04    56     SELL        0
4     09:30:00  23.02    64     SELL        0
...        ...    ...   ...      ...      ...
3406  14:56:00  22.81     6      BUY        0
3407  14:56:00  22.78     4     SELL        0
3408  14:56:00  22.80     3      BUY        0
3409  14:57:00  22.78     1     SELL        0
3410  15:00:00  22.78  1424  NEUTRAL        0

[3411 rows x 5 columns]

~~~

获取个股F10

~~~
from datetime import date

import pandas as pd
from opentdx.tdxClient import TdxClient
from opentdx.const import MARKET, CATEGORY, EX_MARKET, PERIOD, SORT_TYPE

if __name__ == "__main__":
  with TdxClient() as client:
 
    # 获取个股F10
    print(pd.DataFrame(client.stock_f10(MARKET.SZ, '301487'))) 
~~~

output

~~~
    name                                            content
0   最新提示  最新提示☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
1   公司概况  公司概况☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
2   财务分析  财务分析☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
3   股本结构  股本结构☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
4   股东研究  股东研究☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
5   机构持股  机构持股☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
6   分红融资  分红融资☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
7   高管治理  高管治理☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
8   资金动向  资金动向☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
9   资本运作  资本运作☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
10  热点题材  热点题材☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
11  公司公告  公司公告☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
12  公司报道  公司报道☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
13  经营分析  经营分析☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
14  行业分析  行业分析☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
15  研报评级  研报评级☆ ◇301487 盟固利 更新日期：2026-05-15◇ 通达信沪深京F10\r...
16  除权分红  [{'market': MARKET.SZ, 'code': b'301487', 'dat...
17    财报  {'market': MARKET.SZ, 'code': '301487', 'liuto...

~~~





# opentdx — Python TDX 量化行情数据接口

项目创意来自[`pytdx`](https://github.com/rainx/pytdx)

感谢[@rainx](https://github.com/rainx)迈出的第一步

### ✨ 声明

> 本项目为个人**学习项目，并非已完成的开箱即用的产品**，仅用于学习交流
>
> 对于数据有迫切需求的朋友，通达信新推出了[官方量化平台](https://help.tdx.com.cn/quant/)，建议食用。

> 由于项目连接的是通达信客户端明文公开的服务器，是财富趋势科技公司既有的行情软件兼容行情服务器，只是简单整理便于大家学习，**严禁**用于任何**商业用途**，更**严禁滥用接口**，对此造成的任何问题本人概不负责。

又因本项目在持续推进中，接口**难免会有大幅改动，带来的不便请予宽宥**。

> ### 应biner建议，本项目精简为基础数据接口库，mcp相关将移动到 [tdx_mcp](https://github.com/LisonEvf/tdx_mcp)
> ### 又因pytdx2库名rainx已经用了，因此本库改名为opentdx，再次致敬rainx
> ### 又又，协议基本完成解析了，后期就着力于 [tdx_mcp](https://github.com/LisonEvf/tdx_mcp)了和少量组合技接口


## 主要功能

| 功能 | 说明 | 新增 |
|------|------| -|
| 股票行情 | A股、创业板、科创板、北交所 | ✅支持北交所 | 
| 扩展行情 | 期货、港股、美股、期权等 | ✅支持AH股关联查询 |
| K线数据 | 多周期（1分/5分/日线/周线等）|  ✅支持复权、即时换手率 |
| 分时图 | 实时/历史分时数据 | |
| 排行榜 | 涨跌幅、振幅、换手率等 |  |
| 板块数据 | 行业/地区/概念板块列表及成分股 | 🌟 板块K线数据 | 
| 异动监控 | 主力监控精灵数据 | |
| F10资料 | 公司基本信息、财报 | |

## 安装

```bash
pip install opentdx

```

## 指南

```bash
opentdx doc 
```

## 快速上手

```python
from datetime import date

import pandas as pd
from opentdx.tdxClient import TdxClient
from opentdx.const import MARKET, CATEGORY, EX_MARKET, PERIOD, SORT_TYPE

if __name__ == "__main__":
  with TdxClient() as client:
    # 指数信息
    print(pd.DataFrame(client.index_info([(MARKET.SH, '999999'), (MARKET.SZ, '399001')])))
    # 股票列表（带排序过滤）
    print(pd.DataFrame(client.stock_quotes_list(CATEGORY.A, sortType=SORT_TYPE.TOTAL_AMOUNT)))
    # 股票报价
    print(pd.DataFrame(client.stock_quotes(MARKET.SZ, '000001')))
    # 获取行情全景
    for name, board in client.stock_top_board().items():
        print(f"榜单：{name}")
        print(pd.DataFrame(board))
    # 获取k线
    print(pd.DataFrame(client.stock_kline(MARKET.SZ, '000001', PERIOD.DAILY)))
    # 获取指数k线
    print(pd.DataFrame(client.stock_kline(MARKET.SH, '999999', PERIOD.MINS, times=10)))
    # 获取历史分时
    print(pd.DataFrame(client.stock_tick_chart(MARKET.SZ, '000001', date(2026, 3, 16))))
    # 获取个股F10
    print(pd.DataFrame(client.stock_f10(MARKET.SZ, '000001')))
    # 历史成交
    print(pd.DataFrame(client.stock_transaction(MARKET.SZ, '000001', date(2024, 1, 15))))
    
    # 期货K线
    print(pd.DataFrame(client.goods_kline(EX_MARKET.SH_FUTURES, 'AUL8', PERIOD.DAILY)))
    # 获取扩展市场行情列表
    print(pd.DataFrame(client.goods_quotes_list(EX_MARKET.SH_FUTURES, count=5)))
    # 获取美股K线
    print(pd.DataFrame(client.goods_kline(EX_MARKET.US_STOCK, 'TSLA', PERIOD.DAILY)))
    # 美股行情
    print(pd.DataFrame(client.goods_quotes(EX_MARKET.US_STOCK, 'TSLA')))
```

### 🌟 本项目亮点

- ✅ **整体重构**：更加简洁易读
- ✅ **协议简化**：明确了一些协议的细节，更加清晰易懂
- ✅ **自动选服**：自动检查服务器连接速度，并选择最快的服务器
- ✅ **主力监控**：新增异动消息的获取
- ✅ **板块列表**：像 `通达信`一样根据板块获取股票列表，支持 `深市`、`沪市`、`创业板`、`科创板`、`北交所`
- ✅ **扩展行情**：支持 `期货`、`期权`、`债券`、`基金`、`港股`、`美股`等行情的获取
- ✅ **交互式文档**：```python doc.py```一键开启项目探索

#量化交易 #TDX接口 #Python金融

---

[![Star History Chart](https://api.star-history.com/svg?repos=LisonEvf/opentdx&type=Date)](https://star-history.com/#LisonEvf/opentdx&Date)
