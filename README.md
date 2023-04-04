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


## 自测修改后的openvpn
- 安装metal lb作为lb
- 基于kube-ovn环境
```
helm lint openvpn
helm package openvpn
helm install /root/charts/curated/openvpn-3.12.4.tgz --generate-name -f bb-test-openvpn-values.yaml

# bb-test-openvpn-values.yaml
## 仅对齐了 kube-ovn 的默认网段
## 由于当前没弄 pvc 所以禁用了 pvc ，详见区别可以 diff  bb-test-openvpn-values.yaml values.yaml
```
