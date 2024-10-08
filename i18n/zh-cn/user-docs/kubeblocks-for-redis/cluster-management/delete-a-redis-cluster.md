---
title: 删除集群
description: 如何删除集群
keywords: [redis, 删除集群, 删除保护]
sidebar_position: 6
sidebar_label: 删除保护
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# 删除集群

## 终止策略

:::note

终止策略决定了删除集群的方式。

:::

| **terminationPolicy**  | **删除操作**                    |
|:--                     | :--                                       |
| `DoNotTerminate`       | `DoNotTerminate` 禁止删除操作。 |
| `Halt`                 | `Halt` 删除工作负载资源（如 statefulset、deployment 等），但保留 PVC。 |
| `Delete`               | `Delete` 删除工作负载资源和 PVC，但保留备份。 |
| `WipeOut`              | `WipeOut` 删除工作负载资源、PVC 和所有相关资源（包括备份）。|

执行以下命令查看终止策略。

```bash
kbcli cluster list redis-cluster
>
NAME   	        NAMESPACE	CLUSTER-DEFINITION	VERSION        	TERMINATION-POLICY	STATUS 	     CREATED-TIME
redis-cluster	default  	redis    	        redis-7.0.6	    Delete            	Running	     Apr 10,2023 20:27 UTC+0800
```

## 步骤

执行以下命令，删除集群。

```bash
kbcli cluster delete redis-cluster
```
