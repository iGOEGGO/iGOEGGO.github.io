# Deployment

Für das Deployment unserer Anwendung wird grundsätzlich `docker` verwendet und damit natürlich auch benötigt. 
Für weitere Informationen zur Installation von `docker` folgen Sie bitte diesem Link: [link](https://docs.docker.com/engine/install/)



## lokales Deployment 

Das lokale Deployment der Anwendung funktioniert mithilfe des Skripts `deploylocal.sh`

Dieses wird folgendermaßen ausgeführt: 

```shell
git clone https://github.com/iGOEGGO/diplomprojekt
cd diplomprojekt
cd depyloment
sh deploylocal.sh
```



## Deployment auf Heroku

Für das Deployment auf [Heroku](https://heroku.com/) kann das Skript `deploy.sh` verwendet werden: 

```shell
git clone https://github.com/iGOEGGO/diplomprojekt
cd diplomprojekt
cd depyloment
sh deploy.sh
```

