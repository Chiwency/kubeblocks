---
title: Switch over a MongoDB cluster
description: How to switch over a MongoDB cluster
keywords: [mongodb, switch over a cluster, switchover]
sidebar_position: 6
sidebar_label: Switchover
---


# Switch over a MongoDB cluster

You can initiate a switchover for a MongoDB ReplicaSet. Then KubeBlocks modifies the instance roles.

## Before you start

* Make sure the cluster is running normally.
* Check whether the following role probe parameters exist to verify whether the role probe is enabled.

   ```bash
   kubectl get cd mongodb -o yaml
   >
   probes:
     roleProbe:
       failureThreshold: 3
       periodSeconds: 2
       timeoutSeconds: 2
   ```

## Initiate the switchover

You can switch over a secondary of a MongoDB ReplicaSet to the primary role, and the former primary instance to a secondary.

* Switchover with no primary instance specified

    ```bash
    kbcli cluster promote mycluster
    ```

* Switchover with a specified new primary instance

    ```bash
    kbcli cluster promote mycluster --instance='mycluster-mongodb-2'
    ```

* If there are multiple components, you can use `--components` to specify a component.

    ```bash
    kbcli cluster promote mycluster --instance='mycluster-mongodb-2' --components='mongodb'
    ```



## Verify the switchover

Check the instance status to verify whether the switchover is performed successfully.

```bash
kbcli cluster list-instances
```

## Handle an exception

If an error occurs, refer to [Handle an exaception](./../../handle-an-exception/handle-a-cluster-exception.md) to troubleshoot the operation.
