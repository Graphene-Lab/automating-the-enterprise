# 21. La chiusura del mese

Chiudere un mese è la cosa più simile a un rituale religioso che un'impresa piccola possa avere, e come la maggior parte dei rituali viene eseguito perché l'alternativa è peggiore.

Lo scopo è semplice: dichiarare che un periodo è concluso, che i suoi numeri sono definitivi e che nulla verrà aggiunto in seguito. Tutto ciò che un'impresa fa con i propri conti—pagare le tasse, rendere conto a una banca, valutare l'azienda, pagare un dividendo—dipende dall'esistenza di periodi con dei bordi.

Doreen chiudevva un mese in quattro serate, con una calcolatrice, un estratto conto stampato e una lista di cose che non voleva guardare. La prima chiusura con il sistema ha richiesto un pomeriggio, la seconda novanta minuti. Questo capitolo è ciò che è accaduto nel frattempo.

---

## I sette controlli

Il capitolo diciannove elencava le domande. Ecco come si presentano come lavoro.

**Uno: ogni consegna ha una fattura, e ogni fattura ha una consegna.** L'assistente produce la lista degli ordini consegnati non ancora fatturati, e la lista delle fatture senza una consegna alle spalle. La prima deve essere vuota alla fine del mese; la seconda deve essere vuota sempre, perché una fattura senza una consegna è o un servizio (ok) o un errore (non ok).

**Due: ogni fattura di fornitore arrivata è nel sistema.** Questo è il controllo che richiede un atto fisico—svuotare il vassoio della posta, aprire le email—e nessun sistema può farlo per te. Ciò che il sistema può fare è dirti cosa si aspetta: la lista degli ordini di acquisto che sono stati ricevuti ma non fatturati.

**Tre: la banca è d'accordo.** Il giornale bancario viene confrontato con l'estrato conto, riga per riga. Odoo può importare un file di estrato conto e proporre delle corrispondenze; le proposte vengono accettate o rifiutate da una persona. Questo è il controllo che un tempo richiedeva a Doreen tre ore e ora ne richiede quaranta, e i quaranta minuti sono spesi per le sei righe che non hanno corrisposto automaticamente—le interessanti, ovviamente.

**Quattro: debitori e creditori sono d'accordo.** La lista di chi deve cosa, per scadenza, contro il conto del libro maggiore. Se differiscono, c'è una registrazione senza un partner sopra, e trovarla è una ricerca più che una indagine.

**Cinque: le scorte sono corrette.** La valutazione delle scorte nei conti contro il magazzino. Una differenza qui è di solito una consegna che non è mai stata validata, o un costo che non è stato ricalcolato.

**Sei: gli accantonamenti sono corretti.** Una spesa che appartiene a questo mese e che non è ancora stata fatturata—l'elettricità, l'affitto trimestrale, la parcella dell'accountant—deve essere registrata, altrimenti il profitto del mese è adulterato e quello del mese successivo è punito.

**Sette: l'IVA è corretta.** La tassa sulle vendite e sugli acquisti, contro la dichiarazione. Questo è il controllo che ha una scadenza attaccata, e quello in cui un errore è più costoso.

Sette controlli, e il contributo del sistema non è quello di eseguirli. È quello di rendere ciascuno una *lista* più che una *escavazione*.

## La dichiarazione IVA, che è la chiusura con una scadenza

Tutto di questo capitolo fin qui è volontario: un'impresa chiude il mese perché vuole sapere dove si trova. La dichiarazione IVA non è volontaria, ed è l'unica parte della chiusura in cui un errore ha un prezzo attaccato.

La dichiarazione è, in essenza, un riassunto di due numeri: la tassa addebitata sulle vendite, e la tassa pagata sugli acquisti, con la differenza che va o che arriva dall'ufficio tasse. Un bambino potrebbe fare l'aritmetica; la difficoltà è intera nella *classificazione*—quale vendita è tassata normalmente, quale è a tasso zero, quale è fuori campo, e quale acquisto è recuperabile.

Odoo produce la dalle codici fiscali sui documenti, ed è per questo che il capitolo dieci ha insistito sul fatto che la tassa è configurata sul prodotto e non digitata sulla fattura. Un singolo prodotto con il codice sbagliato produce una dichiarazione sbagliata in un modo invisibile: il totale è plausibile, l'aritmetica è corretta, e la classificazione è falsa.

L'abitudine di Doreen, ereditata dall'era della carta, è quella di riconciliare la dichiarazione contro il libro maggiore prima di inviarla: la cifra delle vendite sulla dichiarazione deve uguagliare il saldo attivo sulle conti delle vendite per il periodo, e la cifra degli acquisti deve uguagliare il saldo passivo sui conti degli acquisti. Se sono d'accordo, la classificazione è almeno internamente coerente. Se non lo sono, la differenza è un documento con il codice sbagliato, e trovarla è una ricerca più che un'ipotesi.

L'assistente fa quel confronto in una frase, ed è la cosa più preziosa che fa in tutto il ciclo contabile, perché trasforma una riconciliazione di due ore in un controllo.

## La chiusura dell'anno

La chiusura annuale è quella mensile con più cerimonie e in gioco più in alto, e gli stessi sette controlli si applicano, con tre aggiunte.

**La valutazione delle scorte** deve essere corretta, perché è il numero più grande sul bilancio di un grossista. Un conteggio delle scorte nell'ultima settimana dell'anno non è una formalità; è la differenza tra un profitto e una perdita.

**Gli accantonamenti e i pagamenti anticipati** devono essere completi: un premio assicurativo pagato a novembre per l'anno seguente appartiene in parte all'anno successivo, e un'impresa che ignora questo rende un profitto che non esiste.

**I conti dei direttori o dei proprietari** devono essere in ordine, perché l'ufficio tasse li guarda per primo.

E poi l'anno è chiuso, e i conti sono depositati, e per undici mesi nessuno li guarda di nuovo—ed è per questo che la chiusura *mensile* conta più di quella annuale. Un'impresa che guarda una volta all'anno guida con il parabrezza imbrattato e uno sguardo annuale allo specchietto.

## La chiusura in un'impresa di uno

La maggior parte di questo libro presume un'impresa con un ufficio: diverse persone, una divisione del lavoro, qualcuno che può controllare il lavoro di un altro. La chiusura è diversa in un'impresa di uno, ed vale la pena una sezione perché un gran numero di imprese sono esattamente quello.

In un'impresa di uno, non c'è separazione delle mansioni. La persona che emette la fattura la registra, la paga, la riconcilia e chiude il mese. I controlli che proteggono un'impresa più grande—limiti di approvazione, quattro occhi, una persona diversa che rilascia il pagamento—non esistono, e non possono essere inventati dal software.

Ciò che il sistema può fare invece è rendere il *registro* completo, in modo che l'assenza di un controllo sia almeno visibile. Tre abitudini valgono più di qualsiasi impostazione.

**Chiudi in una seduta, a ora fissa.** Una chiusura mensile sdraiata su tre serate è una chiusura mensile con tre occasioni per perdere il filo. Il sistema rende la seduta possibile: due ore, una volta al mese, con le sette liste davanti a te.

**Scrivi il ragionamento.** Quando una spesa è insolita, quando il saldo di un cliente sembra sbagliato, quando la fattura di un fornitore non corrisponde: una riga in un file che dice cosa hai deciso e perché. Sei mesi dopo, quella riga è l'unica cosa che ti ricorderà.

**Mantieni attuale la riconciliazione bancaria.** In un'impresa di uno, l'estrato conto è l'unico testimone indipendente. Riconciliarlo settimanalmente piuttosto che mensilmente trasforma una indagine di due ore in quattro di dieci minuti, e cattura l'errore mentre te lo ricordi ancora di averlo commesso.

L'assistente aiuta qui in un modo facile sottovalutare: può essere chiesto *qualcosa sembra sbagliato questo mese?* e produrrà le eccezioni—l'importo strano, il riferimento mancante, il cliente che ha pagato due volte. In un'impresa con un dipartimento finanziario, quella domanda è fatta dal dipartimento finanziario. In un'impresa di uno, nessuno la fa a meno che non la faccia il sistema.

## La chiusura come conversazione

La cosa più utile che l'assistente ha fatto durante la prima chiusura di Riverton non è stata produrre un rapporto. Ha risposto a una domanda in mezzo a una.

> *La riconciliazione bancaria ha sei righe non corrispondenti. Cosa sono?*

> *Sei righe non corrispondenti, totale £3.412,60:*
> *1. 2 nov, £1.200,00 attivo — pagamento da Calder & Sons, nessun riferimento di fattura.*
> *2. 3 nov, £14,50 passivo — spesa bancaria, nessuna registrazione nei libri.*
> *3. 7 nov, £2.000,00 passivo — trasferimento all'conto di risparmio, non registrato.*
> *4. 9 nov, £88,10 passivo — pagamento con carta a un fornitore di cancelleria, nessuna fattura.*
> *5. 11 nov, £60,00 attivo — rimborso dal corriere, non registrato.*
> *6. 12 nov, £50,00 attivo — pagatore sconosciuto, riferimento "INV 2025".*

Sei righe, sei storie. Un cliente ha pagato senza riferimento; la banca ha addebitato una tassa; Maggie ha spostato soldi verso il risparmio; qualcuno ha comprato qualcosa con la carta dell'impresa; un corriere ha rimborsato una tassa; e qualcuno ha pagato cinquanta sterline contro una fattura del 2025, che è o un pagamento molto in ritardo o un errore.

La vecchia versione di questa conversazione è accaduta tre settimane dopo, per telefono, con una banca, ed era chiamata "una richiesta di chiarimento". La nuova versione accade il secondo giorno lavorativo del mese, in una finestra, ed è chiamata "martedì".

## Bloccare il periodo

Quando i sette controlli sono fatti, il periodo è bloccato. In Odoo questo è una impostazione sul periodo contabile—una *data di fine* oltre la quale le registrazioni non possono essere fatte—ed è la cosa più simile al sigillo che il sistema abbia.

Bloccare è una promessa al futuro: qualunque dicano i numeri, continueranno a dirlo il prossimo anno. È anche una promessa al passato: nessuno può migliorare silenziosamente i risultati dell'ultimo trimestre spostando una spesa dentro di esso.

Le imprese resistono al blocco, e la resistenza è comprensibile. Bloccare significa che un errore trovato a marzo non può essere corretto a gennaio; deve essere corretto a marzo, con una spiegazione. Quello è scomodo, ed è proprio il punto: un conto che può essere riscritto non è un conto.

## La prima chiusura, e come si è sentita

Il racconto di Doreen della prima chiusura vale la pena di essere citato a lungo, perché è la descrizione più onesta di questo tipo di cambiamento che questo libro abbia.

"Mi sono seduta alle nove aspettandomi di restarci fino alle sette. Avevo la calcolatrice, avevo gli estrati conti stampati, avevo un sandwich. E poi ho chiesto le sette liste e sono tornate, una dopo l'altra, in circa dieci minuti, e ho pensato: bene, ora inizia il lavoro.

"Ma il lavoro era solo... guardare le liste. La banca aveva sei righe e io sapevo cosa fossero quattro di esse. La lista delle consegnate-non fatturate aveva due ordini sopra, e uno di essi era un campione che avevamo mandato al centro giardinaggio, che non avrebbe dovuto essere fatturato per niente, quindi ho corretto la consegna. Le scote erano sbagliate di quaranta risme, che era il pallet arrivato il giovedì e registrato come quaranta pallet—era il mio errore, dall'unità di misura, e l'ho trovata in quattro minuti perché il sistema mi mostrava il movimento.

"Mezzadue fatta avevo fatto tutto tranne l'IVA, e l'IVA ha richiesto un'ora perché la controllo sempre due volte. E poi ho chiuso il mese, e mi sono seduta lì, e non sapevo cosa fare di me stessa."

Si è pausa.

"Trentuno anni, e non ho mai finito una chiusura in un giorno. Non ho mai finito una senza un errore che ho trovato il mattino dopo. Gli errori erano sempre nelle ultime tre ore, quando ero stanca."

## A cosa serviva il tempo

La domanda interessante non è quanto la chiusura sia diventata più veloce. È su cosa il tempo sia stato spato invece.

Nel caso di Riverton, tre cose.

**Il pallet registrato come quaranta pallet** è stato trovato e corretto nello stesso mese, piuttosto che essere scoperto da un conteggio delle scorte a dicembre. Quella è una differenza di soldi veri.

**Due ordini che erano stati consegnati e non fatturati** sono stato fatturati nel mese a cui appartenevano, che ha spostato £3.400 di ricavo nel periodo corretto—e, più importante, nella dichiarazione IVA corretta.

**E le sei righe bancarie** hanno prodotto una conversazione con il corriere su un rimborso che nessuno aveva notato, e una decisione di smettere di usare la carta dell'impresa per piccoli acquisti, perché le ricevute erano un disastro.

Nessuna di quelle è drammatica. Insieme sono la differenza tra un insieme di conti che è un registro e un insieme di conti che è uno *strumento*—qualcosa che puoi usare per prendere una decisione, perché gli fidhi e perché non è a tre settimane di distanza.

---

Il rituale di chiusura mensile ha una funzione in più che raramente si dice, ed vale la pena dirlo chiaramente.

È il momento in cui qualcuno guarda l'intera impresa. Non le vendite, non le scorte, non la banca—l'intera cosa, insieme, con una scadenza. Un'impresa che chiude il mese correttamente ha, dodici volte all'anno, un momento in cui qualcuno competente si siede e chiede *questo ha senso?*

La maggior parte delle piccole imprese non ha quel momento. Hanno una dichiarazione di tasse, preparata affrettamente, da un accountant che vede i numeri due volte all'anno. La differenza tra quelle due imprese non è il software. È se qualcuno mai guarda.

Il contributo del software è quello di rendere il guardare abbastanza economico che accada.
