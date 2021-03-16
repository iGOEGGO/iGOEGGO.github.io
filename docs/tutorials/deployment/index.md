# R-Shiny Server mit Docker und ShinyProxy

Dieses Tutorial befasst sich mit dem Deployment des iGÖGGO. Welche Parameter man verändern kann und wie man die Applikation für mehrere Benutzer zur Verfügung stellt wird ebenfalls angeführt.

## Deployment 
Der iGÖGGO kann local aufgesetzt werden, oder auf der Testplattform Heroku [4].

### Lokales Deployment

Im Verzeichnis `diplomprojekt/deployment` können Sie einfach folgenden Befehl ausführen.

```shell
sh deploylocal.sh <port>
```
Mit dem Parameter `port` wird spezifiziert, auf welchem HTTP-Port der iGÖGGO gestartet wird. Zum Beispiel startet `sh deployment.sh 3838` den iGÖGGO auf `http://localhost:3838`.

Mit `curl` wird am Ende des Skriptes überprüft, ob alles funktioniert hat und der Container läuft.

```shell
curl -v --silent localhost:<port> --stderr - | grep '<header class="main-header">'
```

Nachdem das Skript gestartet wurde ist der iGÖGGO unter `localhost:<port>` erreichbar.

### Deployment mit ShinyProxy

Da ein einzelne Instanz des iGÖGGO nur von einer Benutzerin verwendet werden kann empfiehlt sich ein Skalieren der Anwendung mit einem Loadbalancer. Dieser stellt jeder Benutzerin einen Container zur Verfügung.

 ![](img/docker_shinyproxy_loadbalance.png)

Diese Funktionalität wird von ShinyProxy bereits zur Verfügung gestellt [7]. Wir stellen ein Skript zur Verfügung, welches ShinyProxy startet und dann über `http:localhost:8080` erreichbar ist.

```shell
sh deploylocalproxy.sh
```

Da eine Authentifizierung notwendig ist, weil ShinyProxy anhand des eingeloggten Benutzers skaliert, haben wir uns für eine simple Authentifizierung entschieden. Im `application.yml` kann unter dem Tag `users` eine Liste mit Benutzern angegeben werden. **Wichtig** ist, dass die Benutzer Teil der Gruppe `goeg_employee` sind, da sie sonst nicht auf den iGÖGGO zugreifen können. So könnten zwei Benutzer aussehen:

```yaml
users:
	- name: max
	  password: supersicher
	  groups: goeg_employe
	- name: miriam
	  password: sicherer
	  groups: goeg_employee
```

Natürlich ist dies nicht die sicherste Methode, Nutzerdaten zu speichern. ShinyProxy ermöglicht es, sich über einen LDAP-Server zu authentifizieren, eine genaue Beschreibung kann der offiziellen Website entnommen werden [8].

### Cloud-Deployment mit Heroku

Ein Deployment der Software über Heroku ist denkbar einfach. Wieder gibt es ein Skript, `deploy.sh`, welches Sie auffordert, sich bei Heroku anzumelden, und das iGÖGGO-Dockerfile auf Heroku lädt. Das Installieren können Sie über das Heroku-Log beobachten. Natürlich spielt sich das ganze wieder im Verzeichnis `diplomprojekt/deployment` ab.

```shell
sh deploy.sh
```

Das `deploy.sh`-Skript lädt automatisch auf die Applikation `igoeggo`. Hat man seine eigene Applikation, muss das Skript entsprechend angepasst werden. Folgende Zeilen sind zu bearbeiten.

```shell
heroku container:push web --app <app_name>
heroku container:release web --app <app_name>
until heroku logs --app <app_name> --source app | grep -q "shiny-server - Starting listener"; do
```

Sollte man noch keine Heroku-App haben, muss man sie mit `heroku create <app_name>` in der Kommandozeile erstellt werden.

## Quellen und hilfreiche Links

[1] *verwendetes docker-hub image* https://hub.docker.com/r/rocker/shiny (Accessed June 2nd 2020)

[2] *einfache shiny-applikation* https://shiny.rstudio.com/tutorial/written-tutorial/lesson1/ (Accessed June 2nd 2020)

[3] *docker-compose reference guide* https://docs.docker.com/compose/compose-file/ (Accessed June 2nd 2020)

[4] *heroku* https://heroku.com (Accessed January 13th 2021)

[5] *official Dockerfile reference* https://docs.docker.com/engine/reference/builder/ (Accessed January 13th 2021)

[6] *official docker-compose.yaml reference (v3)* https://docs.docker.com/compose/compose-file/compose-file-v3/ (Accessed January 13th 2021)

[7] *official website of ShinyProxy* https://shinyproxy.io/

[8] *configure LDAP with ShinyProxy* https://shinyproxy.io/documentation/configuration/#ldap