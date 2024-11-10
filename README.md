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

In this example, my http pod is on the 10.129.1.149 IP.

4.  RSH into the network-tools-pod

[keith@vpn-hopper all-in-one]$ oc rsh network-tools-769ff557b7-2c4ll

sh-5.1$ curl http://10.129.1.149:8080

The lack of response shows that it is timing out so there are no comms inside the same namespace/project.

If you want to apply these same network policies on all new projects:

1.  oc apply -f bootstrap-project-template.yaml
2.  oc apply -f project-config.yaml
3.  Now create a new project/namespace and follow the steps from the first section again.



