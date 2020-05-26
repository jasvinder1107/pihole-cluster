# pihole on kubernetes

The pihole.yaml manifest used for deploying pihole DNS on your kubernetes cluster as application. The manifest has a dependency on ingress-controllers for pihole dashboard. The dns is avaiable on nodePort: 31553

```
root@bladerunner:~# kubectl get all  -n pihole-dns
NAME               READY   STATUS    RESTARTS   AGE
pod/pihole-8gbjq   1/1     Running   0          14m

NAME                               TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                     AGE
service/pihole-service-dashboard   ClusterIP   10.97.236.24     <none>        80/TCP                      14m
service/pihole-service-dns         NodePort    10.100.216.108   <none>        53:31553/TCP,53:31553/UDP   14m

NAME                    DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
daemonset.apps/pihole   1         1         1       1            1           <none>          14m
root@bladerunner:~#
```
The yamls are tested in below kubernetes version:

```
root@bladerunner:~# kubectl version
Client Version: version.Info{Major:"1", Minor:"17", GitVersion:"v1.17.2", GitCommit:"59603c6e503c87169aea6106f57b9f242f64df89", GitTreeState:"clean", BuildDate:"2020-01-18T23:30:10Z", GoVersion:"go1.13.5", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"17", GitVersion:"v1.17.2", GitCommit:"59603c6e503c87169aea6106f57b9f242f64df89", GitTreeState:"clean", BuildDate:"2020-01-18T23:22:30Z", GoVersion:"go1.13.5", Compiler:"gc", Platform:"linux/amd64"}
root@bladerunner:~#
```
As of now the deamonset is using defaul service account.
