To do this through Openshift Service Mesh

1.  Install the Service Mesh (version 2), Kiali, and Tempo operators

2.  Create the cluster-wide service mesh control plane (SMCP) in the istio-system namespace

3.  Add tenanta and tenantb namespaces to SMMR (service mesh member roll)

4.  Apply the two denyall policies to tenanta and tenantb.  These are targeting pods with the app: httpd label.  These should be blocked with an rbac error.

5.  Now apply the httpd-pod-sidecar-allowed pod to tenanta and tenantb namespace.  This has a different label and should be allowed.
