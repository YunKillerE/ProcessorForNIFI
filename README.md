# ProcessorForNIFI

NIFI工具中的processor定制开发，以及简单的使用，包括从RDBMS中抽取数据到hdfs/kafka等，以及从hdfs导出数据到RDBMS/kafka等


# 1. NIFI 基本介绍

    NiFi是什么
    NiFi Architecture
    NiFi模块介绍

# 2. NIFI基本使用

    从RDBMS到HDFS
    从HDFS到RDBMS
    从FTP到KAFKA

# 3. NIFI Processor的开发

    开发流程介绍
    案例1：重写SplitJson，实现数据按行并指定分隔符存储到HDFS
    案例2：重写ConvertAvroToJSON，实现数据按行并指定分隔符存储到HDFS，理论上比上面的要高效
    案例3：新增Porcessor，实现将AVRO数据转换成按行存储，理论上比上面两个重写的processor效率都要高

  


