To do this through Openshift Service Mesh

1.  Install the Service Mesh (version 2), Kiali, and Tempo operators

2.  Create the cluster-wide service mesh control plane (SMCP) in the istio-system namespace

3.  Add tenanta and tenantb namespaces to SMMR (service mesh member roll)

4.  Apply these two policies and do curl from network-tools pod in tenanta to httpd pod in tenantb or vice-versa
