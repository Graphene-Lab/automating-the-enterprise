# 10. Insegnare al sistema la forma dell'azienda

L'argomento sul piano dei conti è durato due giorni ed era, in fondo, una questione su
Riverton fosse un negozio di cancelleria o una azienda.

Il piano dei conti è la lista di contenitori nei quali un'azienda ordina i propri soldi. Ogni libra che
si muove viene inserita in uno di essi: vendite di merci, vendite di servizi, trasporto ad addebitare, trasporto a pagare, stipendi, affitto, elettricità, spese bancarie, magazzino, debiti verso clienti, crediti verso fornitori, IVA. Un'piccola azienda ha forse
quaranta contenitori; una grande ne ha quattrocento; la differenza non è sofisticazione, è il numero
di domande che i conti devono rispondere.

Doreen voleva quaranta. Maggie voleva dodici.

"Non è una questione di volerlo", disse Doreen, il secondo mattino, con la pazienza di chi
spiega qualcosa per la terza volta. "Se non posso separare il trasporto che addebitiamo dal
trasporto che paghiamo, non posso dirti se le consegne fanno soldi."

"Non puoi guardare le fatture?"

"No, senza leggere quattrocento fatture."

Quello, Maggie lo ammise, era un punto giusto, ed è la regola che risolve ogni discussione su un
piano dei conti: **un contenitore si guadagna il posto se c'è qualcuno che farà una domanda che solo quel contenitore può rispondere.** Trasporto ad addebitare e trasporto a pagare si guadagnano il loro. "Spese varie" non lo fa; è un
contenitore che esiste affinché nessuno debba decidere, ed diventa il luogo dove i soldi di un'azienda
vanno a essere dimenticati.

---

## Ciò che il sistema porta con sé

Odoo non ti chiede di inventare un piano dei conti. Ti chiede in quale paese ti trovi, e poi
installa il piano che i contabili di quel paese si aspettano—lo stesso numerazione, gli stessi
nomi, gli stessi codici fiscali—affinché il revisore riconosca il luogo, e affinché la dichiarazione
dei redditi abbia un luogo da cui provenire.

Per Riverton ciò significava installare la localizzazione contabile del Regno Unito. È una di un
cento di tali pacchetti; l'installatore aveva già scaricato il codice, ed attivarlo ha richiesto
un minuto nella schermata *Apps*.

![La schermata delle Apps, dove si installa una localizzazione](../../assets/screens/odoo-04-apps.png)

Quando ha finito, il modulo di contabilità aveva un piano dei conti, un insieme di tasse, quattro
registri e un anno fiscale. Nessuno di ciò era ancora di Riverton, e tutto ciò era un punto di
partenza ragionevole—che è esattamente ciò che un piano dei conti dovrebbe essere.

![Il piano dei conti, così come installato dalla localizzazione](../../assets/screens/odoo-05-chart-of-accounts.png)

I conti sono numerati, e la numerazione non è arbitraria. La prima cifra è la classe:
1 per le attività, 2 per le passività, 3 per l'utile, 4 per i ricavi, 5 per le spese, 6 per il costo delle
merci. Un contabile che legge un bilancio di verifica può dire a un sguardo il tipo di numero che sta
guardando, in qualsiasi azienda del paese, senza conoscere l'azienda.

Doreen passò in rassegna la lista con una matita, e fece tre cose.

**Non cancellò nulla.** Un conto senza attività non costa nulla, e cancellarne uno che un
revisore si aspetta di trovare è una conversazione che nessuno vuole.

**Rinominò quattro conti** per farli corrispondere alle parole che Riverton usa davvero. Il sistema chiamava uno "Mercanzia"; Riverton lo chiama "Magazzino — acquistato". Il nome sullo schermo deve essere il nome nella
conversazione, altrimenti le persone non lo useranno.

**Aggiunse due conti:** uno per il trasporto ad addebitare ai clienti, uno per il trasporto a pagare
ai vettori. Erano le due domande che voleva rispondere, e ora poteva.

## Le tre domande che decidono il piano dei conti

Doreen e Maggie risolsero la loro discussione con tre domande, ed vale la pena scriverle
perché funzionano per qualsiasi azienda.

**Cosa chiederai ogni mese?** Le risposte diventarono conti: vendite di merci, vendite di trasporto,
acquisti di merci, acquisti di trasporto, stipendi, affitto. Qualsiasi cosa che nessuno chiederà non
ebbe un conto.

**Cosa deve vedere l'ufficio fiscale separatamente?** Le risposte erano poche—vendite a tariffa
standard, vendite a tariffa zero, esente—e non sono opzionali. Un piano dei conti che non può produrre
le caselle sulla dichiarazione è un piano dei conti che sarà ricostruito nel panico.

**Cosa chiederebbe un revisore per primo?** Le risposte erano la banca, i debiti verso clienti, i
crediti verso fornitori e il magazzino. Quattro devono essere puliti, riconciliati e comprensibili a un
sguardo, perché sono dove si trova il denaro.

Seicento conti uscirono da quelle tre domande, più i conti fiscali che la localizzazione aveva già
creato. È un piano dei conti più piccolo di quello che traccerebbe un contabile e più grande di quello
che un contabile con un foglio di calcolo avrebbe bisogno, che è giusto così.

## Le impostazioni facili da trascurare, e che costano di più

Cinque impostazioni sul modulo dell'azienda sono facili da saltare e costose da scoprire più tardi,
perché compaiono su ogni documento che lascia l'edificio.

**Il logo.** Piccolo, ed la prima cosa che un cliente nota. Un'azienda che invia fatture con il logo
default di Odoo ha detto al cliente qualcosa circa quanto attenzione presta.

**I dati bancari.** Vanno nel piè di pagina di ogni fattura. Un'azienda che li aggiunge a mano a
ogni documento finirà per aggiungere il conto sbagliato a uno di essi, ed è una conversazione con
un cliente che ha pagato l'azienda sbagliata.

**I termini di pagamento predefiniti.** Trenta giorni, o fine mese successivo, o quattordici giorni. Impostarli
sull'azienda significa che ogni nuovo cliente li eredita, e le eccezioni sono le eccezioni
invece della regola.

**Le tasse predefinite.** La tasse applicata a un nuovo prodotto se nessuno ne sceglie una. Se questo
è sbagliato, ogni nuovo prodotto è sbagliato, e l'errore è invis finché non arriva la prima
dichiarazione.

**La fine dell'anno fiscale.** La maggior parte delle aziende usa l'anno solare, e alcune non lo fa. L'impostazione decide
quando l'anno si chiude, ed cambiarla più tardi è una operazione genuinamente dolorosa.

Nessuno di ciò è difficile, e tutti sono il tipo di cosa che si salt su un pomeriggio affollato
e si scopre a marzo. La regola che salva il pomeriggio: **compila il modulo dell'azienda come se
un cliente lo vedrà, perché un cliente lo vedrà.**

## Le tasse

Una tasse in un ERP non è una percentuale. È una piccola macchina con un ingresso e un'uscita: prende
una riga di una fattura, calcola la tasse, decide su quale conto va la tasse, e ricorda il periodo
a cui appartiene affinché la dichiarazione possa essere prodotta.

La localizzazione installò le tariffe standard: venti per cento sulla maggior parte delle merci, cinque
per cento su alcune (come i seggiolini per bambini e certi materiali per il risparmio energetico), zero
su libri e sulla maggior parte del cibo. Riverton vende cancelleria, che è a tariffa standard, e carta,
che è a tariffa standard, e un servizio occasionale, che è sempre a tariffa standard. La tariffa di cinque
per cento c'è e sarà quasi mai usata, che va bene; la cosa importante è che esiste, affinché nessuno
inventi una quarta tariffa al bancone.

C'è una trappola vale la pena nominare, perché intrappola le aziende ogni anno: **la tasse è configurata
per prodotto, non per fattura.** Se un prodotto è impostato sulla tasse sbagliata, ogni fattura che lo
contiene sarà sbagliata, e l'errore sarà trovato dall'ufficio fiscale invece che dal cliente. Il modulo
del prodotto ha un campo per esso, e compilare quel campo correttamente una volta vale più di qualsiasi
quantità di controlli più tardi.

## I registri

Il denaro arriva e lascia attraverso un piccolo numero di porte, ed Odoo le chiama registri: *Fatture
Clienti*, *Fatture Fornitori*, *Banca*, *Cassa*, *Operazioni Varie*. Ogni registro ha un codice—INV,
BILL, BNK, CSH, MISC—e ogni documento registrato attraverso di esso ottiene un numero in sequenza.

La sequenza conta più di quanto sembri. Il numero di una fattura deve essere unico e deve seguire
il precedente, perché è ciò che rende il libro auditable: se la fattura 2026/0042 manca, un revisore
chiederà dove è finita. Odoo impone ciò rifiutandosi di registrare un documento che romperebbe la
sequenza, che è una delle piccole severità che rendono il sistema vale la pena avere.

## Ciò che non fu configurato, e perché

C'è una lunga lista di cose che un'azienda *può* configurare il primo giorno, e quasi tutte
dovrebbero aspettare.

**Valuta multipla.** Riverton compra da un fornitore nella zona euro, quindi alla fine sì. Il primo
giorno, no: i tassi di cambio, i guadagni e le perdite, e il trattamento delle fatture in valuta
straniera sono un argomento a sé, e farle prima che la fatturazione di base funzioni è come un'azienda
si ritrova con un libro che nessuno capisce.

**Contabilità analitica.** La capacità di taggare ogni riga con un progetto, un dipartimento o un centro di
costo. Utile per un'azienda con progetti; una tasse su un'azienda senza di essi.

**Più aziende.** Odoo può tenere diverse aziende in un unico database, con transazioni
tra aziende. Riverton è un'azienda. Aggiungerne una seconda il primo giorno è come un'azienda
scopre, a marzo, che metà delle sue fatture appartengono all'entità legale sbagliata.

**Budget, attività, entrate differite, costi di importazione.** Tutti reali, tutti utili, tutti più tardi.

Il principio è quello che Sam aveva scritto sul tovagliolo e Maggie aveva appuntato alla
lavagna: installa ciò che userai questo mese. Un'impostazione che nessuno usa non è una capacità; è un
dove qualcuno finirà per fare un errore.

---

## La banca, e il saldo iniziale

C'è un altro pezzo di configurazione che un'azienda scopre tardi e wish avesse fatto
prima: la banca.

Odoo installa un registro bancario senza una banca dietro. Collegarlo al conto reale significa
inserire i dati del conto, e poi—questa è la parte che nessuno si aspetta—decidere come il denaro
*esistente* dell'azienda entra nel sistema.

Un'azienda che è in commercio da trenta anni non inizia con zero nella banca. Inizia
con ciò che dice l'estracto conto il giorno in cui il sistema va online, e con una storia che vive nel
vecchio programma di contabilità. Ci sono due modi onesti per gestire ciò, e uno disonesto.

Il modo onesto, per un'piccola azienda, è un **inserimento iniziale**: un'unica registrazione di registro, datata il giorno
prima del go-live, che dichiara ciò che l'azienda possiede e deve—saldo bancario, valore del magazzino, ciò che i clienti
devono, ciò che i fornitori sono dovuti—e si equilibra verso il conto dell'utile. È una fotografia, è auditable,
e richiede un pomeriggio con il bilancio dell'anno precedente.

L'altro modo onesto è **portare dentro la storia**: importare le vecchie fatture e le vecchie fatture per permettere ai
debiti vecchi e ai crediti vecchi di essere documenti reali invece che un unico blocco. Più lavoro, più utile, e
vale la pena se i clienti pagano regolarmente in ritardo—perché nel momento in cui l'assistente può elencare le fatture in ritardo,
ha bisogno di fatture da elencare.

Il modo disonesto è digitare il saldo bancario in un campo che sembra lo accetterà. Lo
accetterà. E poi il libro non si equilibrerà, e qualcuno passerà un weekend a scoprire perché.

Doreen scelse l'inserimento iniziale, con i debiti vecchi importati come documenti, e il pomeriggio che
le richiese fu la prima volta che usò il sistema per qualcosa che le importava davvero. Non stava
configurando software più. Sta movendo i numeri della sua azienda da un insieme di libri a
un altro, e controllando, riga per riga, che nulla fosse stato perso sulla strada.

---

## La prima registrazione

Il terzo pomeriggio, Doreen registrò il primo documento.

Non era una fattura, e non era una vendita. Era un pagamento bancario: duecento lire dall'
account dell'azienda all'account di un fornitore, per la carta consegnata in ottobre. Creò il
fornitore, creò la fattura, registrò il pagamento, e osservò i tre documenti collegarsi tra
loro—fattura al fornitore, pagamento alla fattura, entrambi alla banca.

Poi aprì il libro e guardò ciò che il sistema aveva scritto.

Due registrazioni. Duecento lire fuori della banca; duecento lire su ciò che l'azienda deve al
fornitore. Uguali e opposte, in due conti diversi, datate il giorno del pagamento. La regola di
Pacioli, eseguita da una macchina in una frazione di secondo, in un database in una cartella in un profilo
utente.

Si schirò indietro e disse qualcosa che Maggie scrisse, perché era il momento in cui il sistema
smise di essere software e divenne la memoria dell'azienda.

"È la stessa della mia libro", disse. "È esattamente la stessa della mia libro. Solo io posso chiederle
domande."

Quello è tutto della prima settimana. Non una trasformazione: un riconoscimento. Le regole che il sistema
segue sono le regole che lei aveva seguito a mano per trentuno anni, scritte da
un'altra persona, sei secoli fa, e ora eseguite da una macchina che non si stanca mai e non
dimentica mai di scrivere la seconda riga.

Il resto del libro è ciò che accade quando puoi chiederle domande—e quando qualcos'altro può chiederle
per te.
