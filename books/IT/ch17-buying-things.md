# 17. Acquisto di materiali

L'acquisto è la metà di un'attività di cui nessuno scrive libri.

La vendita ha una sua romanticità: clienti, preventivi, l'emozione dell'ordine. L'acquisto ha un ordine di acquisto, una distinta di consegna, una fattura di un fornitore e un ciclo di pagamento. Eppure ogni libra spesa da un grossista entra da quella porta, e la differenza tra una company che acquista bene e una che acquista male è la differenza tra un margine e un'abitudine.

L'acquisto di Riverton era gestito da Maggie, al telefono, a memoria, per undici anni. Conosceva il fornitore di carta, il fornitore di penne e il fornitore di raccoglitori, e sapeva quanto aveva pagato l'ultima volta perché aveva una cartella. Ciò che non aveva era alcun modo di sapere se il fosse il prezzo fosse salito, o se l'ultima consegna fosse davvero arrivata, o se la fattura che stava per pagare corrispondesse all'ordine che aveva effettuato.

La prima attività di acquisto dell'assistente era una regola di riordino che scattava un mercoledì.

---

## La regola di riordino, e cosa propone

L'undicesimo capitolo ha fissato due numeri su ogni prodotto: un minimo e un massimo. Odoo vigila sulle scorte, e quando un prodotto scende sotto il suo minimo, propone un ordine di acquisto.

Ne ha proposto uno per i raccoglitori ad anelli, il mercoledì, in una lista che Tom ha esaminato con il caffè.

> *Tre prodotti sono sotto il loro punto di riordino: Raccoglitore ad anelli A4 (blu) 62 disponibili, minimo 100; Pennarelle per lavagne (assortite) 44 disponibili, minimo 60; Carta A4 9 risme disponibili, minimo 40.*

Tom ha esaminato la lista, decidendo che la carta poteva aspettare fino alla conferma del prezzo a pallet, e ha chiesto gli altri due.

> *Crea un ordine di acquisto per 500 raccoglitori ad anelli A4, blu, e 200 pacchi di pennarelle per lavagne, assortite, dai nostri soliti fornitori, all'ultimo prezzo pagato. Non confermarlo ancora.*

> *Ordine di acquisto P00008 creato, in bozza. Due fornitori, perché i prodotti provengono da fornitori diversi: 500 × Raccoglitore ad anelli A4 (blu) da Pennine Paper a £2,10; 200 × Pennarelle per lavagne (pacchi da 4, assortite) da Kestrel Supplies a £6,80. Totale netto £2.410,00, IVA £482,00, totale £2.892,00. Non è stato inviato nulla; digita "conferma" per piazzare gli ordini.*

Due cose in quella risposta valgono la pena di essere notate, e entrambe sono il sistema che fa qualcosa che una persona avrebbe dovuto fare a mano.

La prima è *due fornitori*. Tom aveva chiesto due prodotti; il sistema sapeva che provenivano da fornitori diversi e ha prodotto due ordini di acquisto. Una persona avrebbe fatto lo stesso, dopo aver esaminato le schede prodotto. La differenza è che la persona potrebbe aver dimenticato, e ordinato i raccoglitori dal fornitore dei pennarelle.

La seconda è *l'ultimo prezzo pagato*. Non è una lista prezzi; è un fatto storico. Il sistema ha considerato l'acquisto più recente di quel prodotto e ha usato il prezzo. Se il fornitore ha alzato i suoi prezzi, l'ordine sarà sbagliato—ma sarà sbagliato in un modo che si può vedere, perché il prezzo precedente è sulla scheda accanto a quello nuovo.

## Cosa fa la conferma

Confermare un ordine de acquisto fa tre cose, e la terza è quella che conta.

**Impegna** la company a comprare, a un prezzo, entro una data—che è una promessa, e quindi un documento che deve essere esaminato prima di essere emesso.

**Crea una ricevuta attesa**: il magazzino ora sa che cinquecento raccoglitori stanno arrivando, e quando. È ciò che rende possibile rispondere alla domanda *possiamo promettere questo a un cliente la prossima settimana?* con qualcosa di meglio di un'ipotesi.

E **apre una porta alla fattura**: quando arriva il conto del fornitore, può essere confrontato con l'ordine. Non perché il sistema sia sospettoso, ma perché la *triple verifica* è il controllo più antico nel commercio e ancora il migliore.

## La triple verifica

L'idea è semplice abbastanza da stare su un tovagliolo, e ha fatto risparmiare alle company più soldi di qualsiasi funzione software mai inventata.

Hai ordinato cinquecento raccoglitori a £2,10 l'uno. Il magazzino ha ricevuto cinquecento raccoglitori. La fattura del fornitore dice cinquecento raccoglitori a £2,10 l'uno. Tre documenti, tre numeri, e devono concordare prima che il conto sia pagato.

Se la fattura dice £2,30, qualcuno chiede il perché. Se il magazzino ha ricevuto quattrocento ottanta, qualcuno chiede dove sono finiti venti. Se l'ordine era per cinquecento e la fattura per seicento, qualcuno chiede chi ha autorizzato l'extra cento—e la risposta è spesso *nessuno*, che è esattamente il punto.

Il controllo è vecchio. I libri di contabilità dei costi lo descrissero negli anni '20, e fu formalizzato nei manuali di acquisto degli anni '50, quando i grandi produttori scoprirono che la differenza tra ciò che ordinavano e ciò che pagavano era una frazione significativa del loro profitto. Sopravvive perché è economico: tre documenti che già esistono, confrontati da una macchina che non si annoia.

Ciò che è nuovo è che il confronto richiede un secondo e può essere *spiegato*.

> *Crea la fattura del fornitore per l'ordine P00008 e controllala contro l'ordre e la ricevuta.*

> *Fattura del fornitore BILL/2026/0031 creata da P00008 per Pennine Paper: 500 × Raccoglitore ad anelli A4 (blu) a £2,10, netto £1.050,00, IVA £210,00, totale £1.260,00. Confrontato: ordinato 500, ricevuto 500, fatturato 500. Nessuna differenza. La fattura è in bozza.*

Nessuna differenza. In una buona giornata, è tutto il lavoro: tre numeri che concordano, in una frase, in un secondo.

In una giornata cattiva dice qualcosa come: *ordinato 500, ricevuto 480, fatturato 500 — una differenza di 20 unità a £2,10.* E allora una persona deve decidere: il fornitore ha spedito in meno, il magazzino ha sbagliato a contare, o qualcuno ha accettato una consegna parziale e ha dimenticato di registrarla? Il sistema non può rispondere a questo. Può solo rendere la domanda impossibile da evitare.

---

## Pagamento

Pagare un fornitore è l'immagine speculare dell'essere pagati, e ha la stessa forma: un documento (la fattura), un pagamento, e un confronto tra i due.

> *Registra un pagamento per l'intero importo di BILL/2026/0031, datato oggi, tramite bonifico bancario.*

> *Pagamento registrato per BILL/2026/0031: £1.260,00 a Pennine Paper, dal giornale bancario, datato 14 novembre 2026. La fattura è ora completamente pagata; il saldo del fornitore è zero.*

Il giornale bancario non è la banca. È la *registrazione* della company di ciò che la banca ha fatto, e le due devono essere riconciliate—che è il rituale mensile descritto nel capitolo successivo al prossimo. La distinzione conta perché è lì che una company scopre che un pagamento che ha registrato non fu mai fatto, o un pagamento che la banca fece non fu mai registrato.

## Una breve storia dell'ordine de acquisto

L'ordine de acquisto come documento è un figlio dell'era delle ferrovie. Prima delle ferrovie, un commerciante comprava da persone che poteva vedere, e una stretta di mano più una voce a libro bastava. Le ferrovie crearono distanza: un compratore a Manchester che ordinava da un mulino a Leeds aveva bisogno di un documento che dicesse cosa era ordinata, a che prezzo, e quando, perché le merci sarebbero arrivate giorni dopo e l'uomo che le aveva ordinate forse non c'era più.

La forma dell'ordine de acquisto moderno—numero, data, fornitore, righe, quantità, prezzi, condizioni—fu fissata all'inizio del ventesimo secolo e non è cambiata da allora, perché codifica l'informazione minima necessaria per risolvere una controversia. Il software non ha cambiato il documento. Ha cambiato il costo di produzione, invio, confronto e ricerca.

Che è, in una frase, l'argomento di questo intero libro.

## La scheda del fornitore, e a cosa serve

Un fornitore in un ERP non è una voce di rubrica. È un insieme di condizioni, e sono le condizioni a far funzionare la cartacciaia.

Le schede dei fornitori di Riverton furono costruite in un pomeriggio, e ciascuna contiene cinque cose che contano: le **condizioni di pagamento** (trenta giorni dalla data della fattura, o fine mese successivo, che sono cose molto diverse), la **valuta**, il **trattamento fiscale** (se il fornitore carica IVA e sotto quale regime), il **tempo di consegna** che il compratore si aspetta, e il **contatto** che risponde quando qualcosa va male.

Nessuna di queste è decorazione. Le condizioni di pagamento decidono la data di scadenza su ogni fattura, e un fornitore le cui condizioni sono registrate come "30 giorni" quando in realtà sono "60 giorni netto" sarà pagato in anticipo ogni mese per un anno—che suona innocuo ed è in realtà un piccolo prestito permanente a un fornitore che non glielo ha chiesto. La valuta decide se una fattura in euro è convertita al tasso della data della fattura o della data di pagamento, che è una differenza che si manifesta come guadagno o perdita. Il tempo di consegna decide quando il sistema si aspetta le merci, che è ciò che dà significato al report "ordini de acquisto in ritardo".

Il vecchio sistema non aveva nulla di tutto questo. Aveva una cartella di fatture e un numero di telefono scritto sull'interno della cartella.

## Cosa non fa un ordine de acquisto

Vale la pena essere chiari sui limiti, perché una company che si aspetta troppo da un documento sarà delusa dal software che lo produce.

Un ordine de acquisto non **negozia**. Registra il prezzo che è stato concordato, e l'assistente può mostrarti ciò che hai pagato l'ultima volta, e ciò che hai pagato l'ultima volta prima—che è la munizione per una negoziazione, non la negoziazione.

Non **garantisce** la consegna. Crea un'aspettativa, e l'aspettativa è ciò che misura il report degli ordini in ritardo.

Non **controlla le merci**. Quello è la ricevuta, e la ricevuta è una persona con una tavoletta.

E non **paga**. Il pagamento è una decisione separata, presa in seguito, di solito da qualcuno che prima guarda il saldo bancario.

Ciò che fa è rendere visibili tutte e quattro quelle cose, e la visibilità è ciò che trasforma una relazione condotta al telefono in una relazione che può essere esaminata.

## Il prezzo che è salito lentamente

La tassa di pallet che Doreen trovò nel capitolo diciannove aveva una controparte sul lato dell'acquisto, e fu trovata con lo stesso tipo di domanda.

> *Quali fornitori hanno alzato i loro prezzi negli ultimi sei mesi, e di quanto?*

La risposta elencava quattro fornitori e undici prodotti, e uno di questi era la carta: il prezzo d'acquisto era passato da £2,05 a £2,18 a risme nel luglio, che è sei per cento, su un prodotto che Riverton compra a pallet.

Sei per cento sulla carta era, ai volumi di Riverton, circa £1.900 all'anno. Nessuno se ne era accorto, perché nessuno aveva una lista di ciò che avevano pagato prima. Il compratore—Maggie, in questo caso—si era accorto che la fattura "sembrava un po' più alta" e aveva presunto fosse sua immaginazione.

Quello è il modello a cui questo intero libro continua a tornare: i soldi non si perdono in errori grandi e drammatici. Si perdono in cambiamenti troppo piccoli per essere notati uno alla volta e troppo grandi per essere ignorati quando sommati. Un sistema che ricorda il prezzo precedente li rende notabili, e accorgersene è la parte maggiore del lavoro.

## La cosa da fare bene il primo giorno

Se una company porta via una cosa da questo capitolo, deve essere questa: **registrare le condizioni di pagamento sulla scheda del fornitore, non sulla fattura.**

Una fattura con condizioni digitate sopra è un documento che sarà pagato con quelle condizioni una volta sola. Un fornitore con condizioni sulla scheda è un fornitore cui ogni fattura è a scadenza nel giorno giusto, per sempre, senza che nessuno debba pensarci. La differenza è trenta secondi di configurazione e un anno di non dover avere questa conversazione:

"Perché stiamo pagando Pennine in anticipo?"
"No lo so, il sistema dice che la fattura è a scadenza."
"La fattura è a scadenza in sessanta giorni, non trenta."
"Allora la scheda del fornitore è sbagliata."
"Dal quando?"

Dal primo giorno, di solito, e nessuno se ne era accorto perché pagare in anticipo non è un errore di cui qualcuno si lamenta—eccetto la persona che guarda il flusso di cassa nel febbraio.

---

Il giudizio di Tom, alla fine del primo mese di acquisti attraverso il sistema, era caratteristicamente pratico.

"Pensavo che un ordine de acquisto fosse cartacciaia," disse. "Non lo è. È l'unica cosa che mi impedisce di pagare per qualcosa che non ho ricevuto."

Maggie gli chiese se il sistema avesse catturato qualcosa.

"Due volte. Una volta la fattura era per venti in più di quanto ricevuto, e una volta il prezzo era salito senza che qualcuno ce lo dicesse. Entrambe le volte l' avrei pagato, perché avrei guardato la fattura e pensato, sì, questo è più o meno giusto."

*Più o meno giusto* è la frase da ricordare. La maggior parte dei soldi perduti in una piccola company si perde nel gap tra *più o meno giusto* e *giusto*, e il gap non si chiude essendo più attenti. Si chiude avendo tre numeri da confrontare, e una macchina che li confronta ogni volta.
