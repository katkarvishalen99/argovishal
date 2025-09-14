# How to install ArgoCD.

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

How to get argocd password:

kubectl get secrets -n argocd

ubuntu@ip-172-31-3-93:~/argocd$ kubectl get secrets -n argocd 
NAME                          TYPE     DATA   AGE
argocd-initial-admin-secret   Opaque   1      153m
argocd-notifications-secret   Opaque   0      154m
argocd-redis                  Opaque   1      154m
argocd-secret                 Opaque   5      154m

ubuntu@ip-172-31-3-93:~/argocd$ kubectl get secrets -n argocd argocd-initial-admin-secret -o yaml | grep -i password
  password: V003VXhSRWxmMXYzalBXMg==

ubuntu@ip-172-31-3-93:~/argocd$ echo "V003VXhSRWxmMXYzalBXMg==" | base64 -d
WM7UxRElf1v3jPW2

use username as : admin for login

<img width="1577" height="562" alt="image" src="https://github.com/user-attachments/assets/a956bba4-fafc-4d80-97e1-9b47102d8db0" />
<img width="975" height="486" alt="image" src="https://github.com/user-attachments/assets/0e92faf2-a462-4380-846e-f181ec831f24" />
<img width="975" height="407" alt="image" src="https://github.com/user-attachments/assets/08a18f97-905d-4de9-8533-00ea71f150c0" />
<img width="974" height="831" alt="image" src="https://github.com/user-attachments/assets/91fdb349-02bd-4d34-943c-fbfb6410362b" />
<img width="775" height="828" alt="image" src="https://github.com/user-attachments/assets/b5eb53ee-997f-468f-8aad-f56e885bbb29" />
<img width="975" height="301" alt="image" src="https://github.com/user-attachments/assets/5e5c95ac-2983-49a8-be1f-29e14c21b06d" />
<img width="975" height="345" alt="image" src="https://github.com/user-attachments/assets/09df6dfd-50ec-456b-8b51-5e03fee9c32c" />
<img width="975" height="86" alt="image" src="https://github.com/user-attachments/assets/c29f7d5d-a56b-442e-ad46-f05974ac7b75" />
<img width="975" height="220" alt="image" src="https://github.com/user-attachments/assets/9426c4f2-f545-447a-ab7a-f8fd56a7c257" />
<img width="975" height="452" alt="image" src="https://github.com/user-attachments/assets/ebd04cc7-ff5c-4702-b7fa-9308e891bef3" />



# Deploy Nginx with Argocd:

[argocd install.docx](https://github.com/user-attachments/files/22319936/argocd.install.docx)

# Deploy postgresdb with ArgoCD


[Deploy postgresdb with ArgoCD.docx](https://github.com/user-attachments/files/22319984/Deploy.postgresdb.with.ArgoCD.docx)








