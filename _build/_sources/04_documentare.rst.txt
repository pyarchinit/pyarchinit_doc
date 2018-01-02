4. Documentare l'archeologia
****************************************
todo..

4.1 Realizzare una carta archeologica
======================================
todo..

4.2 Gestire la ricognizione Archeologica
=========================================
todo..

4.3 Schedare materiali: dal magazzino e dalla bibliografia
============================================================
todo..

4.4 Documentare i complessi architettonici
===========================================
todo..

4.5 Documentare i contesti stratigrafici
=========================================
todo..


4.5.1 Preparare il progetto di Qgis
---------------------------------------

Facciamo ora una rapida escursione per poter preparare una base Qgis che accolga i nostri dati sfruttando il dataset di pyArchInit. Non scenderemo nel particolare delle singole funzioni di Qgis, dato che per questo è possibile fare riferimento alla documentazione online di Qgis. Quindi daremo per scontato che abbiate una conoscenza di base di Qgis e delle sue funzioni principali.

4.5.2 Preparare la base GIS
-----------------------------------------
Per prima cosa si dovrà aprire la base GIS e fare alcuni settaggi che possono essere trovati nelle opzioni di QGis. Il menù può cambiare in base al sistema operativo, ma sostanzialmente le voci rimangono le medesime tra versioni uguali. Lasciamo gli utenti allo studio delle singole opzioni.

Fondamentale comunque è la scelta del sistema di riferimento spaziale: nel nostro caso specifico useremo l’EPSG ID 3004, sia per l’intero progetto Qgis, sia per tutti i layer che saranno caricati, spuntando la flag per la riproiezione al volo di layer caricati con differente CRS.

Andremo poi a settare i parametri nel driver del database che vogliamo utilizzare. In questo caso useremo il database spatialite che viene caricato in automatico dal plugin al momento della prima installazione dentro alla cartella dell’utente, in una specifica directory chiamata pyarchinit_DB_folder.

Una volta connessi caricheremo tutti i layer, alfanumerici e vettoriali, contenuti nel database e li raggrupperemo per poter meglio trovare le tabelle che ci saranno necessarie nel corso del nostro progetto. Fate attenzione ad abilitare la flag per visualizzare anche le tabelle senza geometria. Un piccolo accorgimento: per individuare le tabelle di pyArchInit seguite questo criterio: le tabelle con prefisso “pyarchinit_” rappresentano le tabelle geometriche, mentre quelle con suffisso “_table” sono le tabelle con dati alfanumerici.

Dopo il raggruppamento dei layer avremo una base con questo aspetto:

Abbiamo creato una cartella “Altri layers” come appoggio per eventuali nuovi layers da utilizzare nel corso del progetto. Se volete createla pure.


4.5.3 Aggiungere layers di riferimento
---------------------------------------
È possibile posizionare uno scavo sfruttando sia un rilevatore GPS, che batta uno o più punti fissi nel nostro scavo e che sfrutteremo per georiferire i nostri GCP, oppure basarsi con punti di controllo esterni, come carte catastali già georeferenziate, layer WMS, WFS, ecc..
In questo caso abbiamo dei punti di controllo a terra presi sul cantiere ma andremo ad aggiungere anche un esempio di layer WMS, in particolare una CTR 1:5000 presa dal sito della regione Emilia Romagna.


4.5.4 Aggiungere i GCP (Ground Control Points)
-----------------------------------------------
Come già detto, non discuteremo i vari passaggi e metodi per poter rilevare sul campo e importare in pyArchInit i nostri punti di controllo ma vi rimandiamo per il loro uso al paragrafo 3.3.4 sui punti di riferimento.

Qundo importerete in pyarchinit_punti i vostri GCP seguite questo semplice schema di compilazione:
sito = il vostro sito archeologico
def_punto = GCP
id_punto = la sigla univoca del vostro punto
quota = la misura della quota  Per esempio -1,56
unita_di_misura = l’unità di misura usate. Per esempio metri slm
area = l’area di riferimento in cui sono stati rilevati

Selezionate dal menu del layer pyarchinit_punti le “proprietà” e sotto la voce “Stile” scegliete un simbolo pratico da leggere e da centrare.

Realizzate una query nel “Costruttore di interrogazioni” e chiamate solo il sito che ci interessa con particolare riferimento al campo def_punto = “GCP”.

Scegliete come etichetta l’id_punto per poter visualizzare a video il nome del singolo GCP

A questo punto avremo una base come questa in cui è possibile visualizzare i vostri GCP georeferenziati.

Zoomando, potrete vedere meglio i vostri GCP con le relative etichette.

4.5.5 Aggiungere progetti collaterali con le Linee di riferimento
-----------------------------------------------------------------
Grazie al layer delle linee di riferimento è possibile aggiungere i progetti collaterali che possono avere interferenze col nostro scavo, o possono aiutarci al posizionamento. Nell’esempio sotto proposto è stato inserito il passaggio di una conduttura con relativo pozzetto di ispezione in base al progetto architettonico.

4.5.6 Aggiungere linee di sezione
----------------------------------
Appoggiandosi al layer pyarchinit_punti, possiamo aggiungere i punti di sezione, inserendo nel campo def_punto il valore “Punto di sezione” e nel campo id_punto il valore relativo all’ID del punto, che nel nostro caso è il punto A che coincide col GCP M6.

Dopo aver aggiunto anche il punto A1, andremo ad aggiungere nel layer pyarchinit_sezioni la linea di sezione opportunamente caratterizzata con una simbologia adeguata. Noterete che ora nei layer abbiamo due layer, uno per i GCP e uno per i punti di sezione: questi non sono altro che il medesimo layer, pyarchinit_punti, caricato 2 volte in 2 tempi differenti con query sulla def_punto come “GCP” e “Punto di sezione” e rinominati in legenda. In questo modo appariranno a video punti di controllo, punti di sezione e linee di sezione contemporaneamente, mantenendo ognuno il proprio stile ed etichetta di distinzione.

4.5.7 Georeferenziare i rilievi di scavo
-----------------------------------------
In questa sezione vedremo brevemente come georeferenziare il vostro rilievo di scavo da un raster (per esempio il classico overlay su lucido). Le procedure per geoereferenziare un raster da dentro Qgis sono ampiamente spiegate nel manuale, ma per comodità dell’utente andremo a riproporre gli step base per poter iniziare a lavorare sul vostro scavo. Diamo quindi per scontato che la vostra documentazione sia stata raccolta sul cantiere secondo le modalità espresse al capitolo in 4.1.

1 - Per prima cosa aprite la vostra base gis caricando i punti di aggancio a terra: GCP:

2 - Dal Menù di QGis Raster scegliete il Georeferenziatore:

3 - Dalla finestra di dialogo che vi si aprirà cliccate sul pulsante Aggiungi Raster e selezionate la vostra planimetria.

4 - A questo punto utilizzando lo strumento  “Aggiungi punto”(i tre pallini rossi) andremo a selezionare a schermo il punto di controllo sul raster e poi scegliere dal canvas di Qgis il punto di controllo corrispondente, precedentemente caricato con pyarchinit_punti. Finite le operazioni di collimazione dei punti, dalle impostazioni (simbolo con la chiave inglese)sceglieremo il tipo di trasformazione più adatto. Cliccando sull’icona di elaborazione (freccia verde verso destra)il raster verrà georeferenziato e caricato sul canvas di Qgis.

5 - Potrete quindi sovrapporre tutti i layer vettoriali o raster utili per iniziare la digitalizzazione delle vostre US.

4.5.8 Dalla stratificazione archeologica alla stratigrafia digitale: dati geografici
--------------------------------------------------------------------------------------------

Nel corso di uno scavo archeologico la stratificazione archeologica individuata e divisa in Unità Stratigrafiche viene tradotta in stratigrafia, ovvero una serie di “regole e convenzioni” grafiche che permettono all’archeologo di rileggere a ritroso il percorso di scavo e trasformare il dato di raccolta osservato sul terreno in dati interpretativi. Esamineremo ora nel dettaglio come importare in un progetto di pyArchInit tutti quei dati di tipo geometrico utili a descrivire una US.

4.5.9 A proposito delle “regole e convenzioni” di rappresentazione delle US
---------------------------------------------------------------------------------------------
L’archeologia, o meglio lo scavo archeologico nelle scienze archeologiche, sono una disciplina che per sua natura non può sfruttare il principio scientifico della riproducibilità in laboratorio di un esperimento: la stratificazione archeologica, una volta individuata, interpretata, tradotta in disegni, immagini e schede, e scavata, non può essere più indagata perchè distrutta. L’unico modo di rileggere i dati a ritroso è quello di avere una serie di regole e convenzioni per rappresentare la realtà che stiamo scavando. Come spesso ricordato dai manuali di archeologia, il momento della raccolta del dato sul campo è paradossalmente un momento di perdita delle informazioni; limiti delle US, composizione, spessori, eterogeneità delle matrici e degli inclusi, sono tutti fattori intepretativi altamente soggettivi, che difficilmente riescono ad essere gestiti secondo regole preimpostate come invece richiederebbe un metodo di documentazione, sia che questo sfrutti un supporto cartaceo che digitale.
Detto questo però è da tener presente come l’archeologia si sia sviluppata con le sue metodologie in vari secoli, in cui il bisogno di rappresentare era ed è il medesimo, mentre gli strumenti per farlo si sono evoluti; semplici disegni a matita, acquerelli, dagherrotipi, negativi, diapositive fino alla fotografia digitale e i laser scanner e nel nostro caso GIS che si appoggia a database spaziali, possono far mutare le modalità di rappresentazione grafica. Il disegno archeologico viaggia spesso su due binari a volte paralleli a volte sovrapposti, che sono da un lato la rappresentazione dal vero che seguono regole più o meno codificate e accettate, dall’altro le convenzioni grafiche.
Un bordo di spessore maggiore su una base cartacea rappresenta il limite di strato, mentre una linea a tratto punto alternati definisce i limiti, mente una linea tratteggiata indica la presenza di una Unità Stratigrafica Negativa. Quindi in una pianta di strato sarà regola fissa rappresentare una US nella sua interezza, mentre per convenzione si dovrà adottare una linea continua o tratteggiata a seconda della tipologia dell’US. Le superfici di strato inoltre possono avere una convenzione di rappresentazione a seconda della natura della matrice, argilla, sabbia, “terra”, carboni, ecc., che dovranno essere rappresentati sullo strato non tanto per segnalarne la posizione esatta ma per dare all’osservatore l’idea della situazione indagata sullo scavo. Altre volte invece, una caratterizzazione di uno strato può richiedere non una texture particolare, ma il disegno degli oggetti che la caratterizzano, collocati nella posizione in cui sono stati rinvenuti: prendiamo ad esempio un battuto in terra, sul quale si è crollato un solaio che ha dato vita ad un incendio: la texture di base del battuto rappresenterà l’argilla di cui è composta la pavimentazione, mentre potremo disegnare dei carboni sulla sua superficie nel punto in cui sono stati individuati al di sotto dell’US di combustione del solaio.
In una base GIS, in cui il singolo oggetto grafico porta con sè i dati di raccolta conservati in un database, la resa grafica diventa fondamentale per una buona uscita all’esterno del sistema, oserei dire che le regole e le convenzioni grafiche diventano quasi una ridondanza, dal momento ogni geometrie avrà in sè tutte le informazioni raccolte sul campo come natura dell’US e inclusi. In questo sistema quindi l’informazione alfanumerica rimane saldamente ancorata al dato geografico, mettendo in secondo piano la serie di regole e convenzioni di rappresentazione: una US tagliata da un’altra US, potranno essere rappresentate nel medesimo modo, dal momento che nel poligono che rappresenta l’US negativa vi sarà sempre il dato che taglia l’US positiva, ecc. ecc.
Quindi il primo concetto da capire per realizzare una buona base GIS è avere delle regole e convenzioni a monte utili e fondamentali nella fase di raccolta del dato con metodo cartaceo, che devono poi essere tradotte in dati geometrici e alfanumerici per poterli gestire e rappresentare non necessariamente per ogni progetto nel medesimo modo.


4.5.10 Digitalizzare i limiti di scavo
-----------------------------------------
I limiti di un’area di scavo possono essere definiti a priori dagli archeologi (a volte pessima idea!!!), seguire un particolare andamento della stratigrafia (per esempio un muro che divide in due la zona di indagine) oppure seguire limiti imposti dalla natura dell’indagine: sondaggio, trincea, scavo limitato per modivi edili.
In ogni caso l’importante è che dentro ad ogni area ricadano le US nel loro complesso, in modo che la medesima US non appartenga a due aree contemporaneamte.

1 - Per prima cosa prendiamo i nostri punti di riferimento che delimitano il nostro scavo e che devono essere salvati sotto pyarchinit_punti (nella figura sottostante rinominati come GCP). Aprire le “Opzioni di snapping” dalle Impostazioni e settare un valore congruo per pyarchinit_punti_rif al vertice.

2 - Dalle proprietà del layer andiamo a modificare il widget di riempimento del campo sito_rs, e prendiamo i dati da site_table, campo “sito” in modo da poter inserire correttamente il nome dello scavo.
 
3 - Sfruttando lo snapping disegnate il poligono delle ripartizioni spaziali e compilate i campi. Nel campo id_rs segnalate l’id univoco: Area 1. Nel tipo_rip date un nome che risfrutterete per richiamare tutte le aree di scavo dei vostri siti. Noi abbiamo scelto Area di scavo.

4 - Assegnate lo stile Contorno preimpostato nella collezione di stili di pyArchInit.

5 - Con lo strumento Sposta Vertice facciamo in modo che il contorno collimi con il disegno sottostante. Questo ci servirà in seguito per ritagliare le US in base al limite.

6 - Ecco come appare il nostro limite di scavo.


4.5.11 Digitalizzare una US
-------------------------------
Iniziamo ora a vedere passo passo come digitalizzare una Unità Stratigrafica.

1 - Sinceriamoci di aver richiamato dal database (nel nostro caso Spatialite) i layer alfanumerici site_table e pyarchinit_thesaurus_sigle e il layer spaziale pyunitastratigrafiche.

2 - Dopo aver caricato il raster della pianta che intendiamo digitalizzare annotiamoci numero di pianta e data di realizzazione della stessa.

 Questo ci permetterà di “sfogliare” sul GIS la sequenza con cui è stato indagato un sito e rivedere per una certa data lo stato di avanzamento del cantiere.

3 - Per poter normalizzare e velocizzare l’inserimento dei dati, apriamo dalle proprietà della tabella site_table, in cui in precedenza è stato creato un sito, il costruttore di interrogazioni e selezioniamo il nostro sito.

4 - Selezioniamo poi la tabella pyarchinit_thesaurus_sigle ed eseguiamo una ricerca sul campo nome tabella selezionando pyunitastratigrafiche. In questo modo avremo disponibili tutti i valori legati alle caratterizzazioni delle geometrie delle US: laterizi, malta, carboni, ecc.

5 - Iniziamo a settare i parametri per la digitalizzazione delle nostre US. Dalle proprietà di pyunitastratigrafiche selezionare il tab “Stile” e assegnarne uno con linea sottile e senza riempimento per poter digitalizzare visualizzando bene la linea.

6 - Spostiamoci ora sul tab “Campi” e iniziamo a settare le modalità di inserimento dei valori. Cliccare su Modifica Valore per il campo Area.

7 - Utilizzare la modalità “Mappa Valori” ed inserire i numeri di Area di scavo che si desidera utilizzare. Nel nostro caso il valore 1.

8 - Passiamo ora alla definizione dello scavo cliccando su Modifica valore

9 - Dopo aver selezionato la modalità Mappa Valori, cliccare su “Carica dati dal vettore”. In questo modo sarà possibile sfruttare i dati presenti in una tabella esterna, nel nostro caso site_table, che andreamo a segnalare nella lista a tendina “Layer”. Selezioniamo sia per il campo Valore che per Descrizione i campi sito; cliccate su “Mostra tutto”. Avendo precedentemente realizzato una query su site_table (vedi sopra) e scelto come valore “Sito archeologico” (il nome fittizio scelto per il nostro scavo), saremo in grado di inserire correttamente il nome del luogo oggetto di scavo.

10 -  Passiamo alla definizione dei valori per lo stratigraph_index_us

11 -  Sempre dalla Mappa Valori, assegniamo come Valore il numero 1 e facciamo corrispondere la descrizione Caratterizzazione US; per il Valore 2, assegniamo come Descrizione “Contorno US”. In questo modo nel widget potremo, selezionando Caratterizzazione US o Contorno US, assegnare al record i valori 1 o 2.

12 - Apriamo ora il widget di modifica per il tipo_us_s.

13 - Da Carica dati dal vettore, selezioniamo sotto Layer la tabella pyarchinit_thesaurus_sigle sia per il valore che per la descrizione il campo sigla_estesa e cliccare su “Mostra tutto”. A questo punto avremo a disposizione tutta la terminologia contenuta nel thesaurus delle sigle per descrivere in maniera normalizzata le US digitalizzate.

14 - Assegniamo un nome al disegnatore.

15 - Assegniamo il numero di pianta che andremo a digitalizzare.

16 - Assegniamo la data della pianta.

17 - Passiamo ora al disegno vero e proprio. Non importa se disegnerete prima il contorno e poi le caratterizzazioni, dato che pyarchinit_us_view riordinerà in base allo stratigraph index, cosa sta sotto e cosa sta sopra. Tuttavia vi possono essere casi, in cui per comodità si disegnano elementi che si sovrappongono e che lo stratigraph index non può risolvere. Quindi tenete presente per ora una regola banale: le cose disegnate per prime saranno visualizzate dal GIS sotto a tutte le altre mentre le ultime finiranno sopra a tutto. Per un muro, come nel caso sottostante, avendo come elementi: Contorno, Malta, Laterizi, per poter campire le US e visualizzare tutto correttamente sarà bene disegnare gli elementi come nell’ordine sopra descritto: contorno, malta, us. In seguito vedremo anche casi particolari. 
Selezionate pyunitastratigrafiche e attivando la modifica (click sull’icona con la pennina blu), selezionate lo strumento poligono.

18 - Scegliete un punto da cui partire e iniziate a ricalcare con singoli click il contorno dell’US. Fate attenzioni a non cliccare 2 volte sullo stesso punto.

19 - Un consiglio è quello di disegnare a volte i contorni non sempre precisi rispetto ai limiti di scavo, perché in quel punto dovranno terminare più strati. Sarà opportuno quindi fare una operazione di taglio alla fine della digitalizzazione in modo da avere le US tutte collimanti con il limite di scavo.

20 - Una volta chiuso il contorno della nostra US, si aprirà il widget di inserimento dati, già predisposto in base ai valori scritti in precedenza nelle proprietà. Dovremo solo inserire il numero di US, il tipo di stratigaph_index (nel nostro caso: Contorno US) e il tipo di US: positiva, negativa, struttura. In questo esempio: struttura.

21 - Cliccando sul dischetto si salverà il disegno corrente e potranno essere fatte ulteriori modifiche quali: aggiunta, rimozione o spostamento di vertici, rimodellazione, divisione in due o più parti, ecc.. Se riterrete che il disegno sia soddisfacente potrete ricliccare sulla pennina per chiudere la modifica.
22 - Con lo strumento “Vertice”, potrete correggere la posizione della vostra linea.

23 - Passiamo ora alle caratterizzazioni. Ricaricate il layer pyunitastratigrafiche e rinominatelo in “Caratterizzazioni” per poter sapere su quale livello state lavorando.

24 - Dalle proprietà del layer fissare tramite una interrogazione le geometrie visualizzate solo su stratigraph_index = 1. Questo in pratica ci permetterà di visualizzare solo le caratterizzazioni che andremo a disegnare man mano. Nel caso di più US già presenti nel database sarà possibile inserire nei valori di ricerca scavo, area e US, in modo da avere un canvas di Qgis pulito.

25 - Come nel caso del contorno delle US disegnate la caratterizzazione e chiudendo la modifica inserite come dati il numero di US, la stratigraph index, in questo caso Caratterizzazione US e il tipo di caratterizzazione: laterizio.

26 - Dalle Impostazioni scegliete le Opzioni di snapping e spuntate il nome del layer in cui sono presenti i contorni dando un valore adatto alla vostra scala per poter snappare, ovvero agganciare i nodi delle caratterizzazioni ai contorni delle US, in caso di caratterizzazioni che collimino con il contorno dell’US.

27 - A questo punto creare una query per il contorno delle US, in cui si visualizza solo il contorno delle US. In questo modo, avremo richiamato 2 volte il medesimo layer, pyunitastratigrafiche, ma su uno disegneremo il contorno dell’US e sull’altro le singole caratterizzazioni.

28 - Nel caso sottostante, un lato del laterizio andrà a collimare con il limite dell’US. Grazie allo snap potremo fare un lavoro preciso con pochi click.

29 - Se avremo più caratterizzazioni di strato, in questo caso laterizi, con forma simile e medesimi dati in tabella potremo ricorrere anche allo strumento copia dopo aver selezionato un elemento..

30 - Spostarlo nella posizione di una nuova geometria da digitalizzare.

31 - Modificarne la forma utilizzando lo strumento “sposta vertice” oppure sfruttando lo strumento di “Reshape”

32 - Di seguito la nuova forma del contorno data dall’applicazione del “Reshape”.

33 - Ecco come si presenta l’US totalmente disegnata.

34 - Ora vediamo come rifinire le parti di perimetro dell’US che collimano con il limite di scavo.
Per prima cosa ripuliamo il “Costruttore di Interrogazioni” di pyunitastratigrafiche da ogni ricerca cliccando su “Cancella”.

35 - Attiviamo lo snapping sui vertici di pyarchinit_ripartizioni_spaziali e selezioniamo pyunitastratigrafiche per poter rimodellare quelle parti di US che vanno oltre i limiti di scavo.

36 - Utilizziamo lo strumento reshape per poter rifinire il contorno.

37 - Ecco come appare il contorno delle US dopo la modifica.


38 - Applichiamo la modifica con il reshape in tutti i punti in cui ce n’è bisogno.

39 - Applichiamo ora uno stile, sfruttando il sistema “Categorizzato”, per caratterizzare i singoli elementi, scegliendo gli stili di pyArchInit.

40 - Ecco come appare ora la nostra US caratterizzata.

41 -  Alla nostra US però manca ancora qualcosa. Essendo un muro, i laterizi sono tenuti insieme da malta. Quindi vediamo come realizzare la malta. Selezioniamo solo il poligono relativo al contorno dell’US. Copiamo e incolliamo.

42 -  Individuiamo il poligono incollato e assegnamo come stratigraph_index il numero 1 delle caratterizzazioni, e da “struttura” cambiamo il campo “tipo_us” in “malta”.

43 - Selezioniamo a questo punto tutte le caratterizzazioni che devono andare sopra alla malta.

44 - Con la modifica attiva, selezionate le geometrie visualizzate, tagliare e poi incollare tutti i materiali.

45 - A questo punto i laterizi e i ciottoli risultano sovrapposti alla malta.

46 - Selezioniamo ora il layer pyarchinit_quote. Dopo aver modificato i widget di immissione dati come nel caso delle US, mettere in modifica il layer e con lo strumento punto aggiungere la quota.

47 - Ecco come appare l’US ultimata la digitalizzazione e con una ipotetica sovrapposizione con un progetto edile.

4.5.12 Inserire le schede US
--------------------------------

1 - Tenendo sotto le vostre piante di scavo e i vostri appunti, iniziate ad inserire le schede US grazie all’apposita interfaccia. In questa fase saranno inseriti tutti i dati riferiti sostanzialmente ai dati di scavo: definizione stratigrafica, descrizione, rapporti stratigrafici, documentazione ecc., lasciando in dietro le interpretazioni come Periodizzazione e Strutture:

2 - Terminato l’inserimento di tutte le schede US ci sposteremo nella sezione Tools per verificare la presenza di eventuali errori.

3 - In questo caso abbiamo verificato la presenza di errori nell’inserimento di alcuni rapporti stratigrafici:

4 - E li abbiamo corretti nelle schede relative. Con il pulsante “vai all’US!” è molto comodo spostarsi attraverso la stratigrafia per verificare la presenza degli errori e ragionare su come correggerli.

5 - Infine abbiamo generato un Matrix per verificare che non vi siano rapporti di ritorno che creino dei paradossi nella stratigrafia a causa di un errato inserimento dei rapporti.

4.5.13 Inserire le schede di Struttura
-------------------------------------------

1 - Nell’apposita interfaccia Struttura andiamo a realizzare la scheda relativa per raggruppare insieme le US appartenenti ad un’unica struttura. Nella fattispecie l’ED1, una casa medievale composta da almeno 2 fasi diverse di vita che andremo poi a dividere in 2 fasi distinte per poter visualizzare in maniera dinamica i nostri strati.

2 - Una volta creata la scheda si passi alla scheda US e si inserisca nell’apposito campo Struttura la sigla scelta.

3 - Ora proviamo a cercare nella Scheda US l’ED1 con la funzione “GIS viewer” attivata. Verificare di aver inserito correttamente tutte le US riferibili alla struttura e correggere l’inserimento in caso di errore.

4 - Carichiamo il layer pyarchinit_ipotesi_strutture e disegniamo l’ipotesi, per quanto possibile, di come poteva essere il nostro edificio, segnalando sia le strutture per come sono state rinvenute, sia le integrazioni in base alle nostre ipotesi ricostruttive.
Visualizziamo infine il risultato sovrapponendo le ipotesi con le US rinvenute...

... e in seguito solo la pianta ricostruttiva.

5 - Per completare il lavoro possiamo selezionare a schermo le US della struttura dal layer delle view, caricarle dentro alla scheda US ed esportare il matrix della sola struttura.


4.5.14 Inserire le schede di Periodizzazione
-------------------------------------------------
Aprire la tabella della Periodizzazione e inserire i periodi che definiscono la scansione temporale. 
In questo esempio abbiamo 2 periodi, uno che rappresenta il medioevo e uno che rappresenta la fase di abbandono di epoca moderna. Infine la periodizzazione medievale è stata divisa in tre fasi: costruzione, ampliamenti, aggiunte.

Dopo aver ordinato i record in base alla cronologia iniziale abbiamo assegnato un numero di Codice periodo.

A questo punto aprire la scheda US e assegnate ai singoli strati la periodizzazione relativa.

Nella sezione Tools, dopo aver selezionato il nome dello scavo cliccate su Crea Codice Periodo per assegnare a tutte le US il codice di periodo.

In questo modo sarà possibile dalla scheda di periodo chiamare una fase semplicemente cliccando sul pulsante “Visualizza il periodo sul GIS”.

In seguito possiamo tematizzare a piacimento il layer pyarchinit_us_view appena visualizzato dividendo per colori le singole fasi.

Come abbiamo fatto per le strutture, anche per i periodi di scavo possiamo selezionare la query della scheda di periodizzazione visualizzata sul GIS e caricare le relative schede US; a questo punto esporteremo il matrix relativo alla periodizzazione scelta che risulterà diviso per periodi e fasi.

4.5.15 Output di stampa
-------------------------
Alla fine possiamo esportare in formato .png o .pdf dal gestore di stampa, includendo tematismi, etichette o immagini esterne.
In questo caso abbiamo esportato le piante di fase di una casa medievale con relativo matrix.