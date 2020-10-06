# kube-state-metrics Helm Chart

* Installs the [kube-state-metrics agent](https://github.com/kubernetes/kube-state-metrics).

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install stable/kube-state-metrics
```

## Configuration

| Parameter                                    | Description                                                                           | Default                                    |
|:---------------------------------------------|:--------------------------------------------------------------------------------------|:-------------------------------------------|
| `image.repository`                           | The image repository to pull from                                                     | `quay.io/coreos/kube-state-metrics`        |
| `image.tag`                                  | The image tag to pull from                                                            | `v2.0.0-alpha`                                   |
| `image.pullPolicy`                           | Image pull policy                                                                     | `IfNotPresent`                             |
| `imagePullSecrets`                           | List of container registry secrets                                                    | `[]`                                       |
| `replicas`                                   | Number of replicas                                                                    | `1`                                        |
| `autosharding.enabled`                       | Set to `true` to automatically shard data across `replicas` pods. EXPERIMENTAL        | `false`                                    |
| `service.port`                               | The port of the container                                                             | `8080`                                     |
| `service.annotations`                        | Annotations to be added to the service                                                | `{}`                                       |
| `customLabels`                               | Custom labels to apply to service, deployment and pods                                | `{}`                                       |
| `hostNetwork`                                | Whether or not to use the host network                                                | `false`                                    |
| `prometheusScrape`                           | Whether or not enable prom scrape                                                     | `true`                                     |
| `rbac.create`                                | If true, create & use RBAC resources                                                  | `true`                                     |
| `serviceAccount.create`                      | If true, create & use serviceAccount                                                  | `true`                                     |
| `serviceAccount.name`                        | If not set & create is true, use template fullname                                    |                                            |
| `serviceAccount.imagePullSecrets`            | Specify image pull secrets field                                                      | `[]`                                       |
| `serviceAccount.annotations`                 | Annotations to be added to the serviceAccount                                         | `{}`                                       |
| `podSecurityPolicy.enabled`                  | If true, create & use PodSecurityPolicy resources. Note that related RBACs are created only if `rbac.enabled` is `true`. | `false` |
| `podSecurityPolicy.annotations`              | Specify pod annotations in the pod security policy                                    | `{}`                                       |
| `podSecurityPolicy.additionalVolumes`        | Specify allowed volumes in the pod security policy (`secret` is always allowed)       | `[]`                                       |
| `securityContext.enabled`                    | Enable security context                                                               | `true`                                     |
| `securityContext.fsGroup`                    | Group ID for the filesystem                                                           | `65534`                                    |
| `securityContext.runAsGroup`                 | Group ID for the container                                                            | `65534`                                    |
| `securityContext.runAsUser`                  | User ID for the container                                                             | `65534`                                    |
| `priorityClassName`                          | Name of Priority Class to assign pods                                                 | `nil`                                      |
| `nodeSelector`                               | Node labels for pod assignment                                                        | `{}`                                       |
| `affinity`                                   | Affinity settings for pod assignment                                                  | `{}`                                       |
| `tolerations`                                | Tolerations for pod assignment                                                        | `[]`                                       |
| `podAnnotations`                             | Annotations to be added to the pod                                                    | `{}`                                       |
| `podDisruptionBudget`                        | Optional PodDisruptionBudget                                                          | `{}`                                       |
| `resources`                                  | kube-state-metrics resource requests and limits                                       | `{}`                                       |
| `args.resources.certificatesigningrequests`      | Enable the certificatesigningrequests collector.                                      | `true`                                     |
| `args.resources.configmaps`                      | Enable the configmaps collector.                                                      | `true`                                     |
| `args.resources.cronjobs`                        | Enable the cronjobs collector.                                                        | `true`                                     |
| `args.resources.daemonsets`                      | Enable the daemonsets collector.                                                      | `true`                                     |
| `args.resources.deployments`                     | Enable the deployments collector.                                                     | `true`                                     |
| `args.resources.endpoints`                       | Enable the endpoints collector.                                                       | `true`                                     |
| `args.resources.horizontalpodautoscalers`        | Enable the horizontalpodautoscalers collector.                                        | `true`                                     |
| `args.resources.ingresses`                       | Enable the ingresses collector.                                                       | `true`                                     |
| `args.resources.jobs`                            | Enable the jobs collector.                                                            | `true`                                     |
| `args.resources.limitranges`                     | Enable the limitranges collector.                                                     | `true`                                     |
| `args.resources.mutatingwebhookconfigurations`   | Enable the mutatingwebhookconfigurations collector.                                   | `true`                                     |
| `args.resources.namespaces`                      | Enable the namespaces collector.                                                      | `true`                                     |
| `args.resources.networkpolicies`                 | Enable the networkpolicies collector.                                                 | `true`                                     |
| `args.resources.nodes`                           | Enable the nodes collector.                                                           | `true`                                     |
| `args.resources.persistentvolumeclaims`          | Enable the persistentvolumeclaims collector.                                          | `true`                                     |
| `args.resources.persistentvolumes`               | Enable the persistentvolumes collector.                                               | `true`                                     |
| `args.resources.poddisruptionbudgets`            | Enable the poddisruptionbudgets collector.                                            | `true`                                     |
| `args.resources.pods`                            | Enable the pods collector.                                                            | `true`                                     |
| `args.resources.replicasets`                     | Enable the replicasets collector.                                                     | `true`                                     |
| `args.resources.replicationcontrollers`          | Enable the replicationcontrollers collector.                                          | `true`                                     |
| `args.resources.resourcequotas`                  | Enable the resourcequotas collector.                                                  | `true`                                     |
| `args.resources.secrets`                         | Enable the secrets collector.                                                         | `true`                                     |
| `args.resources.services`                        | Enable the services collector.                                                        | `true`                                     |
| `args.resources.statefulsets`                    | Enable the statefulsets collector.                                                    | `true`                                     |
| `args.resources.storageclasses`                  | Enable the storageclasses collector.                                                  | `true`                                     |
| `args.resources.validatingwebhookconfigurations` | Enable the validatingwebhookconfigurations collector.                                 | `true`                                     |
| `args.resources.verticalpodautoscalers`          | Enable the verticalpodautoscalers collector.                                          | `true`                                     |
| `args.resources.volumeattachments`               | Enable the volumeattachments collector.                                               | `true`                                     |
| `prometheus.monitor.enabled`                 | Set this to `true` to create ServiceMonitor for Prometheus operator                   | `false`                                    |
| `prometheus.monitor.additionalLabels`        | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`                                       |
| `prometheus.monitor.namespaces`               | Namespace where servicemonitor resource should be created                             | `the same namespace as kube-state-metrics` |
| `prometheus.monitor.honorLabels`             | Honor metric labels                                                                   | `false`                                    |
| `namespaceOverride`                          | Override the deployment namespace                                                     | `""` (`Release.Namespace`)                 |
| `kubeTargetVersionOverride`                  | Override the k8s version of the target cluster                                        | `""`                                       |
| `kubeconfig.enabled`                         | Adds --kubeconfig arg to container at startup                                         | `""`                                       |
| `kubeconfig.secret`                          | Base64 encoded kubeconfig file                                                        | `""`                                       |
