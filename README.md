# Network Policy Demo

This GitHub repository demonstrates how to block communication between pods in the same namespace using Network Policies.

## How it Works

This demo sets up two pods, an `httpd` pod and a `network-tools` pod, and then applies Network Policies to restrict communication between them.

### Applying to an Existing Namespace/Project

1. **Deploy the pods:**
   - Apply the `httpd` deployment: `oc apply -f http-pod.yaml`
   - Apply the `network-tools` deployment: `oc apply -f network-tool-pod.yaml`

2. **Apply the Network Policies:**
   - Apply the `allow-from-api` policy: `oc apply -f allow-from-api-network-policy.yaml`
   - Apply the `allow-from-ingress` policy: `oc apply -f allow-from-ingress-network-policy.yaml`

3. **Get the IP address of the `httpd` pod:**
   - Use `oc get po -o wide` to find the IP address of the `httpd` pod.

4. **Test communication:**
   - `oc rsh` into the `network-tools` pod.
   - Use `curl` to access the `httpd` pod's IP address: `curl http://<httpd-pod-ip>:8080`
   - The request should timeout, indicating that communication is blocked.

### Applying to All New Projects

1. **Apply the bootstrap template:** `oc apply -f bootstrap-project-template.yaml`
2. **Apply the project configuration:** `oc apply -f project-config.yaml`
3. **Create a new project/namespace** and follow the steps above to deploy the pods and Network Policies.

## Files

- `http-pod.yaml`: Deployment configuration for the `httpd` pod.
- `network-tool-pod.yaml`: Deployment configuration for the `network-tools` pod.
- `allow-from-api-network-policy.yaml`: Network Policy to allow traffic from the `api` namespace.
- `allow-from-ingress-network-policy.yaml`: Network Policy to allow traffic from the ingress controller.
- `bootstrap-project-template.yaml`: Template for bootstrapping new projects with Network Policies.
- `project-config.yaml`: Configuration for applying Network Policies to new projects.

## Notes

- This demo assumes you have an OpenShift cluster up and running.
- You may need to adjust the Network Policy configurations to match your specific environment.
- This is a basic example and can be extended to demonstrate more complex Network Policy scenarios.
