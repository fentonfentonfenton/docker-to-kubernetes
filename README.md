kubectl apply -f deployment.yml

kubectl expose deployment nginx-deployment --port=8080 --target-port-80 --node-port-30000 --type=NodePort --name=nginx-service --dry-run=client -o yaml 
kubectl apply -f service.yml
kubectl get service nginx-service -w
kubectl describe deployment nginx-deployment

kubectl exec -it deployment/nginx-deployment bash

kubectl scale deployment nginx-deployment --replicas 3# docker-to-kubernetes
