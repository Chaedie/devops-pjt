### 1. node 성능 부족

```

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

helm_release.metrics_server: Destroying... [id=metrics-server]
helm_release.metrics_server: Destruction complete after 2s
helm_release.metrics_server: Creating...
helm_release.metrics_server: Still creating... [10s elapsed]
...
helm_release.metrics_server: Still creating... [5m0s elapsed]
╷
│ Warning: Helm release "" was created but has a failed status. Use the `helm` command to investigate the error, correct it, then run Terraform again.
│ 
│   with helm_release.metrics_server,
│   on 12-metrics-server.tf line 1, in resource "helm_release" "metrics_server":
│    1: resource "helm_release" "metrics_server" {
│ 
╵
╷
│ Error: context deadline exceeded
│ 
│   with helm_release.metrics_server,
│   on 12-metrics-server.tf line 1, in resource "helm_release" "metrics_server":
│    1: resource "helm_release" "metrics_server" {
│ ```

비용을 들이기 싫어 t2.micro 로 instance type 을 지정하고 진행헀더니 아래와 같은 에러가 발생했다. 
`kubectl describe pod -n kube-system` 을 통해 상태를 보았더니 아래와 같이 "Too many pods" 라는 메세지가 뜨더라. 어쩔 수 없이 t3.small 로 terraform apply 했더니 문제없이 provisioning 이 되었다. 

```
  Warning  FailedScheduling  2m10s (x2 over 7m26s)  default-scheduler  0/1 nodes are available: 1 Too many pods. preemption: 0/1 nodes are available: 1 No preemption victims found for incoming pod.
```