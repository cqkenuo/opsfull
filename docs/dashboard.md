# Kubernetes Dashboard

## 创建Dashboard
```
[root@linux-node1 ~]# kubectl create -f /srv/addons/dashboard/
[root@linux-node1 ~]# kubectl cluster-info
Kubernetes master is running at https://192.168.56.11:6443
kubernetes-dashboard is running at https://192.168.56.11:6443/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

```
## 访问Dashboard

https://192.168.56.11:6443/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy
用户名:admin  密码：admin 选择令牌模式登录。

### 获取Token
```
[root@linux-node1 ~]# kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
Name:         admin-user-token-c97bl
Namespace:    kube-system
Labels:       <none>
Annotations:  kubernetes.io/service-account.name=admin-user
              kubernetes.io/service-account.uid=379208ff-cb86-11e8-9f1c-080027dc9cd8

Type:  kubernetes.io/service-account-token

Data
====
ca.crt:     1359 bytes
namespace:  11 bytes
token:      eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi11c2VyLXRva2VuLWM5N2JsIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImFkbWluLXVzZXIiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiIzNzkyMDhmZi1jYjg2LTExZTgtOWYxYy0wODAwMjdkYzljZDgiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZS1zeXN0ZW06YWRtaW4tdXNlciJ9.LopL7AD9feBZmhAuAUlPNjfthlJ1lJAPG6VXgBl-MZdofZpqNU9m-o-7M4hHa5AXkpeLvQrA1UKWWSR9eWEN06ugIkcH4Pk-tKrSVQUM6CDaE7eBdK91x1ltTonLz62_z_X8IvRYx1piv3wRUijoyRHCdziBnOhg67sT974CSPoRSOpl7ZR0Kn_L0LYRMOE9xfU3w4-sCpSx-jgc5oysAix95NqZgIkaZ6TRANpCnHE66fqL6yUwQxQ5yt7pw7J2iuSE3OxPU_cKArjYlWUvr72zG3SxZaR7dzQEggwmjSSeHRs0OK0968QAtCca1NTmcPaTtKhXYfXXdtusVCx7bA
```
