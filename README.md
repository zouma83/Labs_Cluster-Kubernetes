# Labs_Cluster-Kubernetes
Labs - Cluster Kubernetes
```
|-------------------------------------------------------------------------------------------------|
|     ...                      Tuto Install - Cluster K8S - Docker                       ...      |
|    (o-o)                     Florent Marquez - TSSI27 - AFPA 83                       (o-o)     |
|ooO--(_)--Ooo                     Installation sur VMs KVM                         ooO--(_)--Ooo |
|-------------------------------------------------------------------------------------------------|



                                   _,met$$$$$gg.
                               ,g$$$$$$$$$$$$$$$P.
                             ,g$$P""       """Y$$.".
                            ,$$P'              `$$$. 
                          ',$$P       ,ggs.     `$$b:
                          `d$$'     ,$P"'   .    $$$
                           $$P      d$'     ,    $$P
                           $$:      $$.   -    ,d$$'
                           $$;      Y$b._   _,d$P'
                           Y$$.    `.`"Y$$$$P"' 
                           `$$b      "-.__
                            `Y$$b
                             `Y$$.
                               `$$b.
                                 `Y$$b.
                                   `"Y$b._
                                       `""""

                       _,           _,      ,'`.
                     `$$'         `$$'     `.  ,'
                      $$           $$        `'
                      $$           $$         _,           _ 
                ,d$$$g$$  ,d$$$b.  $$,d$$$b.`$$' g$$$$$b.`$$,d$$b.
               ,$P'  `$$ ,$P' `Y$. $$$'  `$$ $$  "'   `$$ $$$' `$$
               $$'    $$ $$'   `$$ $$'    $$ $$  ,ggggg$$ $$'   $$
               $$     $$ $$ggggg$$ $$     $$ $$ ,$P"   $$ $$    $$
               $$    ,$$ $$.       $$    ,$P $$ $$'   ,$$ $$    $$
               `$g. ,$$$ `$$._ _., $$ _,g$P' $$ `$b. ,$$$ $$    $$
                `Y$$P'$$. `Y$$$$P',$$$$P"'  ,$$. `Y$$P'$$.$$.  ,$$.
   
   
   
                                       

                                       
                                                          ./smMmNMds:`                                                            
                                                      .+yNNdyo+//+shmNms/.                                                        
                                                  -+yNNdyo+//////////+shdNmy/.                                                    
                                              -+hNmdyo+////////ys///////++oydNmy+.                                                
                                            `hNdyo+////////////Nm///////////++oymNs                                               
                                            sMy+////////////+ooNmo++////////////+dM/                                              
                                           `NN+////yho//+shmNNNMMNNNmyo///shs////oMd                                              
                                           oMh/////ohmdhmMNhsoyMMooydNMmhdmh+/////dM:                                             
                                           mN+///////oMMMNy+//yMMo//ohMMMm+///////oMh                                             
                                          /Mh///////+mMmymMNdsdMMhydNMmyNMh////////mM-                                            
                                          dMo///////yMM+/+smMMMNNMMMds+/sMMo///////sMy                                            
                                         :Md////////hMm+osymMMd++mMMdysooMMy///////+NN.                                           
                                         hMo////+oosmMMNNNNmNMNddMMNmNNNNMMdsso+////yMs                                           
                                         Mm/////ydhyyNMmoo++hMMNNMMy++osNMmyydds////+MN                                           
                                         NNo/////+///oNMdo/sMMd+omMNo/omMmo///+/////sMd                                           
                                         -hNh+////////odNNdNMd+//+mMmdNNh+////////odNy.                                           
                                          `+Nms/////////ohMMMNmmmmNMMMyo////////+yNm/                                             
                                            .yNd+///////+hNsosyyyysoyMy////////odNs`                                              
                                              /mNy+/////sNy//////////hNo/////+yNd:                                                
                                               .sNdo////++///////////++/////smNo`                                                 
                                                 :dNy+////////////////////+hNh-                                                   
                                                  `oNmysssssssssssssssssshNm/                                                     
                                                    .+ssssssssssssssssssss/`                                                      
                                                                                                                                  
 ####                      ####                                                                                                   
 ####                      ####                                                                ####                               
 ####                      #### ###         ####          #####      #####          ###        ####           ####         #####  
 #### #####   ####   ####  ##########    #########    ##########   ##########    #########  ############   #########    ##########
 #########    ####   ####  ####  #####  ####   ####   ##########   ####  ####   ####   ####    ####       #####  ####   ####    # 
 #######      ####   ####  ####   ##################  ####         ####  ####  ############    ####       ############  ########  
 ########     ####   ####  ####   #### ############   ####         ####   ###  ############    ####       ###########     ########
 #### #####   ##### #####  ####  #####  ######  ##    ####         ####   ###   #####   ##     #####  ##  ######  ##    ###   ####
 ####  #####   ##########  ##########    ##########   ####         ####   ###    #########      #########  ##########  ###########



                    ##        .            
              ## ## ##       ==            
           ## ## ## ##      ===            
       /""""""""""""""""\___/ ===        
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~   
       \______ o          __/            
         \    \        __/             
          \____\______/                
 
          |          |
       __ |  __   __ | _  __   _
      /  \| /  \ /   |/  / _\ | 
      \__/| \__/ \__ |\_ \__  |

   /----------------------------\
   |                            |
   | Installation sur :         |
   |                            |
   |   * Debian 9.x Serveur *   |
   |     ------------------     |
   |                            |
   |            de :            |
   |                            |
   | *  Cluster K8S - Docker *  |
   |    --------------------    |
   |                            |
   \----------------------------/ 
                                                     
    Cluster Kubernetes K8S - Docker:
    --------------------------------
        x1 Control Tower & HAProxy
        x3 K8S-Master
        x3 K8S-Worker

        Kubernetes  v1.13.1
        Docker      v18.06
```

Pré-requis:
-----------
- x7 VMS Debian Stretch 9.x (en bridged network) (serveur SSH & utilitaires usuels du système)
- vm#1 CT-HAProxy avec environnement de bureau LXDE ou autre
- Full FQDN (/!\ hosts /!\) - DNS: 127.0.0.1 + DNS FAI
- Même sous réseau - Gateway routeur/box (192.168.0.0/24)
- le sous réseau 10.30.0.0/24 devra être disponible, il sera utilisé en interne dans le cluster


O - Confs de départ:
--------------------
 - vm#1: ct-haproxy.cluster-docker.local    192.168.0.100
   spécial vms KVM une 2ème carte reseau en 192.168.100.100 pour les communications avec l'hôte KVM
 - vm#2: k8s-master-1.cluster-docker.local  192.168.0.101
 - vm#3: k8s-master-2.cluster-docker.local  192.168.0.102
 - vm#4: k8s-master-3.cluster-docker.local  192.168.0.103
 - vm#5: k8s-worker-1.cluster-docker.local  192.168.0.201
 - vm#6: k8s-worker-2.cluster-docker.local  192.168.0.202
 - vm#7: k8s-worker-3.cluster-docker.local  192.168.0.203
 
 - Utilisateurs:
    # root #
    $ toor $
    
 - Installation sur toutes les vms des paquets nécessaires à l'installation du Cluster K8S:
    # apt-get update && apt-get upgrade
    # apt-get install curl apt-transport-https software-properties-common
 
 - Option TeamViewer sur vm#1 CT-HAProxy
    $ wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
    # dpkg -i /home/toor/teamviewer_amd64.deb
    # apt-get update --fix-missing
    # apt-get install -f    #(-f = -fix-broken)


I - Installation des clients sur vm#1 CT-HAProxy:
-------------------------------------------------
    
1) - installation du client Cloud Flare SSL:
    $ ssh toor@192.168.100.100
    
    $ wget https://pkg.cfssl.org/R1.2/cfssl_linux-amd64
    
    $ wget https://pkg.cfssl.org/R1.2/cfssljson_linux-amd64
    
    $ chmod +x cfssl*
    
    # mv cfssl_linux-amd64 /usr/local/bin/cfssl
    
    # mv cfssljson_linux-amd64 /usr/local/bin/cfssljson
    
    $ cfssl version
    =>  Version: 1.2.0                                                                                                                                                                                                                              
        Revision: dev                                                                                                                                                                                                                               
        Runtime: go1.6
    
2) - installation du client Kubernetes, kubectl:
    $ wget https://storage.googleapis.com/kubernetes-release/release/v1.13.1/bin/linux/amd64/kubectl
    
    $ chmod +x kubectl
    
    # mv kubectl /usr/local/bin
    
    $ kubectl version
    =>  Client Version: version.Info{Major:"1", Minor:"13", GitVersion:"v1.13.1",
        GitCommit:"eec55b9ba98609a46fee712359c7b5b365bdd920", GitTreeState:"clean", BuildDate:"2018-12-13T10:39:04Z",
        GoVersion:"go1.11.2", Compiler:"gc", Platform:"linux/amd64"}
        The connection to the server localhost:8080 was refused - did you specify the right host or port?
    
3) - installation du HAProxy LoadBalancer:
    # apt-get install haproxy
    
    # nano /etc/haproxy/haproxy.cfg
    ##################################################
global
...

default
...

frontend kubernetes
    bind 192.168.0.100:6443
    option tcplog
    mode tcp
    default_backend kubernetes-master-nodes
    
backend kubernetes-master-nodes
    mode tcp
    balance roundrobin
    option tcp-check
    server k8s-master-1 192.168.0.101:6443 check fall 3 rise 2
    server k8s-master-2 192.168.0.102:6443 check fall 3 rise 2
    server k8s-master-3 192.168.0.103:6443 check fall 3 rise 2
    ##################################################
    # systemctl restart haproxy
    # systemctl status haproxy
    => active & started sans erreur
    
4) - génération des certificats:
    $ nano ca-config.json
    ##################################################
{
  "signing": {
    "default": {
      "expiry": "8760h"
    },
    "profiles": {
      "kubernetes": {
        "usages": ["signing", "key encipherment", "server auth", "client auth"],
        "expiry": "8760h"
      }
    }
  }
}
    ##################################################
    
    $ nano ca-csr.json
    ##################################################
{
  "CN": "Kubernetes",
  "key": {
    "algo": "rsa",
    "size": 2048
  },
  "names": [
  {
    "C": "IE",
    "L": "Cork",
    "O": "Kubernetes",
    "OU": "CA",
    "ST": "Cork Co."
  }
 ]
}
    ##################################################
    
    $ cfssl gencert -initca ca-csr.json | cfssljson -bare ca
    
    $ ls -la
    =>  -rw-------  1 toor toor     1679 déc.  14 13:00 ca-key.pem
        -rw-r--r--  1 toor toor     1363 déc.  14 13:00 ca.pem
    
    $ nano kubernetes-csr.json
    ##################################################
{
  "CN": "kubernetes",
  "key": {
    "algo": "rsa",
    "size": 2048
  },
  "names": [
  {
    "C": "IE",
    "L": "Cork",
    "O": "Kubernetes",
    "OU": "Kubernetes",
    "ST": "Cork Co."
  }
 ]
}
    ##################################################
    
    $ cfssl gencert \
    -ca=ca.pem \
    -ca-key=ca-key.pem \
    -config=ca-config.json \
    -hostname=192.168.0.101,192.168.0.102,192.168.0.103,192.168.0.100,127.0.0.1,kubernetes.default \
    -profile=kubernetes kubernetes-csr.json | \
    cfssljson -bare kubernetes
    
    $ ls -la
    =>  -rw-------  1 toor toor     1675 déc.  14 13:06 kubernetes-key.pem
        -rw-r--r--  1 toor toor     1493 déc.  14 13:06 kubernetes.pem
    
5) copie des certificats sur chaque noeuds du Cluster K8S:
    $ scp ca.pem kubernetes.pem kubernetes-key.pem toor@192.168.0.101:~
    
    $ scp ca.pem kubernetes.pem kubernetes-key.pem toor@192.168.0.102:~
    
    $ scp ca.pem kubernetes.pem kubernetes-key.pem toor@192.168.0.103:~
    
    $ scp ca.pem kubernetes.pem kubernetes-key.pem toor@192.168.0.201:~
    
    $ scp ca.pem kubernetes.pem kubernetes-key.pem toor@192.168.0.202:~
    
    $ scp ca.pem kubernetes.pem kubernetes-key.pem toor@192.168.0.203:~
    
    
II - Préparation des K8S-Master & K8S-Worker:
---------------------------------------------
1) - préparation de la vm#2 K8S-Master-1:
    $ ssh toor@192.168.0.101
    
    # curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
    
    # add-apt-repository \
    "deb https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable"
    
    # apt-get update
    
    # apt-get install -y docker-ce=$(apt-cache madison docker-ce | grep 18.06 | head -1 | awk '{print $3}')
    
    # curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    
    # nano /etc/apt/sources.list.d/kubernetes.list
    ##################################################
deb http://apt.kubernetes.io kubernetes-xenial main
    ##################################################
    
    # apt-get update
    
    # apt-get install kubelet kubeadm kubectl
    
    # swapoff -a
    
    # sed -i '/ swap / s/^/#/' /etc/fstab
    
2) - préparation de la vm#3 K8S-Master-2:
    $ ssh toor@192.168.0.102
    
    # curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
    
    # add-apt-repository \
    "deb https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable"
    
    # apt-get update
    
    # apt-get install -y docker-ce=$(apt-cache madison docker-ce | grep 18.06 | head -1 | awk '{print $3}')
    
    # curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    
    # nano /etc/apt/sources.list.d/kubernetes.list
    ##################################################
deb http://apt.kubernetes.io kubernetes-xenial main
    ##################################################
    
    # apt-get update
    
    # apt-get install kubelet kubeadm kubectl
    
    # swapoff -a
    
    # sed -i '/ swap / s/^/#/' /etc/fstab
    
3) - préparation de la vm#4 K8S-Master-3:
    $ ssh toor@192.168.0.103
    
    # curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
    
    # add-apt-repository \
    "deb https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable"
    
    # apt-get update
    
    # apt-get install -y docker-ce=$(apt-cache madison docker-ce | grep 18.06 | head -1 | awk '{print $3}')
    
    # curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    
    # nano /etc/apt/sources.list.d/kubernetes.list
    ##################################################
deb http://apt.kubernetes.io kubernetes-xenial main
    ##################################################
    
    # apt-get update
    
    # apt-get install kubelet kubeadm kubectl
    
    # swapoff -a
    
    # sed -i '/ swap / s/^/#/' /etc/fstab
    
4) - préparation de la vm#5 K8S-Worker-1:
    $ ssh toor@192.168.0.201
    
    # curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
    
    # add-apt-repository \
    "deb https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable"
    
    # apt-get update
    
    # apt-get install -y docker-ce=$(apt-cache madison docker-ce | grep 18.06 | head -1 | awk '{print $3}')
    
    # curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    
    # nano /etc/apt/sources.list.d/kubernetes.list
    ##################################################
deb http://apt.kubernetes.io kubernetes-xenial main
    ##################################################
    
    # apt-get update
    
    # apt-get install kubelet kubeadm kubectl
    
    # swapoff -a
    
    # sed -i '/ swap / s/^/#/' /etc/fstab
    
5) - préparation de la vm#6 K8S-Worker-2:
    $ ssh toor@192.168.0.202
    
    # curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
    
    # add-apt-repository \
    "deb https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable"
    
    # apt-get update
    
    # apt-get install -y docker-ce=$(apt-cache madison docker-ce | grep 18.06 | head -1 | awk '{print $3}')
    
    # curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    
    # nano /etc/apt/sources.list.d/kubernetes.list
    ##################################################
deb http://apt.kubernetes.io kubernetes-xenial main
    ##################################################
    
    # apt-get update
    
    # apt-get install kubelet kubeadm kubectl
    
    # swapoff -a
    
    # sed -i '/ swap / s/^/#/' /etc/fstab
    
6) - préparation de la vm#7 K8S-Worker-3:
    $ ssh toor@192.168.0.203
    
    # curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
    
    # add-apt-repository \
    "deb https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
    $(lsb_release -cs) \
    stable"
    
    # apt-get update
    
    # apt-get install -y docker-ce=$(apt-cache madison docker-ce | grep 18.06 | head -1 | awk '{print $3}')
    
    # curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    
    # nano /etc/apt/sources.list.d/kubernetes.list
    ##################################################
deb http://apt.kubernetes.io kubernetes-xenial main
    ##################################################
    
    # apt-get update
    
    # apt-get install kubelet kubeadm kubectl
    
    # swapoff -a
    
    # sed -i '/ swap / s/^/#/' /etc/fstab
    
    
III - Installation du service Etcd sur les K8S-Master:
------------------------------------------------------
1) - installation du service Etcd sur vm#2 K8S-Master-1:
    $ ssh toor@192.168.0.101
    
    # mkdir /etc/etcd /var/lib/etcd
    
    # mv ca.pem kubernetes.pem kubernetes-key.pem /etc/etcd
    
    $ wget https://github.com/coreos/etcd/releases/download/v3.3.10/etcd-v3.3.10-linux-amd64.tar.gz
    
    $ tar xvzf etcd-v3.3.10-linux-amd64.tar.gz
    
    # mv etcd-v3.3.10-linux-amd64/etcd* /usr/local/bin/
    
    # nano /etc/systemd/system/etcd.service
    ##################################################
[Unit]
Description=etcd
Documentation=https://github.com/coreos


[Service]
ExecStart=/usr/local/bin/etcd \
  --name 192.168.0.101 \
  --cert-file=/etc/etcd/kubernetes.pem \
  --key-file=/etc/etcd/kubernetes-key.pem \
  --peer-cert-file=/etc/etcd/kubernetes.pem \
  --peer-key-file=/etc/etcd/kubernetes-key.pem \
  --trusted-ca-file=/etc/etcd/ca.pem \
  --peer-trusted-ca-file=/etc/etcd/ca.pem \
  --peer-client-cert-auth \
  --client-cert-auth \
  --initial-advertise-peer-urls https://192.168.0.101:2380 \
  --listen-peer-urls https://192.168.0.101:2380 \
  --listen-client-urls https://192.168.0.101:2379,http://127.0.0.1:2379 \
  --advertise-client-urls https://192.168.0.101:2379 \
  --initial-cluster-token etcd-cluster-0 \
  --initial-cluster 192.168.0.101=https://192.168.0.101:2380,192.168.0.102=https://192.168.0.102:2380,192.168.0.103=https://192.168.0.103:2380 \
  --initial-cluster-state new \
  --data-dir=/var/lib/etcd
Restart=on-failure
RestartSec=5


[Install]
WantedBy=multi-user.target
    ##################################################
    
    # systemctl daemon-reload
    
    # systemctl enable etcd
    
    # systemctl start etcd
    
2) - installation du service Etcd sur vm#3 K8S-Master-2:
    $ ssh toor@192.168.0.102
    
    # mkdir /etc/etcd /var/lib/etcd
    
    # mv ca.pem kubernetes.pem kubernetes-key.pem /etc/etcd
    
    $ wget https://github.com/coreos/etcd/releases/download/v3.3.10/etcd-v3.3.10-linux-amd64.tar.gz
    
    $ tar xvzf etcd-v3.3.10-linux-amd64.tar.gz
    
    # mv etcd-v3.3.10-linux-amd64/etcd* /usr/local/bin/
    
    # nano /etc/systemd/system/etcd.service
    ##################################################
[Unit]
Description=etcd
Documentation=https://github.com/coreos


[Service]
ExecStart=/usr/local/bin/etcd \
  --name 192.168.0.102 \
  --cert-file=/etc/etcd/kubernetes.pem \
  --key-file=/etc/etcd/kubernetes-key.pem \
  --peer-cert-file=/etc/etcd/kubernetes.pem \
  --peer-key-file=/etc/etcd/kubernetes-key.pem \
  --trusted-ca-file=/etc/etcd/ca.pem \
  --peer-trusted-ca-file=/etc/etcd/ca.pem \
  --peer-client-cert-auth \
  --client-cert-auth \
  --initial-advertise-peer-urls https://192.168.0.102:2380 \
  --listen-peer-urls https://192.168.0.102:2380 \
  --listen-client-urls https://192.168.0.102:2379,http://127.0.0.1:2379 \
  --advertise-client-urls https://192.168.0.102:2379 \
  --initial-cluster-token etcd-cluster-0 \
  --initial-cluster 192.168.0.101=https://192.168.0.101:2380,192.168.0.102=https://192.168.0.102:2380,192.168.0.103=https://192.168.0.103:2380 \
  --initial-cluster-state new \
  --data-dir=/var/lib/etcd
Restart=on-failure
RestartSec=5


[Install]
WantedBy=multi-user.target
    ##################################################
    
    # systemctl daemon-reload
    
    # systemctl enable etcd
    
    # systemctl start etcd
    
3) - installation du service Etcd sur vm#4 K8S-Master-3:
    $ ssh toor@192.168.0.103
    
    # mkdir /etc/etcd /var/lib/etcd
    
    # mv ca.pem kubernetes.pem kubernetes-key.pem /etc/etcd
    
    $ wget https://github.com/coreos/etcd/releases/download/v3.3.10/etcd-v3.3.10-linux-amd64.tar.gz
    
    $ tar xvzf etcd-v3.3.10-linux-amd64.tar.gz
    
    # mv etcd-v3.3.10-linux-amd64/etcd* /usr/local/bin/
    
    # nano /etc/systemd/system/etcd.service
    ##################################################
[Unit]
Description=etcd
Documentation=https://github.com/coreos


[Service]
ExecStart=/usr/local/bin/etcd \
  --name 192.168.0.103 \
  --cert-file=/etc/etcd/kubernetes.pem \
  --key-file=/etc/etcd/kubernetes-key.pem \
  --peer-cert-file=/etc/etcd/kubernetes.pem \
  --peer-key-file=/etc/etcd/kubernetes-key.pem \
  --trusted-ca-file=/etc/etcd/ca.pem \
  --peer-trusted-ca-file=/etc/etcd/ca.pem \
  --peer-client-cert-auth \
  --client-cert-auth \
  --initial-advertise-peer-urls https://192.168.0.103:2380 \
  --listen-peer-urls https://192.168.0.103:2380 \
  --listen-client-urls https://192.168.0.103:2379,http://127.0.0.1:2379 \
  --advertise-client-urls https://192.168.0.103:2379 \
  --initial-cluster-token etcd-cluster-0 \
  --initial-cluster 192.168.0.101=https://192.168.0.101:2380,192.168.0.102=https://192.168.0.102:2380,192.168.0.103=https://192.168.0.103:2380 \
  --initial-cluster-state new \
  --data-dir=/var/lib/etcd
Restart=on-failure
RestartSec=5


[Install]
WantedBy=multi-user.target
    ##################################################
    
    # systemctl daemon-reload
    
    # systemctl enable etcd
    
    # systemctl start etcd
    
    $ ETCDCTL_API=3 etcdctl member list
    =>  a5c9f73566fadce, started, 192.168.0.101, https://192.168.0.101:2380, https://192.168.0.101:2379
        4701789a3a673ef5, started, 192.168.0.103, https://192.168.0.103:2380, https://192.168.0.103:2379
        90262c9df511cc4d, started, 192.168.0.102, https://192.168.0.102:2380, https://192.168.0.102:2379


IV - Initialisation des K8S-Master:
-----------------------------------
1) - initialisation du K8S-Master-1:
    $ ssh toor@192.168.0.101
    
    $ nano config.yaml
    ##################################################
apiVersion: kubeadm.k8s.io/v1alpha3
kind: ClusterConfiguration
kubernetesVersion: stable
apiServerCertSANs:
- 192.168.0.100
controlPlaneEndpoint: "192.168.0.100:6443"
etcd:
  external:
    endpoints:
    - https://192.168.0.101:2379
    - https://192.168.0.102:2379
    - https://192.168.0.103:2379
    caFile: /etc/etcd/ca.pem
    certFile: /etc/etcd/kubernetes.pem
    keyFile: /etc/etcd/kubernetes-key.pem
networking:
  podSubnet: 10.30.0.0/24
apiServerExtraArgs:
  apiserver-count: "3"
    ##################################################
    
    # kubeadm init --config=/home/toor/config.yaml
    =>  Your Kubernetes master has initialized successfully!

        To start using your cluster, you need to run the following as a regular user:

            mkdir -p $HOME/.kube
            sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
            sudo chown $(id -u):$(id -g) $HOME/.kube/config

        You should now deploy a pod network to the cluster.
        Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
            https://kubernetes.io/docs/concepts/cluster-administration/addons/

        You can now join any number of machines by running the following on each node
        as root:

        kubeadm join 192.168.0.100:6443 --token figf1e.xmugnpseeym8tgki --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
        
    # scp -r /etc/kubernetes/pki toor@192.168.0.102:~
    
    # scp -r /etc/kubernetes/pki toor@192.168.0.103:~

2) - initialisation du K8S-Master-2:
    $ ssh toor@192.168.0.102
    
    $ rm ~/pki/apiserver.*
    
    # mv /home/toor/pki /etc/kubernetes/
    
    $ nano config.yaml
    ##################################################
apiVersion: kubeadm.k8s.io/v1alpha3
kind: ClusterConfiguration
kubernetesVersion: stable
apiServerCertSANs:
- 192.168.0.100
controlPlaneEndpoint: "192.168.0.100:6443"
etcd:
  external:
    endpoints:
    - https://192.168.0.101:2379
    - https://192.168.0.102:2379
    - https://192.168.0.103:2379
    caFile: /etc/etcd/ca.pem
    certFile: /etc/etcd/kubernetes.pem
    keyFile: /etc/etcd/kubernetes-key.pem
networking:
  podSubnet: 10.30.0.0/24
apiServerExtraArgs:
  apiserver-count: "3"
    ##################################################
    
    # kubeadm init --config=/home/toor/config.yaml
    =>  Your Kubernetes master has initialized successfully!

        To start using your cluster, you need to run the following as a regular user:

            mkdir -p $HOME/.kube
            sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
            sudo chown $(id -u):$(id -g) $HOME/.kube/config

        You should now deploy a pod network to the cluster.
        Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
            https://kubernetes.io/docs/concepts/cluster-administration/addons/

        You can now join any number of machines by running the following on each node
        as root:

        kubeadm join 192.168.0.100:6443 --token 82n789.m8xqzsujnmn1h7cr --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
    
3) - initialisation du K8S-Master-3:
    $ ssh toor@192.168.0.103
    
    $ rm ~/pki/apiserver.*
    
    # mv /home/toor/pki /etc/kubernetes/
    
    $ nano config.yaml
    ##################################################
apiVersion: kubeadm.k8s.io/v1alpha3
kind: ClusterConfiguration
kubernetesVersion: stable
apiServerCertSANs:
- 192.168.0.100
controlPlaneEndpoint: "192.168.0.100:6443"
etcd:
  external:
    endpoints:
    - https://192.168.0.101:2379
    - https://192.168.0.102:2379
    - https://192.168.0.103:2379
    caFile: /etc/etcd/ca.pem
    certFile: /etc/etcd/kubernetes.pem
    keyFile: /etc/etcd/kubernetes-key.pem
networking:
  podSubnet: 10.30.0.0/24
apiServerExtraArgs:
  apiserver-count: "3"
    ##################################################
    
    # kubeadm init --config=/home/toor/config.yaml
    =>  Your Kubernetes master has initialized successfully!

        To start using your cluster, you need to run the following as a regular user:

            mkdir -p $HOME/.kube
            sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
            sudo chown $(id -u):$(id -g) $HOME/.kube/config

        You should now deploy a pod network to the cluster.
        Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
            https://kubernetes.io/docs/concepts/cluster-administration/addons/

        You can now join any number of machines by running the following on each node
        as root:

        kubeadm join 192.168.0.100:6443 --token 6t3yg5.mfd81bxravhnim1k --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
        
    /!\/!\/!\ A CONSERVER /!\/!\/!\
    ===> kubeadm join 192.168.0.100:6443 --token 6t3yg5.mfd81bxravhnim1k --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
    
    
V - initialisation des K8S-Worker:
----------------------------------
1) - initialisation du K8S-Worker-1:
    $ ssh toor@192.168.0.201
    
    # kubeadm join 192.168.0.100:6443 --token 6t3yg5.mfd81bxravhnim1k --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
    =>  This node has joined the cluster:
        * Certificate signing request was sent to apiserver and a response was received.
        * The Kubelet was informed of the new secure connection details.

        Run 'kubectl get nodes' on the master to see this node join the cluster.
    
2) - initialisation du K8S-Worker-2:
    $ ssh toor@192.168.0.202
    
    # kubeadm join 192.168.0.100:6443 --token 6t3yg5.mfd81bxravhnim1k --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
    =>  This node has joined the cluster:
        * Certificate signing request was sent to apiserver and a response was received.
        * The Kubelet was informed of the new secure connection details.

        Run 'kubectl get nodes' on the master to see this node join the cluster.
    
3) - initialisation du K8S-Worker-3:
    $ ssh toor@192.168.0.203
    
    # kubeadm join 192.168.0.100:6443 --token 6t3yg5.mfd81bxravhnim1k --discovery-token-ca-cert-hash sha256:7694a3f266b261de815041f129245261a34f3fca6e5402ab0a551893b2b08d09
    =>  This node has joined the cluster:
        * Certificate signing request was sent to apiserver and a response was received.
        * The Kubelet was informed of the new secure connection details.

        Run 'kubectl get nodes' on the master to see this node join the cluster.
    
    
VI - configuration de Kubectl sur la machine client CT-HAProxy:
---------------------------------------------------------------
1) - check du Cluster et transfert du fichier de configuration admin.conf sur CT-HAProxy:
    $ ssh toor@192.168.0.101
    
    # kubectl --kubeconfig /etc/kubernetes/admin.conf get nodes
    =>  NAME           STATUS     ROLES    AGE     VERSION
        k8s-master-1   NotReady   master   31m     v1.13.1
        k8s-master-2   NotReady   master   19m     v1.13.1
        k8s-master-3   NotReady   master   13m     v1.13.1
        k8s-worker-1   NotReady   <none>   6m34s   v1.13.1
        k8s-worker-2   NotReady   <none>   5m3s    v1.13.1
        k8s-worker-3   NotReady   <none>   3m30s   v1.13.1
        
    # chmod +r /etc/kubernetes/admin.conf
    
    $ scp /etc/kubernetes/admin.conf toor@192.168.0.100:/home/toor/
    
    # chmod 600 /etc/kubernetes/admin.conf
    
2) - création du ~/.kube/config sur CT-HAProxy:
    $ mkdir ~/.kube
    
    $ mv /home/toor/admin.conf ~/.kube/config
    
    $ chmod 600 ~/.kube/config
    
3) - check du cluster et de la communication entre CT-HAProxy et le Cluster K8S:
    $ kubectl get nodes
    =>  NAME           STATUS     ROLES    AGE   VERSION
        k8s-master-1   NotReady   master   39m   v1.13.1
        k8s-master-2   NotReady   master   28m   v1.13.1
        k8s-master-3   NotReady   master   21m   v1.13.1
        k8s-worker-1   NotReady   <none>   14m   v1.13.1
        k8s-worker-2   NotReady   <none>   13m   v1.13.1
        k8s-worker-3   NotReady   <none>   11m   v1.13.1


VII - déploiement de Weavenet comme réseau interne au cluster K8S depuis la machine CT-HAProxy:
-----------------------------------------------------------------------------------------------

    $ kubectl apply -f https://git.io/weave-kube-1.6
    
    $ kubectl get pods -n kube-system   #(/!\ attendre et renouveler jusqu'à ce que tout les pods soient "Running" /!\)
    =>  NAME                                   READY   STATUS    RESTARTS   AGE
        coredns-86c58d9df4-52x5r               1/1     Running   0          47m
        coredns-86c58d9df4-7ztvp               1/1     Running   0          47m
        kube-apiserver-k8s-master-1            1/1     Running   0          46m
        kube-apiserver-k8s-master-2            1/1     Running   0          36m
        kube-apiserver-k8s-master-3            1/1     Running   0          30m
        kube-controller-manager-k8s-master-1   1/1     Running   3          46m
        kube-controller-manager-k8s-master-2   1/1     Running   4          36m
        kube-controller-manager-k8s-master-3   1/1     Running   1          30m
        kube-proxy-57qxq                       1/1     Running   0          47m
        kube-proxy-7xszr                       1/1     Running   0          21m
        kube-proxy-d58wq                       1/1     Running   0          30m
        kube-proxy-h94ms                       1/1     Running   0          19m
        kube-proxy-kchvv                       1/1     Running   0          23m
        kube-proxy-nmjfg                       1/1     Running   0          36m
        kube-scheduler-k8s-master-1            1/1     Running   3          47m
        kube-scheduler-k8s-master-2            1/1     Running   2          36m
        kube-scheduler-k8s-master-3            1/1     Running   0          30m
        weave-net-4vhwq                        2/2     Running   0          5m4s
        weave-net-g9whn                        2/2     Running   0          5m4s
        weave-net-gfpnv                        2/2     Running   0          5m4s
        weave-net-ls44t                        2/2     Running   0          5m3s
        weave-net-pnxf2                        2/2     Running   0          5m3s
        weave-net-r5ft8                        2/2     Running   0          5m3s
    
    $ kubectl get nodes
    =>  NAME           STATUS   ROLES    AGE   VERSION
        k8s-master-1   Ready    master   49m   v1.13.1
        k8s-master-2   Ready    master   37m   v1.13.1
        k8s-master-3   Ready    master   31m   v1.13.1
        k8s-worker-1   Ready    <none>   24m   v1.13.1
        k8s-worker-2   Ready    <none>   22m   v1.13.1
        k8s-worker-3   Ready    <none>   21m   v1.13.1


VII - installation du Dashboard Kubernetes depuis la machine CT-HAProxy:
------------------------------------------------------------------------
1) - déploiement du Dashboard & check accès au Dashboard
    $ kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
    
    $ kubectl proxy
    =>  Starting to serve on 127.0.0.1:8001
    
    -> Depuis le navigateur (firefox) de CT-HAProxy:
    ===> http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
    
    $ [ctrl] + [c] pour arrêter le proxy

2) - création du compte Admin du Dashboard:
    $ kubectl create serviceaccount dashboard -n default
    
    $ kubectl create clusterrolebinding dashboard-admin -n default --clusterrole=cluster-admin --serviceaccount=default:dashboard
    
    $ kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
    => Token de l'Admin:
    eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImRhc2hib2FyZC10b2tlbi16NGs3ayIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJkYXNoYm9hcmQiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiI2ZTQ2NTQ2OS1mZmFlLTExZTgtOWYyOC01MjU0MDA5NTAxZmIiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6ZGVmYXVsdDpkYXNoYm9hcmQifQ.Nhl5hkwyXR-et1dnnN8szQ0_rF5nbrBEeRmLT0uvg5nyvBiSyUyuD96Pg7q-SDu8JN4G-WuiYitaBG_ifH0TrIqKt7X85xmcwQMviuirVMuS_S_2xuUHmMax1k90pBITZZ2B21H0z2aEmACrptj7_Kn8X3ncfViDRvXNe5WjLHeQzQvxlMB7_XZl86vGfcfytNdky_re4DiOmG3GotaS-71JoKtyQDidjj6cgXJfn_o0PETq5WlBrrvscVcjUrJF4wPh1s2Ye1qCkyaweajLqF9tnyv06f2w6u305B-eu7ZMLnOa2triNv5Fkpq_6-c_TD-ECz7fmuNJZwM_jBKP8Q
    
    /!\/!\/!\ TOKEN DE L'ADMIN A CONSERVER /!\/!\/!\
    ===>
    eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImRhc2hib2FyZC10b2tlbi16NGs3ayIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJkYXNoYm9hcmQiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiI2ZTQ2NTQ2OS1mZmFlLTExZTgtOWYyOC01MjU0MDA5NTAxZmIiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6ZGVmYXVsdDpkYXNoYm9hcmQifQ.Nhl5hkwyXR-et1dnnN8szQ0_rF5nbrBEeRmLT0uvg5nyvBiSyUyuD96Pg7q-SDu8JN4G-WuiYitaBG_ifH0TrIqKt7X85xmcwQMviuirVMuS_S_2xuUHmMax1k90pBITZZ2B21H0z2aEmACrptj7_Kn8X3ncfViDRvXNe5WjLHeQzQvxlMB7_XZl86vGfcfytNdky_re4DiOmG3GotaS-71JoKtyQDidjj6cgXJfn_o0PETq5WlBrrvscVcjUrJF4wPh1s2Ye1qCkyaweajLqF9tnyv06f2w6u305B-eu7ZMLnOa2triNv5Fkpq_6-c_TD-ECz7fmuNJZwM_jBKP8Q


VIII - installation de l'addon Heapster pour le monitoring du Cluster K8S depuis la machine CT-HAProxy:
-------------------------------------------------------------------------------------------------------
    $ nano heapster.yaml
    ##################################################
apiVersion: v1
kind: ServiceAccount
metadata:
  name: heapster
  namespace: kube-system
---
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: heapster
  namespace: kube-system
spec:
  replicas: 1
  template:
    metadata:
      labels:
        task: monitoring
        k8s-app: heapster
    spec:
      serviceAccountName: heapster
      containers:
      - name: heapster
        image: gcr.io/google_containers/heapster-amd64:v1.5.4
        imagePullPolicy: IfNotPresent
        command:
        - /heapster
        - --source=kubernetes.summary_api:''?useServiceAccount=true&kubeletHttps=true&kubeletPort=10250&insecure=true
---
apiVersion: v1
kind: Service
metadata:
  labels:
    task: monitoring
    # For use as a Cluster add-on (https://github.com/kubernetes/kubernetes/tree/master/cluster/addons)
    # If you are NOT using this as an addon, you should comment out this line.
    kubernetes.io/cluster-service: 'true'
    kubernetes.io/name: Heapster
  name: heapster
  namespace: kube-system
spec:
  ports:
  - port: 80
    targetPort: 8082
  selector:
    k8s-app: heapster
---
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  name: heapster
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: system:heapster
subjects:
- kind: ServiceAccount
  name: heapster
  namespace: kube-system
    ##################################################
    
    $ kubectl create -f heapster.yaml
    
    $ kubectl edit clusterrole system:heapster
    ##################################################
...
- apiGroups:
  - ""
  resources:
  - nodes/stats
  verbs:
  - get
    ##################################################
    

IX - Vérifications, lancement du Proxy et accès au Dashboard Kubernetes:
------------------------------------------------------------------------
1) - Cheking du Cluster K8S
    $ kubectl config view
    =>  apiVersion: v1
        clusters:
        - cluster:
            certificate-authority-data: DATA+OMITTED
            server: https://192.168.0.100:6443
        name: kubernetes
        contexts:
        - context:
            cluster: kubernetes
            user: kubernetes-admin
        name: kubernetes-admin@kubernetes
        current-context: kubernetes-admin@kubernetes
        kind: Config
        preferences: {}
        users:
        - name: kubernetes-admin
        user:
            client-certificate-data: REDACTED
            client-key-data: REDACTED

    $ kubectl get pods -n kube-system
    =>  NAME                                    READY   STATUS    RESTARTS   AGE
        coredns-86c58d9df4-52x5r                1/1     Running   0          92m
        coredns-86c58d9df4-7ztvp                1/1     Running   0          92m
        heapster-667876699f-f69pb               1/1     Running   0          9m24s
        kube-apiserver-k8s-master-1             1/1     Running   0          92m
        kube-apiserver-k8s-master-2             1/1     Running   0          82m
        kube-apiserver-k8s-master-3             1/1     Running   0          75m
        kube-controller-manager-k8s-master-1    1/1     Running   4          92m
        kube-controller-manager-k8s-master-2    1/1     Running   5          81m
        kube-controller-manager-k8s-master-3    1/1     Running   2          75m
        kube-proxy-57qxq                        1/1     Running   0          92m
        kube-proxy-7xszr                        1/1     Running   0          67m
        kube-proxy-d58wq                        1/1     Running   0          75m
        kube-proxy-h94ms                        1/1     Running   0          65m
        kube-proxy-kchvv                        1/1     Running   0          68m
        kube-proxy-nmjfg                        1/1     Running   0          82m
        kube-scheduler-k8s-master-1             1/1     Running   5          92m
        kube-scheduler-k8s-master-2             1/1     Running   4          82m
        kube-scheduler-k8s-master-3             1/1     Running   2          75m
        kubernetes-dashboard-79ff88449c-xpmc9   1/1     Running   0          39m
        weave-net-4vhwq                         2/2     Running   0          50m
        weave-net-g9whn                         2/2     Running   0          50m
        weave-net-gfpnv                         2/2     Running   0          50m
        weave-net-ls44t                         2/2     Running   0          50m
        weave-net-pnxf2                         2/2     Running   0          50m
        weave-net-r5ft8                         2/2     Running   0          50m
    
    $ kubectl get nodes
    =>  NAME           STATUS   ROLES    AGE   VERSION
        k8s-master-1   Ready    master   94m   v1.13.1
        k8s-master-2   Ready    master   83m   v1.13.1
        k8s-master-3   Ready    master   76m   v1.13.1
        k8s-worker-1   Ready    <none>   69m   v1.13.1
        k8s-worker-2   Ready    <none>   68m   v1.13.1
        k8s-worker-3   Ready    <none>   66m   v1.13.1
    
    $ kubectl cluster-info
    =>  Kubernetes master is running at https://192.168.0.100:6443
        Heapster is running at https://192.168.0.100:6443/api/v1/namespaces/kube-system/services/heapster/proxy
        KubeDNS is running at https://192.168.0.100:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
    
    $ kubectl proxy
    =>  Starting to serve on 127.0.0.1:8001
    
    ===> Depuis le navigateur (firefox) de CT-HAProxy:
    => http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
    
    => utiliser le Token de l'Admin
eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImRhc2hib2FyZC10b2tlbi16NGs3ayIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJkYXNoYm9hcmQiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiI2ZTQ2NTQ2OS1mZmFlLTExZTgtOWYyOC01MjU0MDA5NTAxZmIiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6ZGVmYXVsdDpkYXNoYm9hcmQifQ.Nhl5hkwyXR-et1dnnN8szQ0_rF5nbrBEeRmLT0uvg5nyvBiSyUyuD96Pg7q-SDu8JN4G-WuiYitaBG_ifH0TrIqKt7X85xmcwQMviuirVMuS_S_2xuUHmMax1k90pBITZZ2B21H0z2aEmACrptj7_Kn8X3ncfViDRvXNe5WjLHeQzQvxlMB7_XZl86vGfcfytNdky_re4DiOmG3GotaS-71JoKtyQDidjj6cgXJfn_o0PETq5WlBrrvscVcjUrJF4wPh1s2Ye1qCkyaweajLqF9tnyv06f2w6u305B-eu7ZMLnOa2triNv5Fkpq_6-c_TD-ECz7fmuNJZwM_jBKP8Q
    
    $ [ctrl] + [c] pour arrêter le proxy
        
        
X - Modification sur tout les Masters du NodePort Range des containers:
-----------------------------------------------------------------------
    
    ===> de préférence à faire à l'initialisation des Masters par le flag: --service-node-port-range=[port.de.début]-[port.de.fin]
    
1) modification du NodePort Range sur K8S-Master-1:
    $ ssh toor@192.168.0.101
    
    # nano /etc/kubernetes/manifests/kube-apiserver.yaml
    ##################################################
...
    - --service-cluster-ip-range=10.96.0.0/12
    - --service-node-port-range=1-32767
    - --tls-cert-file=/etc/kubernetes/pki/apiserver.crt
...
    ##################################################
    
    # reboot
    
2) modification du NodePort Range sur K8S-Master-2:
    $ ssh toor@192.168.0.102
    
    # nano /etc/kubernetes/manifests/kube-apiserver.yaml
    ##################################################
...
    - --service-cluster-ip-range=10.96.0.0/12
    - --service-node-port-range=1-32767
    - --tls-cert-file=/etc/kubernetes/pki/apiserver.crt
...
    ##################################################
    
    # reboot

3) modification du NodePort Range sur K8S-Master-3:
     $ ssh toor@192.168.0.103
    
    # nano /etc/kubernetes/manifests/kube-apiserver.yaml
    ##################################################
...
    - --service-cluster-ip-range=10.96.0.0/12
    - --service-node-port-range=1-32767
    - --tls-cert-file=/etc/kubernetes/pki/apiserver.crt
...
    ##################################################
    
    # reboot   
        
        
XI - Installation des Tools: MetalLB - Helm/Tiller - Cert-Manager (+certificat fictif) - Nginx-Ingress:
-------------------------------------------------------------------------------------------------------

1) Installation de MetalLB depuis CT-HAProxy:
    ===> permet d'exposer un service avec une IP extérieure au cluster et de faire du LoadBalancing entre containers
    
        $ nano metallb.yaml
    ##################################################
apiVersion: v1
kind: Namespace
metadata:
  name: metallb-system
  labels:
    app: metallb
---
apiVersion: v1
kind: ServiceAccount
metadata:
  namespace: metallb-system
  name: controller
  labels:
    app: metallb
---
apiVersion: v1
kind: ServiceAccount
metadata:
  namespace: metallb-system
  name: speaker
  labels:
    app: metallb
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: metallb-system:controller
  labels:
    app: metallb
rules:
- apiGroups: [""]
  resources: ["services"]
  verbs: ["get", "list", "watch", "update"]
- apiGroups: [""]
  resources: ["services/status"]
  verbs: ["update"]
- apiGroups: [""]
  resources: ["events"]
  verbs: ["create", "patch"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: metallb-system:speaker
  labels:
    app: metallb
rules:
- apiGroups: [""]
  resources: ["services", "endpoints", "nodes"]
  verbs: ["get", "list", "watch"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: metallb-system
  name: leader-election
  labels:
    app: metallb
rules:
- apiGroups: [""]
  resources: ["endpoints"]
  resourceNames: ["metallb-speaker"]
  verbs: ["get", "update"]
- apiGroups: [""]
  resources: ["endpoints"]
  verbs: ["create"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: metallb-system
  name: config-watcher
  labels:
    app: metallb
rules:
- apiGroups: [""]
  resources: ["configmaps"]
  verbs: ["get", "list", "watch"]
- apiGroups: [""]
  resources: ["events"]
  verbs: ["create"]
---
## Role bindings
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: metallb-system:controller
  labels:
    app: metallb
subjects:
- kind: ServiceAccount
  name: controller
  namespace: metallb-system
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: metallb-system:controller
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: metallb-system:speaker
  labels:
    app: metallb
subjects:
- kind: ServiceAccount
  name: speaker
  namespace: metallb-system
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: metallb-system:speaker
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  namespace: metallb-system
  name: config-watcher
  labels:
    app: metallb
subjects:
- kind: ServiceAccount
  name: controller
- kind: ServiceAccount
  name: speaker
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: Role
  name: config-watcher
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  namespace: metallb-system
  name: leader-election
  labels:
    app: metallb
subjects:
- kind: ServiceAccount
  name: speaker
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: Role
  name: leader-election
---
apiVersion: apps/v1beta2
kind: DaemonSet
metadata:
  namespace: metallb-system
  name: speaker
  labels:
    app: metallb
    component: speaker
spec:
  selector:
    matchLabels:
      app: metallb
      component: speaker
  template:
    metadata:
      labels:
        app: metallb
        component: speaker
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "7472"
    spec:
      serviceAccountName: speaker
      terminationGracePeriodSeconds: 0
      hostNetwork: true
      containers:
      - name: speaker
        image: metallb/speaker:v0.6.1
        imagePullPolicy: IfNotPresent
        args:
        - --port=7472
        - --config=config
        env:
        - name: METALLB_NODE_NAME
          valueFrom:
            fieldRef:
              fieldPath: spec.nodeName
        ports:
        - name: monitoring
          containerPort: 7472
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
            - all
            add:
            - net_raw
---
apiVersion: apps/v1beta2
kind: Deployment
metadata:
  namespace: metallb-system
  name: controller
  labels:
    app: metallb
    component: controller
spec:
  revisionHistoryLimit: 3
  selector:
    matchLabels:
      app: metallb
      component: controller
  template:
    metadata:
      labels:
        app: metallb
        component: controller
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "7472"
    spec:
      serviceAccountName: controller
      terminationGracePeriodSeconds: 0
      securityContext:
        runAsNonRoot: true
        runAsUser: 65534 # nobody
      containers:
      - name: controller
        image: metallb/controller:v0.6.1
        imagePullPolicy: IfNotPresent
        args:
        - --port=7472
        - --config=config
        ports:
        - name: monitoring
          containerPort: 7472
        resources:
          limits:
            cpu: 100m
            memory: 100Mi 

        securityContext:
          allowPrivilegeEscalation: false
          capabilities:
            drop:
            - all
          readOnlyRootFilesystem: true
    ##################################################
    
    $ kubectl apply -f metallb.yaml
    
    $ kubectl get pods -n metallb-system    #(/!\ attendre et renouveler jusqu'à ce que tout les pods soient "Running" /!\)
    =>  NAME                        READY   STATUS    RESTARTS   AGE                                                                                                                                                                                
        controller-cb44bd97-vxqdq   1/1     Running   0          49s                                                                                                                                                                                
        speaker-7cjfz               1/1     Running   0          49s                                                                                                                                                                                
        speaker-lt6n5               1/1     Running   0          49s
    
    $ nano metallb-configmap.yaml
    ##################################################
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: metallb-system
  name: config
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - 192.168.0.150-192.168.0.200
    ##################################################
    
    $ kubectl apply -f metallb-configmap.yaml
    
    $ kubectl get pods -n metallb-system
    =>  NAME                        READY   STATUS    RESTARTS   AGE
        controller-cb44bd97-zjlgq   1/1     Running   0          2m7s
        speaker-8wkqx               1/1     Running   0          2m7s
        speaker-kv6gr               1/1     Running   0          2m7s
        speaker-sxj5v               1/1     Running   0          2m7s
    

2) Installation de Helm/Tiller depuis CT-HAProxy:
    ===> permet d'installer d'jouter des applis (containers/pods) au Cluster
    ===> /!\ pas certain que le namespace kube-system soit le plus judicieux, à tester dans un namespace dédié /!\
    
    # sudo adduser toor sudo
    
    # reboot
    
    $ curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
    
    $ chmod 700 get_helm.sh
    
    $ ./get_helm.sh
    
    $ kubectl create serviceaccount tiller --namespace kube-system
    
    $ nano tiller-clusterrolebinding.yaml
    ##################################################
apiVersion: v1
kind: ServiceAccount
metadata:
  name: tiller
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: tiller
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
  - kind: ServiceAccount
    name: tiller
    namespace: kube-system
    ##################################################
    
    $ kubectl apply -f tiller-clusterrolebinding.yaml
    
    $ helm init --service-account tiller
    =>  Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

        Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
        To prevent this, run `helm init` with the --tiller-tls-verify flag.
        For more information on securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation
        Happy Helming!
    
    $ kubectl get pods -n kube-system
    =>  ...
        tiller-deploy-c4fd4cd68-wdttd           1/1     Running   0          2m36s
        ...    
        
        
        /!\ WARNING /!\
3) installation de Cert-Manager depuis CT-HAProxy:
    $ helm install \
    --name cert-manager \
    --namespace kube-system \
    --set ingressShim.defaultIssuerName=letsencrypt-staging \
    --set ingressShim.defaultIssuerKind=ClusterIssuer \
     stable/cert-manager \
    --version v0.4.1
    =>  NAME:   cert-manager
        LAST DEPLOYED: Wed Dec 19 07:30:45 2018
        NAMESPACE: kube-system
        STATUS: DEPLOYED

        RESOURCES:
        ==> v1/ServiceAccount
        NAME          SECRETS  AGE
        cert-manager  1        8s

        ==> v1beta1/CustomResourceDefinition
        NAME                               AGE
        certificates.certmanager.k8s.io    7s
        clusterissuers.certmanager.k8s.io  7s
        issuers.certmanager.k8s.io         6s

        ==> v1beta1/ClusterRole
        NAME          AGE
        cert-manager  5s

        ==> v1beta1/ClusterRoleBinding
        NAME          AGE
        cert-manager  5s

        ==> v1beta1/Deployment
        NAME          DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
        cert-manager  1        1        1           0          4s

        ==> v1/Pod(related)
        NAME                           READY  STATUS             RESTARTS  AGE
        cert-manager-5b664566dc-pw7px  0/1    ContainerCreating  0         3s


        NOTES:
        cert-manager has been deployed successfully!

        In order to begin issuing certificates, you will need to set up a ClusterIssuer
        or Issuer resource (for example, by creating a 'letsencrypt-staging' issuer).

        More information on the different types of issuers and how to configure them
        can be found in our documentation:

        https://cert-manager.readthedocs.io/en/latest/reference/issuers.html

        For information on how to configure cert-manager to automatically provision
        Certificates for Ingress resources, take a look at the `ingress-shim`
        documentation:

        https://cert-manager.readthedocs.io/en/latest/reference/ingress-shim.html
        
        $ kubectl get pods -n kube-system
        =>  cert-manager-5b664566dc-pw7px           1/1     Running   0          11m
            ...

4) Création d'un certificat fictif depuis CT-HAProxy:
    $ nano letsencrypt-staging.yaml
    ##################################################
apiVersion: certmanager.k8s.io/v1alpha1
kind: ClusterIssuer
metadata:
  namespace: kube-system
  name: letsencrypt-staging
spec:
  acme:
    # The ACME server URL
    server: https://acme-staging-v02.api.letsencrypt.org/directory
    # Email address used for ACME registration
    email: <mail@domain.x>
    # Name of a secret used to store the ACME account private key
    privateKeySecretRef:
      name: letsencrypt-sec-staging
    # Enable HTTP01 validations
    http01: {}
    ##################################################
    
    $ kubectl create -f letsencrypt-staging.yaml
    
    --- /!\ note pour prod /!\
    Let's Encrypt production service imposes strict limits.
    I suggest that you use their staging service to test things out.
    Once you are ready, create a new ClusterIssuer that points to production:
    https://acme-v02.api.letsencrypt.org/directory
    --- /!\ note pour prod /!\
        
5) Installation d'Nginx-Ingress depuis CT-HAProxy:
    ===> Serveur Web, Reverse Proxy, LoadBalancing, exposition sur IP externe au Cluster des ports 80 & 443
    ===> /!\ pas certain que le namespace kube-system soit le plus judicieux, à tester dans un namespace dédié /!\
    
    /!\ helm custom ! /!\
    
    $ helm install stable/nginx-ingress \
    --name uck-nginx \
    --set rbac.create=true \
?    --set controller.publishService.enabled=true \
??    --set controller.service.enableHttps=true \
    --namespace kube-system
    =>  NAME:   uck-nginx
        LAST DEPLOYED: Wed Dec 19 07:44:18 2018
        NAMESPACE: kube-system
        STATUS: DEPLOYED

        RESOURCES:
        ==> v1beta1/ClusterRole
        NAME                     AGE
        uck-nginx-nginx-ingress  8s

        ==> v1beta1/ClusterRoleBinding
        NAME                     AGE
        uck-nginx-nginx-ingress  8s

        ==> v1beta1/Role
        NAME                     AGE
        uck-nginx-nginx-ingress  8s

        ==> v1/Service
        NAME                                     TYPE          CLUSTER-IP      EXTERNAL-IP  PORT(S)                   AGE
        uck-nginx-nginx-ingress-controller       LoadBalancer  10.110.165.69   <pending>    80:3438/TCP,443:4454/TCP  7s
        uck-nginx-nginx-ingress-default-backend  ClusterIP     10.100.194.240  <none>       80/TCP                    5s

        ==> v1/ConfigMap
        NAME                                DATA  AGE
        uck-nginx-nginx-ingress-controller  1     9s

        ==> v1/ServiceAccount
        NAME                     SECRETS  AGE
        uck-nginx-nginx-ingress  1        8s

        ==> v1/Pod(related)
        NAME                                                      READY  STATUS             RESTARTS  AGE
        uck-nginx-nginx-ingress-controller-fc466bb65-9sphl        0/1    ContainerCreating  0         3s
        uck-nginx-nginx-ingress-default-backend-6b6b89b45d-7khqd  0/1    ContainerCreating  0         3s

        ==> v1beta1/RoleBinding
        NAME                     AGE
        uck-nginx-nginx-ingress  8s

        ==> v1beta1/Deployment
        NAME                                     DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
        uck-nginx-nginx-ingress-controller       1        1        1           0          5s
        uck-nginx-nginx-ingress-default-backend  1        1        1           0          5s


        NOTES:
        The nginx-ingress controller has been installed.
        It may take a few minutes for the LoadBalancer IP to be available.
        You can watch the status by running 'kubectl --namespace kube-system get services -o wide -w uck-nginx-nginx-ingress-controller'

        An example Ingress that makes use of the controller:

        apiVersion: extensions/v1beta1
        kind: Ingress
        metadata:
            annotations:
            kubernetes.io/ingress.class: nginx
            name: example
            namespace: foo
        spec:
            rules:
            - host: www.example.com
                http:
                paths:
                    - backend:
                        serviceName: exampleService
                        servicePort: 80
                    path: /
            # This section is only required if TLS is to be enabled for the Ingress
            tls:
                - hosts:
                    - www.example.com
                secretName: example-tls

        If TLS is enabled for the Ingress, a Secret containing the certificate and key must also be provided:

        apiVersion: v1
        kind: Secret
        metadata:
            name: example-tls
            namespace: foo
        data:
            tls.crt: <base64 encoded cert>
            tls.key: <base64 encoded key>
        type: kubernetes.io/tls
        
    $ kubectl get pods -n kube-system
    => check
    
    $ kubectl get services -n kube-system
    => check

