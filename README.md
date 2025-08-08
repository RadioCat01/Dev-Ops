```
eval "$(ssh-agent -s)"   //Start agent in current shell session
ssh-add /path/to/key     //Add the key
ssh-add -l
DOCKER_HOST=ssh://<user Name>@<public IP>   //Connect Docker CLI
```
