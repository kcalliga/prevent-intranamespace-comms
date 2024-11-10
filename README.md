This Github repo is meant to show how to block communications between pods in the same namespace.  Here is how it work

If your namespace/project already exists:

1.  Inside of your namespace, create net-tool deployment and the httpd deployment.  These are the http-pod.yaml and network-tool-pod.yaml

oc apply -f http-pod.yaml

oc apply -f network-tool-pod.yaml

2.  Create the two network policies inside of this namespace/project



