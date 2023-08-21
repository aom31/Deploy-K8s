Docker Registry is image repository on Docker HUB , 
We can push/pull image via network 
And this one path on distribution pipeline to make CI

- basic concept : Deployment, Service, Ingress
- create config file with kubectl
- mount Volume , like hostPath
- edit hosts to use instead DNS
- push/pull image from registry



#Command

kubectl create ns my-registry
kubectl create deploy my-registry --image=registry:2 --port=5000 --dry-run=client -o yaml -n my-registry 
kubectl create service clusterip my-registry --tcp=5000 --dry-run=client -o yaml -n my-registry  
kubectl create ingress my-registry --rule="registry.home.lan/*=my-registry:5000" --dry-run=client -o yaml -n my-registry
kubectl apply -f my-registry.yaml
sudo nano /etc/docker/daemon.json
sudo service docker restart
docker compose up -d
docker pull nginx
docker tag nginx registry.home.lan/nginx
docker push registry.home.lan/nginx
docker pull registry.home.lan/nginx