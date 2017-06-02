# 需求

从RDBMS抽取数据到HDFS，这里从oracle，其他关系型数据库都差不多

# 总流程

<img src="https://github.com/jimmy-src/ProcessorForNIFI/blob/master/image/oralce2hdfs.png" width = "600" height = "400" alt="图片名称" align=center />

详细过程参考template

[oracle到hdfs的template](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/processor_template/OracleTohdfsAndhdfsToOracle.xml)

# 每一步配置

## 从oracle查询数据出来

<img src="https://github.com/jimmy-src/ProcessorForNIFI/blob/master/image/oracle2hdfs_step1.png" width = "600" height = "400" alt="图片名称" align=center />

点击数据库连接池创建一个连接，接着点击右边那个箭头进行连接池配置

<img src="https://github.com/jimmy-src/ProcessorForNIFI/blob/master/image/oracle2hdfs_conpool.png" width = "600" height = "400" alt="图片名称" align=center />


