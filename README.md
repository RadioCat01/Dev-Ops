## Remote Docker CLI
```
eval "$(ssh-agent -s)"   //Start agent in current shell session
ssh-add /path/to/key     //Add the key
ssh-add -l
DOCKER_HOST=ssh://<user Name>@<public IP>   //Connect Docker CLI
```
## Docker Multi-arch Build
```
docker buildx build \
  --platform linux/amd64,linux/arm64 \
  -t myapp:latest .
```
## Kubernetes Shortcuts
```
sudo apt install kubectx  //shortcut commands for Kubernetes namespaces
kubens   //List down Namespaces
kubens <namespace> //Change the current namespace

https://learnkube.com/troubleshooting-deployments

```
```
alias k="kubectl"
alias d="docker"
alias t="tree -L 1"
alias c="clear"
```
```
temp load balancer for kind
go install sigs.k8s.io/cloud-provider-kind@latest
sudo install ~/go/bin/cloud-provider-kind /usr/local/bin
cloud-provider-kind
```
## Helm Commands
update helm chart and roll back
```
helm upgrade --install postgresql bitnami/postgresql \
--version=<v> \
--create-namespace \
-- values=<yml file>

helm rollback postgresql  //name
```

## Linux Networking and Firewall
```
ss -nltp //list network sockets  
nohup java -jar <app.jar> > app.log>&1 & //Run Jar on bg logs written in to app.log file
```
### Firewall Port Configuration (Manual for Oracle VM )
```
sudo apt install firewalld
sudo firewall-cmd --zone=public --permanent --add-port=<portNumber>/tcp 
sudo firewall-cmd --reload 
```

http://140.245.228.222:8080/
