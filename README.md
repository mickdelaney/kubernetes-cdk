to run juju deploy manually for kubernetes-core or a bundle. 
you need to 
1: create a juju model, name it k8s 
    juju add-model k8s
2: update the lxd profile for this k8s model
    cat lxc-profile-kubernetes.yaml  | lxc profile edit juju-k8s

https://github.com/lxc/lxd/blob/master/doc/profiles.md


juju scp kubernetes-master/0:config ~/.kube/config


watch -c juju status --color

juju debug-log
juju run-action kubernetes-master/0 restart
juju show-status-log kubernetes-master/0


 juju show-action-output