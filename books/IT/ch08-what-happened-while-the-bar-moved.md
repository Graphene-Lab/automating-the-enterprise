# 8. Cosa è successo mentre il bar si muoveva

L'installazione ha richiesto quaranta minuti, dei quali la maggior parte è stata dedicata a guardare uno schermo che non cambiava.

Questo capitolo descrive cosa è successo durante quei quaranta minuti, spiegato per chi non dovrà mai eseguirlo a mano ma che pur meritano di sapere cosa sta girando sulla macchina—perché un sistema che non comprendi è un sistema che non puoi fidarti, e un sistema che non puoi fidarti è un sistema che abbandonerai a marzo.

Ci sono cinque cose da spiegare: il database, l'ambiente Python, l'ERP, il connettore e l'assistente. Vivono in una sola cartella, e conoscere quella cartella è conoscere l'installazione.

---

## La cartella

Tutto ciò che l'installer crea va in un unico posto:

```
%LOCALAPPDATA%\odoo-tool-stack
```

Su una macchina Windows tipica è `C:\Users\<tu>\AppData\Local\odoo-tool-stack`. All'interno, quattro sottocartelle, una per componente, più i file di log. Nulla è sparso sul disco, nessun file viene inserito in `Windows`, e nulla viene registrato oltre al servizio del database e a due scorciatoie.

Quello è una decisione di progettazione deliberata e ha una conseguenza pratica enorme: **disinstallare significa eliminare una cartella.** Una compagnia che prova il sistema a gennaio e lo abbandona a febbraio non lascia un fossile nella macchina per i prossimi cinque anni. Elimina una directory e disinstalla il database.

I dati propri dell'utente—le impostazioni dell'assistente, le sue conversazioni, la configurazione del connettore—vivono separatamente, in `%LOCALAPPDATA%\agent`, in modo che l'aggiornamento o la reinstallazione dello stack non li distruggano.

## Il database

PostgreSQL viene installato nel modo in cui PostgreSQL è destinato a essere installato su Windows: come servizio, con una directory dati propria, in ascolto su una porta. Il servizio significa che parte con la macchina e gira senza che nessuno effettui il login; la directory dati significa che la memoria della compagnia è un insieme di file in un posto noto, che è ciò che rende possibile un backup.

L'installer ha scelto la porta. Voleva la 5432, l'ha trovata occupata dal database all'interno di Windows Subsystem for Linux, e ha preso la 5433. Poi ha fatto tre cose che una persona altrimenti avrebbe dovuto fare a mano:

1. Ha creato un utente del database chiamato `odoo`, con una password, in modo che l'ERP non si connetta mai come superuser. Questa è la differenza tra dare al contabile la chiave dell'ufficio e darle la chiave maestra dell'edificio.
2. Ha creato un database chiamato `odoo`, posseduto da quell'utente.
3. Ha scritto la porta e le credenziali nel file di configurazione dell'ERP.

La password del superuser è `odoo` a meno che la persona che installa non abbia scelto diversamente, e l'installer la stampa nel riepilogo. È un account locale. Non ha nulla a che fare con qualsiasi account su internet, ed è la password che ti servirà se mai dovessi ripristinare un backup a mano.

## L'ambiente Python

Odoo è scritto in Python, e i programmi Python necessitano di librerie. L'installer crea un ambiente isolato—una *virtual environment*—dentro la cartella dello stack, e installa al suo interno esattamente le librerie di cui Odoo ha bisogno, alle versioni che Odoo si aspetta.

La parola "isolato" sta facendo un lavoro reale qui. Senza di essa, installare Odoo cambierebbe il Python che usano altri programmi sulla macchina, e un giorno qualcosa di non correlato smetterebbe di funzionare. Con essa, lo stack porta con sé il proprio Python e non può rompere nulla al di fuori della sua cartella.

Se la macchina non avesse affatto un Python utilizzabile, l'installer ne installava uno per primo—e lo verificava eseguendolo, non cercandolo, perché su una macchina Windows moderna il comando `python` è spesso un annuncio per il Microsoft Store piuttosto che un programma.

## L'ERP

Odoo stesso è una cartella di sorgente Python e un grande insieme di moduli. L'installer ha scaricato la versione in fase di installazione, ha creato lo schema del database, e ha caricato i moduli base—quelli che forniscono il modello di una compagnia: partner, prodotti, documenti, il libro mastro, l'interfaccia web.

Questo è il passo che richiede il più tempo e che sembra il più nulla. Un database sta venendo costruito: centinaia di tabelle, migliaia di regole, lo schema contabile di una compagnia generica, le tasse di un paese generico, i menu di un utente generico. Quando finisce, l'ERP è un programma funzionante che sa come essere una compagnia ma che non conosce ancora quale compagnia sia. È per questo che serve la pagina dei primi passi.

## Il connettore

Il connettore è il piccolo programma che traduce tra l'assistente e l'ERP. Viene installato come plugin—una cartella di file che l'assistente carica all'avvio—e viene configurato con due fatti: l'indirizzo dell'ERP (`http://localhost:8069`) e una chiave.

La chiave viene generata durante l'installazione e scritta nella configurazione del connettore. È una chiave API di Odoo: una credenziale che appartiene a un utente, può essere revocata senza cambiare la password di quell'utente, e trasporta le autorizzazioni di quell'utente. Quando l'assistente chiede a Odoo di creare una fattura, è quella chiave che viaggia con la richiesta, e Odoo la verifica esattamente come verificherebbe il login di una persona.

Questa è la parte dell'architazione su cui il revisore di una compagnia chiederà, e la risposta è rassicurante: l'assistente è un *utente*. Appare nella lista utenti dell'ERP. Ha un ruolo. Ogni record che crea è timbrato col suo nome. Può essere disabilitato con un clic, e la traccia di revisione mostrerà comunque ciò che ha fatto.

## L'assistente

L'assistente arriva come una release pubblica: un eseguibile, una cartella di strumenti, e una chat nel browser. L'installer lo estrae, installa il connettore al suo interno, e crea la scorciatoia **AI Odoo**.

La scorciatoia è il pezzo che fa sentire il sistema un prodotto piuttosto che un progetto scientifico. Facendo doppio clic su di essa si avvia l'ERP se non è in esecuzione, si apre la pagina iniziale nel browser, e si apre l'assistente in una finestra di terminale. Un'icona, e poi due finestre: la pagina che dice dove sta tutto, e la finestra nera dove si scrive. Il lavoro può iniziare.

La configurazione propria dell'assistente—quale fornitore AI, quale modello, quale chiave—viene chiesta al suo primo avvio, dallo stesso assistente, nella stessa finestra di terminale in cui digiterai le tue istruzioni. Quello è un buon posto per chiederlo, perché è l'unico luogo in cui la chiave può essere effettivamente verificata: l'assistente recupera la lista di modelli del fornitore con la chiave che hai incollato, e se la lista torna indietro, la chiave funziona.

---

## Cosa poteva andare sbagliato

Tutto quanto sopra ha funzionato al secondo tentativo. Vale la pena elencare cosa è andato sbagliato al primo, perché ogni elemento è un punto in cui una compagnia che installa questo per davvero perderà un pomeriggio, e ognuno è stato risolto piuttosto che documentato come problema noto.

**Il download che ricominciava.** Descritto nel capitolo precedente: l'installer eliminava il download parziale prima di ogni tentativo, così una linea lenta significava tre fallimenti invece di un unico successo lento. Risolto mantenendo il file parziale, nominandolo secondo la sua versione, e riprendendolo.

**Una lista di versioni che diventa obsoleta.** L'installer conosceva i nomi di file di tre build recenti di PostgreSQL. Il fornitore aveva pubblicato una quarta, che non era sulla lista. Un lettore che installasse tra sei mesi avrebbe incrociato una lista di file che non esistono più. Risolto aggiungendo la build corrente e rendendo il messaggio di fallimento esattamente su quale file recuperare a mano.

**Il messaggio del gestore di pacchetti nella lingua della macchina.** Quando `winget` fallisce, spiega il perché nella lingua di Windows. L'installer ripeteva gli ultimi duecento caratteri di quella spiegazione, e su una console il cui code page non è UTF-8 le lettere accentate arrivavano come spazzatura—così lo schermo mostrava un frammento di italiano, storpiato, in mezzo a un'installazione in inglese. Risolto due volte: la console è ora impostata su UTF-8, e l'installer non ripete più affatto il testo del gestore di pacchetti. Il codice di uscita è il fatto; la riga successiva dice cosa succede invece.

**Il silenzio durante l'installazione del database.** L'installer proprio del database gira senza output, così lo schermo resta fermo per diversi minuti. Questo non è risolto, perché la soluzione sarebbe inventare una barra di avanzamento che mente. Viene invece documentato, qui e nell'appendice: se lo schermo non è cambiato per cinque minuti, guarda la cartella `C:\Program Files\PostgreSQL`—se sta crescendo, l'installazione sta funzionando.

Nessuno di questi è drammatico. Insieme sono la differenza tra una procedura che una persona non tecnica può completare su una connessione pessima e una che finisce con un ticket di supporto.

---

## I due file che vale la pena comprendere

Dentro la cartella del connettore ci sono due piccoli file, e sono l'unica configurazione che una compagnia è probabile tocchi.

**`odoo.json`** contiene l'indirizzo dell'ERP, il nome del database e la chiave. Sono quattro righe di testo. Se l'ERP si sposta su un'altra porta, questo è il file che cambia; se la chiave viene revocata, questo è il file che riceve quella nuova.

**`toolset.json`** contiene la lista di strumenti che l'assistente è autorizzato a usare. Questo è il file che decide se l'assistente può toccare un file, navigare sul web, o solo parlare con l'ERP. È la singola impostazione di sicurezza più importante di tutta l'installazione, ed è una riga di testo.

La prima settimana di Riverton ha prodotto una lezione su quel secondo file che vale la pena raccontare, perché è il genere di cosa che nessun manuale prevede.

L'installer aveva abilitato quattro strumenti: il connettore ERP, uno strumento di file, uno strumento web e uno strumento di controllo versioni. Quello è un default ragionevole per un assistente a uso generale. Ma la prima istazione che la compagnia ha dato—*crea un cliente chiamato Ashfield Academy, Mill Lane, Ashfield*—è stata risposta dall'assistente che andava a cercare l'indirizzo sul web, perché uno strumento web era disponibile e un indirizzo è una cosa che si cerca.

Non era sbagliato, esattamente. Era inutile, era lento, e usava uno strumento che la compagnia non aveva considerato. La soluzione ha richiesto una riga: la toolset è stata ridotta al connettore e allo strumento di file, e l'assistente ha smesso di navigare e ha iniziato a chiedere all'ERP.

Quello è una decisione di progettazione che ogni compagnia deve prendere, e il default dovrebbe essere quello stretto. Un assistente con uno strumento che non gli serve è un assistente che alla fine lo userà, al momento peggiore possibile, per un motivo che è sembrato sensato a un modello linguistico.

C'è una risposta migliore del restringere la lista, però, ed è quella che questo libro raccomanda.

Un modello linguistico sceglie uno strumento leggendo ciò che lo strumento dice di essere per. Se il connettore ERP si descrive come *query e gestione dei dati ERP Odoo* e nient'altro, allora una istazione che contiene le parole "cliente" e "indirizzo" è una corrispondenza justa per una ricerca web—un indirizzo è, dopo tutto, una cosa che si cerca. Il modello non è stupido; è letterale riguardo a due descrizioni egualmente plausibili.

La soluzione è una frase nella descrizione stessa dello strumento, nel punto in cui il modello legge effettivamente: *questo strumento è il sistema di registrazione della compagnia: per qualsiasi domanda o azione su clienti, fornitori, prodotti, prezzi, vendite, acquisti, fatture, pagamenti o scorte, usa questi metodi piuttosto che una ricerca web, un file o conoscenze generali; cerca prima qui un record con nome, e dillo quando non è qui.*

Quella frase è stata aggiunta, i quattro strumenti sono stati rimessi, e il comportamento è cambiato: la stessa installazione, con lo strumento di file, lo strumento web e lo strumento di controllo versioni tutti abilitati, ora risponde "quanti clienti abbiamo" dall'ERP, in un secondo, con il criterio che ha usato e i record dietro il numero.

Due lezioni, e puntano in direzioni opposte.

**Per la compagnia:** non risolvere un problema di instradamento prendendo strumenti via. Un vero ufficio ha bisogno del web, dei file e dell'ERP insieme; un assistente che è stato acciecato per comportarsi è un assistente che fallirà il giorno in cui il lavoro avrà bisogno dello strumento che hai rimosso.

**Per chi scrive la descrizione dello strumento:** la descrizione è l'interfaccia. Viene letta dal modello ad ogni turno, non costa nulla, e una singola frase su *quando usare questo e quando non farlo* vale più di qualsiasi quantità di prompt engineering nell'istruzione. Le regole che contengono appartengono al riassimo dello strumento, in brevi righe imperative—non in un manuale, e non in una nota che il modello non vede mai.

## La forma della cosa

Quando l'installer ha finito, Riverton aveva cinque programmi dove prima aveva un archivio.

Un database, che ricorda. Un ERP, che sa cosa significano i fatti. Un ambiente Python, che fa girare l'ERP. Un connettore, che traduce. Un assistente, che agisce. E una cartella, che contiene tutto ciò e può essere eliminata.

Maggie ha scritto il percorso della cartella sul foglio di carta, sotto la password, e l'ha guardato per un momento. Era una sensazione strana, aver sostituito trentuno anni di carta con una directory nel suo profilo utente—come se la memoria della compagnia fosse diventata una cosa che poteva essere copiata su una chiavetta USB in quaranta minuti.

In realtà poteva essere copiata su una chiavetta USB in quaranta minuti. Questo è ciò che è un backup, ed è l'argomento di una conversazione che avrebbe con Sam tre settimane dopo, dopo la prima paura.

Ma prima dei backup, prima delle fatture, prima di qualsiasi lavoro, c'era una pagina nel browser che chiedeva quale valuta usasse la compagnia.

---

## La prima paura, e cosa è realmente un backup

La paura è arrivata un giovedì, tre settimane dopo, e non era un crash.

Maggie aveva chiesto all'assistente una domanda—quanto abbiamo fatturato il mese scorso?—e la risposta era più piccola di quanto si aspettasse. Non sbagliata, esattamente: più piccola. Ha controllato la lista delle fatture, e c'erano meno fatture di quanto ricordasse di aver approvato.

La causa, quando Sam l'ha trovata, era innocente: Doreen stava sperimentando con un filtro nella lista delle fatture, e il filtro era rimasto attivo. L'assistente ha risposto alla domanda che gli era stata fatta, contro la lista che gli era stata data, e la lista era filtrata. Non era stato eliminato nulla. Non era stato perso nulla.

Ma per venti minuti, Maggie ha creduto che tre settimane di fatturazione fossero scomarse, e la sensazione di quei venti minuti è ciò di cui tratta questa sezione. Perché la seconda domanda che ha fatto, prima di chiedere anything a Sam, era: *abbiamo un backup?*

La risposta, quel giorno, era: non davvero. C'era una copia della cartella del giorno dell'installazione, fatta dallo stesso installer, e nient'altro da allora.

Cosa è un backup, in un sistema come questo, sono tre cose e non una.

**Il database.** Uno dump di tutto ciò che l'ERP conosce, fatto con lo strumento proprio del database, su un programma. È un unico file, può essere ripristinato in un'installazione vuota, ed è l'unica copia che conta per il libro mastro.

**La cartella.** Il sorgente dell'ERP, la configurazione, le impostazioni dell'assistente, la chiave del connettore. Piccola, e tediosa da ricreare a mano, che è esattamente perché vale la pena copiarla.

**Il controllo.** Una volta al mese, ripristina il backup in un'installazione di prova e guardalo. Un backup che non è mai stato ripristinato è un file con un nome speranzoso. La regola di Sam—*un backup non verificato è un desiderio*—deriva dall'aver visto una compagnia scoprire, al momento peggiore possibile, che il suo lavoro notturno stava scrivendo su un disco pieno.

Gli strumenti per tutti e tre sono nella cartella dello stack: uno script che fa lo dump del database, una cartella da copiare, e un documento con le quattro comandi per ripristinare. La versione di Riverton gira alle due di notte, mantiene trenta giorni, e scrive in una cartella che OneDrive sincronizza. Ha richiesto a Sam un'ora per configurarla ed è, di gran lunga, l'assicurazione più economica che la compagnia abbia mai comprato.
