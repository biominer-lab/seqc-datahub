# Level1数据文件存储规范

## File Naming Conventions
Please follow the [`Naming Conventions`](./names.md) document.

## Keep Sync with Metadata
After uploading the data files to the following service provider, you need to update the access links to the metadata (datafile entity) within `seqc-datahub`.

After the metadata is updated, you need to submit a pull request to the repo. When the pull request is merged into the master branch, the GitHub action will automatically sync the metadata to the [`DataHub System`](http://datahub.3steps.cn), Then the users can access it to analyze and get the updated metadata and data files.

DataHub System's Website: http://datahub.3steps.cn

## Service Provider
### [AliCloud OpenData](https://www.aliyun.com/acts/opendata#/)

### [NODE - The National Omics Data Encyclopedia](https://www.biosino.org/node/)

### [GSA - Genome Sequence Archive](https://ngdc.cncb.ac.cn/gsa/)

### [SRA - Sequence Read Archive](https://www.ncbi.nlm.nih.gov/sra/)

# Level3数据文件存储规范

## [AliCloud OSS](https://help.aliyun.com/product/31815.html)