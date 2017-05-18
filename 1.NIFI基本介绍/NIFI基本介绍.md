# 背景

大数据集成的困境讲到大数据，我们首先要有数据。没有数据，是大数据研究的第一个困境。

访问真正的大规模数据集，是一项大公司的数据科学家所有的特权，大多数学术研究人员缺无法触及。

比如数据是机器学习研究的命门。2016年1月14日，雅虎实验室对外发布了史上最大规模的机器学习数据集（雅虎新闻种子数据集，记录了2015年2月至5月间2千万用户约1100 亿个事件），达 13.5 TB。

这令业界非常欣喜，因为外部研究人员可以基于这个数据集研究新算法或新方法的应用。关于这个数据可以参考 Yahoo News Feed Datasethttp://webscope.sandbox.yahoo.com/catalog.php?datatype=r&did=75

对于企业来说如何利用数据呢？

可以分为三个阶段:

    1 充分利用企业内部已有的数据，比如CRM系统，OA系统，企业资金管理系统等
    
    2 企业借助外部数据发展业务，比如投资公司使用互联网数据来判断股票的热度
    
    3 企业将数据变成产品，比如天气数据、金融数据都可以在数据市场上交易,实现数据变
    
当务之急，就是企业需要快速高效的集成内部和外部的数据。那么大数据集成的困境是什么呢？系统连接的困境：企业数据孤岛。 集团公司各个子公司之间的数据孤立，公司的各个系统孤立，数据的物理存储和逻辑结构孤立。

数据获取的困境：繁杂专用获取数据工具。 每一个系统都有专用的数据获取工具，不同的数据格式有不同的工具。

那么我们需要的是什么？

在统一的平台上自动化数据在不同类型系统间的流动， 将各类异构数据导入到大数据环境NiFi的出现正好可以解决这两大困境。



# NIFI是什么

Apache NiFi 是一个易于使用、功能强大而且可靠的数据拉取、数据处理和分发系统。Apache NiFi 是为数据流设计。它支持高度可配置的指示图的数据路由、转换和系统中介逻辑，支持从多种数据源动态拉取数据。NiFi原来是NSA的一个项目，现在开源出来，由Apache基金会进行管理。

<img src="http://nifi.apache.org/assets/images/flow-th.png" width = "300" height = "200" alt="图片名称" align=center />

NiFi是基于Java的，使用Maven支持包的构建管理。 NiFi基于Web方式工作，后台在服务器上进行调度。可以为数据处理定义一个流程，然后进行处理，后台具有数据处理引擎、任务调度等组件。

# NiFi Architecture

## 单机模式 & 集群模式

http://img10.weixinnu.com/article/getImage.php?url=http://cdn.read.html5.qq.com/image?src=tag&r=8&imageUrl=http%3A%2F%2Fmmbiz%2Eqpic%2Ecn%2Fmmbiz%2FA0SiaGa3pvSS4B2vwxicajhmjY4cKlqjIwpw4UPFYpibpdEz40qTibv0aGV17gyeJg21wgNTXZoeiahHdqlyaicBMXpg%2F0%3Fwx%5Ffmt%3Dpng&referUrl=http%3A%2F%2Fmp%2Eweixin%2Eqq%2Ecom%2Fs%3F%5F%5Fbiz%3DMzI2MjE0MDUzNg%3D%3D%26idx%3D1%26mid%3D2652914277%26sn%3D20a55251ac5603a1f77027350e011665

<img src="http://img10.weixinnu.com/article/getImage.php?url=http://cdn.read.html5.qq.com/image?src=tag&r=8&imageUrl=http%3A%2F%2Fmmbiz%2Eqpic%2Ecn%2Fmmbiz%2FA0SiaGa3pvSS4B2vwxicajhmjY4cKlqjIwpw4UPFYpibpdEz40qTibv0aGV17gyeJg21wgNTXZoeiahHdqlyaicBMXpg%2F0%3Fwx%5Ffmt%3Dpng&referUrl=http%3A%2F%2Fmp%2Eweixin%2Eqq%2Ecom%2Fs%3F%5F%5Fbiz%3DMzI2MjE0MDUzNg%3D%3D%26idx%3D1%26mid%3D2652914277%26sn%3D20a55251ac5603a1f77027350e011665" width = "300" height = "200" alt="图片名称" align=center />

单机模式 在一台主机上，同一个Java虚拟机里，运行一个WebServer, 和Flow Controller。 FlowController 是NiFi的心脏。他负责处理器(processor)的调度，FlowFile 的路由控制等核心功能。存储池主要有三类，FlowFile池（文件属性等信息），Content池（用户数据），Provenance池(数据的变迁信息)

集群模式 图的右侧 集群模式,采用主从架构。引入了一个集群管理器NiFi Cluster Manager (NCM)。NCM由Web Server 和请求复制器组成。 他同时也负责管理节点进入和退出集群。NiFi Nodes, 互相独立的运行流程，需要交互的地方通过SharedCache来共享数据。

## NiFi的特点

基于网页的用户界面: 数据流设计，控制，反馈和监控各方面的无缝体验。

数据投递有保障: 

    数据投递的保证性(Guaranteeddelivery)通过专门开发的持久化的预写日志(WAL)和内容仓库来实现。

数据缓冲:

    数据缓存具有反压和释放压机制

高度可配置:

    数据吞吐量(Low latency vs high throughput)；
    动态优先级(Dynamic prioritization）；
    运行时数据流调整(Flow can be modified at runtime)；
    反压机制(Back pressure)

数据跟踪:

    从始致终的数据历史跟踪

## 安全
   
* 提供各种安全的传输方式(SSL, SSH, HTTPS)
   
* 可以对内容加密
   
* 可插拔的基于角色的认证和授权

## NiFi核心理念

基于数据流的编程 Flow-Based Programming(FBP)。应用是由处理器黑盒，连接器组成的网络。数据进入一个节点，由该节点对数据进行处理，根据不同的处理结果将数据路由到后续的其他节点进行处理。这是NiFi的流程比较容易可视化的一个原因。关于FBP 大家可以参考http://www.jpaulmorrison.com/fbp/

## NIFI基本概念

<img src="http://img10.weixinnu.com/article/getImage.php?url=http://cdn.read.html5.qq.com/image?src=tag&r=8&imageUrl=http%3A%2F%2Fmmbiz%2Eqpic%2Ecn%2Fmmbiz%2FA0SiaGa3pvSS4B2vwxicajhmjY4cKlqjIwNOeKU8ITwRSfLUuxl2v7TYibS3eCodKFLibLkCFY2m7N6iaBQV9HxwmFQ%2F0%3Fwx%5Ffmt%3Dpng&referUrl=http%3A%2F%2Fmp%2Eweixin%2Eqq%2Ecom%2Fs%3F%5F%5Fbiz%3DMzI2MjE0MDUzNg%3D%3D%26idx%3D1%26mid%3D2652914277%26sn%3D20a55251ac5603a1f77027350e011665" width = "300" height = "200" alt="图片名称" align=center />

NiFi的基本概念时主要参照FBP的概念进行对照。具体见上述表格。

简单来讲 FlowFile 是在各个节点间流动的数据；

FlowFileProcessor 是数据的处理模块；

Connection是各个处理模块间的一个队列；

Flow Controller。复杂流程的调度；

Process Group分装流程的层次关系。

# NiFi主要模块介绍

NiFi的琳琅满目的模块是 NiFi的强大之处，正是因为有了这些模块，我们可以不用写代码就可以实现数据的处理。

NiFi主要模块分三类: Processors, Controller Services,Reporting Tasks

1. Processor是实际操作数据的模块 。

Processor负责创建，接收，发送，转换,路由，拆分，合并，处理FlowFile。 NiFi中提供了丰富的Processor，来帮助我们进行各种数据处理。

2. ControllerService提供服务给Processor使用。

比如StandardSSLContextService可以管理KeyStore和TrustStore,这样所有需要SSL服务的Processor都可以使用统一的SSL服务，而不用每个都独立配置。

3. Report Task在后台运行，提供NiFi运行的统计报告。

典型的ReportTask有ControllerStatusReportingTask，MonitorDiskUsage ，MonitorMemory 等。


本文来源：http://www.weixinnu.com/tag/article/47458000

详细可以参考官方文档：

    http://nifi.apache.org/docs.html
    
    