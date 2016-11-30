# skydive-sdn-openshift
A mini tutorial to use Openstack Skydive project to visualize the Openshift SDN
Simply based on kube template http://skydive-project.github.io/skydive/getting-started/kubernetes/



## Create Project 
oc new-project network

## Give Rights to access sdn sockets (catch all, should fine tune)
oadm policy add-scc-to-user  privileged system:serviceaccount:$(oc project -q):default

## Daemon Set to deploy collector
oc label nodes --all sky-dive-collector=true

## Deploy Objects 
oc create -f https://raw.githubusercontent.com/ivanthelad/skydive-sdn-openshift/master/skydive-oscp.yaml


Browse to the Route endpoint and the visualizer should be available 
