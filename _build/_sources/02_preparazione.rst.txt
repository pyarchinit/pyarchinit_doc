2. Preparare la documentazione
******************************
todo..


2.1 Carte Archeologiche
=======================
todo..


2.1.1 - Documentare l'edito e l'inedito
----------------------------------------

todo..


2.1.2 - Aerofotointerpretazione
-------------------------------

todo..


2.1.3 Georeferenziare la cartografia storica
--------------------------------------------

todo..


2.2 Ricognizione del territorio
===============================

todo..


2.3 Documentare materiali (Collezioni private, magazzini, musei)
================================================================

todo..


2.4 Archeologia dell'architettura
=================================

todo..


2.5 Indagini stratigrafiche
===========================

todo..


2.5.1 Preparare lo scavo per la documentazione
--------------------------------------------------

Iniziamo ora a vedere nella pratica come documentare uno scavo archeologico. Anche in questo caso una premessa è d’obbligo: l’archeologia è una disciplina che a volte sfiora il campo “dell’arte”, dove l’interpretazione soggettiva e a volte arzigogolati modi di interpretare e gestire lo spazio prendono il sopravvento sulla praticità; ogni archeologo che ha scavato almeno su due siti differenti e con equipe diverse, si sarà accorto di piccole differenze sostanziali sia nel modo di leggere la stratificazione archeologica, sia nel modo di tradurre la stessa in stratigrafia. Un primo esempio banale può essere la divisione delle aree di scavo: chi le chiama quadrati, chi settori, chi usa tutte e tre i termini in gerarchie:

-Aree;
     -Settori;
         -Quadrati.

Inoltre, anche in caso di un medesimo modo di nominare una ripartizione di scavo come Area, ci troveremmo sempre di fronte a come siglare tale area: chi usa lettere, A, B, C, chi usa numeri in progressione: 1, 2, 3, …, o ancora chi usa numeri ma non a partire da 1, ma da 1000, con le US inserite all’interno della numerazione di area: per l’Area 1000, avremo le US da 1 a 999 (non stiamo qui a parlare del dramma di quell’archeologo che arrivato al 999, inizia a numerare le US come 1001a, 1002a, per non sovrapporre i numeri di US).
Va sottolineato infine che ogni archeologo ritiene il suo metodo IL METODO, ed è molto difficile farlo deviare dal proprio modus operandi.

Altra problematica nasce dall’informatizzazione dei dati rispetto alla praticità di lavorare sul campo. L’obiettivo di porre regole informatiche alla base del nostro modo di gestire i dati deve tenere presente almeno 4 momenti distinti:
-raccolta dati
-importazione dati nel sistema
-elaborazione dati
-esportazione dati

Il momento spesso critico sta proprio nella fase 1 e nel passaggio dalla fase 1 alla fase 2. Spesso su un cantiere poter disporre di strumenti informatici pratici all’uso non è sempre possibile: problemi di corrente elettrica, ostilità dei delicati strumenti elettronici rispetto all’ambiente di scavo, velocità di registrazione manuale di un dato rispetto alle regole fisse imposte da una scheda elettronica. Questo fa propendere molte volte per un uso del cartaceo nel momento della registrazione e di una trascrizione a posteriori in formato digitale. Va da se che scrivere sul cartaceo genera di per se errori, dato che il controllo di inserimento è delegato all’utente. La trascrizione ne genera altresì ulteriori, dato che un dato può essere riportato male.
In questo piccolo manuale proveremo a dare per scontato che il lavoro si faccia tutto in formato digitale fin da subito per motivi di praticità.

Quindi, anche con pyArchInit abbiamo dovuto operare delle scelte di metodo, cercando di basarci in prima istanza sulla propria esperienza nel campo dello scavo archeologico e in seconda battuta ad un modello di gestione dati di tipo informatico, che rendesse più rigoroso il sistema di data entry.
4.1 Preparare lo scavo per la documentazione
Per poter ben documentare una pianta di una US, sarà necessario per prima cosa posizionare sul campo una serie di picchetti o punti fissi, possibilmente che comprendano al loro interno le US che andremo a scavare. Questi punti in seguito dovranno essere georeferenziati o in base a punti fiduciali noti, ad edifici circostanti riconoscibili sulla cartografia di riferimento o ancora meglio, mediante una battitura GPS con precisione subcentimetrica.

Daremo quindi per assodato che i nostri punti siano già stati posizionati in cantiere e battuti tramite una stazione totale, già agganciati a punti georeferenziati e pronti per essere importati dentro la nostra base. Nel corso dello scavo potremo eseguire un classico rilievo su lucido oppure un rilievo fotogrammetrico. Cosa FONDAMENTALE è che in ogni pianta o fotogrammetria siano presenti i GCP (Ground Control Points - ovvero Punti di Controllo a Terra, più banalmente i classici picchetti).

Quindi, anche con pyArchInit abbiamo dovuto operare delle scelte di metodo, cercando di basarci in prima istanza sulla propria esperienza nel campo dello scavo archeologico e in seconda battuta ad un modello di gestione dati di tipo informatico, che rendesse più rigoroso il sistema di data entry.

Per poter ben documentare una pianta di una US, sarà necessario per prima cosa posizionare sul campo una serie di picchetti o punti fissi, possibilmente che comprendano al loro interno le US che andremo a scavare. Questi punti in seguito dovranno essere georeferenziati o in base a punti fiduciali noti, ad edifici circostanti riconoscibili sulla cartografia di riferimento o ancora meglio, mediante una battitura GPS con precisione subcentimetrica.

Daremo quindi per assodato che i nostri punti siano già stati posizionati in cantiere e battuti tramite una stazione totale, già agganciati a punti georeferenziati e pronti per essere importati dentro la nostra base. Nel corso dello scavo potremo eseguire un classico rilievo su lucido oppure un rilievo fotogrammetrico. Cosa FONDAMENTALE è che in ogni pianta o fotogrammetria siano presenti i GCP (Ground Control Points - ovvero Punti di Controllo a Terra, più banalmente i classici picchetti).

.. image:: ./_images/schedaus.png


