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
|    |       |- README.md
|- docs/                             -> 存放规范文档，含字段声明、管理模式、更新要求等
|- README.md                         -> 快速指南
|- CHANGELOG                         -> 数据集版本变更说明
|- LICENSE                           -> 版权声明文件
```

## 数据集

## 数据集与Metadata管理方案

1. 数据集由符合指定规范的Metadata表格文件组成，其中Level1-3数据文件存放在`数据仓库(GSA/NODE/SRA/ENA的统称)`并以链接形式记录在Metadata表格中；
2. 实体、属性与关系的设计需要在数据采集清理难度与尽可能还原真实之间进行权衡；
3. 数据上传时多采用TSV/CSV/JSON/XML格式文件，尤其是前两者最常用，对用户最友好；
4. 实体间关系多数属于一对一或一对多，因此，可以考虑采用以下方式管理元数据文件，而对于存在多对多关系的实体则特殊处理；

   ```
   # 目录结构，每个实体一个目录，每个目录下放置N个Batch文件，每个Batch包含100条左右记录
   |- program
   |    |- program-2021-03-18.csv
   |- project
   |    |- project-2021-03-18.csv
   |- donor (Each file contains a project_id to be associate to the project file. 100 records/Batch)
   |    |- donor-2021-03-18.csv (Batch 1)
   |    |- donor-2021-03-19.csv (Batch 2)
   ```

   :exclamation: 哪些实体间可能存在多对多关系？(待讨论) :exclamation:

   :exclamation: 如何通过TSV/CSV文件来记录多对多关系？(待讨论) :exclamation:

5. Metabase管理Metadata时，采用`实体表`与`合并表`共存的策略来平衡易用性与录入便利性
   
   策略：在每一个实体对应一个表的方案不变的基础上，依据常见需求由数据导入程序自动生成合并表，如由所有实体子表合并而成的总表(表名为`full_metadata`)

   ```
   # 导入程序处理后
    |- [实体子表] project.csv
    |- [实体子表] donor.csv
    |- [总表] full_metadata.csv
   ```

## 数据管理规范细则

1. [Metadata标准与规范](./docs/metadata.md)
2. [Level1/3数据文件存放规范](./docs/datafile.md)
3. [Apps - 标准化分析流程](./docs/apps.md)
4. [命名规范](./docs/names.md)


## Contribution Guidelines