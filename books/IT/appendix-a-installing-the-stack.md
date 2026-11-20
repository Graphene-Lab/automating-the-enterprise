# Appendice A — Installazione dello stack, passo dopo passo

Questa appendice è l'installazione senza la storia: la stessa procedura del capitolo sette, scritta come elenco che puoi seguire a libro chiuso. Presume Windows 10 o 11; la procedura Linux è lo stesso script con un nome diverso, e l'installer è progettato per comportarsi identicamente.

## Prima di iniziare

| Requisito | Perché | Come verificare |
|---|---|---|
| Windows 10 o 11, 64-bit | il motore del database e l'assistente sono programmi Windows | Impostazioni → Sistema → Informazioni |
| Circa 12 GB di spazio libero | database, sorgente ERP, pacchetti Python, assistente | Esplora file → Questo PC |
| Un account amministratore | il database installa un servizio Windows | l'installer lo dice alla fine se manca il diritto |
| Una connessione a internet | le parti vengono scaricate una volta | qualsiasi browser |
| Un nome di azienda | compare sui tuoi documenti | decidilo ora |

**Non** ti serve: una password del database, un numero di porta, .NET, Git, Docker, un'installazione di Python o qualsiasi conoscenza della riga di comando.

## Passo 1 — Procurarsi l'installer

Scarica `install.bat` dalla pagina delle rilasci di OdooTool e mettilo in una cartella vuota, per esempio
`C:\Users\<tu>\Downloads\odoo-install\`.

Il file è di pochi kilobyte. Scarica il resto di sé stesso se deve, quindi funziona anche quando
arriva da solo.

## Passo 2 — Esegui

Fai doppio clic su `install.bat`. Si apre una finestra di console con il titolo *Installer di OdooTool*.

Se Windows chiede il permesso di apportare modifiche, concedilo: il database deve registrare un servizio.

## Passo 3 — Rispondi alle domande

In una esecuzione normale l'installer chiede il **nome di azienda** e accetta il valore predefinito suggerito
per tutto il resto premando Invio. In una esecuzione non assistita le risposte possono essere date in anticipo tramite
variabili d'ambiente, e l'installer non chiede nulla.

L'installer stampa un'intestazione chiamata *Domande* con le risposte che intende usare, così puoi
vedere cosa ha deciso prima che inizi a lavorare.

## Passo 4 — Osserva le quattro fasi

Lo schermo stampa una intestazione per fase. Ogni intestazione è seguita da righe che dicono cosa sta
avvenendo; non c'è nulla da digitare.

1. **Spazio libero.** Rifiuta di iniziare sotto i dodici gigabyte.
2. **Verifica di PostgreSQL, Python e Git.** Riporta ciò che ha trovato e ciò che installerà.
3. **Installazione.** La parte lunga: il database, il runtime di Python se serve, la sorgente ERP, i
   pacchetti Python, il database stesso, l'assistente, il connettore.
4. **Sintesi.** Indirizzi, credenziali e ciò che manca ancora, se qualcosa manca.

Due messaggi durante la fase 2 sono normali e non sono errori:

- *La porta TCP 5432 è già in uso; il nuovo PostgreSQL ascolterà sulla 5433 invece.* Qualcos'altro
  sulla macchina detiene la porta standard. L'installer sceglie la prossima libera e la usa
  ovunque.
- *PostgreSQL non è installato. Viene installato ora con la password del superuser 'postgres' impostata su
  'odoo'.* La password è assegnata dall'installer, è locale a questa PC, ed è stampata alla
  fine. Non c'è nulla da ricordare o da cercare.

## Passo 5 — Se lo scaricamento è lento

L'installer del database è di circa 390 MB e proviene dal sito dello stesso produttore. Su una linea lenta lo
scaricamento può richiedere un'ora o fallire. L'installer conserva il file parziale e lo riprende alla prossima
esecuzione, quindi **rieseguirlo è la risposta corretta**—continua da dove si è fermato e riutilizza ciò
che è già presente.

Se la macchina non può raggiungere il produttore per niente, scarica da te l'installer di PostgreSQL 16 per Windows
da enterprisedb.com, lascialo nella cartella che l'installer riporta, ed esegui di nuovo `install.bat`.
Lo troverà e ne verificherà la dimensione prima di usarlo.

## Passo 6 — Conserva la sintesi

Alla fine la finestra stampa qualcosa come questo. Scrivilo, o fai la foto dello schermo.

```
  Odoo (l'ERP, nel browser):  http://localhost:8069
  Login: admin@yourcompany.example
  Password: (quella che l'installer ha generato, o quella che gli hai dato)
  Assistente (parlagli qui):  http://localhost:5290/OfficeManager
```

Se l'account amministratore esisteva già da un'esecuzione precedente, l'installer stampa il login che
c'è davvero nel database e dice che la password è invariata, invece di inventarne una nuova che non
funzionerebbe.

Il browser apre la **pagina iniziale**: un file su questo computer con l'indirizzo, l'account e un
link. Quella pagina è l'inizio della configurazione, non la fine dell'installazione.

## Passo 7 — L'icona, e le tre finestre

Fai doppio clic sull'icona **AI Odoo** sul desktop. Avvengono tre cose:

1. l'ERP parte, se non era in esecuzione;
2. la pagina iniziale si apre nel browser;
3. l'assistente si apre nella propria finestra nera.

*Apri Odoo* sulla pagina iniziale porta alla pagina di accesso su
`http://localhost:8069/web/login?db=odoo_agent`. L'assistente è la finestra nera, ed è lì che si
scrive; va lasciata aperta mentre lavori, perché chiuderla ferma l'assistente, mentre Odoo continua a
girare.

Al suo primo avvio l'assistente chiede il fornitore AI: scegli il servizio, incolla la chiave, e
recupera l'elenco dei modelli di quel servizio. Non serve nient'altro—l'indirizzo dell'ERP e la
chiave di accesso sono stati scritti dall'installer.

## Passo 8 — Verifica che funzioni

Tre verifiche, in ordine, e ciascuna ti dice quale delle tre macchine è insoddisfatta se fallisce.

1. **L'ERP.** Clicca *Apri Odoo* sulla pagina iniziale, o apri
   `http://localhost:8069/web/login?db=odoo_agent` in un browser, ed entra. Se la pagina non si
   carica, l'ERP o il database non sono in esecuzione; il file `odoo.log` nella cartella di
   installazione dice perché.
2. **Il connettore.** Nell'assistente, chiedi: *verifica la connessione a Odoo e dimmi quale versione
   è in esecuzione.* Un numero di versione significa che la chiave e l'indirizzo sono corretti.
3. **Il modello.** Chiedi: *quanti clienti abbiamo?* Un numero significa che l'assistente può leggere i
   dati dell'ERP come il suo utente, con i permessi di quell'utente.

Se tutte e tre rispondono, l'installazione è completa.

## Disinstallazione

Due script annullano l'installazione, e sono il modo supportato: `uninstall.bat` su Windows e
`uninstall.sh` su Linux. Stanno accanto all'installer nella stessa release, e ciascuno può essere
scaricato ed eseguito da solo.

Cosa rimuovono:

- il database di Odoo, con ogni cliente, prodotto, ordine, fattura e movimento di magazzino dentro;
- la cartella di installazione (`%LOCALAPPDATA%\odoo-tool-stack`, o `~/odoo-tool-stack`);
- le scorciatoie **AI Odoo** e la regola del firewall.

Chiedono due volte, e la seconda domanda non è una formalità. La prima è un sì/no che elenca cosa
sparisce. La seconda richiede la frase **DESTROY ALL**, scritta in maiuscolo. Se la frase non è
esatta, non viene toccato niente—non un file, non una riga. La cancellazione è irreversibile e
l'uninstaller non fa nessun backup, quindi una copia del database presa prima è l'unica via di
ritorno.

AgentBridge viene chiesto a parte, perché può ospitare altri strumenti e tiene le proprie
impostazioni e chiavi API: rispondere *no* lo conserva e rimuove solo la metà Odoo.

PostgreSQL resta installato. È un servizio che altri programmi possono condividere, e si rimuove da
*App e funzionalità* come qualunque altro programma, quando nient'altro ne ha bisogno. Il ruolo
database `odoo` resta ed è innocuo: una futura installazione lo riusa.
