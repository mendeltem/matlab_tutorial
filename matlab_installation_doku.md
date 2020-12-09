# Doku für Matlab  Offline installation

## 1. Matlab Installieren.


### 1.1 Zuerst Matlab für Windows Version runterladen.

Mit dem Windows Version laden wir die Linux Version runter.

https://de.mathworks.com/downloads/web_downloads/

### 1.2 Die volle Linux Version runterladen

Nach dem Entpacken des ZIP Ordners auf setup.exe klicken.  
Recht oben auf Matlab download only runterscrollen und wählen.  
 
### 1.3 Nach lokalen Ordner Kopieren 
 
Nach dem runterladen die ganze Datei auf die Lokale Home Ordner der Server verschieben/kopieren.  
(Grund: Wenn der Link zu lang ist kann das zu Problemen führen.)
'''sh
	cp -r Matlab_R2020b_glnxa64 ~/
'''

### 1.4 Vollständig Entpacken 

Danach im lokaen Matlab Ordner folgenden Befehl eingeben.
(Grund: Fehlende Bibliotheken)
```sh
	sudo unzip -X -K matlab_R2020b_glnxa64.zip 
```

### 1.5 Installieren


Im Ornder von Matlab_R2020b_glnxa64/  mit folgenden Befehl installieren.

```sh
	sudo ./install
```

Danach Sollte ein Matlab Installations Fenster erscheinen.  

Hier zustimmen.  

![Installieren](images_for_matlab_installation/installation.png)

Hier werden nach den Key und File gefragt

![Installieren](images_for_matlab_installation/installation2.png)

Hier den Ort der Installation eingeben.

![Installieren](images_for_matlab_installation/installation3.png)


### 1.6 Installation Abschließen falls danach fehlen sollte.  


'''sh
	sudo nano MATLAB/R2020b/licenses/network.lic
'''

Hier die Namen MAC Adresse und freien Port

Beispiel

SERVER s-csb-gpu E41F13EFED30 27000
USE_SERVER


'''sh
	cd MATLAB/R2020b/etc/

./lmstart
'''


Falls Fehler beim Aktivieren der lizenz Server gibt.

'''sh
	less /var/tmp/lm_TMW.log
'''

Danach mit kontrollieren ob der Lizenz Server funktioniert.

'''sh
	netstat -anp | grep 27000
'''



## 2. Lizenz Aktivieren und die Keys holen

Multiuser Lizenz bei Lizenzmanagement bei der Charite (LIC) nachfragen. (Derzeit Jan Bessert)

Bei der Abfrage sollten folgende Daten mit eingegeben werden.  

OS: Linux

Hostname:  
s-csb-gpu.charite.de

MAX-Adresse:   
Kann durch den Befehl herausfinden. 

'''sh
	ip address
''' 
 
e4-1f-13-ef-ed-30

IP-Adresse:
10.47.120.23



## 3. Fehlermöglichkeit


Wenn Sudo befehl folgende Fehlermeldung entsteht.


MobaXterm X11 proxy: Authorisation not recognised
Unable to init server: Broadway display type not supported: localhost:19.0
Error: cannot open display: localhost:19.0


In Terminal eingeben.  (Achtung Benutzer Name ändern!!!)

```sh

    sudo xauth add $(xauth -f ~temuuleu/.Xauthority list|tail -1)
```

https://blog.mobatek.net/post/how-to-keep-X11-display-after-su-or-sudo/

