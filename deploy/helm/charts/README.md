## Introduction

This chart bootstraps OpenEBS NDM deployment on a [Kubernetes](http://kubernetes.io) cluster using the 
[Helm](https://helm.sh) package manager.

## Installation

You can run OpenEBS NDM on any Kubernetes 1.13+ cluster in a matter of seconds.

Please visit the [link](https://openebs.github.io/node-disk-manager/) for install instructions via helm3.

## Configuration

The following table lists the configurable parameters of the OpenEBS NDM chart and their default values.

| Parameter                               | Description                                   | Default                                   |
| ----------------------------------------| --------------------------------------------- | ----------------------------------------- |
| `imagePullSecrets`                      | Provides image pull secrect                   | `""`                                      |
| `ndm.enabled`                           | Enable Node Disk Manager                      | `true`                                    |
| `ndm.image.registry`                    | Registry for Node Disk Manager image          | `""`                                      |
| `ndm.image.repository`                  | Image repository for Node Disk Manager        | `openebs/node-disk-manager`               |
| `ndm.image.pullPolicy`                  | Image pull policy for Node Disk Manager       | `IfNotPresent`                            |
| `ndm.image.tag`                         | Image tag for Node Disk Manager               | `1.4.0`                                   |
| `ndm.sparse.path`                       | Directory where Sparse files are created      | `/var/openebs/sparse`                     |
| `ndm.sparse.size`                       | Size of the sparse file in bytes              | `10737418240`                             |
| `ndm.sparse.count`                      | Number of sparse files to be created          | `0`                                       |
| `ndm.updateStrategy.type`               | Update strategy for NDM daemonset             | `RollingUpdate`                           |
| `ndm.annotations`                       | Annotations for NDM daemonset metadata        | `""`                                      |
| `ndm.podAnnotations`                    | Annotations for NDM daemonset's pods metadata | `""`                                      |
| `ndm.resources`                         | Resource and request and limit for containers | `""`                                      |
| `ndm.podLabels`                         | Appends labels to the pods                    | `""`                                      |
| `ndm.nodeSelector`                      | Nodeselector for daemonset pods               | `""`                                      |
| `ndm.tolerations`                       | NDM daemonset's pod toleration values         | `""`                                      |
| `ndm.securityContext`                   | Seurity context for container                 | `""`                                      |
| `ndm.filters.enableOsDiskExcludeFilter` | Enable filters of OS disk exclude             | `true`                                    |
| `ndm.filters.osDiskExcludePaths`        | Paths/Mountpoints to be excluded by OS Disk Filter| `/,/etc/hosts,/boot`                           || `ndm.filters.enableVendorFilter`        | Enable filters of venders                     | `true`                                    |
| `ndm.filters.excludeVendors`            | Exclude devices with specified vendor         | `CLOUDBYT,OpenEBS`                        |
| `ndm.filters.enablePathFilter`          | Enable filters of paths                       | `true`                                    |
| `ndm.filters.includePaths`              | Include devices with specified path patterns  | `""`                                      |
| `ndm.filters.excludePaths`              | Exclude devices with specified path patterns  | `loop,fd0,sr0,/dev/ram,/dev/dm-,/dev/md,/dev/rbd,/dev/zd`|
| `ndm.probes.enableSeachest`             | Enable Seachest probe for NDM                 | `false`                                    |
| `ndm.probes.enableUdevProbe`            | Enable Udev probe for NDM                     | `true`                                    |
| `ndm.probes.enableSmartProbe`           | Enable Smart probe for NDM                    | `true`                                    |
| `ndm.healthCheck.initialDelaySeconds`   | Delay before liveness probe is initiated      | `30`                                      |
| `ndm.healthCheck.periodSeconds`         | How often to perform the liveness probe       | `60`                                      |
| `ndmOperator.enabled`                   | Enable NDM Operator                           | `true`                                    |
| `ndmOperator.replica`                   | Pod replica count for NDM operator            | `1`                                       |
| `ndmOperator.upgradeStrategy`           | Update strategy NDM operator                  | `"Recreate"`                              |
| `ndmOperator.image.registry`            | Registry for NDM operator image               | `""`                                      |
| `ndmOperator.image.repository`          | Image repository for NDM operator             | `openebs/node-disk-operator`              |
| `ndmOperator.image.pullPolicy`          | Image pull policy for NDM operator            | `IfNotPresent`                            |
| `ndmOperator.image.tag`                 | Image tag for NDM operator                    | `1.4.0`                                   |
| `ndmOperator.annotations`               | Annotations for NDM operator metadata         | `""`                                      |
| `ndmOperator.podAnnotations`            | Annotations for NDM operator's pods metadata  | `""`                                      |
| `ndmOperator.resources`                 | Resource and request and limit for containers | `""`                                      |
| `ndmOperator.podLabels`                 | Appends labels to the pods                    | `""`                                      |
| `ndmOperator.nodeSelector`              | Nodeselector for operator pods                | `""`                                      |
| `ndmOperator.tolerations`               | NDM operator's pod toleration values          | `""`                                      |
| `ndmOperator.securityContext`           | Seurity context for container                 | `""`                                      |
| `ndmOperator.healthCheck.initialDelaySeconds`   | Delay before liveness probe is initiated      | `30`                              |
| `ndmOperator.healthCheck.periodSeconds`         | How often to perform the liveness probe       | `60`                              |
| `ndmOperator.readinessCheck.initialDelaySeconds`| Delay before readiness probe is initiated     | `4`                               |
| `ndmOperator.readinessCheck.periodSeconds`      | How often to perform the readiness probe      | `10`                              |
| `ndmOperator.readinessCheck.failureThreshold`   | Failure threshold for the readiness probe     | `1`                               |
| `helperPod.image.registry`              | Registry for helper image                     | `""`                                      |
| `helperPod.image.repository`            | Image for helper pod                          | `openebs/linux-utils`                     |
| `helperPod.image.pullPolicy`            | Pull policy for helper pod                    | `IfNotPresent`                            |
| `helperPod.image.tag`                   | Image tag for helper image                    | `2.8.0`                                   |
| `varDirectoryPath.baseDir`              | Directory to store debug info and so forth    | `/var/openebs`                            |
| `serviceAccount.create`                 | Create a service account or not               | `true`                                    |
| `serviceAccount.name`                   | Name for the service account                  | `true`                                    |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
helm install <release-name> -f values.yaml ndm/openebs-ndm 
```

> **Tip**: You can use the default [values.yaml](values.yaml)
