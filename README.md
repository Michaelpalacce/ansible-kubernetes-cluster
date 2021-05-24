Ansible playbook that is used to setup a kubernetes cluster.

# Dependencies

`michaelpalacce.kubernetes_preflight` Used to get all the binaries before setting the cluster up

# Important
This roles does NOT install a CRI. You must install one beforehand. Consider adding `michaelpalacce.docker` role to install docker as a cri.

# Supported variables

~~~
multi_master
~~~
Setup a multiple stacked masters cluster or just a single master cluster.
Defaults to: `no`.

~~~
load_balancer
~~~
In the case of a multi_master setup we need to provide a loadbalancer that points to the initial master.
Defaults to: ``


~~~
pod_cidr
~~~
The POD CIDR to be provided to the kubeadm init command. Check out your CNI for more information on what to pass here. For example Calico 
by default uses 192.168.0.0/16
Defaults to: `192.168.0.0/16`

