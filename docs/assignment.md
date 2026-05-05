---
title: Kubernetes Command-Line Interface (kubectl)
author: Craig Vaccaro
date: 2026-05-05
tags: [Kubernetes, kubectl, troubleshooting, debugging, beginner]
---
![Spectro Cloud logo with docs inline](logo_landscape_for_white.png)
# Kubernetes Command-Line Interface (kubectl)
`kubectl` is the Command-Line Interface (CLI) that communicates with the Kubernetes Application Programming Interface  server to perform actions. You can use `kubectl` to deploy, manage, and troubleshoot Kubernetes resources. For more information about installing and configuring `kubectl`, see [Install Tools](https://kubernetes.io/docs/tasks/tools/#kubectl) in the official Kubernetes documentation.
## kubectl Debugging Commands
Use the following `kubectl` commands to diagnose problems with your containers, pods, and other Kubernetes resources. This section provides basic syntax and output examples for common debugging use cases. For more information about `kubectl` commands, including full syntax and capabilities, see [kubectl reference](https://kubernetes.io/docs/reference/kubectl/generated/) in the official Kubernetes documentation.
### `kubectl get pods`
Lists the status of all pods in a specified namespace. 
#### Syntax
```bat
kubectl get pods --namespace <existingnamespace>
```
#### Use Cases
- Verify the status of your deployed pods. Any state other than **Running** might indicate a problem with the pod. For more information about pod status, see [Pod Lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/) in the official Kubernetes documentation.
- Check the age and number of restarts to determine if a persistent problem is causing the pod to restart frequently.
#### Sample Output
```bat
C:\WINDOWS\system32>kubectl get pods --namespace default
NAME                              READY   STATUS             RESTARTS      AGE
hello-minikube-58f7c595dd-6stjw   1/1     Running            1 (15m ago)   23h
node-debugger-minikube-8sdsp      0/1     ImagePullBackOff   0             23h
node-debugger-minikube-nzghh      0/1     Error              0             23h
```
### `kubectl logs`
Retrieves troubleshooting logs for a specified pod.
#### Syntax
```bat
kubectl logs <existingpodname> -n <existingnamespace>
```
#### Use Cases
- Review the logs for any pod that reports status problems and try to determine the cause.
- Configure Kubernetes to generate different log types and formats to help diagnose different problems. For more information about logging in Kubernetes, see [A Practical Guide to Kubernetes Logging](https://www.cncf.io/blog/2020/10/05/a-practical-guide-to-kubernetes-logging/) on the official Cloud Native Computing Foundation blog.
#### Sample Output
```bat
C:\WINDOWS\system32>kubectl logs kube-apiserver-minikube -n kube-system
I0504 20:45:59.306792       1 options.go:263] external host was not specified, using 192.168.49.2
I0504 20:45:59.309385       1 server.go:150] Version: v1.35.1
I0504 20:45:59.309426       1 server.go:152] "Golang settings" GOGC="" GOMAXPROCS="" GOTRACEBACK=""
I0504 20:45:59.384326       1 shared_informer.go:349] "Waiting for caches to sync" controller="node_authorizer"
W0504 20:45:59.384913       1 logging.go:55] [core] [Channel #2 SubChannel #4]grpc: addrConn.createTransport failed to connect to {Addr: "127.0.0.1:2379", ServerName: "127.0.0.1:2379", BalancerAttributes: {"<%!p(pickfirstleaf.managedByPickfirstKeyType={})>": "<%!p(bool=true)>" }}. Err: connection error: desc = "transport: authentication handshake failed: context canceled"
W0504 20:45:59.384920       1 logging.go:55] [core] [Channel #1 SubChannel #3]grpc: addrConn.createTransport failed to connect to {Addr: "127.0.0.1:2379", ServerName: "127.0.0.1:2379", BalancerAttributes: {"<%!p(pickfirstleaf.managedByPickfirstKeyType={})>": "<%!p(bool=true)>" }}. Err: connection error: desc = "transport: authentication handshake failed: context canceled"
I0504 20:45:59.388522       1 shared_informer.go:370] "Waiting for caches to sync"
```
### `kubectl debug`
Performs various debugging tasks on specified resources.
#### Syntax
```bat
kubectl debug node/<existingnodename> -it --image=<existingimagename>
```
```bat
kubectl debug <existingpodname> -it --image=<existingimagename> --copy-to=<newpodname>
```
#### Use Cases
- Add a container to an active pod with an image containing any diagnostic tools or utilities you might need.
- Create a persistent clone of an existing pod to test configuration changes.
- Add standard input streams and terminal functionality to interact with containers in a pod.
#### Sample Output
```bat
C:\WINDOWS\system32>kubectl debug node/minikube -it --image=busybox
Creating debugging pod node-debugger-minikube-z2mnn with container debugger on node minikube.
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
/ #
```
### `kubectl exec`
Directly issue commands to services within a specified container.
#### Syntax
```bat
kubectl exec <existingnodename> -i -t -- ls -t /usr
```
```bat
kubectl exec <existingpodname> -c <existingcontainername> -i -t -- bash -il
```
#### Use Cases
- Browse the file system inside a container.
- Switch to raw terminal mode for a container.
- Get output from commands issued to services in a container.
#### Sample Output
```bat
C:\WINDOWS\system32>kubectl exec node-debugger-minikube-z2mnn -it -- ls -t /usr
bin   sbin
```
