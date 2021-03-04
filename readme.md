# Kubernetes practice

## Preparation:

1. Install Oracel VirtualBox `sudo apt install virtualbox virtualbox—ext–pack`
2. Install Vagrant `sudo apt install vagrant`


| Node    | name         | cpus | memory | OS (Vagrant box)             | IP            | hostname     | username | password |
|---------|--------------|------|--------|------------------------------|---------------|--------------|----------|----------|
| master  | master.dora  | 2    | 2048   | tranphuquy19/centos7         | 172.16.10.100 | master.dora  | root     | 11231123 |
| worker1 | worker1.dora | 1    | 1024   | tranphuquy19/centos7         | 172.16.10.101 | worker1.dora | root     | 11231123 |
| worker2 | worker2.dora | 1    | 1024   | tranphuquy19/centos7         | 172.16.10.102 | worker2.dora | root     | 11231123 |

## Init master-node

`kubeadm init --apiserver-advertise-address 172.16.10.100 --pod-network-cidr=10.244.0.0/16`

## Làm việc với cluster

| Lệnh | Diến giải |
|-|-|
| kubectl get nodes | Danh sách các Node trong Cluster |
| kubectl describe node name-node | Thông tin chi tiết về Node có tên name-node |
| kubectl get pods | Liệt kê các POD trong namespace hiện tại, thêm tham số -o wide hiện thị chi tiết hơn, thêm -A hiện thị tất cả namespace, thêm -n namespacename hiện thị Pod của namespace namespacename |
| kubectl explain pod --recursive=true | Xem cấu trúc mẫu định nghĩa POD trong file cấu hình yaml |
| kubectl apply -f firstpod.yaml | Triển khai tạo các tài nguyên định nghĩa trong file firstpod.yaml |
| kubectl delete -f firstpod.yaml | Xóa các tài nguyên tạo ra từ định nghĩa firstpod.yaml |
| kubectl describe pod/namepod | Lấy thông tin chi tiết POD có tên namepod, nếu POD trong namespace khác mặc định thêm vào tham số -n namespace-name |
| kubectl logs pod/podname | Xem logs của POD có tên podname |
| kubectl exec mypod command | Chạy lệnh từ container của POD có tên mypod, nếu POD có nhiều container thêm vào tham số -c và tên container |
| kubectl exec -it mypod bash | Chạy lệnh bash của container trong POD mypod và gắn terminal |
| kubectl proxy | Tạo server proxy truy cập đến các tài nguyên của Cluster. http://localhost/api/v1/namespaces/default/pods/mypod:8085/proxy/, truy cập đến container có tên mypod trong namespace mặc định. |
| kubectl delete pod/mypod | Xóa POD có tên mypod |