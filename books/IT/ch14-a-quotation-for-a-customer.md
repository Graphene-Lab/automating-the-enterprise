# 14. Una quotazione per un cliente

Il primo vero lavoro che l'assistente ha svolto a Riverton è stata una quotazione, e riguardava il cliente la cui fattura aveva dato inizio all'intera storia.

L'Ashfield Academy voleva quattrocento raccoglitori con anelli e venti scatole di pennelli per lavagne, in occasione dell'inizio del termine estivo. Priya aveva la richiesta in una email, che aveva letto due volte, perché le quantità erano insolite: quattrocento raccoglitori rappresentavano l'intero termine, e venti scatole di pennelli erano più di quanto la scuola avesse mai ordinato in un'unica soluzione.

Sul vecchio sistema ciò le avrebbe richiesto dodici minuti: aprire il programma di contabilità, trovare il cliente, creare una quotazione, aggiungere due righe, cercare i prezzi nella spreadsheet che conteneva i prezzi contrattuali, applicare lo sconto, stamparla, inviarla via email, archiviarla. Sul nuovo sistema ha richiesto quaranta secondi, e le dodici minuti sono finite da qualche parte più utile—in una telefonata a Carol all'Ashfield per chiedere se i pennelli fossero per l'intera scuola o per il dipartimento di arte, che è il tipo di domanda che previene un reso.

Ecco cosa ha digitato Priya.

> *Crea una quotazione per Ashfield Academy per 400 raccoglitori A4 con anelli, blu, e 20 scatole di pennelli per lavagne, colori assortiti, ai prezzi contrattuali. Consegna presso la scuola, fine della prossima settimana.*

Ed ecco cosa è arrivato in risposta.

> *Quotation S00012 creata per Ashfield Academy: 400 × Raccoglitore A4 (blu) a £3.40, 20 × Pennelli per lavagne (confezione da 4, assortiti) a £11.40. Netto £1,588.00, IVA £317.60, totale £1,905.60. Data di consegna impostata venerdi 27 giugno. La quotazione è in bozza—digita "confirm" quando vuoi che diventi un ordine.*

Quaranta secondi, e ogni numero in essa era verificabile.

---

## La lista prezzi, e perché il prezzo contrattuale non è uno sconto

Il prezzo che l'assistente ha usato per Ashfield—£3.40 per un raccoglitore che ha prezzo di listino £3.95—non proveniva né dalla scheda prodotto né da uno sconto. proveniva da una *lista prezzi*, e la distinzione è una che le aziende sbagliano da anni.

Una lista prezzi in Odoo è un insieme di regole associate a un cliente (o a un gruppo di clienti, o a una valuta): per questo prodotto, o per questa categoria, o per tutto, applica questo prezzo, o questa percentuale di sconto, o questa formula. Ashfield ha una lista prezzi contrattuale da gennaio, concordata in una riunione, firmata su una singola pagina, e indica cosa paga la scuola per i dodici prodotti che acquista regolarmente.

La differenza tra una lista prezzi e uno sconto non è cosmetica.

Uno **sconto** è un adattamento a un prezzo, applicato a un documento, da una persona, nel momento della vendita. È visibile sulla quotazione, è verificabile, ed è una decisione presa da qualcuno.

Una **lista prezzi** è il prezzo. Non è un adattamento; è ciò che il cliente paga, e il prezzo di listino è un numero diverso che questo cliente non vede mai. Una quotazione per Ashfield che mostrasse £3.95 con uno sconto di quindici per cento sarebbe *corretta* e sarebbe anche un piccolo insulto: direbbe al cliente che il prezzo reale dell'azienda è più alto e che loro stanno ricevendo un favore.

Esiste una terza possibilità, che è ciò che la maggior parte delle piccole aziende fa realmente: una spreadsheet con i prezzi contrattuali al suo interno, consultata da una persona, e digitata a mano sulla quotazione. Fun finché la persona non è in vacanza, la spreadsheet non è aggiornata, o il contratto è rinegoziato e la spreadsheet non lo è.

## Cosa succede quando il prezzo è sbagliato

Ogni azienda ha una storia su un prezzo che era sbagliato su una quotazione, e le storie hanno tutte la stessa forma: l'errore è stato trovato dopo che l'ordine era stato confermato, il cliente è stato telefonato, e qualcuno ha dovuto decidere se onorare il prezzo o spiegare l'errore.

La decisione è solitamente onorarlo—la differenza è piccola e la relazione non lo è—e il costo viene scritto a parte come lezione. Ciò che l'azienda impara da la lezione è solitamente la cosa sbagliata: *essere più attenti*, piuttosto che *rendere il prezzo un fatto piuttosto che una memoria*.

Una lista prezzi rende il prezzo un fatto. Vive in un unico posto, è datato, si applica a ogni documento per quel cliente, e quando il contratto è rinegoziato qualcuno lo cambia una volta. L'assistente lo legge allo stesso modo in cui lo farebbe una persona, eccetto che non può dimenticare quale spreadsheet è quella corrente.

L'unica cosa che una lista prezzi non può fare è *decidere*. Se Ashfield riceve quindici per cento di sconto dal prezzo di listino, o un prezzo fisso, o un prezzo che cresce con l'indice della carta, è una decisione commerciale presa dalle persone. Il lavoro del sistema è applicarlo esattamente, ogni volta, e renderlo visibile quando cambia—che è il soggetto della prossima sezione.

## La quotazione che ha cambiato un prezzo

Tre mesi dopo, Priya ha posto una domanda che non era stata possibile prima.

*Quali clienti stanno pagando un prezzo che non è cambiato da gennaio, e cosa ci costerebbe alzarlo di tre per cento?*

La risposta è stata una lista di nove clienti e un numero: circa £4,100 all'anno di ulteriore fatturato, con l'aritmetica per cliente. I prezzi non erano cambiati perché nessuno aveva guardato, e nessuno aveva guardato perché guardare richiedeva l'apertura di nove liste prezzi e il loro confronto con i prezzi di acquisto, che avrebbe richiesto un pomeriggio.

Se alzarle i prezzi è una decisione commerciale, e Riverton le ha alzate per quattro dei nove e ha lasciato gli altri tranquilli per motivi che non avevano nulla a che fare con l'aritmetica. Ma la decisione è stata presa con un numero davanti a sé, in dieci secondi, invece di essere rimandata di un altro anno.

Quello è di nuovo il modello: la macchina non decide. Rende la decision abbastanza economica da intraprendere.

---

## Cosa è realmente successo

Vale la pena rallentare, perché la velocità non è la parte interessante.

L'assistente non sapeva cosa fosse un raccoglitore con anelli. Non aveva mai visto il contratto dell'Ashfield Academy, e non aveva idea di cosa fosse un termine scolastico. Ciò che aveva era un insieme di strumenti e una descrizione di cosa fa ciascuno, e un modello dell'azienda che qualcun altro aveva costruito.

Quindi quando l'istruzione di Priya è arrivata, l'assistente ha fatto ciò che fa un nuovo dipendente nel primo giorno: ha cercato le cose.

Ha cercato tra i clienti un nome corrispondente a *Ashfield Academy* e ne ha trovato uno—e, perché è cauto per progettazione, avrebbe chiesto se ne avesse trovati due. Ha cercato tra i prodotti *raccoglitore con anelli* e ha trovato un prodotto con varianti, e ha scelto quello blu perché Priya aveva detto blu. Ha cercato i penneli e ha trovato la confezione da quattro, assortiti. Ha chiesto all'ERP il prezzo di ciascuno, per quel cliente, in quella data, che è una domanda diversa da "qual è il prezzo di questo prodotto" e la differenza è l'intero capitolo dieci.

Poi ha creato la quotazione: un documento con un cliente, una data, due righe, un calcolo fiscale e uno stato. E poi si è fermato, perché una quotazione in bozza non è un impegno, e lo ha detto.

Quell'ultima frase è la cosa più importante che l'assistente ha fatto. Non ha confermato l'ordine. Non ha riservato lo stock. Non ha inviato nulla a nessuno. Ha prodotto una *proposta*, e ha detto a Priya che la proposta era in attesa di lei.

---

## La macchina degli stati, e perché conta

Una quotazione, un ordine e una fattura non sono tre documenti. Sono tre stati della stessa intenzione, e le transfrazioni tra loro sono i momenti in cui un'azienda si impegna.

**Bozza.** Una proposta. Non è stato promesso nulla, nessun stock è riservato, il prezzo può cambiare. In Odoo questo è chiamato quotazione, e ha una data di validità, perché un prezzo quotato a giugno non è necessariamente un prezzo a settembre.

**Confermato.** Un ordine. L'azienda ha promesso di consegnare, a un prezzo, entro una data. Lo stock è riservato (o, in un'azienda che non riserva, almeno l'intenzione è registrata), e il documento riceve un numero che apparirà sulla nota di consegna e sulla fattura.

**Consegnato.** Le merci sono partite. Ora c'è uno spostamento di stock, e un pezzo di carta che il cliente ha firmato.

**Fatturato.** Il denaro è stato chiesto. Ora c'è una registrazione a libro, e un punto fiscale.

**Pagato.** Il denaro è arrivato. Ora c'è una transazione bancaria che deve essere abbinata alla fattura, che è il passo in cui la maggior parte delle piccole aziende perdono il controllo del loro contante.

Ogni transazione è una decisione, e il lavoro dell'ERP è assicurarsi che la decisione sia fatta deliberatamente. Una quotazione che diventa un ordine senza che nessuno decida è una promessa che l'azienda non sapeva di aver fatto. Un ordine che diventa una fattura prima che le merci partano è un punto fiscale che si è spostato senza permesso.

Priya ha letto la quotazione, ha cambiato una cosa—ha ridotto i raccoglitori a trecentocinquantuno, perché il dipartimento di arte aveva trovato un armadio pieno—e l'ha confermata.

> *Cambia la quantità di raccoglitori a 350 e conferma l'ordine.*

> *Sales order S00012 confermato: 350 × Raccoglitore A4 (blu), 20 × Pennelli per lavagne. Totale £1,712.40. Data di consegna venerdì 27 giugno. Stock riservato: 350 raccoglitori disponibili, pennelli disponibili.*

Nota cosa ha aggiunto l'assistente alla fine: *stock riservato, disponibile*. Non gli era stato chiesto. Ha verificato, perché la cosa successiva che sarebbe successa era una consegna, e una consegna che non può essere fatta è peggiore di una quotazione che non può essere confermata.

![La stessa operazione sull'installazione di dimostrazione: ordine S00002 confermato, con i totali, lo stato e due cose che l'assistente pensava che tu dovessi sapere](../../assets/screens/assistant-06-order.png)

La figura sopra vale la pena leggerla con attenzione, perché è il comportamento per cui questo capitolo ha arguito, catturato piuttosto che descritto. L'assistente riporta il numero dell'ordine, lo stato (*bozza → vendita*), l'importo senza tasse, la tassa e il totale; poi offre due cose che non erano state richieste—che la tassa è stata applicata automaticamente a quindici per cento, e che la conferma di un ordine non crea né una consegna né una fattura. E finisce dicendo come ha verificato: *ho verificato la registrazione rileggendola dopo la conferma.*

Quell'ultima frase è la differenza tra un assistente e un modulo. Un modulo ti dice cosa ha salvato. Un collega ti dice cosa ha fatto e come sa che ha funzionato.

---

## Una breve storia della quotazione

La parola *quotation* deriva dal latino *quotare*, numerare—la stessa radice di *quote* nel senso di citare un passaggio. Nel commercio ha significato, per almeno quattrocento anni, una dichiarazione di prezzo offerta a un acquirente, e il suo status legale è stato discusso in aula da allora in poi.

L'argomento è sempre lo stesso: una quotazione è una offerta, che diventa un contratto quando accettata, o una invito a trattare, che è meramente una posizione iniziale? La risposta dipende dalla formulazione, dal contesto e dalla giurisdizione, ed è la ragione per cui un modulo di quotazione di solito porta una riga come *questa quotazione è valida per trenta giorni* e *soggetto a disponibilità*.

Un ERP non settle la domanda legale, ma fa qualcosa di correlato e utile: registra *quale* quotazione è stata spedita, *quando*, *a chi*, e *cosa diceva*. Quando un cliente telefona a settembre e dice "mi hai quotato quattrocento sterline", l'azienda può trovare il documento e vedere se diceva quattrocento o quattrocento e cinquanta, e in che data, e per quanti.

Quello non è una cosa piccola. Nel vecchio sistema, la risposta viveva in una thread di email, in una copia stampata in un vassoio, e nella memoria di Priya—in quell'ordine di affidabilità.

## Cosa l'assistente non ha fatto

Tre cose valgono la pena di essere notate in ciò che *non* è successo.

Non ha applicato uno sconto. Ashfield ha un prezzo contrattuale, che è un meccanismo diverso da uno sconto, e l'assistente ha usato il prezzo contrattuale perché è ciò che dice il record del cliente. Se Priya avesse voluto uno sconto, avrebbe dovuto chiederne uno, e lo sconto sarebbe stato registrato—che è la differenza tra un prezzo e un favore.

Non ha scelto la data di consegna da sola. Ha preso *fine della prossima settimana* e l'ha trasformata in una data, che è un piccolo atto di interpretazione, e ha detto quale data aveva scelto in modo che Priya potesse correggerla.

E non ha spedito la quotazione. La spedizione è un'azione con un cliente all'altra estremità, e l'assistente non ha uno strumento per l'email nella configurazione di Riverton—deliberatamente. La quotazione è stata stampata in un PDF dall'ERP e allegata a una email da una persona, che ha richiesto a Priya trenta secondi e ha mantenuto l'ultimo passo, quello in cui un documento lascia l'edificio, nelle umane mani.

Alcune aziende vorranno automatizzare quel passo, e il sistema può farlo. Riverton ha deciso, nel primo mese, che nulla sarebbe stato spedito a un cliente senza che una persona lo guardasse. È una decisione che un'azienda può rivedere; non è una decisione che un'azienda dovrebbe fare per incidente.

---

L'ordine è rimasto nel sistema per due giorni, in attesa della data di consegna.

Giovedì, Tom ha chiesto all'assistente una domanda che Priya non aveva pensato di chiedere.

> *Quali ordini sono dovuti per la consegna nei prossimi tre giorni, e c'è lo stock per tutti quanti?*

La risposta è stata una lista di quattro ordini e una frase che ha cambiato la settimana: i raccoglitori per Ashfield c'erano, i pennelli c'erano, ma l'ordine per Northgate Library Service necessitava di dodici scatole di carta A4 e ce ne erano nove.

Novi scatole, e una promessa di consegnare lunedì. Quello è il tipo di fatto che una volta veniva scoperto da un autista al piano di carico, ed è stato scoperto invece un pomeriggio di giovedì da qualcuno che ha pensato di chiedere.
