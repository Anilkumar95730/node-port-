# node-port
installation process:
# To install kubectl

  1  curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
    2  chmod +x ./kubectl
    3  sudo mv ./kubectl /usr/local/bin/kubectl

# To install docker
    
    4  sudo apt-get update && >     sudo apt-get install docker.io -y

# To install minikube

    5  curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
    
    6  sudo apt install conntrack -y
    7  git clone https://github.com/Mirantis/cri-dockerd.git
    
    8  apt  install golang-go
   
    9  wget https://storage.googleapis.com/golang/getgo/installer_linux
       chmod +x ./installer_linux
       ./installer_linux

   10  cd cri-dockerd
       mkdir bin
       go get && go build -o bin/cri-dockerd
       mkdir -p /usr/local/bin
       install -o root -g root -m 0755 bin/cri-dockerd /usr/local/bin/cri-dockerd
       cp -a packaging/systemd/* /etc/systemd/system
       sed -i -e 's,/usr/bin/cri-dockerd,/usr/local/bin/cri-dockerd,' /etc/systemd/system/cri-docker.service
       systemctl daemon-reload
       systemctl enable cri-docker.service
       systemctl enable --now cri-docker.socket

   11  VERSION="v1.24.1"
       curl -L https://github.com/kubernetes-sigs/cri-tools/releases/download/$VERSION/crictl-${VERSION}-linux-amd64.tar.gz --output crictl-${VERSION}-linux-amd64.tar.gz

   12  sudo tar zxvf crictl-$VERSION-linux-amd64.tar.gz -C /usr/local/bin
       rm -f crictl-$VERSION-linux-amd64.tar.gz

   13                               VERSION="v1.24.1"
                                  wget https://github.com/kubernetes-sigs/cri-tools/releases/download/$VERSION/crictl-$VERSION-linux-amd64.tar.gz

   14                          sudo tar zxvf crictl-$VERSION-linux-amd64.tar.gz -C /usr/local/bin
                                rm -f crictl-$VERSION-linux-amd64.tar.gz


   15                           sudo apt install -y containernetworking-plugins

   16                          wget https://github.com/containernetworking/plugins/releases/download/v1.2.0/cni-plugins-linux-amd64-v1.2.0.tgz
   17                          sudo mkdir -p /opt/cni/bin
   18                         sudo tar -C /opt/cni/bin -xzf cni-plugins-linux-amd64-v1.2.0.tgz


   19                        sudo sysctl fs.protected_regular=0
   
   20                         sudo minikube start --vm-driver=none
   
   
