# ThermoLink: Bridging disulfide bonds and enzyme thermostability through database construction and machine learning prediction

[English](README.md) | [简体中文](README.zh-CN.md)

本仓库整理用户提供的 ThermoLink 相关二硫键与酶热稳定性工作簿，仅包含数据和说明。统计结果针对本次提供的文件；尚未核验其与论文最终建模数据或当前在线数据库完全一致。

关联论文：Xu, R., et al. (2024). **ThermoLink: Bridging disulfide bonds and enzyme thermostability through database construction and machine learning prediction**. *Protein Science*, 33(9), e5097。[DOI: 10.1002/pro.5097](https://doi.org/10.1002/pro.5097)。

## 文件

- [原始 Excel 工作簿](data/raw/ssbond_database.xlsx)：原样保留，未修改。
- [CSV 数据及统计](data/processed/)：UTF-8 编码；`summary.json` 包含记录数、缺失字段检查、重复编号检查、原表列名和原始文件 SHA-256 校验值。

| 工作表 | 有效记录数 | CSV |
|---|---:|---|
| All datasets | 442 | [all_datasets.csv](data/processed/all_datasets.csv) |
| Increase | 217 | [increase.csv](data/processed/increase.csv) |
| Decrease | 136 | [decrease.csv](data/processed/decrease.csv) |
| No Change | 28 | [no_change.csv](data/processed/no_change.csv) |
| Other | 28 | [other.csv](data/processed/other.csv) |

## 字段说明

| CSV 字段 | Excel 列 / 表头 | 含义 |
|---|---|---|
| record_id | A / Index | 记录编号 |
| reference_url | B / Reference_ID | 原始文献链接 |
| reference_id | C / Reference | 原表文献标识符 |
| protein | D / Protein | 蛋白质名称 |
| organism | E / Organism | 来源物种 |
| uniprot_url | F / Uniprot ID_ID | UniProt 链接 |
| uniprot_id | G / Uniprot ID | UniProt 编号 |
| residue_i | H / AA | 原表 i 位点残基 |
| position_i | I / i | i 位点，保留原始编号 |
| residue_j | J / AA | 原表 j 位点残基 |
| position_j | K / j | j 位点，保留原始编号 |
| thermostability | L / Thermostability | 原始实验结果标签 |

## 数据处理与使用

CSV 仅统一列名、去除单元格首尾空格并跳过全空行，保留记录顺序、标签、位点和拼写；未填补、合并或重新标注数据。数值按文本导出，Excel 格式仅保留在原始工作簿中。

总表包含 244 条 `Increase`、140 条 `Decrease`、21 条 `No change`、8 条 `Less 1` 和 29 条其他结果。分类工作表并非总表的完整、一致划分，其中 No Change 工作表包含 20 条 `No change` 和 8 条 `Less 1`。请勿直接拼接所有工作表，或将各工作表当作训练/测试划分。

建议从 `all_datasets.csv` 开始，并记录研究所采用的筛选规则。不要将含义不明确的标签、表达或活性结果自动映射为热稳定性类别。残基位点编号尚未与序列或结构比对核验。

各工作表内部未发现空字段或重复记录编号，但这不等同于完成生物学质量验证。

## 引用与许可

使用相关研究时请引用上述论文；具体实验记录的原始来源见文献字段。数据再分发许可证尚未指定，论文出版许可不自动作为本仓库的数据许可。
