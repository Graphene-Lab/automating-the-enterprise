# 7. Un file e un doppio clic

La scrivania di scarto a Riverton dava su una finestra che si affacciava sul cortile dove venivano caricate le furgonette.
Maggie l'aveva liberata lei stessa, cioè aveva spostato quattro scatole di cataloghi sul pavimento e pulito la scrivania con un panno che non era del tutto pulito. Sopra vi pose un laptop, una tazza, e un foglio di carta con tre righe scritte.

Sam Okafor guardò il foglio.

"È questo?"

"È questo."

Le tre righe erano: *nome dell'azienda, email dell'amministratore, password dell'amministratore*. Tutto il resto, aveva deciso, la macchina poteva calcolarlo da sé.

---

Prima del doppio clic, ci sono quattro cose che un'azienda deve verificare, e nessuna di esse è tecnica.

**Un computer che non sta facendo nient'altro.** Lo stack esegue tre programmi insieme—il database, l'ERP e l'assistente—e su un laptop affollato competiranno con qualsiasi altra cosa aperta. Riverton usava una macchina che era stata acquistata per lo shop web e mai usata per quello. otto gigabyte di memoria bastano; sedici sono comodi; il disco vuole circa dodici gigabyte liberi prima che l'installatore parta, e li verifica.

**Una connessione a internet, una volta.** L'installatore scarica le parti di cui ha bisogno. Da quel momento il sistema funziona senza connessione, salvo il modello linguistico, che è un servizio in un altro edificio (o su un'altra macchina tua, se preferisci).

**Il permesso di installare.** Su Windows il motore del database installa un servizio, e ciò richiede i diritti di amministratore. Se l'account che usi non li ha, l'installatore lo dice alla fine anziché fallire silenziosamente, e una seconda esecuzione con l'account giusto finisce il lavoro.

**Un nome d'azienda.** Non necessariamente il nome legale—il nome che vuoi vedere in cima alle tue fatture. Riverton usava "Riverton Office Supply", che è così la chiamano i suoi clienti.

Questa è l'intera lista. Non c'è una password del database da inventare, non c'è una porta da scegliere, non c'è un file di configurazione da modificare. L'installatore assegna da sé la password dell'utente super del database, la stampa alla fine, e sceglie una porta libera se quella standard è occupata. Il fornitore dell'AI viene chiesto in seguito, dall'assistente, al primo avvio—dove una chiave può effettivamente essere testata contro il servizio che l'ha emessa.

---

Il file si chiama `install.bat`, ed è uno dei pochi pensieri genuinamente buoni nella storia della distribuzione del software aziendale: un singolo file di testo, abbastanza piccolo da essere inviato per email, che sa come recuperare tutto il resto.

Maggie vi fece doppio clic. Si aprì una finestra nera, con una barra del titolo che recava *OdooTool installer*, e la prima cosa che fece fu porre una domanda.

Non una domanda tecnica. Stampò quattro intestazioni—*Domande*, *Spazio libero*, *Verifica di PostgreSQL, Python e Git*—e sotto *Domande* elencò ciò che si sarebbe accinto di chiedere. In una esecuzione non assistita non c'era nulla da digitare, perché le tre risposte erano nell'ambiente; in una esecuzione ordinaria avrebbe chiesto il nome dell'azienda e nient'altro.

C'è una decisione di progetto nascosta in quell'ordine, ed è vale la pena notarla perché è la differenza tra un installatore in cui la gente si fida e uno che abbandona. Le intestazioni vengono *prima* del lavoro: l'installatore ti dice ciò che si accinge di chiedere, poi ciò che ha trovato, poi ciò che si accinge di fare. Non si scopre nulla a metà strada, quando è troppo tardi per cambiare idea. Una persona che legge la prima schermata conosce la forma delle prossime quaranta minuti.

La finestra stessa è volutamente semplice—testo bianco su nero, nessuna barra di avanzamento, nessun logo, nessuna animazione. Ciò non è pigrizia. Una finestra di console che stampa una riga per ogni evento reale è una finestra il cui output può essere *letto*, copiato in una email, e confrontato con l'esecuzione di un'altra persona. Gli installatori che nascondono il loro output dietro un cerchio che gira sono quelli che non possono essere diagnosticati quando si fermano.

La seconda intestazione era il disco: *Spazio libero su C: 79,53 GB*. L'installatore rifiuta di partire sotto i dodici gigabyte, che è una decisione presa da chi ha visto fallire un'installazione al novanta per cento e ha dovuto spiegare perché.

La terza intestazione produsse due righe che valgono la pena di capire, perché sono il genere di cose che fanno pensare che un computer sia rotto.

```
! La porta TCP 5432 è già in uso su questo PC; il nuovo PostgreSQL ascolterà sulla 5433 invece.
PostgreSQL non è installato. È installato ora con la password dell'utente super 'postgres' impostata su 'odoo'.
```

La prima riga non è un errore. È la rendicontazione di qualcosa di ordinario: un altro programma sulla macchina—in questo caso un database dentro Windows Subsystem for Linux, instradato verso il lato Windows da un piccolo aiuto chiamato `wslrelay`—era già in uso sulla porta standard di PostgreSQL. Le porte sono numeri di porte, e solo un programma può ascoltare dietro ogni porta. L'installatore cercò la prima porta libera dopo la 5432, trovò la 5433, e decise di usarla per tutto—il database, l'ERP, e il lanciatore. Nessuno deve ricordare il numero; l'installatore lo scrive dove deve essere scritto.

La seconda riga è l'installatore che dice ciò che sta per fare, e—questo è il punto che conta per una piccola azienda—che sta per scegliere la password del database da sé. La password è `odoo`, è un account locale su questo PC, e non ha nulla a che fare con qualsiasi account su internet. L'installatore la stampa alla fine così che il proprietario della macchina possa trovarla in seguito.

---

Poi cominciò l'attesa, e l'attesa è dove questo capitolo guadagna il suo posto nel libro, perché il primo tentativo fallì.

L'installatore provò prima il gestore di pacchetti di Windows, che è il modo educato di installare software su Windows. Il gestore di pacchetti non poteva raggiungere la sua fonte—una rete aziendale, una rete di hotel o un prodotto antivirus faranno questo—e restituì un errore. L'installatore lo disse, in una riga, e ricorse al download dell'installatore ufficiale del database direttamente. Quella è la comportamento corretto, ed è per questo che la cosa successiva sullo schermo fu un download.

Il download era lento. Non "un poco lento": sessanta kilobyte al secondo, su una linea che era stata misurata a quattrocento. L'installatore del database è trecento ottantasei megabyte, che a quella velocità è un'ora e tre quarti, e la connessione cadde tre volte prima che il file fosse completo. Ogni caduta ricominciava il trasferimento da zero, perché era così che il codice faceva in quel momento, e dopo il terzo tentativo l'installatore desistì e stampò la frase che manda la gente a un forum di supporto:

> PostgreSQL non poteva essere scaricato (sia winget che il download diretto hanno fallito). Installalo tu stesso da enterprisedb.com e riesegui questo installatore.

Questa è la prima colpa genuina di questo libro, ed è vale la pena essere precisi su cosa fosse sbagliato, perché non era la rete.

L'installatore usava già `curl`, che può riprendere un trasferimento parziale. Ma cancellava il file parziale prima di ogni tentativo, così il riprendere non aveva nulla da riprendere. Su una connessione veloce nessuno avrebbe mai notato. Su una lenta, trasformava un download di trenta minuti in tre fallimenti di mezz'ora.

La correzione è tre righe di pensiero e una dozzina di righe di codice: mantenere il file parziale, nominarlo dopo la versione a cui appartiene così che non possa mai essere confuso con un altro, e chiedere a `curl` di continuare da dove si era fermato (`-C -`). Un file che è già della giusta dimensione è riutilizzato senza alcun trasferimento, e un file che è *più grande* della dimensione dichiarata è scartato, perché non può essere un prefisso di quello reale.

Con quel cambiamento, la seconda esecuzione dell'installatore stampò una singola riga e proseguì:

```
==> riutilizzo del download verificato di 16.16-1
```

Quella riga è l'intera differenza tra un prodotto e un prototipo. La prima versione chiedeva all'utente di risolvere un problema di rete. La seconda versione lo risolse e lo disse in sette parole.

Mentre il database si installava—trecento novanta megabyte da decomprimere, che richiede pochi minuti su un disco ordinario—l'installatore non stampò nulla, perché non c'era nulla da stampare. Aspettava che l'installatore stesso del database finisse, e l'installatore del database è silenzioso per progetto. Una barra di avanzamento sarebbe stata più bella. Il silenzio, almeno, era onesto.

---

Il database finì. L'installatore verificò che poteva raggiungerlo, con la password che aveva assegnato, e stampò una riga per dirlo. Poi si voltò verso Python.

Python è il linguaggio in cui Odoo è scritto, e l'approccio dell'installatore verso di esso è l'approccio di un buon collega: se una versione utilizzabile è già lì, usala; se non lo è, installane una. Su Windows ciò è più delicato di quanto sembri, perché il comando `python` su una macchina moderna è spesso non Python affatto ma un annuncio del Microsoft Store—un piccolo adattamento che apre il Store quando digiti `python`. Un installatore che si fida del comando non installerà nulla e poi fallirà misteriosamente in seguito. Questo lo esegue e verifica la risposta, che è l'unico test affidabile.

Poi recuperò Odoo stesso—una copia del sorgente della versione in installazione—e i pacchetti Python di cui ha bisogno, e creò il database, e caricò i moduli base. Ognuno di quei passaggi stampa una riga, e ogni riga è un piccolo pezzo di rassicurazione: *sta ancora procedendo, e procede nella direzione giusta.*

L'ultimo passo fu l'assistente: scaricare la release pubblica, decomprimerla, installare il connettore che gli permette di parlare con l'ERP, scrivere l'indirizzo dell'ERP e una chiave appena generata nella configurazione del connettore, e avviare l'ERP.

Poi la finestra stampò un riassunto. È vale la pena citarlo, perché è l'unica parte dell'installazione che un utente deve conservare.

```
==> Fatto

Odoo:          http://localhost:8069
Amministratore: admin@riverton.example
Password:      OdooDemo2026
Database:      odoo sulla porta 5433
Assistente:    AI Odoo (icona desktop)
```

Tre di quelle righe sono quelle che Maggie scrisse sul foglio di carta e pose nel cassetto con la salvietta: l'indirizzo, l'utente, la password. La quarta è la porta, che non aveva bisogno di conoscere, e la quinta è l'icona che avrebbe fatto doppio clic ogni mattina per l'anno successivo.

## Cosa l'installatore non farà

È vale la pena dire chiaramente cosa lo script lascia a te, perché un'azienda che si aspetta che l'installatore produca un'azienda funzionante sarà delusa in un'ora.

Non farà **scegliere il tuo piano dei conti**, oltre a installare quello che usa il tuo paese. I conti che la tua azienda realmente necessita—trasporto a carico, trasporto pagato, le due o tre spese che contano—sono una conversazione con il tuo ragioniere.

Non farà **inserire i tuoi prodotti, clienti o scorte**. Quelle sono le fattui della tua azienda, e nessun altro le ha.

Non farà **decidere chi può fare cosa**. Crea l'amministratore e l'utente dell'assistente; il resto è un giudizio sulla tua gente.

Non farà **configurare il fornitore dell'AI per te** oltre a scrivere l'indirizzo e la chiave che gli hai dato in anticipo; in una esecuzione ordinaria, l'assistente chiede al primo avvio.

E non farà **fare il backup dei tuoi dati**, perché in quel momento in cui si esegue non c'è alcun dato da fare il backup. Quella è la prima cosa da configurare in seguito, e il capitolo otto spiega come.

Il lavoro dell'installatore è stretto ed è fatto bene: mette le tre macchine nella stanza, le collega insieme, e stampa le tre fattui di cui hai bisogno per accedere. Tutto dopo quello è il lavoro di cui questo libro parla.

---

C'è un piccolo pezzo di teatro alla fine che è facile trascurare e che ti dice qualcosa sulle persone che hanno scritto l'installatore. Finito, apre la pagina dei primi passi dell'ERP nel browser. Non l'assistente, non una pagina di marketing: la pagina in cui a una nuova azienda si chiede quale valuta usa, come dovrebbe apparire il suo piano dei conti, e cosa vende.

Il messaggio è: non hai finito, sei appena arrivato. La prossima ora è configurazione, ed è l'ora che decide se il sistema diventa la verità o diventa un altro programma abbandonato. L'installatore non può fare quella parte per te, e non finge di farlo.

Maggie sedette davanti alla pagina dei primi passi per un lungo momento. Poi chiamò Doreen, perché il piano dei conti sarebbe stato un'argomentazione, ed era meglio avere l'argomentazione con la persona che aveva tenuto i conti per trentuno anni che averla con un consulente.

Quella conversazione è il prossimo capitolo.
