docker ps

minikube start --driver=docker

kubectl get ns

kubectl get nodes

kubectl create namespace argocd

kubectl apply \
    --namespace argocd \
    --filename https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

watch kubectl get all --namespace argocd

kubectl port-forward \
    --namespace argocd \
    svc/argocd-server 8000:443
Forwarding from 127.0.0.1:8000 -> 8080
Forwarding from [::1]:8000 -> 8080

kubectl get secret argocd-initial-admin-secret \
    --namespace argocd \
    --output jsonpath="{.data.password}" \
    | base64 --decode \
    && echo

ssh-keygen -t ed25519 -f ~/.ssh/argocd-test.pem

 ls -l ~/.ssh

mv ~/.ssh/argocd-test.pem.pub ~/.ssh/argocd-test.pub

cat ~/.ssh/argocd-test.pub

cat ~/.ssh/argocd-test.pem

git clone https://github.com/quanghoangson/argocd-test.git
cd argocd-test/
ls -l 
kubectl apply --filename argocd-app.yaml

kubectl port-forward \
    --namespace my-app \
    svc/my-app-svc 5000:5000
