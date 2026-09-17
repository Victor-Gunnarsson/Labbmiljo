# Labbdmiljö, CLI, Git & AI
## Victor Gunnarsson - ISCX26
### Beskrivning av detta dokument

## Del 1: Skapa och och initiera projektet med Git

Först skapade jag en mapp på min lokala dator som innehåller filerna som ska laddas vara i ett Git-repo. För att göra detta körde jag dessa kommandon för att sätta mappen som ett repo, och sedan för att koppla det till min Github.

1. git init
2. git add Labbdokumentation_Victor_Gunnarsson.md
3. git commit -m "Första versionen av dokumentationen"
4. git branch -M main
5. git remote add origin git@github.com:Victor-Gunnarsson/Labbmiljo.git
6. git push -u origin main

## Del 2: Virtuell Labbmiljö & Nätverk

Detta labb är uppsatt med en server som kör Ubuntu och en klient som kör Windows 11. Dessa är båda virtualiserade i Virtualbox med nätverkskorten satta till Internal Network och statiska IP adresser är satta så de kan kommunicera med varandra. Nedan är en tabell med snabbinfo:

| Information | Linux | Windows |
| ----------| -------- | ------- |
| Hostname | ubuntuserverlab | Windows11lab |
| Operativsystem | Ubuntu 26.04 LTS | |
| IP address | 192.168.10.10 | |
| Subnetmask | 255.255.255.0 | |
| MAC-address | 08:00:27:6e:4d:94 | |
| Interface | enp0s3 |  |

## Del 3: Kommandoraden & Felsökning


## Del 4: AI-stöd & Kritisk utvärdering