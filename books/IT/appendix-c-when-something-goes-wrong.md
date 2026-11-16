# Appendice C — Quando qualcosa va sbagliato

Questa appendice è organizzata per sintomo, perché è così che i problemi si presentano. Ogni voce indica cosa vedrai, cosa di solito significa e cosa fare. Le voci contrassegnate con *osservate* sono fallimenti accaduti durante la scrittura di questo libro, sull'installazione che ha prodotto le sue schermate; non sono ipotetici.

Prima di tutto, un'abitudine. Quando qualcosa va sbagliato, non reinstallare. Leggi le ultime venti righe del log e guarda quale delle tre caselle sul fazzoletto è infelice: la memoria (il database), il modello (l'ERP) o l'assistente. Nove volte su dieci la risposta ti dice cosa fare, e reinstallare distrugge le prove.

---

## L'installatore si ferma con "psql not found"

**Cosa vedrai.** L'installatore segnala che PostgreSQL non è installato, prova con `winget`, poi prova a scaricare direttamente l'installatore ufficiale, e infine si ferma con un messaggio che dice che `psql` non è stato trovato e che nulla dopo questo passo avrebbe funzionato.

**Cosa significa.** PostgreSQL non è sulla macchina. L'installatore ha provato a le ha installato e non ci è riuscito: o `winget` non è riuscito a raggiungere la sua fonte, oppure il download dal sito del fornitore non è terminato. Su una connessione lenta o instabile questo è il fallimento più comune di tutta la procedura.

**Cosa fare.** Rendi l'installatore di nuovo. Prosegue da dove si è fermato e riutilizza ciò che è già presente; un download parziale è ripreso piuttosto che riavviato, così ogni tentativo arriva più lontano del precedente. Se sei su una connessione più lenta di circa mezzo megabit al secondo, scarica tu stesso l'installatore di PostgreSQL, con un browser, dal sito del fornitore, e posizionalo nella cartella che l'installatore segnala; la prossima esecuzione lo troverà e lo userà. Se preferisci installare PostgreSQL a mano, qualsiasi versione 16.x funziona, e l'installatore lo rileverà alla prossima esecuzione—incluso la sua porta, che legge dal file di configurazione del server stesso.

*Osservato durante la scrittura di questo libro:* la prima esecuzione è fallita esattamente a questo punto, dopo tre tentativi di download, su una connessione che correva a circa sessanta kilobytes al secondo. La seconda esecuzione ha ripreso il file parziale e lo ha completato.

---

## "TCP port 5432 is already in use"

**Cosa vedrai.** All'inizio dell'esecuzione, un avvertimento che la porta 5432 è occupata e che PostgreSQL ascolterà sulla 5433 invece.

**Cosa significa.** Qualcos'altro sulla macchina sta usando la porta standard del database. Spesso è un database dentro Windows Subsystem for Linux, inoltrato verso il lato Windows, o un container Docker.

**Cosa fare.** Niente. L'installatore sceglie la prima porta libera e la porta per tutta la pila—il ruolo del database, il database, l'ERP e il launcher. Questo non è un errore; è l'installatore che fa la cosa giusta su una macchina affollata. Scrivi la porta se hai intenzione di connetterti al database con altri strumenti.

---

## `winget` non può installare nulla

**Cosa vedrai.** Un messaggio che `winget` è uscito con un errore di connessione, seguito dall'installatore che ricorre a un download diretto.

**Cosa significa.** La fonte del pacchetto non era raggiungibile. Le reti aziendali, le reti degli hotel e alcuni prodotti antivirus interferiscono con il Windows Package Manager.

**Cosa fare.** Lascia che il ricorso faccia il suo lavoro. Se entrambe le vie falliscono, installa il componente a mano (PostgreSQL e Python sono le sole due cose che l'installatore necessita dall'esterno), poi rendi l'installatore di nuovo.

---

## L'ERP non risponde sulla sua porta

**Cosa vedrai.** Dopo l'installazione, il browser non raggiunge l'indirizzo stampato alla fine (il default è `http://localhost:8069`), oppure il launcher apre una pagina vuota.

**Cosa significa.** Il processo ERP non è in esecuzione, o è partito e poi si è fermato a causa di un errore nel suo log.

**Cosa fare.** Apri il file chiamato `odoo.log` nella cartella che l'installatore ha creato (di default sotto i dati applicazione locali, in `odoo-tool-stack`). Le ultime righe dicono perché. Le tre cause comuni sono: il servizio del database non è in esecuzione; la password del database nella configurazione non corrisponde più al database; e la porta è occupata da un altro programma. E tre sono risolvibili senza reinstallare.

---

## L'assistente risponde, ma non trova l'ERP

**Cosa vedrai.** Chiedi "elenca i clienti" e l'assistente risponde che non può connettersi, o che la configurazione è mancante.

**Cosa significa.** Il connettore dell'assistente non ha indirizzo, non ha chiave, o una chiave che l'ERP non accetta più. Il connettore legge le sue impostazioni dall'ambiente o da un piccolo file nella cartella dati dell'assistente.

**Cosa fare.** Controlla che l'ERP sia in esecuzione e raggiungibile in un browser prima. Poi controlla la chiave: nell'ERP, apri il menu utente, vai alla pagina di sicurezza dell'account, e crea una nuova chiave API. Incollala nella configurazione del connettore. Se hai cambiato la password dell'utente ERP, le chiavi esistenti di solito sopravvivono; se hai cancellato e ricreato l'utente, non lo fanno.

---

## L'assistente crea un cliente duplicato

**Cosa vedrai.** Due clienti chiamati quasi allo stesso modo: "Ashfield Academy" e "Ashfield Academy Ltd."

**Cosa significa.** L'assistente è stato chiesto di creare un cliente e ha fatto ciò che gli era stato ordinato. Non decide automaticamente che un nome simile è la stessa azienda, e non dovrebbe: due diramazioni della stessa organizzazione possono legittimamente essere due registrazioni.

**Cosa fare.** Formula l'istruzione per cercare prima—"trova il cliente Ashfield e aggiungi un contatto"—o chiedi all'assistente di mostrarti le corrispondenze prima di creare qualcosa. Quando un duplicato appare, uniscilo o archivialo nell'ERP piuttosto che cancellarlo, così che la storia delle fatture resti intatta.

---

## Un documento non può essere pubblicato

**Cosa vedrai.** L'ERP rifiuta di pubblicare una fattura, o una consegna, e mostra un messaggio su un account mancante, una tassa mancante, o un periodo che è chiuso.

**Cosa significa.** Il modello è incompleto. Un prodotto non ha un account di reddito, o l'azienda non ha una tassa configurata, o il periodo contabile è stato bloccato.

**Cosa fare.** Leggi il messaggio; nomina il campo. Correggi la configurazione nelle impostazioni dell'ERP, poi pubblica di nuovo. Questo è l'ERP che fa il suo lavoro: rifiuta di scrivere una voce che Pacioli non riconoscerebbe.

---

## Tutto è lento

**Cosa vedrai.** Le schermate impiegano secondi a caricarsi; l'assistente impiega molto tempo a rispondere.

**Cosa significa.** Due cose diverse, di solito confuse. Se le schermate ERP sono lente, il problema è locale: il database, il disco, o la memoria della macchina. Se solo l'assistente è lento, il problema è il modello linguistico—o il servizio remoto, o il modello locale se ne esegui uno.

**Cosa fare.** Guardala prima la memoria e il disco della macchina. Poi guarda il log dell'assistente: registra quanto tempo ha preso ogni richiesta e quali strumenti sono stati chiamati. Una singola richiesta che impiega trenta secondi perché ha fatto dodici chiamate di strumento non è un difetto; è una richiesta che avrebbe dovuto essere formulata più strettamente.

---

## Hai perso la password dell'amministratore

**Cosa significa.** La password stampata alla fine dell'installazione non è stata scritta.

**Cosa fare.** Su un'installazione self-hosted tu sei il proprietario della macchina, così puoi resettarla dal database. Ferma l'ERP, connettiti al database con l'account amministratore del database stesso, e imposta una nuova hash password per l'utente amministratore. La procedura è documentata nella documentazione dell'ERP stesso sotto "reset the administrator password", e impiega due minuti. Non cancellare il database per risolvere un problema di password.

---

## La sola regola

Qualsiasi cosa succeda, tieni due cose: il file di log, e una copia del database prima del cambiamento. Con quelle due, quasi qualsiasi problema può essere diagnosticato e la maggior parte può essere annullata. Senza di esse, ogni problema diventa una discussione su cosa usava essere vero.
