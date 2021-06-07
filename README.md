Ansible playbook that is used to setup a kubernetes cluster.

This will just init the cluster and it will copy the join commands for workers and for masters.
This role will also setup a CNI according to `setup_cni`.

Can be used to generate join commands when there is already a cluster running.

# Important
`michaelpalacce.kubernetes_preflight` Or something that sets up all the dependencies must be used
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


~~~
service_cidr
~~~
The Service CIDR to be provided to the kubeadm init command.
Defaults to: `10.96.0.0/12`


~~~
setup_cni
~~~
A flag whether this role should setup a CNI according to the given variables.
Defaults to: `yes`


~~~
cni_setup_command
~~~
The CNI setup command. Usually most CNIs have some manifest you can apply directly.
Defaults to: `kubectl apply -f https://docs.projectcalico.org/manifests/tigera-operator.yaml && kubectl apply -f https://docs.projectcalico.org/manifests/custom-resources.yaml`


~~~
cni_controller_name
~~~
The CNI controller name that will be used to verify the CNI is up and running
Defaults to: `calico-kube-controllers`



~~~
generate_join_commands
~~~
A flag whether to generate join commands for the workers.
If multi_master is set, then master join commands will be generated as well.
Defaults to: `yes`



~~~
output_dir
~~~
An absolute or relative path where the join commands and the config will be fetched.
Defaults to: `./output`