# Apphub on Github

## Use the curated folder chart

```
helm repo add hubcurated https://cloudnativeapp.github.io/charts/curated/
helm repo update
helm search repo hubcurated -l
```

## Use the subbmitted folder chart

```
helm repo add hubsubbmitted https://cloudnativeapp.github.io/charts/subbmitted/
helm repo update
helm search repo hubsubbmitted -l
```


## 自测修改后的 openvpn
- 安装 metalLB 作为 lb
- 基于 kube-ovn 环境
```
helm lint openvpn
helm package openvpn
mv /root/charts/curated/openvpn-2.5.8.tgz /tmp
helm install /tmp/openvpn-2.5.8.tgz --generate-name -f my-values.yaml

# my-values.yaml 复用 values.yaml
## 仅对齐了 kube-ovn 的默认网段
## 由于当前环境没有 pvc 所以禁用了 pvc ，详见区别可以 diff  bb-test-openvpn-values.yaml values.yaml


```
