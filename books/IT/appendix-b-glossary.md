# Appendice B — Un glossario per chi non programma

Ogni parola qui sotto è una di quelle che questo libro ha usato, o che qualcuno userà con te mentre installi il sistema. Le definizioni sono volutamente semplici e occasionalmente imprecise; dove una definizione precisa avrebbe aiutato un programmatore e confuso un responsabile d'ufficio, ha vinto quella semplice.

**Agente.** Un programma che può ricevere una istruzioni in lingua ordinaria e agire su di essa—cercare informazioni, creare registrazioni, eseguire un processo—invece di limitarsi a rispondere con del testo. In questo libro, l'agente è AgentBridge, il programma con cui parli in una finestra di terminale.

**API.** Application Programming Interface. Un modo documentato per cui un programma ne chiede un altro di fare qualcosa. Pensalo come lo sportello di servizio di un ristorante: la cucina non vuole che tu entri in cucina, ma c'è un modo corretto per consegnare un ordine e ricevere un piatto.

**Chiave API.** La password che un programma usa invece di un essere umano. È una lunga sequenza di caratteri, viene mostrata una sola volta, e va trattata come una chiave della cassaforte: tenuta in un gestore di password, mai in una email, mai in un documento che viene inoltrato.

**Backup.** Una copia dei dati prelevata in un momento preciso, conservata in un luogo diverso dalla macchina che contiene l'originale. Un backup non verificato è un desiderio; un backup che hai aperto e letto è un backup.

**Database.** Un programma il cui compito è conservare i fatti e restituirli in modo accurato, anche quando l'alimentazione si interrompe in mezzo a una modifica. In questo libro, PostgreSQL.

**Documento (in un ERP).** Non un pezzo di carta: una registrazione di qualcosa che è successo o succederà—un ordine, una consegna, una fattura, un pagamento—con una data, una parte, una lista di righe e uno stato. I documenti conservano la propria copia dei fatti con cui sono stati creati, in modo che la fattura di mese scorso mostri ancora il prezzo di mese scorso.

**ERP.** Enterprise Resource Planning. Software che conserva il cliente, il prodotto, l'ordine, le scorte, la fattura e la contabilità in un unico modello collegato, in modo che un fatto inserito una volta sola sia visibile ovunque. Il nome fu coniato dalla società di analisi Gartner nel 1990.

**Campo.** Un'informazione in una registrazione: il numero di telefono del cliente, il prezzo di un prodotto, la data di una fattura.

**Voce di registro.** La registrazione contabile a doppia entrata che produce ogni evento finanziario: un importo in un conto e lo stesso importo, opposto, in un altro. Inventata molto prima del software; codificata da Luca Pacioli nel 1494; ancora la ragione per cui i libri possono essere verificati.

**JSON.** Un modo di scrivere i dati come testo, in modo che un programma possa inviarli a un altro. Ti capiterà di vederlo solo in un file di log, dove appare come un paragrafo di punteggiatura.

**Modello linguistico (LLM).** Un programma addestrato su una quantità enorme di testo, capace di produrre testo plausibile in risposta a una istruzione. È bravo con il linguaggio e inaffidabile con i fatti, a meno che non sia *radicato*—cioè a meno che non venga fatto cercare i fatti invece di ricordarli.

**MCP.** Model Context Protocol. Uno standard aperto, pubblicato da Anthropic nel novembre 2024, che permette a un programma di descrivere gli strumenti che offre a un assistente in modo uniforme. È la ragione per cui uno strumento scritto per un assistente può essere usato da un altro.

**Modello (in questo libro, due significati).** 1. La rappresentazione di una azienda all'interno di un ERP: parti, prodotti, documenti, denaro. 2. L'artefatto addestrato dietro un assistente: il "modello linguistico." Il contesto chiarisce quale; quando non lo fa, di solito il significato che conta è il primo.

**Modulo.** Un pacchetto che aggiunge una capacità a un ERP—contabilità, inventario, produzione, acquisti. Installare un modulo aggiunge schermate, registrazioni e regole; non cambia i dati sottostanti.

**Odoo.** Un ERP open-source, iniziato nel 2005 con il nome TinyERP, ribattezzato OpenERP nel 2008 e Odoo nel 2014. L'edizione Community è gratuita; l'edizione Enterprise è con licenza. La versione 20, usata in questo libro, è stata rilasciata nel settembre 2026.

**PostgreSQL.** Il database open-source usato da Odoo. Iniziò come progetto di ricerca all'Università della California a Berkeley negli anni '80 ed è ora uno dei database più usati al mondo.

**Prompt.** La istruzione che digiti verso l'assistente, in lingua ordinaria. Un buon prompt dice cosa vuoi, per chi, e per quando; un cattivo prompt dice "fai le fatture" e spera.

**Registrazione.** Una riga in una tabella: un cliente, un prodotto, una fattura.

**Schema.** La lista di tabelle e campi che un database contiene, e le regole su ciò che può entrarvi. Quando qualcuno dice "lo schema dice che un cliente deve avere un nome," intende che il database rifiuterà di salvare un cliente senza uno.

**Movimento di scorta.** La registrazione di merci che si spostano da un luogo a un altro: da un fornitore a un magazzino, da una mensola a un furgone, da un furgone tornato a una mensola perché il cancello della scuola era chiuso. Il livello di scorta di un prodotto è la somma dei suoi movimenti; non si digita mai direttamente.

**Token.** L'unità con cui si misura il lavoro di un modello linguistico. Grossolanamente, un token è tre quarti di una parola. I fornitori addebitano per token, ed è per questo che un documento molto lungo costa di più da elaborare rispetto a una domanda breve.

**Strumento (nel contesto di un assistente).** Un'unica azione che l'assistente è autorizzato a compiere, con un nome e una descrizione: *cercare clienti*, *creare una fattura*, *registrare un pagamento*. Un assistente senza strumenti può solo parlare. Un assistente con strumenti può lavorare.

**Transazione.** Una modifica che accade completamente o per niente. È la promessa che rende affidabile un database: non esiste uno stato in cui esista mezza fattura.

**Variante.** Una versione di un prodotto che differisce per un attributo—dimensione, colore, tensione. Un prodotto con dodici varianti non è dodici prodotti, e modellarlo correttamente è la differenza tra un report utile e uno inutile.

**Interfaccia web (o web UI).** Le schermate che vedi in un browser. L'interfaccia web di Odoo è dove configuri la azienda, guardi le registrazioni, e stampi i documenti; l'assistente è un secondo modo per raggiungere le stesse registrazioni.

**Flusso di lavoro.** La sequenza di stati che un documento attraversa—bozza, confermato, consegnato, fatturato, pagato—e le regole su chi può spostarlo da uno all'altro. In un buon ERP, il flusso di lavoro è la politica della azienda, scritta e fatta rispettare.
