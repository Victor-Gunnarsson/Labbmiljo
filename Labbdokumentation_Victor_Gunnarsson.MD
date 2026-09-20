# Labbmiljö, CLI, Git & AI
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

Denna labb är uppsatt med en server som kör Ubuntu och en klient som kör Windows 11. Båda virtualiserade i Virtualbox med nätverkskorten satta till Internal Network och statiska IP adresser är satta så de kan kommunicera med varandra. Nedan är en tabell med snabbinfo:

| Information | Linux | Windows |
| ----------| -------- | ------- |
| Hostname | ubuntuserverlab | WINDOWS11LAB |
| Operativsystem | Ubuntu 26.04 LTS |Microsoft Windows 11 Home 10.0.26200 |
| IP address | 192.168.10.10 | 192.168.10.20 |
| Subnetmask | 255.255.255.0 | 255.255.255.0 |
| MAC-address | 08:00:27:6e:4d:94 | 08-00-27-EB-8B-5C |
| Interface | enp0s3 | Ethernet adapter Ethernet |

## Del 3: Kommandoraden & Felsökning

Efter att jag satt statiska IP-adresser enligt ovan tabell började jag pinga, först från Windows med kommandont `ping 192.168.10.10`:

![Ping från Windows](windowsping.png)

Testade samma sak från Ubuntu med `ping 192.168.10.20 -c 4`för att ping Windows-maskinen 4 gånger (-c 4) men det gick ej:

![Ping från ubuntu](ubuntuping.png)

Jag frågade AI:
> Jag kan pinga från en Windows-dator till Ubuntu men inte tvärtom, vad kan ligga bakom och hur felsöker jag detta?

Fick svaret att brandväggen på Windows-datorn troligtvis ligger bakom och att jag ska kolla den, först kolla om regeln för att blocka Echo Request (ping) är påslagen:

`netsh advfirewall firewall show rule name="File and Printer Sharing (Echo Request - ICMPv4-In)"`

Står att regeln inte är igång som tillåter Echo Requests, kommandot för att sätta igång det fick jag av AI i nästa steg:

`New-NetFirewallRule -Name "Allow-ICMPv4-In" -Protocol ICMPv4 -IcmpType 8 -Direction Inbound -Action Allow`

Testade ping igen från Ubuntu-maskinen och det lyckades!

![Ping från ubuntu](ubuntupingsuccess.png)

 Linux | Windows |
 -------- | ------- |
| ![Ubuntu](ipubuntu.png) | ![Windows](ipwindows.png) |

## Del 4: AI-stöd & Kritisk utvärdering