This Github repo is meant to show how to block communications between pods in the same namespace.  Here is how it work

If your namespace/project already exists:

1.  Inside of your namespace, create net-tool deployment and the httpd deployment.  These are the http-pod.yaml and network-tool-pod.yaml

oc apply -f http-pod.yaml

oc apply -f network-tool-pod.yaml

2.  Create the two network policies inside of this namespace/project

oc apply -f allow-from-api-network-policy.yaml

oc apply -f allow-from-ingress-network-policy.yaml

3.  Get the IP address of the http pod

[keith@vpn-hopper all-in-one]$ oc get po -o wide

NAME                             READY   STATUS    RESTARTS   AGE   IP             NODE    NOMINATED NODE   READINESS GATES

httpd-7f98548fcf-msrr6           1/1     Running   0          11m   10.129.1.149   home2   <none>           <none>

network-tools-769ff557b7-2c4ll   1/1     Running   0          11m   10.129.1.150   home2   <none>           <none>

In this example

