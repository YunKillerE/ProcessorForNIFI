# ProcessorForNIFI

NIFI工具中的processor定制开发，以及简单的使用，包括从RDBMS中抽取数据到hdfs/kafka等，以及从hdfs导出数据到RDBMS/kafka等

# [1. NIFI 基本介绍](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/1.NIFI%E5%9F%BA%E6%9C%AC%E4%BB%8B%E7%BB%8D/NIFI%E5%9F%BA%E6%9C%AC%E4%BB%8B%E7%BB%8D.md)

    NiFi是什么
    NiFi Architecture
    NiFi模块介绍

# 2. NIFI基本使用

[从RDBMS到HDFS](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/2.NIFI%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/%E4%BB%8ERDBMS%E5%88%B0HDFS.md)

[从HDFS到RDBMS](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/2.NIFI%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/%E4%BB%8EHDFS%E5%88%B0RDBMS.md)

[从FTP到KAFKA](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/2.NIFI%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/%E4%BB%8EFTP%E5%88%B0KAFKA.md)

[从FTP到HBase](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/2.NIFI%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/RDBMS%E5%88%B0HBase.md)

# 3. NIFI Processor的开发

[开发流程介绍](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/3.NIFI%20Processor%E7%9A%84%E5%BC%80%E5%8F%91/%E5%BC%80%E5%8F%91%E6%B5%81%E7%A8%8B%E4%BB%8B%E7%BB%8D.md)

[案例1：重写SplitJson，实现数据按行并指定分隔符存储到HDFS](https://github.com/jimmy-src/ProcessorForNIFI/blob/master/3.NIFI%20Processor%E7%9A%84%E5%BC%80%E5%8F%91/%E6%A1%88%E4%BE%8B1.md)

案例2：重写ConvertAvroToJSON，实现数据按行并指定分隔符存储到HDFS，理论上比上面的要高效

案例3：新增Porcessor，实现将AVRO数据转换成按行存储，理论上比上面两个重写的processor效率都要高

# 4. nifi template example

我用过的案例：https://github.com/jimmy-src/ProcessorForNIFI/tree/master/processor_template
hortonworks提供：https://github.com/hortonworks-gallery/nifi-templates

# 5. 环境

idea

nifi 1.2.0

java 1.8

cdh 5.8.4

