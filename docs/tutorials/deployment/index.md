# R-Shiny Server mit docker

Für das Deployment unserer Anwendung wird grundsätzlich `docker` verwendet und damit natürlich auch benötigt. 
Für weitere Informationen zur Installation von `docker` folgen Sie bitte diesem Link: [link](https://docs.docker.com/engine/install/)

## Deployment 
Der iGÖGGO kann local aufgesetzt werden, oder auf der Testplattform Heroku [4].

### Lokales Deployment

Im Verzeichnis `diplomprojekt/deployment` einfach folgenden Befehl ausführen.

```shell
sh deploylocal.sh
```
Nachdem das Skript gestartet wurde kann es ca eine Minute dauern, bis der iGÖGGO unter `localhost:3456` erreichbar ist. Das liegt daran, dass die benötigten R-Pakete installiert werden.

Mit `curl` wird (nachdem die Pakete installiert wurden) überrüft, ob alles funktioniert hat.
```shell
curl -v --silent localhost:3456 --stderr - | grep '<header class="main-header">'
```

**depracted**

Ein lokales Deployment der Software ist durch folgende Befehlsabfolge im Verzeichnis `diplomprojekt/deployment` möglich: 

```shell
cd deployment
docker-compose up -d
```

### Cloud-Deployment mit Heroku

Ein Deployment der Software über Heroku ist denkbar einfach. Wieder gibt es ein Skript, `deploy.sh` welches den Benutzer über Heroku anmelden lässt, und das iGÖGGO-Dockerfile auf heroku hochlädt. Das Installieren kann dann über das Heroku-Log beobachtet werden. Natürlich spielt sich das ganze wieder im Verzeichnis `diplomprojekt/deployment` ab.

```shell
sh deploy.sh
```

#### eigene Heroku App für den iGÖGGO
das `deploy.sh`-Skript lädt automatisch auf die App `igoeggo`. Hat man seine eigene App, muss das Skript entsprechend angepasst werden. Folgende Zeilen sind zu bearbeiten.

```shell
heroku container:push web --app <dein_app_name>
heroku container:release web --app <dein_app_name>
```

Sollte man noch keine Heroku-App haben, muss man sie mit `heroku create <dein_app_name>` erstellt werden.

**genaue Durchführung mithilfe unseres Repos**

```shell
cd deployment
heroku login -i
heroku container:login
heroku create <app_name>
heroku container:push web --app <app_name>
heroku container:release web --app <app_name>
```

### Änderungen am lokalen Deployment vornehmen
Gewisse Parameter können geändert werden, wenn das notwendig ist.

#### Port
Der Port, auf welchem `deploylocal.sh` die App startet ist **3456**. Jedoch ist es möglich, diesen zu Ändern. Dazu müssen folgende drei Zeilen im `deploylocal.sh` abgeändert werden. Angenommen man möchte auf den Port 8080 ändern:

```shell
sed -i -e 's|<PORT_EXPORT>|export PORT=3456|' start.sh
# wird zu
sed -i -e 's|<PORT_EXPORT>|export PORT=8080|' start.sh

docker run -d -p 3456:3456 testshiny
# wird zu
docker run -d -p 8080:8080 testshiny

sed -i -e 's|export PORT=3456|<PORT_EXPORT>|' start.sh
# wird zu
sed -i -e 's|export PORT=8080|<PORT_EXPORT>|' start.sh
```

#### Dockerimage Name
Möchte mann den Namen des docker-Images verändern müssen folgende zwei Zeilen im `deploylocal.sh` geändert werden:

```shell
docker build . -t <neuer_image_name>
docker run -d -p 3456:3456 <neuer_image_name>
```



## Quellen und hilfreiche Links

[1] *verwendetes docker-hub image* https://hub.docker.com/r/rocker/shiny (Accessed June 2nd 2020)

[2] *einfache shiny-applikation* https://shiny.rstudio.com/tutorial/written-tutorial/lesson1/ (Accessed June 2nd 2020)

[3] *docker-compose reference guide* https://docs.docker.com/compose/compose-file/ (Accessed June 2nd 2020)

[4] *heroku* https://heroku.com (Accessed January 13th 2021)

[5] *official Dockerfile reference* https://docs.docker.com/engine/reference/builder/ (Accessed January 13th 2021)

[6] *official docker-compose.yaml reference (v3)* https://docs.docker.com/compose/compose-file/compose-file-v3/ (Accessed January 13th 2021)
