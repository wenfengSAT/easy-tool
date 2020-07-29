<h1 align="center">常用SQL的语句汇总</h1>

本文收集了一些在开发过程中常用SQL的语句汇总，也欢迎大家补充。

## 1.1 MySQL数据修复常用SQL
### 常见SQL
有异常数据需要修复时，可能用到以下SQL

```
# 表备份SQL
create table tableName_20200604_bak as select * from tableNmael WHERE id IN('202003301526315761','202003310858300900','202003301646584072');

# 新增字段
ALTER TABLE tableName
ADD COLUMN column1 varchar(200) NULL DEFAULT ''  COMMENT '备注' ,
ADD COLUMN column2 datetime NULL  COMMENT '备注' ,
ADD COLUMN column3 int(11)  DEFAULT 0  COMMENT '备注' ;

# 增加索引
ALTER TABLE tableName ADD INDEX iddex_name (column_name);


#删除唯一约束
drop index unique_name on tableName;

# 增加唯一约束
alter table tableName add unique(column_name)

#修复数据
update tableName set column1 = concat('xxxx',column2);
update tableName set column1 = 'xxx' where column2 like 'xxx%';

# 修改字段长度
alter table tableName modify column column1 longtext,
modify column column2 numeric(18,0),
modify column column3 int(11),
modify column column3 varchar(11);


```
