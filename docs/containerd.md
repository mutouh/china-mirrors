# containerd
## 配置
谷歌 Kubernetes `k8s.gcr.io` 使用国内阿里源。
```bash
echo '
server = "https://k8s.gcr.io"

[host."https://registry.aliyuncs.com/v2/google_containers"]
  capabilities = ["pull", "resolve"]
  override_path = true
' | sudo tee /etc/containerd/certs.d/k8s.gcr.io/hosts.toml
```

## 使用
```bash
[root@wrk-1 ~]$ ctr --debug images pull --hosts-dir "/etc/containerd/certs.d" k8s.gcr.io/pause:3.8
DEBU[0000] fetching                                      image="k8s.gcr.io/pause:3.8"
DEBU[0000] loading host directory                        dir=/etc/containerd/certs.d/k8s.gcr.io
DEBU[0000] resolving                                     host=registry.aliyuncs.com
DEBU[0000] do request                                    host=registry.aliyuncs.com request.header.accept="application/vnd.docker.distribution.manifest.v2+json, application/vnd.docker.distribution.manifest.list.v2+json, application/vnd.oci.image.manifest.v1+json, application/vnd.oci.image.index.v1+json, */*" request.header.user-agent=containerd/1.6.6 request.method=HEAD url="https://registry.aliyuncs.com/v2/google_containers/pause/manifests/3.8?ns=k8s.gcr.io"
...
```

## 链接
官方关于 containerd [hosts][1] 的说明文档。

[1]: https://github.com/containerd/containerd/blob/main/docs/hosts.md
