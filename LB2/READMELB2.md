# Dockerfile
Das Dockerfile sagt am Docker, wie er ein Image mit einem PHP und WordPress Container erstellen soll.

Das Dockerfile kann man mit folgendenden Befehlen erstellen und editieren.
```touch Dockerfile```
```nano Dockerfile```

# docker-compose.yml
Das docker-compose.yml File sagt am Docker wie er die Wordpress und MariaDB Container starten soll.

Das docker-compose File kann man gleich wie das Dockerfile erstellen und editieren.
```touch docker-compose.yml```
```nano docker-compose.yml```

# Container starten
Container starten und sie im Hintergrund laufen lassen:
```docker-compose up -d```

Container starten und im Vordergrund laufen lassen:
```docker-compose up```

Es sollte dann folgende Meldung erscheinen:
```Creating wordpress-compose_mariadb_1 ... done```
```Creating wordpress-compose_wordpress_1 ... done```

# Weitere Docker Befehle
Alle gestoppten Container starten
```docker-compose start```

Alle laufende Container stoppen
```docker-compose stop```

Konfigurationen validieren und zeigen
```docker-compose config```

Alle laufende Container anzeigen
```docker-compose ps```

Alle Container stoppen und entfernen
```docker-compose down```

# Reflexion
Primär versuchte ich das Docker Tool per Vagrant zu installieren, jedoch kam es konstant zu Fehlermledungen. Anschliessend versuchte ich das selbe mit einer Composer VM, die dann Docker verwaltet, mit den selben Ergbnissen. Schlussendlich installierte ich das Docker Tool lokal und konfigurierte den Service dort. Docker ist ein hilfreiches Tool, jedoch muss man sich mit den Feinheiten vertraut machen, da man ansonsten viel Zeit verliert.
