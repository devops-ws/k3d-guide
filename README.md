# k3d-guide

## Registry
```yaml
# this file will be mounted into /etc/rancher/k3s/registries.yaml 
mirrors:
    "10.121.218.184:30002":
       endpoint:
         - "http://10.121.218.184:30002"
configs:
  "10.121.218.184:30002":
    tls:
      insecure_skip_verify: true
```

下面的命令参数可以让 k3d 使用自定义的 Registry 配置，实现拉取镜像时不做 TLS 校验：
```shell
k3d cluster create --registry-config config/registry/default.yaml
```

## 指定 k3s 镜像
```shell
k3d cluster create --image 10.121.218.184:30002/cache/rancher/k3s
```
