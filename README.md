# Kubernetes basic commands for monitoring and troubleshooting
### Get commands with basic output

| Command | Description |
| --- | --- |
| `kubectl get pods` | List all pods in the namespace |
| `kubectl get pods -n <namespace name>` | List all pods in specific namespace |
| `kubectl get pods --all-namespaces` | List all pods in all namespaces |
| `kubectl get pods -o wide` | List all pods in the current namespace in wide format , with more details |
| `kubectl get pods -o wide --all-namespaces` | List all pods in all namespaces in wide format , with more details |
| `kubectl get pod <pod name> -o yaml` , `kubectl get pods <pod name> -o json` | List all resources in json or yaml format  |
| `kubectl get pods --sort-by='.status.containerStatuses[0].restartCount'` | List pods Sorted by Restart Count |
| `kubectl get pods --show-labels` | Show labels for all pods (or any other Kubernetes object that supports labelling) |
| `kubectl get services` | List all services in the namespace |
| `kubectl get services --sort-by=.metadata.name` | List Services Sorted by Name |
| `kubectl get deployment` | List all deployments in the namespace |
| `kubectl get node` | List all nodes |
| `kubectl get namespaces` | List all namespaces |
| `kubectl get events --sort-by=.metadata.creationTimestamp` | List Events sorted by timestamp |

### Describe commands with verbose output

| Command | Description |
| --- | --- |
| `kubectl describe nodes <node name>` | Describe node details  |
| `kubectl describe pods <pod name>` | Describe pod details  |
| `kubectl describe deployment <deployment name>` | Describe deployment details  |

### Log commands with basic output
| Command | Description |
| --- | --- |
| `kubectl logs <pod name>` | dump pod logs (stdout) |
| `kubectl logs -l name=myLabel` | dump pod logs, with label name=myLabel (stdout) |
| `kubectl logs -f <pod name>` | stream pod logs (stdout) |
| `kubectl logs deploy/<deployment name>` | dump Pod logs for a Deployment (single-container case) |
| `kubectl logs deploy/my-deployment -c my-container` | dump Pod logs for a Deployment (multi-container case) |

### Interacting with pod (pod must running status)
| Command | Description |
| --- | --- |
| `kubectl exec <pod name> -- ls` | Running individual commands in a pod |
| `kubectl exec -it <pod name> -- sh` | run a shell to connected to your pod |
| `kubectl exec deploy/<deployment name> -- ls` | run command in first Pod and first container in Deployment (single- or multi-container cases) |

### Example other kubernetes command 
| Command | Description |
| --- | --- |
| `kubectl apply -f ./my-manifest.yaml` | create resource(s) |
| `kubectl apply -f ./my1.yaml -f ./my2.yaml` | create from multiple files |
| `kubectl apply -f ./dir` | create resource(s) in all manifest files in dir |
| `kubectl rollout restart deployment/frontend` | Rolling restart of the "frontend" deployment |
| `kubectl label pods my-pod new-label=awesome` | Add a Label |
| `kubectl scale --replicas=3 rs/foo` | Scale a replicaset named 'foo' to 3 |
| `kubectl autoscale deployment foo --min=2 --max=10` | Auto scale a deployment "foo" |
| `kubectl edit svc/docker-registry` | Edit the service named docker-registry |

### Understanding Pod status
| Status | Meaning |
| --- | --- |
| `Init:N/M` | The Pod has **M** Init Containers, and **N** have completed so far. |
| `Init:Error` | An Init Container has failed to execute. |
| `Init:CrashLoopBackOff` | An Init Container has failed repeatedly. |
| `Pending` | The Pod has not yet begun executing Init Containers. |
| `PodInitializing or Running` | The Pod has already finished executing Init Containers. |

----
Reference : https://kubernetes.io/docs/reference/kubectl/cheatsheet/

Reference : https://kubernetes.io/docs/tasks/debug/_print/
