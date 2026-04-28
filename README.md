<!-- ghmig:moved -->
> **This repository has moved to [https://git.navicore.tech/navicore/kafka-yaml-generator](https://git.navicore.tech/navicore/kafka-yaml-generator).**
>
> The GitHub copy is archived and no longer maintained.

# kafka-yaml-generator

kafka yaml generator for test instances (do not use in prod)

* works on azure
* cheats by using privileged mode and host file mounts so use nodeSelector

quick and dirty testing while I'm figuring out storage class issues with the helm package

1. create services from services yaml
2. create zookeepers with istio sidecars
```console
kubectl  apply -f <(istioctl kube-inject -f  ./zookeeper-cluster.yaml)
```
3. create brokers with istio sidecars
```console
kubectl  apply -f <(istioctl kube-inject -f  ./kafka-controller1.yaml)
```
... for each broker