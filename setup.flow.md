

- `cd ./servcer`

- `kubectl create -f server-app-service.yaml`

- run `kubectl get service` to get the PORT

- `cd ../client`

- run `minikube ip` to get IP

- replace the `REACT_APP_baseAPIURL` in Dockerfile with `http://${IP}:{PORT}`

- build client image by running `docker image build -t todo-client-kubernetes-app . `

- docker image ls

- save local image that just builded  to the docker image by running `docker save todo-client-kubernetes-app | (eval $(minikube docker-env) && docker load)`

- `kubectl create -f client-app-deploy.yaml`

- `kubectl get deploy,rs,pod`

- `kubectl create -f client-app-service.yaml`

- `kubectl get service`

- `cd ../server`

- `kubectl create -f persistent-vol-server-app.yaml`

- `kubectl create -f persistent-vol-claim-server-app.yaml`

- `kubectl create -f mongodb-pod.yaml`

- `kubectl create -f mongodb-service.yaml`

-  `kubectl get pv,pvc,pod,svc`

- `docker image build -t todo-server-kubernetes-app .`

- `docker image ls`

- `docker save todo-server-kubernetes-app | (eval $(minikube docker-env) && docker load)`

- `kubectl create -f server-app-configs.yaml`

- `kubectl create secret generic server-side-secrets --from-literal=JWT_SECRET=thisIsMySecretKeyForJWT*@.[123`

- `kubectl create -f server-app-deploy.yaml`

- `kubectl scale deploy todo-client-app-deploy --replicas=<count> `

- `kubectl scale deploy todo-server-app-deploy --replicas=<count>`


Ref
===

- [React, Express, Node Js, and MongoDB (MERN Stack) microservices-based application deployment on Kubernetes](https://medium.com/@aamirpinger/react-express-node-js-and-mongodb-mern-stack-microservices-based-application-deployment-on-ec4607cec74d)
- [Setting Up Self-Signed HTTPS Access To Local Dev K8s Cluster in Minikube
](https://itnext.io/setting-up-self-signed-https-access-to-local-dev-k8s-cluster-in-minikube-539bc62ad62f)







