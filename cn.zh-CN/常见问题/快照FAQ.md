# 快照FAQ {#concept_j5z_vrr_lgb .concept}

本文汇总了使用云服务器ECS快照时的常见问题。

-   对象存储OSS相关问题
    -   [如果我已经开通了OSS，快照会自动存到我的OSS Bucket吗？](intl.zh-CN/快照/快照FAQ.md#section_wnf_qh1_4gb)
    -   [使用快照创建了自定义镜像后，可以将镜像存到OSS Bucket吗？](#section_agb_789_ug8)
-   计费问题
    -   [快照采用什么计费方式，有案例吗？](#section_svk_hax_cq5)
    -   [\#section\_27q\_hxw\_8v0](#section_27q_hxw_8v0)
    -   [如何查看不同地域下快照价格？](#section_nom_iuk_an9)
    -   [账号欠费对快照有什么影响？](#section_qs5_lyg_4gb)
    -   [快照使用相对频繁的话我如何降低使用成本？](#section_75v_zgn_06k)
-   快照类型和块存储类型问题
    -   [手动快照和自动快照有区别或冲突吗？](#section_vj5_5ws_ngb)
    -   [本地盘支持创建快照吗？](#section_8bp_ymj_xsh)
    -   [用加密数据盘创建快照并生成镜像，无法共享镜像怎么办？](#section_m0o_tpa_pb2)
-   快照容量问题
    -   [在ECS实例内删除文件会减少空间占用吗？](#section_akt_4yg_4gb)
    -   [为什么快照容量大于文件系统内看到的数据量？](#section_rr2_pyg_4gb)
    -   [文件系统与云盘和快照有什么关系？](#section_tsa_qqu_wdx)
-   删除快照问题
    -   [我如何保留快照，避免被阿里云删除？](#section_wj5_5ws_ngb)
    -   [我如何删除快照，降低备份使用成本？](#section_pjl_hqz_ngb)
    -   [更换系统盘、实例到期或释放云盘后，自动快照会被删除吗？](#section_ck5_5ws_ngb)
    -   [如何删除已创建了镜像、云盘的快照？](#section_hji_juh_uhk)
-   自动快照策略问题
    -   [如果我用自动快照创建自定义镜像或云盘，执行快照策略会失败吗？](#section_xj5_5ws_ngb)
    -   [一块云盘能否设置多个自动快照策略？](#section_dx2_bzg_4gb)
-   使用快照回滚云盘问题
    -   [怎么避免错误操作引起的数据丢失？](#section_oou_9ap_jvp)
    -   [更换系统盘后，历史系统盘快照能否用于回滚新的系统盘？](#section_hpz_qkh_mgb)

## 如果我已经开通了OSS，快照会自动存到我的OSS Bucket吗？ {#section_wnf_qh1_4gb .section}

不会自动保存到已有的OSS Bucket。快照存放的位置与您自建的OSS Bucket相互独立，您无需为快照创建新的Bucket。

## 使用快照创建了自定义镜像后，可以将镜像存到OSS Bucket吗？ {#section_agb_789_ug8 .section}

可以。您可以通过导出镜像的方式，镜像会导出到您设置的OSS Bucket中供您下载。详细步骤请参见[导出镜像](../../../../intl.zh-CN/镜像/自定义镜像/导出镜像.md#)。但是，自定义镜像无法直接存储到OSS Bucket。

## 快照采用什么计费方式，有案例吗？ {#section_svk_hax_cq5 .section}

快照即将商业化并实行按量付费计费方式，单GiB价格与OSS标准型存储一致，单位为USD/GiB/月。阿里云各地域的快照价格表请参见[云服务器ECS产品详情页](https://www.alibabacloud.com/product/ecs)。快照商业化时间请关注阿里云公告。

有关按量付费的案例，请参见[快照计费方式](../../../../intl.zh-CN/产品定价/快照计费方式.md#)。

## 如何查看不同地域下快照价格？ {#section_nom_iuk_an9 .section}

单GiB价格与OSS标准型存储一致，单位为USD/GiB/月。阿里云各地域的快照价格表请参见[云服务器ECS产品详情页](https://www.alibabacloud.com/product/ecs)的定价页面。向下滚动鼠标至**快照价格**处，根据地域查看价格列表。您也可以单击**Download price**下载CSV或者JSON格式的价格列表。

![Download price](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10124/156575844851569_zh-CN.png)

## 账号欠费对快照有什么影响？ {#section_qs5_lyg_4gb .section}

账号欠费24小时后会停止快照服务。从欠费之日起：

-   15天内，保留所有快照，停止创建自动快照。保留时间小于15天的自动快照会被正常清理。
-   15天后，除了创建过云盘或自定义镜像的快照，其余快照都会被删除。

欠费后，您可以充值账号恢复服务。详细步骤请参见[充值介绍](https://help.aliyun.com/knowledge_list/37106.htm)。

## 快照使用相对频繁的话我如何降低使用成本？ {#section_75v_zgn_06k .section}

建议您保留合适数量的快照并定时删除不再需要的快照。更多详情，请参见[优化快照使用成本](intl.zh-CN/快照/使用快照/优化快照使用成本.md#)。

## 手动快照和自动快照有区别或冲突吗？ {#section_vj5_5ws_ngb .section}

没有。本质上，手动快照和自动快照都是某一时间点一块云盘和共享块存储的数据状态文件。但是，如果某一块云盘正在创建自动快照时，您需要等待自动快照完成后，才能手动创建快照。

## 本地盘支持创建快照吗？ {#section_8bp_ymj_xsh .section}

不支持。建议您在应用层做好数据冗余处理，或者为集群创建部署集，提高应用的高可用性。

## 用加密数据盘创建快照并生成镜像，无法共享镜像怎么办？ {#section_m0o_tpa_pb2 .section}

为保证数据的私密性，使用加密快照创建的自定义镜像无法共享镜像。建议您使用非加密快照创建自定义镜像，然后共享给其他用户。

## 在ECS实例内删除文件会减少空间占用吗？ {#section_akt_4yg_4gb .section}

不会。删除文件操作相当于在需要删除的文件头部做删除标记，并不会减少云盘本身的空间占用。

## 为什么快照容量大于文件系统内看到的数据量？ {#section_rr2_pyg_4gb .section}

-   问题现象：您在ECS实例内删除文件后再创建快照，发现快照容量并没有变小，或者快照比从文件系统查询到的云盘占用空间大。
-   原因分析：格式化文件系统操作、删除文件操作以及写入数据操作都会使得云盘空块数量不断减少，减弱了创建快照时消除空块的能力。因此，您看到快照容量比文件系统内展示的数据量要大。以下原因可能造成文件系统与快照大小不一致：
    -   文件系统的元数据会占用磁盘空间。
    -   文件系统在初始化阶段被写入大量数据块（Block，指磁盘的逻辑块地址LBA被块存储划分为相同大小的块），写入数据操作会占用磁盘空间。
    -   文件系统为了降低性能消耗，删除文件时只在文件属性中创建弃用标记。磁盘无法感知删除指令，数据块仍然是已分配状态，同时数据块会被拷贝到快照中，导致快照容量大于文件系统。
    -   虚拟化驱动KVM的Virtio-block和Xen的Block-front等模块不支持TRIM指令（磁盘I/O指令，提示逻辑块地址LBA上的某段数据不再使用，可以被删除），磁盘无法感知数据可以被删除。

## 文件系统与云盘和快照有什么关系？ {#section_tsa_qqu_wdx .section}

您在磁盘分区上创建的是文件系统。文件系统负责管理磁盘空间，管理操作最终均转化为磁盘的I/O请求。磁盘会记录数据块状态，按需将数据一并拷贝到对象存储OSS，这就是创建快照的过程。文件系统与快照之间的关系如下图所示：

![文件系统与云盘和快照的关系](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10122/156575844839434_zh-CN.png)

**说明：** 上图中，只要被写过数据的数据块，即使在磁盘中的相关文件已经被删除，数据块仍会被记录到快照中。文件系统中所谓删除只是在需要删除的文件头部做个标记，让您知道这块空间可以利用了，不会减少磁盘本身的空间占用。

## 我如何保留快照，避免被阿里云删除？ {#section_wj5_5ws_ngb .section}

-   手动快照：无论您是否执行了释放云盘或者释放实例操作，阿里云均不会删除您自行创建的快照。
-   自动快照：可以[修改自动快照策略](intl.zh-CN/快照/使用自动快照策略/修改自动快照策略.md#)的**保留时间**属性为**持续保留**，直至云盘达到快照额度后（当前为64份快照），系统会自动删除创建时间最早的自动快照。

## 我如何删除快照，降低备份使用成本？ {#section_pjl_hqz_ngb .section}

-   手动快照：自行删除手动快照。
-   自动快照：您可以自行删除自动快照。或者等待云盘达到快照额度后，创建时间最早的自动快照会被系统删除。

## 更换系统盘、实例到期或释放云盘后，自动快照会被删除吗？ {#section_ck5_5ws_ngb .section}

-   自动快照策略设置了**自动快照随磁盘释放**属性：自动快照会被删除。
-   自动快照策略取消了**自动快照随磁盘释放**属性：自动快照遵循快照策略的保留时间设置。如有需要，您可以[修改自动快照策略](intl.zh-CN/快照/使用自动快照策略/修改自动快照策略.md#)。

## 如何删除已创建了镜像、云盘的快照？ {#section_hji_juh_uhk .section}

-   创建过云盘的快照，可以单独删除。删除快照后，您无法操作依赖于原始快照数据状态的业务，例如[重新初始化云盘](../../../../intl.zh-CN/块存储/云盘/重新初始化云盘/重新初始化系统盘.md#)。
-   创建过自定义镜像的快照，必须预先删除所对应的镜像，才能删除快照。
-   创建过实例的镜像，可以单独删除。删除镜像后，您无法操作依赖于原始快照数据状态的业务，例如[重新初始化云盘](../../../../intl.zh-CN/块存储/云盘/重新初始化云盘/重新初始化系统盘.md#)。

## 如果我用自动快照创建自定义镜像或云盘，执行快照策略会失败吗？ {#section_xj5_5ws_ngb .section}

不会。

## 一块云盘能否设置多个自动快照策略？ {#section_dx2_bzg_4gb .section}

不能。

## 怎么避免错误操作引起的数据丢失？ {#section_oou_9ap_jvp .section}

在有操作风险的场景中，您可以提前创建快照备份数据。例如修改关键系统文件、实例从经典网络迁移至专有网络VPC、日常数据备份、实例误释放恢复、预防网络攻击、更换操作系统、为生产环境提供数据支撑和其他具有操作风险的场景。出现错误操作时，您可以及时回滚云盘，降低风险。详情请参见[创建快照](intl.zh-CN/快照/使用快照/创建快照.md#)和[使用快照回滚云盘](intl.zh-CN/快照/使用快照/使用快照回滚云盘.md#)。

## 更换系统盘后，历史系统盘快照能否用于回滚新的系统盘？ {#section_hpz_qkh_mgb .section}

不能。

