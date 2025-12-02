```bash

$ rke2 --version
rke2 version v1.33.5+rke2r1 (d1092839cf08cb901b1d40461b0fa6e7ae6f8fc4)
go version go1.24.6 X:boringcrypto
$

$ rke2 --help
NAME:
   rke2 - Rancher Kubernetes Engine 2

USAGE:
   rke2 [global options] command [command options]

VERSION:
   v1.33.5+rke2r1 (d1092839cf08cb901b1d40461b0fa6e7ae6f8fc4)

COMMANDS:
   server           Run management server
   agent            Run node agent
   etcd-snapshot    Manage etcd snapshots
   certificate      Manage RKE2 certificates
   secrets-encrypt  Control secrets encryption and keys rotation
   token            Manage tokens
   completion       Install shell completion script
   help, h          Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --help, -h     show help
   --version, -v  print the version
$
$ rke2 server --help
NAME:
   rke2 server - Run management server

USAGE:
   rke2 server [OPTIONS]

OPTIONS:
   --config FILE, -c FILE                                                                         (config) Load configuration from FILE (default: "/etc/rancher/rke2/config.yaml") [$RKE2_CONFIG_FILE]
   --debug                                                                                        (logging) Turn on debug logs (default: false) [$RKE2_DEBUG]
   --bind-address value                                                                           (listener) rke2 bind address (default: 0.0.0.0)
   --advertise-address value                                                                      (listener) IPv4/IPv6 address that apiserver uses to advertise to members of the cluster (default: node-external-ip/node-ip)
   --tls-san value [ --tls-san value ]                                                            (listener) Add additional hostnames or IPv4/IPv6 addresses as Subject Alternative Names on the server TLS cert
   --tls-san-security                                                                             (listener) Protect the server TLS cert by refusing to add Subject Alternative Names not associated with the kubernetes apiserver service, server nodes, or values of the tls-san option (default: true) (default: true)
   --data-dir value, -d value                                                                     (data) Folder to hold state (default: "/var/lib/rancher/rke2") [$RKE2_DATA_DIR]
   --cluster-cidr value [ --cluster-cidr value ]                                                  (networking) IPv4/IPv6 network CIDRs to use for pod IPs (default: 10.42.0.0/16)
   --service-cidr value [ --service-cidr value ]                                                  (networking) IPv4/IPv6 network CIDRs to use for service IPs (default: 10.43.0.0/16)
   --service-node-port-range value                                                                (networking) Port range to reserve for services with NodePort visibility (default: "30000-32767")
   --cluster-dns value [ --cluster-dns value ]                                                    (networking) IPv4/IPv6 Cluster IP for coredns service. Should be in your service-cidr range (default: 10.43.0.10)
   --cluster-domain value                                                                         (networking) Cluster Domain (default: "cluster.local")
   --egress-selector-mode value                                                                   (networking) One of 'agent', 'cluster', 'pod', 'disabled' (default: "agent")
   --servicelb-namespace value                                                                    (networking) Namespace of the pods for the servicelb component (default: "kube-system")
   --write-kubeconfig value, -o value                                                             (client) Write kubeconfig for admin client to this file [$RKE2_KUBECONFIG_OUTPUT]
   --write-kubeconfig-mode value                                                                  (client) Write kubeconfig with this mode [$RKE2_KUBECONFIG_MODE]
   --write-kubeconfig-group value                                                                 (client) Write kubeconfig with this group [$RKE2_KUBECONFIG_GROUP]
   --helm-job-image value                                                                         (helm) Default image to use for helm jobs
   --token value, -t value                                                                        (cluster) Shared secret used to join a server or agent to a cluster [$RKE2_TOKEN]
   --token-file value                                                                             (cluster) File containing the token [$RKE2_TOKEN_FILE]
   --agent-token value                                                                            (cluster) Shared secret used to join agents to the cluster, but not servers [$RKE2_AGENT_TOKEN]
   --agent-token-file value                                                                       (cluster) File containing the agent secret [$RKE2_AGENT_TOKEN_FILE]
   --server value, -s value                                                                       (cluster) Server to connect to, used to join a cluster [$RKE2_URL]
   --cluster-reset                                                                                (cluster) Forget all peers and become sole member of a new cluster (default: false) [$RKE2_CLUSTER_RESET]
   --cluster-reset-restore-path value                                                             (db) Path to snapshot file to be restored
   --kube-apiserver-arg value [ --kube-apiserver-arg value ]                                      (flags) Customized flag for kube-apiserver process
   --etcd-arg value [ --etcd-arg value ]                                                          (flags) Customized flag for etcd process
   --kube-controller-manager-arg value [ --kube-controller-manager-arg value ]                    (flags) Customized flag for kube-controller-manager process
   --kube-scheduler-arg value [ --kube-scheduler-arg value ]                                      (flags) Customized flag for kube-scheduler process
   --kube-cloud-controller-manager-arg value [ --kube-cloud-controller-manager-arg value ]        (flags) Customized flag for kube-cloud-controller-manager process
   --datastore-endpoint value                                                                     (db) Specify etcd, NATS, MySQL, Postgres, or SQLite (default) data source name [$RKE2_DATASTORE_ENDPOINT]
   --datastore-cafile value                                                                       (db) TLS Certificate Authority file used to secure datastore backend communication [$RKE2_DATASTORE_CAFILE]
   --datastore-certfile value                                                                     (db) TLS certification file used to secure datastore backend communication [$RKE2_DATASTORE_CERTFILE]
   --datastore-keyfile value                                                                      (db) TLS key file used to secure datastore backend communication [$RKE2_DATASTORE_KEYFILE]
   --etcd-expose-metrics                                                                          (db) Expose etcd metrics to client interface. (default: false) (default: false)
   --etcd-disable-snapshots                                                                       (db) Disable automatic etcd snapshots (default: false)
   --etcd-snapshot-name value                                                                     (db) Set the base name of etcd snapshots (default: etcd-snapshot-<unix-timestamp>) (default: "etcd-snapshot")
   --etcd-snapshot-schedule-cron value                                                            (db) Snapshot interval time in cron spec. eg. every 5 hours '0 */5 * * *' (default: "0 */12 * * *")
   --etcd-snapshot-reconcile-interval value                                                       (db) Snapshot reconcile interval (default: 10m0s)
   --etcd-snapshot-retention value                                                                (db) Number of snapshots to retain (default: 5)
   --etcd-snapshot-dir value                                                                      (db) Directory to save db snapshots. (default: ${data-dir}/server/db/snapshots)
   --etcd-snapshot-compress                                                                       (db) Compress etcd snapshot (default: false)
   --etcd-s3                                                                                      (db) Enable backup to S3 (default: false)
   --etcd-s3-endpoint value                                                                       (db) S3 endpoint url (default: "s3.amazonaws.com")
   --etcd-s3-endpoint-ca value                                                                    (db) S3 custom CA cert to connect to S3 endpoint
   --etcd-s3-skip-ssl-verify                                                                      (db) Disables S3 SSL certificate validation (default: false)
   --etcd-s3-access-key value                                                                     (db) S3 access key [$AWS_ACCESS_KEY_ID]
   --etcd-s3-secret-key value                                                                     (db) S3 secret key [$AWS_SECRET_ACCESS_KEY]
   --etcd-s3-session-token value                                                                  (db) S3 session token [$AWS_SESSION_TOKEN]
   --etcd-s3-bucket value                                                                         (db) S3 bucket name
   --etcd-s3-bucket-lookup-type value                                                             (db) S3 bucket lookup type, one of 'auto', 'dns', 'path'; default is 'auto' if not set
   --etcd-s3-region value                                                                         (db) S3 region / bucket location (optional) (default: "us-east-1")
   --etcd-s3-folder value                                                                         (db) S3 folder
   --etcd-s3-retention value                                                                      (db) S3 retention limit (default: 5)
   --etcd-s3-proxy value                                                                          (db) Proxy server to use when connecting to S3, overriding any proxy-releated environment variables
   --etcd-s3-config-secret value                                                                  (db) Name of secret in the kube-system namespace used to configure S3, if etcd-s3 is enabled and no other etcd-s3 options are set
   --etcd-s3-insecure                                                                             (db) Disables S3 over HTTPS (default: false)
   --etcd-s3-timeout value                                                                        (db) S3 timeout (default: 5m0s)
   --disable value [ --disable value ]                                                            (components) Do not deploy packaged components and delete any deployed components (valid items: rke2-coredns, rke2-metrics-server, rke2-snapshot-controller, rke2-snapshot-controller-crd, rke2-snapshot-validation-webhook)
   --disable-scheduler                                                                            (components) Disable Kubernetes default scheduler (default: false)
   --disable-cloud-controller                                                                     (components) Disable rke2 default cloud controller manager (default: false)
   --disable-kube-proxy                                                                           (components) Disable running kube-proxy (default: false)
   --embedded-registry                                                                            (components) Enable embedded distributed container registry; requires use of embedded containerd; when enabled agents will also listen on the supervisor port (default: false)
   --supervisor-metrics                                                                           (experimental/components) Enable serving rke2 internal metrics on the supervisor port; when enabled agents will also listen on the supervisor port (default: false)
   --node-name value                                                                              (agent/node) Node name [$RKE2_NODE_NAME]
   --with-node-id                                                                                 (agent/node) Append id to node name (default: false)
   --node-label value [ --node-label value ]                                                      (agent/node) Registering and starting kubelet with set of labels
   --node-taint value [ --node-taint value ]                                                      (agent/node) Registering kubelet with set of taints
   --image-credential-provider-bin-dir value                                                      (agent/node) The path to the directory where credential provider plugin binaries are located (default: "/var/lib/rancher/credentialprovider/bin")
   --image-credential-provider-config value                                                       (agent/node) The path to the credential provider plugin config file (default: "/var/lib/rancher/credentialprovider/config.yaml")
   --container-runtime-endpoint value                                                             (agent/runtime) Disable embedded containerd and use the CRI socket at the given path; when used with --docker this sets the docker socket path
   --default-runtime value                                                                        (agent/runtime) Set the default runtime in containerd
   --disable-default-registry-endpoint                                                            (agent/containerd) Disables containerd's fallback default registry endpoint when a mirror is configured for that registry (default: false)
   --nonroot-devices                                                                              (agent/containerd) Allows non-root pods to access devices by setting device_ownership_from_security_context=true in the containerd CRI config (default: false)
   --snapshotter value                                                                            (agent/runtime) Override default containerd snapshotter (default: "overlayfs")
   --private-registry value                                                                       (agent/runtime) Private registry configuration file (default: "/etc/rancher/rke2/registries.yaml")
   --system-default-registry value                                                                (agent/runtime) Private registry to be used for all system images [$RKE2_SYSTEM_DEFAULT_REGISTRY]
   --node-ip value, -i value [ --node-ip value, -i value ]                                        (agent/networking) IPv4/IPv6 addresses to advertise for node
   --node-external-ip value [ --node-external-ip value ]                                          (agent/networking) IPv4/IPv6 external IP addresses to advertise for node
   --node-internal-dns value [ --node-internal-dns value ]                                        (agent/networking) internal DNS addresses to advertise for node
   --node-external-dns value [ --node-external-dns value ]                                        (agent/networking) external DNS addresses to advertise for node
   --resolv-conf value                                                                            (agent/networking) Kubelet resolv.conf file [$RKE2_RESOLV_CONF]
   --kubelet-arg value [ --kubelet-arg value ]                                                    (agent/flags) Customized flag for kubelet process
   --kube-proxy-arg value [ --kube-proxy-arg value ]                                              (agent/flags) Customized flag for kube-proxy process
   --protect-kernel-defaults                                                                      (agent/node) Kernel tuning behavior. If set, error if kernel tunables are different than kubelet defaults. (default: false)
   --enable-pprof                                                                                 (experimental) Enable pprof endpoint on supervisor port (default: false)
   --secrets-encryption-provider value                                                            (experimental) Secret encryption provider (valid values: 'aescbc', 'secretbox') (default: "aescbc")
   --selinux                                                                                      (agent/node) Enable SELinux in containerd (default: false) [$RKE2_SELINUX]
   --lb-server-port value                                                                         (agent/node) Local port for supervisor client load-balancer. If the supervisor and apiserver are not colocated an additional port 1 less than this port will also be used for the apiserver client load-balancer. (default: 6444) [$RKE2_LB_SERVER_PORT]
   --cni value [ --cni value ]                                                                    (networking) CNI Plugins to deploy, one of none, calico, canal, cilium, flannel; optionally with multus as the first value to enable the multus meta-plugin (default: "canal") [$RKE2_CNI]
   --ingress-controller value [ --ingress-controller value ]                                      (networking) Ingress Controllers to deploy, one of none, ingress-nginx, traefik; the first value will be set as the default ingress class (default: "ingress-nginx") [$RKE_INGRESS_CONTROLLER]
   --enable-servicelb                                                                             (components) Enable rke2 default cloud controller manager's service controller (default: false) [$RKE2_ENABLE_SERVICELB]
   --kube-apiserver-image value                                                                   (image) Override image to use for kube-apiserver [$RKE2_KUBE_APISERVER_IMAGE]
   --kube-controller-manager-image value                                                          (image) Override image to use for kube-controller-manager [$RKE2_KUBE_CONTROLLER_MANAGER_IMAGE]
   --cloud-controller-manager-image value                                                         (image) Override image to use for cloud-controller-manager [$RKE2_CLOUD_CONTROLLER_MANAGER_IMAGE]
   --kube-proxy-image value                                                                       (image) Override image to use for kube-proxy [$RKE2_KUBE_PROXY_IMAGE]
   --kube-scheduler-image value                                                                   (image) Override image to use for kube-scheduler [$RKE2_KUBE_SCHEDULER_IMAGE]
   --pause-image value                                                                            (image) Override image to use for pause [$RKE2_PAUSE_IMAGE]
   --runtime-image value                                                                          (image) Override image to use for runtime binaries (containerd, kubectl, crictl, etc) [$RKE2_RUNTIME_IMAGE]
   --etcd-image value                                                                             (image) Override image to use for etcd [$RKE2_ETCD_IMAGE]
   --kubelet-path value                                                                           (experimental/agent) Override kubelet binary path [$RKE2_KUBELET_PATH]
   --cloud-provider-name value                                                                    (cloud provider) Cloud provider name [$RKE2_CLOUD_PROVIDER_NAME]
   --cloud-provider-config value                                                                  (cloud provider) Cloud provider configuration file path [$RKE2_CLOUD_PROVIDER_CONFIG]
   --node-name-from-cloud-provider-metadata                                                       (cloud provider) Set node name from instance metadata service hostname (default: false) [$RKE2_NODE_NAME_FROM_CLOUD_PROVIDER_METADATA]
   --profile value                                                                                (security) Validate system configuration against the selected benchmark (valid items: cis, etcd) [$RKE2_CIS_PROFILE]
   --audit-policy-file value                                                                      (security) Path to the file that defines the audit policy configuration [$RKE2_AUDIT_POLICY_FILE]
   --pod-security-admission-config-file value                                                     (security) Path to the file that defines Pod Security Admission configuration [$RKE2_POD_SECURITY_ADMISSION_CONFIG_FILE]
   --control-plane-resource-requests value [ --control-plane-resource-requests value ]            (components) Control Plane resource requests [$RKE2_CONTROL_PLANE_RESOURCE_REQUESTS]
   --control-plane-resource-limits value [ --control-plane-resource-limits value ]                (components) Control Plane resource limits [$RKE2_CONTROL_PLANE_RESOURCE_LIMITS]
   --control-plane-probe-configuration value [ --control-plane-probe-configuration value ]        (components) Control Plane Probe configuration [$RKE2_CONTROL_PLANE_PROBE_CONFIGURATION]
   --kube-apiserver-extra-mount value [ --kube-apiserver-extra-mount value ]                      (components) kube-apiserver extra volume mounts [$RKE2_KUBE_APISERVER_EXTRA_MOUNT]
   --kube-scheduler-extra-mount value [ --kube-scheduler-extra-mount value ]                      (components) kube-scheduler extra volume mounts [$RKE2_KUBE_SCHEDULER_EXTRA_MOUNT]
   --kube-controller-manager-extra-mount value [ --kube-controller-manager-extra-mount value ]    (components) kube-controller-manager extra volume mounts [$RKE2_KUBE_CONTROLLER_MANAGER_EXTRA_MOUNT]
   --kube-proxy-extra-mount value [ --kube-proxy-extra-mount value ]                              (components) kube-proxy extra volume mounts [$RKE2_KUBE_PROXY_EXTRA_MOUNT]
   --etcd-extra-mount value [ --etcd-extra-mount value ]                                          (components) etcd extra volume mounts [$RKE2_ETCD_EXTRA_MOUNT]
   --cloud-controller-manager-extra-mount value [ --cloud-controller-manager-extra-mount value ]  (components) cloud-controller-manager extra volume mounts [$RKE2_CLOUD_CONTROLLER_MANAGER_EXTRA_MOUNT]
   --kube-apiserver-extra-env value [ --kube-apiserver-extra-env value ]                          (components) kube-apiserver extra environment variables [$RKE2_KUBE_APISERVER_EXTRA_ENV]
   --kube-scheduler-extra-env value [ --kube-scheduler-extra-env value ]                          (components) kube-scheduler extra environment variables [$RKE2_KUBE_SCHEDULER_EXTRA_ENV]
   --kube-controller-manager-extra-env value [ --kube-controller-manager-extra-env value ]        (components) kube-controller-manager extra environment variables [$RKE2_KUBE_CONTROLLER_MANAGER_EXTRA_ENV]
   --kube-proxy-extra-env value [ --kube-proxy-extra-env value ]                                  (components) kube-proxy extra environment variables [$RKE2_KUBE_PROXY_EXTRA_ENV]
   --etcd-extra-env value [ --etcd-extra-env value ]                                              (components) etcd extra environment variables [$RKE2_ETCD_EXTRA_ENV]
   --cloud-controller-manager-extra-env value [ --cloud-controller-manager-extra-env value ]      (components) cloud-controller-manager extra environment variables [$RKE2_CLOUD_CONTROLLER_MANAGER_EXTRA_ENV]
   --help, -h                                                                                     show help
$
$ rke2 agent --help
NAME:
   rke2 agent - Run node agent

USAGE:
   rke2 agent [OPTIONS]

COMMANDS:

   help, h  Shows a list of commands or help for one command

OPTIONS:
   --config FILE, -c FILE                                                                         (config) Load configuration from FILE (default: "/etc/rancher/rke2/config.yaml") [$RKE2_CONFIG_FILE]
   --debug                                                                                        (logging) Turn on debug logs (default: false) [$RKE2_DEBUG]
   --token value, -t value                                                                        (cluster) Token to use for authentication [$RKE2_TOKEN]
   --token-file value                                                                             (cluster) Token file to use for authentication [$RKE2_TOKEN_FILE]
   --server value, -s value                                                                       (cluster) Server to connect to [$RKE2_URL]
   --data-dir value, -d value                                                                     (data) Folder to hold state (default: "/var/lib/rancher/rke2") [$RKE2_DATA_DIR]
   --node-name value                                                                              (agent/node) Node name [$RKE2_NODE_NAME]
   --with-node-id                                                                                 (agent/node) Append id to node name (default: false)
   --node-label value [ --node-label value ]                                                      (agent/node) Registering and starting kubelet with set of labels
   --node-taint value [ --node-taint value ]                                                      (agent/node) Registering kubelet with set of taints
   --image-credential-provider-bin-dir value                                                      (agent/node) The path to the directory where credential provider plugin binaries are located (default: "/var/lib/rancher/credentialprovider/bin")
   --image-credential-provider-config value                                                       (agent/node) The path to the credential provider plugin config file (default: "/var/lib/rancher/credentialprovider/config.yaml")
   --selinux                                                                                      (agent/node) Enable SELinux in containerd (default: false) [$RKE2_SELINUX]
   --lb-server-port value                                                                         (agent/node) Local port for supervisor client load-balancer. If the supervisor and apiserver are not colocated an additional port 1 less than this port will also be used for the apiserver client load-balancer. (default: 6444) [$RKE2_LB_SERVER_PORT]
   --protect-kernel-defaults                                                                      (agent/node) Kernel tuning behavior. If set, error if kernel tunables are different than kubelet defaults. (default: false)
   --container-runtime-endpoint value                                                             (agent/runtime) Disable embedded containerd and use the CRI socket at the given path; when used with --docker this sets the docker socket path
   --default-runtime value                                                                        (agent/runtime) Set the default runtime in containerd
   --snapshotter value                                                                            (agent/runtime) Override default containerd snapshotter (default: "overlayfs")
   --private-registry value                                                                       (agent/runtime) Private registry configuration file (default: "/etc/rancher/rke2/registries.yaml")
   --disable-default-registry-endpoint                                                            (agent/containerd) Disables containerd's fallback default registry endpoint when a mirror is configured for that registry (default: false)
   --nonroot-devices                                                                              (agent/containerd) Allows non-root pods to access devices by setting device_ownership_from_security_context=true in the containerd CRI config (default: false)
   --node-ip value, -i value [ --node-ip value, -i value ]                                        (agent/networking) IPv4/IPv6 addresses to advertise for node
   --bind-address value                                                                           (listener) rke2 bind address (default: 0.0.0.0)
   --node-external-ip value [ --node-external-ip value ]                                          (agent/networking) IPv4/IPv6 external IP addresses to advertise for node
   --node-internal-dns value [ --node-internal-dns value ]                                        (agent/networking) internal DNS addresses to advertise for node
   --node-external-dns value [ --node-external-dns value ]                                        (agent/networking) external DNS addresses to advertise for node
   --resolv-conf value                                                                            (agent/networking) Kubelet resolv.conf file [$RKE2_RESOLV_CONF]
   --kubelet-arg value [ --kubelet-arg value ]                                                    (agent/flags) Customized flag for kubelet process
   --kube-proxy-arg value [ --kube-proxy-arg value ]                                              (agent/flags) Customized flag for kube-proxy process
   --enable-pprof                                                                                 (experimental) Enable pprof endpoint on supervisor port (default: false)
   --kube-apiserver-image value                                                                   (image) Override image to use for kube-apiserver [$RKE2_KUBE_APISERVER_IMAGE]
   --kube-controller-manager-image value                                                          (image) Override image to use for kube-controller-manager [$RKE2_KUBE_CONTROLLER_MANAGER_IMAGE]
   --cloud-controller-manager-image value                                                         (image) Override image to use for cloud-controller-manager [$RKE2_CLOUD_CONTROLLER_MANAGER_IMAGE]
   --kube-proxy-image value                                                                       (image) Override image to use for kube-proxy [$RKE2_KUBE_PROXY_IMAGE]
   --kube-scheduler-image value                                                                   (image) Override image to use for kube-scheduler [$RKE2_KUBE_SCHEDULER_IMAGE]
   --pause-image value                                                                            (image) Override image to use for pause [$RKE2_PAUSE_IMAGE]
   --runtime-image value                                                                          (image) Override image to use for runtime binaries (containerd, kubectl, crictl, etc) [$RKE2_RUNTIME_IMAGE]
   --etcd-image value                                                                             (image) Override image to use for etcd [$RKE2_ETCD_IMAGE]
   --kubelet-path value                                                                           (experimental/agent) Override kubelet binary path [$RKE2_KUBELET_PATH]
   --cloud-provider-name value                                                                    (cloud provider) Cloud provider name [$RKE2_CLOUD_PROVIDER_NAME]
   --cloud-provider-config value                                                                  (cloud provider) Cloud provider configuration file path [$RKE2_CLOUD_PROVIDER_CONFIG]
   --node-name-from-cloud-provider-metadata                                                       (cloud provider) Set node name from instance metadata service hostname (default: false) [$RKE2_NODE_NAME_FROM_CLOUD_PROVIDER_METADATA]
   --profile value                                                                                (security) Validate system configuration against the selected benchmark (valid items: cis, etcd) [$RKE2_CIS_PROFILE]
   --audit-policy-file value                                                                      (security) Path to the file that defines the audit policy configuration [$RKE2_AUDIT_POLICY_FILE]
   --pod-security-admission-config-file value                                                     (security) Path to the file that defines Pod Security Admission configuration [$RKE2_POD_SECURITY_ADMISSION_CONFIG_FILE]
   --control-plane-resource-requests value [ --control-plane-resource-requests value ]            (components) Control Plane resource requests [$RKE2_CONTROL_PLANE_RESOURCE_REQUESTS]
   --control-plane-resource-limits value [ --control-plane-resource-limits value ]                (components) Control Plane resource limits [$RKE2_CONTROL_PLANE_RESOURCE_LIMITS]
   --control-plane-probe-configuration value [ --control-plane-probe-configuration value ]        (components) Control Plane Probe configuration [$RKE2_CONTROL_PLANE_PROBE_CONFIGURATION]
   --kube-apiserver-extra-mount value [ --kube-apiserver-extra-mount value ]                      (components) kube-apiserver extra volume mounts [$RKE2_KUBE_APISERVER_EXTRA_MOUNT]
   --kube-scheduler-extra-mount value [ --kube-scheduler-extra-mount value ]                      (components) kube-scheduler extra volume mounts [$RKE2_KUBE_SCHEDULER_EXTRA_MOUNT]
   --kube-controller-manager-extra-mount value [ --kube-controller-manager-extra-mount value ]    (components) kube-controller-manager extra volume mounts [$RKE2_KUBE_CONTROLLER_MANAGER_EXTRA_MOUNT]
   --kube-proxy-extra-mount value [ --kube-proxy-extra-mount value ]                              (components) kube-proxy extra volume mounts [$RKE2_KUBE_PROXY_EXTRA_MOUNT]
   --etcd-extra-mount value [ --etcd-extra-mount value ]                                          (components) etcd extra volume mounts [$RKE2_ETCD_EXTRA_MOUNT]
   --cloud-controller-manager-extra-mount value [ --cloud-controller-manager-extra-mount value ]  (components) cloud-controller-manager extra volume mounts [$RKE2_CLOUD_CONTROLLER_MANAGER_EXTRA_MOUNT]
   --kube-apiserver-extra-env value [ --kube-apiserver-extra-env value ]                          (components) kube-apiserver extra environment variables [$RKE2_KUBE_APISERVER_EXTRA_ENV]
   --kube-scheduler-extra-env value [ --kube-scheduler-extra-env value ]                          (components) kube-scheduler extra environment variables [$RKE2_KUBE_SCHEDULER_EXTRA_ENV]
   --kube-controller-manager-extra-env value [ --kube-controller-manager-extra-env value ]        (components) kube-controller-manager extra environment variables [$RKE2_KUBE_CONTROLLER_MANAGER_EXTRA_ENV]
   --kube-proxy-extra-env value [ --kube-proxy-extra-env value ]                                  (components) kube-proxy extra environment variables [$RKE2_KUBE_PROXY_EXTRA_ENV]
   --etcd-extra-env value [ --etcd-extra-env value ]                                              (components) etcd extra environment variables [$RKE2_ETCD_EXTRA_ENV]
   --cloud-controller-manager-extra-env value [ --cloud-controller-manager-extra-env value ]      (components) cloud-controller-manager extra environment variables [$RKE2_CLOUD_CONTROLLER_MANAGER_EXTRA_ENV]
   --help, -h                                                                                     show help
$

$ systemctl enable rke2-server.service
Created symlink /etc/systemd/system/multi-user.target.wants/rke2-server.service → /usr/local/lib/systemd/system/rke2-server.service.
$

export RKE2_DEBUG=true && systemctl start rke2-server.service

journalctl -u rke2-server -f

```
