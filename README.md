# pihole on kubernetes

The pihole.yaml manifest used for deploying pihole DNS on your kubernetes cluster as application. The manifest has a dependency on ingress-controllers for pihole dashboard. Started using DNS on loadbalancer service using metallb

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

