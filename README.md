How to install ArgoCD.

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get netpol -n argocd

kubectl delete netpol -n argocd <POLICY-NAME>

kubectl get all -n argocd

kubectl edit svc -n argocd argocd-server   >> edit service with NodePort tyep and nodePort

argocd-server                             NodePort    172.20.97.22     <none>        80:30128/TCP,443:32311/TCP   11m

kubectl get pods -n argocd

ubuntu@ip-172-31-3-93:~/argocd$ kubectl get pod -n argocd  -o wide
NAME                                                READY   STATUS    RESTARTS   AGE     IP           NODE                                        NOMINATED NODE   READINESS GATES
argocd-application-controller-0                     1/1     Running   0          7m38s   10.0.2.247   ip-10-0-2-205.ap-south-1.compute.internal   <none>           <none>
argocd-applicationset-controller-54f96997f8-x96hf   1/1     Running   0          7m38s   10.0.1.100   ip-10-0-1-204.ap-south-1.compute.internal   <none>           <none>
argocd-dex-server-798cbff4c7-knwcp                  1/1     Running   0          7m38s   10.0.1.88    ip-10-0-1-204.ap-south-1.compute.internal   <none>           <none>
argocd-notifications-controller-644f66f7df-jb9qq    1/1     Running   0          7m38s   10.0.1.200   ip-10-0-1-204.ap-south-1.compute.internal   <none>           <none>
argocd-redis-6684c6947f-kvtqw                       1/1     Running   0          7m38s   10.0.2.56    ip-10-0-2-205.ap-south-1.compute.internal   <none>           <none>
argocd-repo-server-6fccc5759b-p8jgl                 1/1     Running   0          7m38s   10.0.2.138   ip-10-0-2-205.ap-south-1.compute.internal   <none>           <none>
argocd-server-64d5fcbd58-zb9fp                      1/1     Running   0          7m38s   10.0.1.35    ip-10-0-1-204.ap-south-1.compute.internal   <none>           <none>


ubuntu@ip-172-31-3-93:~/argocd$ kubectl get nodes -o wide
NAME                                        STATUS   ROLES    AGE    VERSION               INTERNAL-IP   EXTERNAL-IP     OS-IMAGE                       KERNEL-VERSION                    CONTAINER-RUNTIME
ip-10-0-1-204.ap-south-1.compute.internal   Ready    <none>   3h1m   v1.32.8-eks-99d6cc0   10.0.1.204    13.201.96.135   Amazon Linux 2023.8.20250818   6.1.147-172.266.amzn2023.x86_64   containerd://1.7.27
ip-10-0-2-205.ap-south-1.compute.internal   Ready    <none>   3h1m   v1.32.8-eks-99d6cc0   10.0.2.205    13.204.62.237   Amazon Linux 2023.8.20250818   6.1.147-172.266.amzn2023.x86_64   containerd://1.7.27

accesss argocd with argocd server pod node and nodeport
http://13.201.96.135:30128 or https://13.201.96.135:32311

<img width="1577" height="562" alt="image" src="https://github.com/user-attachments/assets/a956bba4-fafc-4d80-97e1-9b47102d8db0" />
