## Remote Docker CLI
```
eval "$(ssh-agent -s)"   //Start agent in current shell session
ssh-add /path/to/key     //Add the key
ssh-add -l
DOCKER_HOST=ssh://<user Name>@<public IP>   //Connect Docker CLI

```
```
sudo apt install kubectx  //shortcut commands for Kubernetes namespaces
kubens   //List down Namespaces
kubens <namespace> //Change the current namespace
```
```
alias k="kubectl"
alias d="docker"
alias t="tree -L 1"
alias c="clear"
```
