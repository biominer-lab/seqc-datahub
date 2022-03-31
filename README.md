# DataHub for SEQC Project

[![Latest Release](https://img.shields.io/github/release/biominer-lab/seqc-datahub.svg?label=Latest%20Release)](https://github.com/biominer-lab/seqc-datahub/releases)

SEQC Datahub仓库用于管理本组织收集整理的多组学质量控制相关数据集及制定的数据管理规范文档等。其中一个数据集可以由一到多个项目的Metadata表格文件组成，但推荐一个数据集对应一个项目，并以项目名命名。但在下游整合分析场景时，有需求构建Level3数据合集，可考虑创建包含多个项目的数据集，以具体分析目的命名；

仓库结构如下：

```
目录说明：
|- .github/                          -> 存放持续集成与持续发布相关脚本文件，当仓库数据文件更新时触发系统将Metadata自动更新至Metabase
|- data/                             -> 存放数据集关联的Metadata表格文件（每个项目一个子文件夹，每个子文件夹中包含若干实体描述文件，具体参考规范文档）
|    |- <标准物质名称>_RNA/
|    |       |- project/
|    |       |- donor/
|    |       |- biospecimen/
|    |       |- reference_materials/
|    |       |- library/
|    |       |- sequencing/
|    |       |- datafile/
|    |       |- README.md
|- docs/                             -> 存放规范文档，含字段声明、管理模式、更新要求等
|- README.md                         -> 快速指南
|- CHANGELOG                         -> 数据集版本变更说明
|- LICENSE                           -> 版权声明文件
```

## Datasets
1. [MAQC RNA](./data/MAQC_RNA/)

## The Specification for Data Management

1. [Naming Conventions](./docs/names.md)
2. [Metadata Specifications](./docs/metadata.md)
3. [Level1/3数据文件存放规范](./docs/datafile.md)
4. [Apps - 标准化分析流程](./docs/apps.md)

## Metadata Validation

1. [JSON Schemas for Metadata](./specs/metadata.json)
2. [Metadata Validator](https://github.com/biominer-lab/metadata-validator.git)


## Contribution Guidelines