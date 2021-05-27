# Workshop Graphdatenbanken WS 2021

Willkommen beim Workshop Graphdatenbanken der Firma CONET im Rahmen der Vorlesung "Business Intelligence" im Masterstudiengang Wirtschaftsinformatik der Hochschule Bonn-Rhein-Sieg. Hier werden zunächst alle Schritte beschrieben die Du ausführen musst, um erfolgreich an der Veranstaltung teilnehmen zu können.

## Einrichten der Arbeitsumgebung

Alle Installationsschirtte werden auf Basis von Windows 10 dokumentiert und erläutert. Lassen sich aber auch problemlos auf andere Systeme adaptieren.

### Installation Neo4j

Lade dir von der [Neo4j Homepage](https://neo4j.com/download/) Neo4j 4.2 für den Desktop herunter. Dieses ist für die folgenden Systeme verfügbar MacOS 10.10 (Yosemite)+, Windows 7+, Ubuntu 12.04+, Fedora 21, Debian 8. 
Nach der Eingabe deiner Daten startet der Download und Du wirst auf eine Seite weitergeleitet, auf der Du einen Neo4j Desktop Activation Key erhältst. Kopiere diesen Key in die Zwischenablagen. Führen dann das Setup aus und folgen den Anweisungen der Installation. Starte nach erfolgreicher Installation Neo4j Desktop und klicke dich durch die Einrichtung der Software. Nach zwei Schritten gelangst Du zur Maske „Software Registration“. Gib hier den Key ein, den Du beim Download erhalten hast oder registriere dich erneut.

![image](https://user-images.githubusercontent.com/3823750/119736769-8a470900-be7e-11eb-8a09-167fa1b0c0b7.png)

Nach Abschluss des ersten Starts von Neo4j solltest Du ein Fenster ähnlich dem der nachfolgenden Abbildung sehen können.

![image](https://user-images.githubusercontent.com/3823750/119736906-bd899800-be7e-11eb-9d26-c8e9caff2b01.png)

### Anlegen einer neuen Datenbank

Leg innerhalb des „Example Project“ über die Schalfläche „Add“ ein neues „Local DBMS“ an.

![image](https://user-images.githubusercontent.com/3823750/119736977-dbef9380-be7e-11eb-8a8d-f4502fd6f958.png)

Gib der Datenbank einen sprechenden Namen und überleg dir ein Passwort. Als Version wähle bitte 4.2.6 (latest) aus und bestätige über die Schaltfläche „Create“ das Anlegen des neuen DBMS. 

![image](https://user-images.githubusercontent.com/3823750/119737311-5c15f900-be7f-11eb-8995-3967e5f240a2.png)

Die neuste Version der Datenbank wird nun heruntergeladen und ein lokales DMBS wird auf deinem System angelegt. 
Wenn alles geklappt hat, wird das neue DBMS unterhalb des Movie DBMS angezeigt.

![image](https://user-images.githubusercontent.com/3823750/119737368-7a7bf480-be7f-11eb-96d1-c9428949042c.png)

Damit wir später die Panama Paper in die Datenbank importieren und mit den Daten arbeiten können, ist es notwendig die Speicherkonfiguration des DMBS anzupassen. Öffne dazu über das Drei-Punkte-Menü den Eintrag **Settings**.

![image](https://user-images.githubusercontent.com/3823750/119737722-fd9d4a80-be7f-11eb-920f-2f0b9d5251c7.png)

Suche in der Konfiguration die folgenden Einträge und passe Sie wie im Code-Listing angegeben an. Durch "Apply" und "Close" kannst du die Konfiguration nun wieder verlassen.

```
dbms.memory.heap.initial_size=3g
dbms.memory.heap.max_size=3g
dbms.memory.pagecache.size=1g
```

### Plugins installieren

wenn du auf dein neu angelegtes DMBS klickst, erscheint auf der rechten Seite des Fenster ein neuer Bereich, in dem Du über den mittleren Reiter "Plugins" funktionale Erweiterungen in das DMBS hinzufügen kannst. Installiere hier bitte APOC und die Graph Data Science Library jeweils über die Schaltfläche "install".

![image](https://user-images.githubusercontent.com/3823750/119739367-6a194900-be82-11eb-8d5f-b175c63be33f.png)

### Panama Paper laden

Der Datensatz, den wir uns im Rahmen dieses Workshops anschauen, wurde vom **International Consortium of Investigative Journalists** [ICIJ](https://www.icij.org/) erstellt und ist unter der [Open Database License](http://opendatacommons.org/licenses/odbl/1.0/) lizensiert. Der Content der Datenbank steht wiederum unter der [Creative Commons Attribution-ShareAlike](http://creativecommons.org/licenses/by-sa/3.0/) Lizenz. Bei der Verwendung der Datenbank und der Daten ist die Referenz auf das ICIJ und die Lizenz stehts anzugeben. 

Die "Roh-Daten" können auf einer Downloadseite des ICIJ als unaufbereitete CSV-Dateien heruntergeladen werden. Alternativ steht auch direkt ein Download in Form einer (leider relativ alten) Neo4j Datenbank zur Verfügung. Ich habe das Format der Daten zur Verwendung in einer aktuellen Neo4j Version angepasst und [hier](https://1drv.ms/u/s!Aq1EaJ_JNtZ-nsNZD_LhvUJ7q51r4w?e=Lcgl9G) zum Download zur Verfügung gestellt. 

Lade die Daten herunter und entpacke Sie in das Import Verzeichnis deines vorhin erstellen DBMS. Diese erreichst du, wie im Screenshot dargestellt über das Drei-Punkte-Menü.

![image](https://user-images.githubusercontent.com/3823750/119739775-07747d00-be83-11eb-9aa2-e55600b8ba03.png)

#### Import Vorgang starten

Um den Importvorgang starten zu können, musst Du in einer Powershell in das Verzeichnis deines DMBS navigieren. Der einfachst Weg dies zu machen ist sicherlich über das bereits bekannte Drei-Punkte-Menü das DBMS-Verzeichnis zu öffnen und dann in der Adresszeile `powershell` einzugeben.

In der Powershell musst du dann den folgenden Befehl ausführen.

```bat
bin\neo4j-admin import --ignore-empty-strings=true --database=neo4j --id-type=INTEGER --multiline-fields=true --nodes=import/offshore-nodes.csv --relationships=import/offshore-relationships.csv
```

Nun sind die Daten in Neo4j importiert und Du kannst die Datenbank über die Schalfläche "Start" endliche starten.

Alles weitere folgt dann in der Veranstaltung.
