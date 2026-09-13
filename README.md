# Global Companies Data Guide (Open Edition)

> 全球企业数据开源指南 —— BigPicture 1700 万家企业档案的 AI 时代使用手册。
> 源数据集 License：ODC-BY（可商用可改编，需署名）· 本指南为独立重组导读

## 这是什么

HuggingFace 上 `bigpictureio/companies-2023-q4-sm` 收录全球超 1700 万家企业档案，是当前非商用许可中体量最大的企业基础数据之一（下载量 597+）。

**核心洞察**：公司数据 = 锚点。有了企业 ID 和基本信息，才能挂接海关进出口、展会名录、电商平台等二三级数据——这是外贸/供应链/商研所有场景的地基。

## Schema 核心字段

| 字段 | 说明 | 外贸/商研价值 |
|------|------|-------------|
| `name` | 企业全称 | 品牌识别 / 海关报关 |
| `website` | 官网域名 | 主动开发信 / 竞品监控 |
| `size` | 企业规模 | 采购量级判断 |
| `year_founded` | 成立年份 | 供应商资质筛选 |
| `industry` | 所属行业 | 赛道定位 / NAICS 编码 |
| `city/state/country` | 地理信息 | 物流成本评估 / 原产地核验 |
| `linkedin_url` | LinkedIn 主页 | B2B 触达 / 组织架构研判 |

## 三大主流场景

### 1. 外贸拓客（主动开发）
以产品/行业关键词筛选目标企业 → 抓取 LinkedIn 联系人 → AI 生成个性化开发信。核心动作：行业 + 国家 + 规模三重筛。

### 2. 供应链尽职调查（合规风控）
挂接海关数据，验证进出口记录是否与官网描述匹配；发现"成立 3 年但出口量异常大"的异常信号。
💡 可与 LEI 法人编码数据集（如 zalizedata/global-lei-company-registry-dataset）联合使用，提升企业唯一标识准确率。

### 3. 市场结构分析（选赛道）
以行业 + 国家为维度统计企业数量分布，识别"竞争蓝海"或"过度内卷"市场。适合投资人/展会策划/跨境平台选品团队。

## Freemium 数据架构借鉴（给开发者）

原数据集 README 尾部有付费升级导流（265M 政府核验实体 + NAICS 编码 + 法律实体层级）——这是成熟的商业路径：**用免费 17M 跑通 MVP，再说服用户付费升级**。设计自己的企业数据库产品时可借鉴此分层。

## 快速上手

```python
# 下载数据集（HuggingFace datasets 库）
from datasets import load_dataset
ds = load_dataset("bigpictureio/companies-2023-q4-sm")
# 按行业+国家筛选（示例：美国软件公司）
us_software = ds["train"].filter(lambda x: x["country"]=="US" and x["industry"]=="Software")
```

## License & 来源声明

- 源数据：https://huggingface.co/datasets/bigpictureio/companies-2023-q4-sm （ODC-BY）
- 本指南：CC0 1.0 Universal，可自由使用/修改/商用，署名自愿（欢迎注明 Lunarwave @ lu7897859-tech）
- 加工声明：重组自源数据卡 + 独立增量解读（场景/架构/工作流），非原文搬运

## Keywords

global company data, open database companies, business registry dataset, company search, B2B lead generation, supplier due diligence, market structure analysis, 全球企业数据, 企业数据库, 外贸拓客, ODC-BY dataset, company schema, linkedin url dataset, NAICS industry data, cross-border ecommerce research
