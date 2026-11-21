# 五笔 86 方案包

本包提供三个 [Rime](https://github.com/rime/rime) schema，与官方同名，作为 drop-in 替换使用：

- `wubi86`：主方案，单字表 + 按类目拆分的词表。
- `wubi_pinyin`：五笔 + 拼音混输，共用同一份主词表。
- `wubi_trad`：简入繁出，共用同一份主词表。

三个 schema 的差异只在字/词库结构、反查前缀与转换过滤器；主词表 `wubi86.dict.yaml` 共用。

## 包内文件

- `wubi86.schema.yaml`、`wubi_pinyin.schema.yaml`、`wubi_trad.schema.yaml`
- `wubi86.dict.yaml`（主表，用 `import_tables` 汇总）
- `wubi86.zi.dict.yaml`（字表）
- `wubi86.ci.<slug>.dict.yaml`（按类目拆分的词表）
- `README.md`、`LICENSE`

本包不提供 `.custom.yaml`。

## 安装与覆盖风险

把本目录的全部文件复制到 Rime 用户配置目录，重新部署后在方案列表选择需要的 schema。

三个 schema 与官方同名，部署后会遮蔽官方三件套。已有的 `wubi86.custom.yaml`、同名用户词典与同步目录会继续作用于本方案；升级或试用前请先备份用户配置，必要时清理同名 custom 与 userdb。本包的用户词典与同步沿用 Rime 默认设置，不提供相关配置。

## 依赖

- `pinyin_simp`：拼音反查，三个 schema 均依赖，需先在 Rime 中安装袖珍简化字拼音方案。
- [OpenCC](https://github.com/BYVoid/OpenCC) 与 `s2t.json`：仅 `wubi_trad` 使用，作为运行时依赖，不随包分发。

## 裁剪类目

编辑 `wubi86.dict.yaml` 的 `import_tables`，注释掉不需要的类目行后重新部署。分发的词表与物料类目一一对应；`wubi86.zi` 字表应保留。

## 许可

本包采用 [LGPL-3.0](LICENSE)。随包发布的纯词库物料采用 [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)。本包按现状提供，不附带任何明示或暗示的担保。

类目名称与代码参照 [GB/T 20093-2022](https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=88537A39BE1C3D1B5C6294F70838096E)，地名参照 [GB/T 2260](https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=C9C488FD717AFDCD52157F41C3302C6D) / [GB/T 2659](https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=FBCE39BE204B54F6F944092C209121F2)；标准只引用不复刻，标准原文不随包分发。
