# Cheatsheet


## Intro    

Hi! 


😴 :sleeping:	😟 :worried:	😦 :frowning:
😧 :anguished:	😮 :open_mouth:	😬 :grimacing:
😕 :confused:	😯 :hushed:	😑 :expressionless:
😒 :unamused:	😅 :sweat_smile:	😓 :sweat:
😥 :disappointed_relieved:	😩 :weary:	😔 :pensive:
😞 :disappointed:	😖 :confounded:	😨 :fearful:
😰 :cold_sweat:	😣 :persevere:	😢 :cry:
😭 :sob:	😂 :joy:	😲 :astonished:
😱 :scream:	:neckbeard: :neckbeard:	😫 :tired_face:
😠 :angry:	😡 :rage:	😤 :triumph:
😪 :sleepy:	😋 :yum:	😷 :mask:
😎 :sunglasses:	😵 :dizzy_face:	👿 :imp:
😈 :smiling_imp:	😐 :neutral_face:	😶 :no_mouth:
😇 :innocent:	👽 :alien:	💛 :yellow_heart:
💙 :blue_heart:	💜 :purple_heart:	❤️ :heart:


This is a crappy little repo to illustrate running something in compose and k8s.

The `nginx` container runs a script to grab some news headlines on runtime, this will be at `localhost:8080` in `docker` and `localhost:30000` on `k8s` 

In `docker-compose` you only run one container, therefore only seeing a bit of news - but what if you want to show more news to more people, at random? Maybe deploy in `kubernetes` and scale up the instance count? Won't I need a service?

What if you want to force the news to update more? Will you need a sidecar?

What if you want to put in dynamic HTML rather than this stupid script?


### Docker

`docker-compose up`

`docker-compose exec nginx sh`

### k8s

```
kubectl apply -f deployment.yml

kubectl expose deployment nginx-deployment --port=8080 --target-port-80 --node-port-30000 --type=NodePort --name=nginx-service --dry-run=client -o yaml 
kubectl apply -f service.yml
kubectl get service nginx-service -w
kubectl describe deployment nginx-deployment

kubectl exec -it deployment/nginx-deployment bash

kubectl scale deployment nginx-deployment --replicas 3# docker-to-kubernetes


kubectl delete deployment nginx-deployment
kubectl delete service nginx-service
```
