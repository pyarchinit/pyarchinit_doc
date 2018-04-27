5. Installazione
****************************************
Ecco una serie di tutorial per l'installazione di pyArchInit.


5.1 pyArchInit 3 per Qgis 3 su Windows
======================================

Versione pyArchInit: 3
Nome: Garibaldi
Versione di Qgis richiesta: Qgis 3.x
Sistema operativo: Windows 7 e Windows 10
Testato su: Windows 7 e Windows 10 a 32 bit e 64bit
Usabilità: SOLO PER IL DEBUG
Versione python: 3.x
Prerequisiti richiesti: Graphviz 2.x, moduli python: sqlalchemy, reportlab, graphviz forniti con l'installer di pyarchinit da eseguire a parte.

Al momento stiamo testando il porting dalla versione 2.7 di Python alla versione 3. Il nuovo pyArchInit andrà sotto al nome di pyArchInit 3 - Garibaldi.
Se vuoi aiutarci a correggere i problemi e gli errori segui questi semplici step.

!!!!WARNING!!!! L'installazione crea una cartella di nome "pyarchinit" all'interno del vostro utente.

Sinceratevi che sotto a "C:\\Utenti\\vostroutente\\" non vi sia alcuna cartella chiamata "pyarchinit". !!!!WARNING!!!!

1 - Scaricare QGIS da https://qgis.org/it/site/

2 - Scaricare Graphviz da http://www.graphviz.org/

3 - Scaricare la versione master di pyarchinit da: https://github.com/serenasensini/pyarchinit_3

4 - Estrarre dalla cartella pyarchinit-master.zip /scripts il file modules_installer.py in un cartella che in seguito potremo raggiungere

5 - Avviare "Osgeo4W Shell" facendo tasto destra "Esegui come amministratore". Potete cercarla sotto Avvio o Start -> Programmi ->Qgis 

6 - Nella shell digitate: >>py3_env e date invio.

7 - Navigate nella shell per posizionarvi sulla cartella in cui avete estratto il file modules_installer.py.
Se non lo avete mai fatto sappiate che il comand cd sta per choos directory e vi permette di scegliere una cartella in cui entrare; il simbolo composto cd <SPAZIO> e due punti fermi consecutivi, ovvero CD .. serve per andare indietro di una cartella. 

Quindi se abbiamo estratto sotto al nostro utente il file, nella console scriviamo >>cd C:\\users\\nomedelmioutente\\ e date invio.

In questo modo saremo nella cartella utente.

Per sapere se il nostro file è presente date il seguente comando per listare la cartella >>dir e date invio.

Vi appariranno tutti i file che sono presenti nella vostra cartella utente. Guardate se c'è il file modules_installer.py.
Se c'è allora proseguite allo step 8 altrimenti rifate lo step 7.

8 - digitate nella shell il seguente comando >>python modules_installer.py e date invio. Una volta terminato il processo potete chiudere la shell.

9 - Lanciate Qgis.

10 - Dal menù in altro cercate Plugins->Gestici e installa plugin... e selezionate la sezione "Installa da zip". Selezionate il file pyarchinit-master.zip e cliccate su "Installa plugin". Attendete.

!!!!WARNING!!!!IN FASE DI SPERIMENTAZIONE!!!!WARNING!!!!
11 - Se vi appare correttamente il plugin, andate nelle configurazioni di pyArchInit cliccando sul pulsante

.. image:: ./_images/img_51.PNG
   :align: center
   
Aggiungete nella casella delle variabili il percorso C:\Program Files (x86)\bin e salvate.
!!!!WARNING!!!!!!!!WARNING!!!!!!!!WARNING!!!!!!!!WARNING!!!!!!!!WARNING!!!!!!!!WARNING!!!!!!!!WARNING!!!!
