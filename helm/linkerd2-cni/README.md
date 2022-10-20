# linkerd2-cni

Linkerd is a *service mesh*, designed to give platform-wide observability,
reliability, and security without requiring configuration or code changes. The
Linkerd [CNI plugin](https://linkerd.io/2/features/cni/) takes care of setting
up your pod's network so  incoming and outgoing traffic is proxied through the
data plane.

![Version: 0.7.4](https://img.shields.io/badge/Version-0.7.4-informational?style=flat-square)

![AppVersion: 2.12.1](https://img.shields.io/badge/AppVersion-2.12.1-informational?style=flat-square)

**Homepage:** <https://github.com/giantswarm/linkerd2-cni-app>

## Requirements

Kubernetes: `>=1.21.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| cniPluginImage | string | `"giantswarm/linkerd2-cni-plugin"` | Docker image for the CNI plugin |
| cniPluginVersion | string | `"stable-2.12.1"` | Tag for the CNI container Docker image |
| destCNIBinDir | string | `"/opt/cni/bin"` | Directory on the host where the CNI configuration will be placed |
| destCNINetDir | string | `"/etc/cni/net.d"` | Directory on the host where the CNI plugin binaries reside |
| enablePSP | bool | `true` | Add a PSP resource and bind it to the linkerd-cni ServiceAccounts. Note PSP has been deprecated since k8s v1.21 |
| extraInitContainers | list | `[]` | Add additional initContainers to the daemonset |
| ignoreInboundPorts | string | `""` | Default set of inbound ports to skip via iptables |
| ignoreOutboundPorts | string | `""` | Default set of outbound ports to skip via iptables |
| image.registry | string | `"quay.io"` |  |
| imagePullSecrets | string | `nil` |  |
| inboundProxyPort | int | `4143` | Inbound port for the proxy container |
| logLevel | string | `"info"` | Log level for the CNI plugin |
| outboundProxyPort | int | `4140` | Outbound port for the proxy container |
| portsToRedirect | string | `""` | Ports to redirect to proxy |
| priorityClassName | string | `""` | Kubernetes priorityClassName for the CNI plugin's Pods |
| privileged | bool | `false` | Run the install-cni container in privileged mode |
| proxyAdminPort | int | `4191` | Admin port for the proxy container |
| proxyControlPort | int | `4190` | Control port for the proxy container |
| proxyUID | int | `2102` | User id under which the proxy shall be ran |
| resources.limits.cpu | string | `"500m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"50m"` |  |
| resources.requests.memory | string | `"64Mi"` |  |
| useWaitFlag | bool | `false` | Configures the CNI plugin to use the -w flag for the iptables command |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)