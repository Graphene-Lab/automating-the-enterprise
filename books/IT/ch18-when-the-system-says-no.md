# 18. Quando il sistema dice di no

Il primo rifiuto arrivò un pomeriggio di giovedì, e fu il momento in cui Doreen cessò di sospettare del sistema e iniziò a fidarsi di lui.

Aveva chiesto all'assistente di correggere un errore: una fattura era stata registrata con la quantità sbagliata, e voleva che fosse corretta.

> *Cambia la quantità della fattura INV/2026/0007 da 350 a 300.*

> *Non posso cambiarla. INV/2026/0007 è registrata, e le fatture registrate sono di sola lettura: le scritture in bilancio e il momento fiscale sono già registrati. Per correggerla, annulla la fattura e emetti una nota di credito, oppure emetti una nota di credito per la differenza. Quale preferisci?*

Doreen la lesse due volte, poi chiamò Maggie.

"Non vuole farla," disse.

"Non vuole o non può?"

"Non può. Dice che il bilancio è già scritto."

Questa distinzione—*non vuole* versus *non può*—è l'argomento di questo capitolo, ed è la ragione per cui un sistema aziendale differisce da un collega disponibile.

---

## I tre tipi di no

Un ERP rifiuta per tre motivi diversi, e vale la pena imparare a distinguerli, perché ciascuno richiede una risposta diversa.

**Il sistema non può farla perché il modello lo vieta.** Non puoi registrare una fattura senza righe, consegnare merci che non possiedi, o cambiare un documento che ha già prodotto scritture in bilancio. Questi rifiuti sono strutturali: proteggono l'integrità del modello, e non c'è alcuna possibilità di superarli, perché un superamento romperebbe la garanzia che rende il modello utile.

**Il sistema non può farla perché l'*utente* non è autorizzato.** L'assistente è un utente con un ruolo, e se il ruolo non include l'eliminazione di record, la richiesta viene rifiutata dal sistema di prima prima di raggiungere il modello. Questi rifiuti riguardano l'autorità, e possono essere cambiati—da chi ha il diritto di cambiarli, deliberatamente, e con traccia del fatto.

**Il sistema non può farla perché i *dati* non ci sono.** Il cliente non esiste, il prodotto non ha prezzo, le scorte sono in una posizione che l'utente non può vedere. Questi rifiuti riguardano lo stato del mondo, e sono di solito i più utili, perché indicano qualcosa che va corretto piuttosto che qualcosa che va superata.

Un buon assistente ti dice quale tipo di no è. È quello che è successo sopra: il rifiuto nominava il documento, il motivo, e due alternative legittime.

## I rifiuti che hanno insegnato qualcosa a Riverton

Nei primi mesi, il sistema disse di no in un paio di modi, ognuno dei quali era una piccola lezione.

**"Sufficiente scorta."** Tom chiese una consegna di seicento binder quando ce ne erano quattrocentododici. Il sistema rifiutò, e propose di consegnare ciò che era disponibile e di creare un backorder per il resto. Tom scelse il backorder, e il cliente fu telefonato prima che il van partisse—che è tutto il punto del rifiuto: spostò la conversazione dal piano di carico al telefono, dove poteva ancora essere utile.

**"Il periodo contabile è chiuso."** Doreen cercò di registrare una fattura datata il mese precedente, dopo che il mese era stato bloccato. Il sistema rifiutò e spiegò che il periodo era chiuso. Spostò la fattura al mese corrente, poi chiese all'assistente una lista di tutto ciò che era stato registrato dopo la chiusura—che tornò vuota, che è a ciò che serve un periodo chiuso.

**"Questo utente non può eliminare record."** L'assistente, chiesto di rimuovere un cliente duplicato, disse che non poteva, e propose di archiviarlo invece. L'archiviazione mantiene il record e lo nasconde dalle liste, che è la risposta corretta per un duplicato che ha documenti allegati. Il rifiuto era stato configurato di proposito, nel capitolo dodici, da qualcuno che ci aveva pensato in anticipo.

**"Questo prodotto non ha tasse."** Un nuovo prodotto era stato creato senza un tasso di tassazione, e la quotazione rifiutò di calcolare un totale. Il rifiuto indicava il modulo del prodotto, e la correzione richiese trenta secondi. Senza il rifiuto, la quotazione sarebbe uscita senza IVA—e la company l'avrebbe scoperta alla fine del trimestre, in una dichiarazione che non tornava.

## Leggere il log

Ogni rifiuto lascia una traccia, e imparare a leggere la traccia è la competenza che trasforma un assistente da scatola nera in un collega.

L'assistente scrive un log: ciò per cui gli era stato chiesto, quali strumenti ha scelto, con quali argomenti, cosa è tornato, e quanto tempo ha richiesto. Non è un documento bello—è un file, in una cartella, con timestamp—ed è il primo luogo dove guardare quando qualcosa è andato storto.

Tre modelli valgono la pena di essere riconosciuti.

**Un loop.** Lo stesso strumento chiamato con gli stessi argomenti, tre o quattro volte. È l'assistente che cerca di far funzionare qualcosa e fallisce nello stesso modo ogni volta—di solito perché un documento è in uno stato che non si aspettava. Il rifiuto è nel log, tre volte, e leggerlo una volta basta.

**Uno strumento sbagliato.** L'assistente scelse *create* quando avrebbe dovuto scegliere *update*, e l'ERP rifiutò perché il record esisteva già. Il log mostra la scelta; la correzione è nell'istruzione, che non diceva *update*.

**Un successo silenzioso che non era ciò che si voleva.** Nessun errore, nessun rifiuto, e un risultato che è tecnicamente corretto e praticamente inutile. Questo è il modello più difficile, perché nulla nel log sembra sbagliato. La difesa è il controllo: chiedi all'assistente cosa ha fatto, e confrontalo con ciò che intendevi.

Doreen legge il log ogni venerdì, per la stessa ragione per cui leggeva l'estrazione di conto: non perché si aspetta un problema, ma perché leggerlo è come si impara cosa sia il normale—e quindi come si nota quando non lo è.

## Il rifiuto che ha salvato un cliente

Un rifiuto nel primo anno di Riverton valeva più di qualsiasi successo, e accadve nel mezzo di una discussione.

Un cliente—uno grande, e difficile—aveva ricevuto una fattura per una consegna che affermava non fosse mai arrivata. La nota di consegna era firmata, ma la firma era illeggibile, e il manager degli acquisti del cliente insisteva che le merci fossero state rifiutate al cancello.

Priya chiese all'assistente di emettere una nota di credito, perché il cliente minacciava di portare il suo altrove e la fattura era di £640.

Il sistema rifiutò, e il motivo che diede è il motivo per cui questa storia è nel libro.

> *Posso creare una nota di credito, ma dovresti sapere come apparirà nel bilancio: una nota di credito senza un ritorno dietro di essa registra che le merci non sono mai state fornite. La consegna è stata validata il 3 settembre da Tom Beck, e lo spostamento di stock mostra 40 articoli lasciare la scaffaleria A. Se il cliente ha rifiutato la consegna, le merci dovrebbero tornare e non c'è un ritorno registrato. Se non l' hanno rifiutata, la nota di credito pagherebbe merci che sono state consegnate. Quale delle due?*

Priya telefonò al cliente, fece la domanda che l'assistente aveva fatto, e scoprì che la consegna era stata accettata da una guardia di sicurezza temporanea che aveva messo il pallet in una stanza di deposito e non aveva detto a nessuno. La fattura fu pagata in pieno, e il cliente si scusò.

Il rifiuto non salvava £640. Salvava una relazione, e lo faceva rifiutandosi di lasciare che una persona saltasse una domanda—che è ciò che un buon contabile ha sempre fatto, e ciò che questo sistema fa perché qualcuno lo ha configurato per.

## I rifiuti che una company dovrebbe progettare di proposito

La maggior parte dei rifiuti arrivano con il software. Alcuni dovrebbero essere aggiunti, deliberatamente, e sono quelli che trasformano un ERP da sistema di registrazione a sistema di controllo.

Quattro valgono la pena di essere considerati in qualsiasi company che permetta a un assistente di scrivere.

**Un limite di credito sui clienti.** Quando un ordine porterebbe un cliente sopra il suo limite, il sistema può rifiutarsi di confermarlo, o richiedere approvazione. L'assistente allora riferirà il rifiuto e il numero, che è esattamente la conversazione che un venditore dovrebbe avere con il proprietario—prima che le merci partano, non dopo.

**Uno sconto massimo.** Odoo può essere configurato in modo che uno sconto sopra una soglia richieda una seconda persona. L'assistente non può concederlo, perché l'assistente è un utente con un ruolo; può solo dire chi potrebbe.

**Un periodo chiuso.** Una volta che un mese è bloccato, nulla si registra in esso, da chiunque, incluso l'assistente. Quella è la singola più efficace tra le controlli in tutto il sistema, e costa una configurazione.

**Una regola dei quattro occhi sui pagamenti.** In Odoo questa è una configurazione del processo di pagamento, non una caratteristica dell'assistente, ma l'effetto è lo stesso: l'assistente prepara la corsa di pagamento, una persona la rilascia.

Nessuno di questi è una formalità. Ognuno codifica una decisione che la company ha già preso su come vuole essere gestita, e ognuno trasforma quella decisione in qualcosa che non può essere dimenticato in un venerdì affollato.

## Cosa costa un rifiuto

C'è un costo nella severità, ed vale la pena nominarlo perché le company che lo ignorano finiscono per spegnere le regole.

Un rifiuto ferma il lavoro. Qualcuno deve smettere ciò che sta facendo, scoprire perché, e o correggere i dati o chiedere una eccezione. In una small company, quello qualcuno è spesso il proprietario, e il proprietario è spesso la persona più occupata nell'edificio.

Il costo è reale, e il modo per tenerlo piccolo non è indebolire la regola ma rendere il rifiuto *informativo*. Un messaggio che dice *limite di credito superato: £2.310 di £2.000, cliente Calder and Sons, ultimo controllo a marzo* dice alla persona cosa fare. Un messaggio che dice *accesso negato* non lo fa.

Quello è l'argomento per un assistente davanti a un ERP in una frase: le regole sono dell'ERP, e l'*spiegazione* è dell'assistente.

## Perché la severità è la caratteristica

C'è una tentazione, quando un sistema rifiuta qualcosa, di cercare la configurazione che spegne il rifiuto. La maggior parte degli ERP hanno tali configurazioni, e la maggior parte di esse sono un errore.

Considera cosa proteggono i rifiuti.

Il rifiuto di modificare una fattura registrata protegge la **traccia di revisione**: il record di ciò che è stato inviato al cliente, e quando. Una company che può modificare la propria storia non può dimostrare nulla su di essa.

Il rifiuto di consegnare scorta che non c'è protegge la **promessa**: il cliente è stato informato di una data, e la data dipende da merci che esistono.

Il rifiuto di registrare in un periodo chiuso protegge gli **conti**: un periodo è chiuso perché qualcuno ha riportato su di esso—alla bank, all'ufficio tasse, ai proprietari—e riaprirlo silenziosamente renderebbe la relazione una menzogna.

Il rifiuto di lasciare che un utente elimini protegge la **responsabilità**: se un documento può svanire, allora l'assenza di un documento non significa nulla.

Nessuno di questi è sulla pulizia. Ognuno è sulla uno proprietà che rende un ERP vale il suo costo: che ciò che dice è vero, e può essere mostrato come vero.

## La parte dell'assistente in questo

Un assistente rende i rifiuti *migliori*, in un modo che è facile trascurare.

Una persona che incontra un rifiuto in uno schermo vede una casella rossa con un codice e una frase. Un assistente che incontra lo stesso rifiuto può spiegarlo nel linguaggio del business, offrire le alternative, e fare quello legittimo se sei d'accordo. Quella è la differenza tra *Errore: non si può modificare una registrazione registrata* e *la fattura è registrata, quindi non si può modificare; posso emettere una nota di credito per la differenza, o annullare e riemettere—quale vuoi?*

C'è un rischio in quella fluidità, ed vale la pena nominarlo: un assistente che spiega i rifiuti in modo utile può farli sentire negoziabili. Non lo sono. La spiegazione è una cortesia; la regola è la regola. L'assistente non può superare l'ERP, perché l'assistente non è l'autorità—e qualsiasi assistente che afferma il contrario ha ricevuto troppo potere, che è un difetto nell'installazione, non una caratteristica del modello.

## L'unico rifiuto che non è un rifiuto

C'è un quarto tipo di no, ed è il più pericoloso perché sembra un sì.

L'assistente, chiesto una la cui risposta non è nel sistema, può rispondere *plausibilmente*. Non perché mente, ma perché è ciò che fa un modello linguistico quando non ha fatti: produce la frase più probabile. Questo è il problema dell'illusione, e la difesa è architettonica, non morale: l'assistente deve essere fatto ottenere i suoi dati dall'ERP, attraverso gli strumenti, e dire quando lo strumento torna nulla.

La regola di Riverton, sul parete accanto al tovagliolo, è una singola frase: *se non può mostrarti da dove viene il numero, non usare il numero.*

Quella regola è perché ogni risposta in questo libro include i documenti dietro di essa—il numero di fattura, l'ordine, la lista di movimenti. Non è decorazione. È la differenza tra un sistema che puoi revisionare e un sistema che hai credenza.

---

Doreen emise la nota di credito, e la fattura restò.

Quella sera disse qualcosa a Maggie che nessuno dei due si aspettava.

"Mi piace che discuta con me."

"Perché?"

"Perché il mio vecchio sistema faceva qualsiasi cosa digitavo. Se digitavo il numero sbagliato, prendeva il numero sbagliato, e non mi diceva mai. Questo mi fa dire ciò che intendo."

Pensò per un momento.

"È come avere un contabile che lo fa da seicento anni e non ha modi."

Che è, più o meno, esattamente ciò che sono le regole di Pacioli: senza modi, senza memoria delle tue scuse, e senza interesse su se sei di fretta. Solo le due facce della pagina, e il rifiuto di lasciare che discordino.
