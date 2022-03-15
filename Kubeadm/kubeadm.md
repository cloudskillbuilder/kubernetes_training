ilk asamada calısıtırlması gereken komutlar (her iki sunucuda da - Control and Data Plane)

1.komut:

$ cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
br_netfilter
EOF


2.komut 
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF


3.komut

sudo sysctl --system

4.komut

cat <<EOF | sudo tee /etc/modules-load.d/containerd.conf
overlay
br_netfilter
EOF


5.komut

$ sudo modprobe overlay
$ sudo modprobe br_netfilter

6.komut

cat <<EOF | sudo tee /etc/sysctl.d/99-kubernetes-cri.conf
net.bridge.bridge-nf-call-iptables  = 1
net.ipv4.ip_forward                 = 1
net.bridge.bridge-nf-call-ip6tables = 1
EOF

sudo sysctl --system

7. komut

$ sudo apt-get update
$ sudo apt-get upgrade -y

8.komut

$ sudo apt-get install containerd -y
$ sudo mkdir -p /etc/containerd
$ sudo su -
$ containerd config default | tee /etc/containerd/config.toml
$ exit
$ sudo systemctl restart containerd


9.Kubeadm 

$ sudo apt-get update
$ sudo apt-get install -y apt-transport-https ca-certificates curl
$ sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
$ echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
$ sudo apt-get update
$ sudo apt-get install -y kubelet kubeadm kubectl
$ sudo apt-mark hold kubelet kubeadm kubectl

10.kubernetes Images

sudo kubeadm config images pull

11. Kubeadm init (Bu komuta kadar aynı)

sudo kubeadm init --pod-network-cidr=10.34.0.0/16 --apiserver-advertise-address=172.31.83.219 --control-plane-endpoint=172.31.83.219

12. komut NotReady Master node içerisinde

$ kubectl create -f https://docs.projectcalico.org/manifests/tigera-operator.yaml
$ kubectl create -f https://docs.projectcalico.org/manifests/custom-resources.yaml




