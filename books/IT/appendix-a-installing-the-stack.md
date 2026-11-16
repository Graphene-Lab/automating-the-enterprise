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
Odoo:          http://localhost:8069
Amministratore: admin@yourcompany.example
Password:      (quella che l'installer ha generato, o quella che gli hai dato)
Database:      odoo sulla porta 5433
Assistente:     AI Odoo (icona del desktop)
```

Il browser apre la pagina dei primi passi dell'ERP. Quella pagina è l'inizio della configurazione, non
la fine dell'installazione.

## Passo 7 — Primo avvio dell'assistente

Fai doppio clic sull'icona **AI Odoo** sul desktop. Avvengono due cose: l'ERP inizia (se non era
in esecuzione) e l'assistente si apre nella propria finestra di terminale. Il browser apre la pagina dell'ERP.

Al suo primo avvio l'assistente chiede il fornitore AI: scegli il servizio, incolla la chiave, e
questo recupera l'elenco dei modelli di quel servizio. Non serve nient'altro—l'indirizzo dell'ERP e la
chiave di accesso sono stati scritti dall'installer.

## Passo 8 — Verifica che funzioni

Tre verifiche, in ordine, e ciascuna ti dice quale delle tre macchine è insoddisfatta se fallisce.

1. **L'ERP.** Apri `http://localhost:8069` in un browser ed entra. Se la pagina non si carica,
   l'ERP o il database non sono in esecuzione; il file `odoo.log` nella cartella di installazione dice perché.
2. **Il connettore.** Nell'assistente, chiedi: *verifica la connessione a Odoo e dimmi quale versione
   è in esecuzione.* Un numero di versione significa che la chiave e l'indirizzo sono corretti.
3. **Il modello.** Chiedi: *quanti clienti abbiamo?* Un numero significa che l'assistente può leggere i
   dati dell'ERP come il suo utente, con i permessi di quell'utente.

Se tutte e tre rispondono, l'installazione è completa.

## Disinstallazione

Lo stack vive in una cartella, `%LOCALAPPDATA%\odoo-tool-stack`, più il servizio del database e i
dati utente in `%LOCALAPPDATA%\agent`. Per rimuoverlo:

1. Ferma l'ERP e l'assistente (chiudi le loro finestre).
2. Disinstalla PostgreSQL da *App e funzionalità* (o esegui il suo disinstallatore), ed elimina la cartella che
   lascia in `C:\Program Files\PostgreSQL` se qualcosa resta.
3. Elimina `%LOCALAPPDATA%\odoo-tool-stack` e `%LOCALAPPDATA%\agent`.
4. Elimina la scorciatoia **AI Odoo** dal desktop e dal menu Start.

Questa è l'intera rimozione. Non c'è nulla registrato altrove, il che è uno dei vantaggi di un
sistema che gira sulla tua macchina.
