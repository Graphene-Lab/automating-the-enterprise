# 24. Il documento che lascia l'edificio

Nell'ufficio di Riverton c'è uno scaffile che contiene quattro raccoglitori, e sono gli ultimi documenti che l'azienda conserva.

Non sono fatture. Le fatture sono nel sistema e nelle caselle email dei clienti. I raccoglitori contengono le cose che devono essere firmate: le note di consegna tornate con le iniziali del custode, le note di credito che un cliente ha contestato, e i due contratti che contano. Tutto il resto è un PDF.

Questo capitolo riguarda il momento in cui un documento lascia l'edificio, che è il momento in cui il software incontra il mondo fisico—e in cui un numero sorprendente di sistemi altrimenti validi falliscono.

---

## Cosa rende un documento stampabile

Un documento stampabile non è uno schermo rimpicciolito. È un oggetto diverso, con regole diverse, e il motore di report di Odoo vale la pena di essere compreso perché le impone.

**Ha un layout fisso.** Uno schermo si rielabora; una pagina no. Il modello della fatture decide dove va il logo, quanto è larga la colonna della descrizione, e cosa succede quando il nome di un prodotto è più lungo della colonna. (La risposta, in un buon modello, è che va a capo—e la riga si allunga. In uno cattivo, si sovrappale al prezzo, e il cliente vede un numero che appartiene a un'altra riga.)

**Ha un'intestazione e un piè di pagina che si ripetono.** La pagina uno di una fattura di cinque pagine deve dire di chi è la fattura, e la pagina cinque deve dire che è la pagina cinque di cinque. Non è vanità: una pagina che arriva da sola, senza intestazione, è una pagina che può essere contestata.

**Trasporta l'identità dell'azienda.** Nome, indirizzo, numero fiscale, registrazione, dati bancari. Non sono decorazione; sono i campi che rendono il documento una pretesa legale, e provengono dal record dell'azienda configurato nel capitolo nove.

**È riproducibile.** La stessa fattura, stampata un anno dopo, deve apparire identica. È per questo che il modello è un modello e non un documento modificato da qualcuno: una fattura che può essere modificata dopo i fatti è una fattura che non prova nulla.

## I tre documenti che un grossista stampa davvero

Riverton stampa tre cose, e ognuna ha un compito diverso.

**La fattura**, come PDF allegato a un'email. È la richiesta di pagamento e il documento fiscale, ed è quella che il reparto amministrazione del cliente archiverà.

**La nota di consegna**, stampata sulla stampante del furgone e firmata alla porta. Non è un documento finanziario; è la prova che la merce è arrivata, ed è la cosa che risolve la discussione tre settimane dopo su se il pallet sia stato firmato per.

**L'estratto conto**, inviato mensilmente ai clienti con diverse fatture aperte. È una lista, non una richiesta, ed è lo strumento di recupero più efficace che esista—perché mette ogni voce aperta davanti alla persona che paga, in una sola pagina, senza accuse.

Ce n'è un quarto, meno evidente: la **relazione di magazzino**. Non viene inviata a nessuno. Viene stampata perché Tom la legge nel furgone, e leggere una cosa a stampa è diverso dal leggerla su schermo—più lentamente, e quindi più probabile che venga presa in considerazione.

## Il flusso di lavoro che ha sostituito la busta

Il vecchio flusso di lavoro di Doreen era: stampare, piegare, indirizzare, francobollare, spedire, archiviare la copia. Cinque passi, e l'ultimo era quello che falliva, perché archiviare è il passo che non ha scadenza.

Il nuovo flusso di lavoro è: generare, verificare, inviare, e lasciare che il sistema l'archivi. Tre passi, e l'archiviazione è automatica—che significa che succede, che significa che quando un cliente telefona a novembre per una fattura di giugno, la risposta è una ricerca e non una spedizione nella sala fatture.

La verifica è il passo che conta, ed è quello che le aziende saltano. Un documento generato da una macchina non è automaticamente corretto: è corretto se i dati su cui si basa sono corretti, e i dati su cui si basa sono stato inseriti da qualcuno. L'abitudine di Doreen, che ha mantenuto dall'era della carta, è leggere la prima fattura di ogni serie—non tutte, la prima—and guardare il nome del cliente, l'indirizzo, il totale e la tassa. Se quei quattro sono corretti, il resto quasi certamente lo sono.

## Cosa fa l'assistente, e cosa non fa

L'assistente può produrre il PDF e allegarlo a un'email. A Riverton non lo fa, e la decisione vale la pena di essere registrata perché è una scelta, non un limite.

Il ruolo dell'assistente è *preparare*: creare la fattura, registrarla, produrre il documento, e dire a Doreen che è pronta. L'invio è fatto da una persona, nel client email, perché l'invio è il passo in cui un errore raggiunge un cliente—e un errore che raggiunge un cliente costa più del minuto che ci vuole per prevenirlo.

Quella è una scelta conservatrice, e un'azienda con cento fatture al giorno non può farla. Riverton ne ha quindici, e quindici minuti di attenzione umana sono accessibili. Il principio che scala, tuttavia, è lo stesso a qualsiasi volume: **il passo che lascia l'edificio è il passo in cui dovrebbe esserci un essere umano, finché non hai visto la macchina farlo correttamente cento volte.**

## Una breve storia della forma della fattura

La fattura stampata è un figlio del diciannovesimo secolo, e la sua forma fu fissata dalle ferrovie e dal telegrafo.

Prima che la stampa fosse economica, una fattura era una nota manoscritta. Quando le aziende crebbero, e quando lo stesso cliente iniziò a comprare da diversi reparti dello stesso fornitore, la nota divenne un modulo: stampato con il nome dell'azienda, con righe numerate, con colonne per quantità, descrizione, prezzo e importo. Le colonne non sono arbitrarie—riflettono la sequenza con cui un impiegato verifica il documento, da sinistra a destra, concludendo con il totale.

Il modulo è sopravvissuto a ogni tecnologia da allora, inclusa questa, perché codifica l'informazione minima necessaria per risolvere una disputa: chi, cosa, quanti, a che prezzo, quanta tassa, in totale, entro quando. Il software non ha cambiato la forma. Ha cambiato il costo di produrla, e—più importante—il costo di *trovarla* dopo.

Quell'ultimo cambiamento è quello che nessuno nota. Nel 1975, una copia di una fattura viveva in un archivio, in una cartella, sotto il nome di un cliente, e trovarla richiedeva una persona che conoscesse il sistema. Nel 2026, vive in un database e può essere trovata da chiunque sa digitare il nome di un cliente—che significa che può essere trovata dalla persona che è effettivamente al telefono, anziché dalla persona che per caso sa dove è la cartella.

## L'archivio

Ogni documento che lascia l'edificio deve essere trovabile in seguito, e questo è dove l'abitudine di una piccola azienda e la capacità di un sistema di solito divergono.

Odoo conserva ogni documento registrato e può rigenerare il suo PDF in qualsiasi momento, che significa che il *file* non deve essere archiviatoseparatamente: il documento sono i dati, e il PDF è una loro vista. È elegante, ed è anche leggermente allarmante la prima volta che lo senti—che succede se il modello cambia e la fattura si stampa diversamente tra un anno?

La risposta è che lo farà, e che questo è accettabile, perché ciò che conta è il *contenuto* e il contenuto è salvato. Se la tua giurisdizione richiede il PDF esatto come emesso, Odoo può allegare il PDF generato al record quando viene registrato, e il file è allora fisso. Riverton lo fa per le fatture inviate all'estero, dove l'autorità fiscale è più esigente, e non per quelle nazionali.

## La stampante, e tutto ciò che va sbagliato con essa

Un capitolo sulla stampa che non menzionasse la stampante sarebbe un capitolo scritto da qualcuno che non ha mai lavorato in un ufficio.

La stampante è il componente meno affidabile di tutto lo stack, ed è quello che fallisce nel momento di massima urgenza—che è la natura delle stampanti. Tre cose valgono la pena di essere sapute.

**Stampare su PDF non è stampare.** Ogni documento descritto in questo capitolo può essere prodotto come PDF senza che una stampante sia coinvolta, e per le fatture e gli estratti conto è ciò che un'azienda dovrebbe fare: generare il PDF, allegarlo a un'email, e tenere la carta per le cose che necessitano di una firma. La stampante di Riverton è usata per le note di consegna e la relazione di magazzino del venerdì, e per nient'altro.

**Un documento che è stato stampato non è un documento che è stato inviato.** Sembra ovvio ed è la fonte della fattura Ashfield all'inizio di questo libro. Il sistema sa che il PDF è stato generato; non sa se l'email è stata inviata. Se l'invio conta, l'invio deve essere registrato—che è uno dei motivi per cui le alla fine automatizzano l'intero passo, così che il record esista.

**L'inceppamento di carta è un rischio aziendale.** Una nota di consegna che non può essere stampata è una consegna che non può partire, perché il conducente non andrà senza la carta che il cliente firma. Ogni azienda che dipende da una stampante al piano di carico deve averne una seconda, o un modo per stampare la nota all'indirizzo del cliente. Riverton l'ha imparato un sabato, e ora tiene una di scorta in un armadio.

## Le tre cose che va sbagliato con una serie di stampa

Ogni azienda che stampa documenti ha incontrato queste tre, e ognuna ha una soluzione economica.

**Il modello cambia e nessuno nota.** Un logo aggiornato, un indirizzo cambiato, un dato bancario corretto—e il modello mostra ancora quello vecchio perché il cambiamento è stato fatto sul record dell'azienda e il modello legge una copia. I modelli di Odoo leggono il record dell'azienda direttamente, quindi questo è più raro che nei sistemi che copiano; ma un modello personalizzato può comunque hardcodare un valore, e il modo per scoprirlo è stampare un documento dopo ogni cambiamento e leggerlo.

**La carta è delle dimensioni sbagliate.** Una nota di consegna progettata per l'A4 stampata sulla stampante A5 del furgone perde la sua colonna di destra—che è dove sono le quantità. La soluzione è un secondo modello per il formato piccolo, o una stampante che accetta l'A4, ed vale la pena deciderlo prima della prima consegna piuttosto che dopo.

**La copia del cliente e la copia di archivio divergono.** Qualcuno scrive sulla copia stampata—una nota, una correzione, una firma—e l'archivio mantiene la versione immacolata. Quello è corretto per la fattura e sbagliato per la nota di consegna: la nota firmata *è* il record, e deve essere scannizzata o archiviata, non buttata via perché "è nel sistema".

## Cosa significa una firma

La nota di consegna torna con uno scarabocchio sopra, e lo scarabocchio è la cosa più legalmente interessante di tutto lo stack.

Una firma su una nota di consegna è un riconoscimento: *ho ricevuto questa merce, in questa quantità*. Non è un contratto—il contratto era l'ordine—e non è una ricevuta di pagamento. È una prova, e il suo valore è che è stata fatta nel momento della consegna da qualcuno che c'era.

È per questo che la nota di consegna è ancora stampata, e che all'assistente non è permesso segnare una consegna come firmata. La firma è un atto fisico di una terza parte, e nessuna quantità di software può eseguirlo. Ciò che il software può fare è assicurarsi che la nota che viene firmata sia quella giusta: il cliente giusto, l'ordine giusto, le quantità giuste, e una pagina che il conducente possa realmente leggere in un furgone.

Il giorno in cui la nota è firmata e torna, qualcuno valida la consegna nel sistema—e la carta va in una cartella per sei anni, perché è così a lungo che un'azienda può aver bisogno di provare che la merce è arrivata.

## L'archivio dei documenti inviati

C'è una domanda che un'azienda fa a sé stessa la prima volta che un cliente contesta una fattura di due anni fa: *possiamo provare ciò che abbiamo inviato?*

La risposta dipende da una decisione fatta molto tempo prima, ed vale la pena farla deliberatamente: il sistema conserva il *documento* o i *dati*?

Conservare i dati—il record della fattura e le sue righe—significa che il PDF può essere rigenerato in qualsiasi momento, e apparirà come il modello di oggi anziché quello usato al momento. Per la maggior parte degli scopi quello è sufficiente, ed è ciò che Odoo fa per impostazione predefinita.

Conservare il documento significa allegare il PDF generato al record quando viene registrato, così che il file sia fisso. Questo costa poche centinaia di kilobyte per fattura e risolve ogni discussione su ciò che è stato inviato, nella forma in cui è stato inviato.

Riverton allega il PDF per le fatture ai clienti all'estero, dove l'autorità fiscale è più esigente, e per i due contratti che contano. Per le fatture nazionali si affida ai dati, che è una decisione che Doreen ha preso dopo aver chiesto al suo commercialista, e che rivede ogni anno.

---

I raccoglitori sullo scaffile sono l'eccezione che dimostra la regola: le cose che devono essere firmate sono ancora carta, perché una firma è ancora un atto fisico nella maggior parte del mondo. Tutto il resto è diventato un file, e lo scaffile non è cresciuto in un anno.

Doreen se ne è accorta prima di chiunque altro.

"Lo scaffile si riempiva di giugno," ha detto. "Dovevo cominciarne uno nuovo. Quest'anno ne ho usati circa quattro pollici."

L'ha osservato per un momento.

"È strano. Ho passato trenta anni a fare carta, e non mi manca. Quello che mi manca è sapere dove sono le cose—e l'ho riavuto, in un modo diverso."

Quello è il scambio che l'intero libro ha stato descrivendo, detto dalla persona che lo ha realizzato: non la scomparsa della carta, ma il ritorno del sapere dove sono le cose, senza bisogno di essere la persona che le ha archiviate.
