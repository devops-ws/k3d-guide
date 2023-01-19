# k3d-guide

## Registry
```yaml
# this file will be mounted into /etc/rancher/k3s/registries.yaml 
mirrors:
  "10.121.218.184:30002":
    endpoint:
      - "http://10.121.218.184:30002"
  "docker.io":
    endpoint:
      - "http://10.121.218.184:30002/v2/cache"
  "quay.io":
    endpoint:
      - "http://10.121.218.184:30002/v2/quay.io"
  "ghcr.io":
    endpoint:
      - "http://10.121.218.184:30002/v2/ghcr.io"
configs:
  "10.121.218.184:30002":
    auth:
      username: robot_readonly
      password: npcCnfZicoeZTupZnX39ew9cfIvldyZV
    tls:
      insecure_skip_verify: true
```

下面的命令参数可以让 k3d 使用自定义的 Registry 配置，实现拉取镜像时不做 TLS 校验：
```shell
k3d cluster create --registry-config config/registry/default.yaml
```

k3d 内部使用 containerd 作为容器运行时，更多有关 containerd 的信息请参考[这里](https://github.com/devops-ws/containerd-guide)。
## 指定 k3s 镜像
```shell
k3d cluster create --image 10.121.218.184:30002/cache/rancher/k3s
```
