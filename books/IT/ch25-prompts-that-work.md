# 25. Prompt che funzionano

Verso la primavera, Riverton aveva un documento sul drive condiviso chiamato *Come chiedere*, ed era lungo quattro pagine. Nessuno l'aveva scritto come manuale; era cresciuto da un filad i email in cui le persone pubblicavano le istruzioni che avevano funzionato, e quelle che non avevano funzionato, e quando Maggie lo stampò era diventato il documento più letto dell'azienda.

Questo capitolo è quel documento, riscritto.

---

## Le quattro parti di una istruzione

Ogni istruzione che funzionava, nei mesi di test che precedono questo libro, aveva quattro parti, che la persona che la scriveva ne fosse consapevole o no.

**Un verbo.** Cosa fare. *Elencare. Creare. Modificare. Annullare. Totalizzare. Confrontare. Inviare.* Una istruzione senza verbo è un argomento, e l'assistente risponderà con un paragrafo di conversazione piuttosto che con lavoro.

**Un oggetto.** A cosa farlo, nominato nel modo in cui l'azienda lo nomina. *Le fatture per Ashfield Academy. I raccoglitori con anelli. L'ordine d'acquisto di martedì.* Se l'oggetto è ambiguo—*l'ordine*—l'assistente deve indovinare, e indovinerà in modo plausibile piuttosto che corretto.

**Un ambito.** Quali, quanti, su quale periodo. *Fatture non pagate più vecchie di trenta giorni. Ordini dello scorso mese. I cinque prodotti con il minor magazzino.* L'ambito è dove falliscono la maggior parte delle istruzioni, perché un essere umano che chiede a un collega si appella a un contesto condiviso, e l'assistente non ne ha alcuno se non gli viene fornito.

**Un vincolo, quando c'è.** *Ai prezzi standard. Consegna lunedì prossimo. Non pubblicarla ancora.* Un vincolo è la differenza tra una bozza e un impegno, ed è la parte che le persone dimenticano, e poi incolpano la macchina per aver fatto ciò per cui era stata istruita.

Confrontate:

> *Fate le fatture.*

> *Create fatture da ogni ordine di vendita confermato datato la settimana scorsa, lasciatele in bozza, e datemi il totale.*

La prima è ciò che le persone digitano quando hanno fretta, e la risposta che ottengono è o una domanda o un'indovinazione. La seconda sono quaranta secondi di digitazione e produce lavoro.

## La differenza tra una domanda e un'azione

L'assistente può fare due cose molto diverse, e le stesse parole possono scatenare l'una o l'altra.

Una **domanda** produce una risposta: *quanti clienti ci devono del soldi?* Nulla nell'ERP cambia.

Un'**azione** produce un documento: *crea la fatture.* L'ERP cambia, permanentemente, con un timestamp e un nome utente allegati.

La differenza conta perché le due hanno diversi costi dell'errore. Una risposta sbagliata costa un minuto; una fattura sbagliata costa un pomeriggio. L'abito sicuro—e quello che il libro raccomanda desde il primo giorno—è chiedere prima la domanda, e poi agire sulla risposta:

> *Quali fatture sono in ritardo di più di trenta giorni? Elencatele con l'importo e il cliente.*

e poi, dopo aver letto l'elenco:

> *Create un promemoria per le tre più grandi, in bozza, e datemi il testo prima di inviarlo.*

Questo abito a due passi non è timidezza. È il modo in cui un buon impiegato lavora con un nuovo sistema: guardare, poi agire.

## Nominare le cose nel modo in cui l'azienda le nomina

Un ERP ha tre nomi per tutto: il nome sul record, il riferimento interno, e il nome che le persone usano. L'assistente lavora con i primi due, e il terzo è quello che avete in testa.

Riverton scoprì questo la prima settimana. Qualcuno chiese *i raccoglitori blu* e ottenne un elenco di nulla, perché il prodotto si chiama *Raccoglitore con anelli A4*, con una variante di colore, e la parola "blu" vive nella variante, non nel nome. Una volta che la richiesta divenne *Raccoglitori con anelli A4, variante blu*, funzionò.

La soluzione non è insegnare all'assistente i sinonimi. La soluzione è un'abito aziendale: quando un prodotto, un cliente o un documento ha un nome nel sistema, usate quel nome nella istruzione. È la stessa disciplina di quando usate il numero di conto del cliente quando telefonate alla banca.

## Le istruzioni che funzionano meglio

Quattro tipi di istruzione produssero i migliori risultati nei test, e valgono la pena di essere appresi deliberatamente.

**La spazzata.** *Elencate tutto ciò che corrisponde a questa condizione.* Le spazzate sono dove l'assistente batte una persona apertamente, perché una persona deve aprire schermi e l'assistente non lo fa. *Ogni fatture non pagata per più di trenta giorni. Ogni prodotto sotto il suo punto di riordino. Ogni cliente che non ha ordinato da gennaio.*

**La catena.** *Fate questo, poi quello, poi datemi il risultato.* Le catene sono la seconda grande forza dell'assistente: non perde il filo tra uno step e l'altro. *Create l'ordine, confermatelo, consegnatelo, fatturatelo, e datemi il numero di fattura.*

**Il confronto.** *Confrontate questo periodo con quell'altro.* I confronti sono dove una persona dovrebbe esportare due fogli di calcolo. *Confrontate le vendite di questo mese con lo stesso mese dello scorso anno, per prodotto.*

**L'eccezione.** *Datemi solo notizia delle cose che sono sbagliate.* Questa è la più preziosa e la meno usata. *Mostratem i gli assestamenti di magazzino dove la ragione è mancante. Mostratem i le fatture il cui totale non corrisponde all'ordine.*

## Cosa non chiedere

Quattro tipi di istruzione produssero nulla di utile, e i fallimenti sono abbastanza costanti da valere la pena di essere nominati.

**Il verbo vago.** *Gestite le fatture. Sistemate il magazzino. Occupatevi dei conti in ritardo.* L'assistente chiederà cosa intendete, che è il comportamento corretto e uno spreco di un minuto.

**La richiesta di un giudizio che non può fare.** *Quali clienti valgono la pena di essere mantenuti?* Può darvi i numeri—fatturazione, margine, comportamento di pagamento, da quanto tempo sono stati—e può classificarli. Non può dirti cosa valora la vostra azienda, perché quello non è nel database.

**La istruzione che dipende da qualcosa che non è nel sistema.** *Fatturate il lavoro che abbiamo fatto per la scuola giovedì scorso.* Se il lavoro non fu mai registrato, l'assistente troverà nulla, e la risposta corretta è nulla. Questo non è un limite dell'assistente; è lo stesso limite che ha un nuovo impiegato, e la cura è la stessa: scriverlo.

**La istruzione che la fa indovinare.** *Create il cliente da questo email.* Può leggere l'email se gli date l'email; non può leggere la vostra casella di posta a meno che qualcuno non gli abbia dato quello strumento, e non inventerà un indirizzo per essere utile. Se volete che estraga, ditelo: *leggete questo email e proponete il record del cliente, ma non createlo finché io non lo dico.*

## L'abito di verifica

Ogni istruzione che produce un'azione deve essere seguita da un controllo, e il controllo deve essere la risposta dell'assistente a una domanda su ciò che ha fatto.

> *Confermate l'ordine.*
>
> *Quale ordine avete confermato, e qual è il suo totale?*

La seconda istruzione costa cinque secondi e chiude il gap tra ciò che intendevate e ciò che è successo. Nei mesi di test, questo abito catturò ogni errore che contava, e gli errori che catturò furono quasi sempre *definizione*, non aritmetica: l'assistente aveva fatto esattamente ciò che era stato chiesto, e ciò che era stato chiesto non era ciò che era stato inteso.

## La istruzione che chiede un giudizio

C'è una categoria di istruzione che le persone scrivono costantemente e che quasi mai funziona, ed vale la pena di essere nominata perché sembra così ragionevole: la istruzione che chiede all'assistente di decidere.

*Quali clienti dovremmo inseguire? Quali prodotti dovremmo interrompere? Questo fornitore è troppo costoso?*

Ognuna di quelle è una decisione, e una decisione ha tre cose che l'assistente non ha: cosa valora l'azienda, quali sono le alternative, e chi sopporta le conseguenze. Ciò che l'assistente ha è dati, e la versione utile di ogni domanda gli fornisce i dati e mantiene la decisione:

*Elencate i clienti con una fatture in ritardo e nessun ordine in novanta giorni, con l'importo e la data dell'ultimo ordine.* La decisione—inseguire, aspettare, o scriver via—è poi fatta da una persona, in un minuto, con i fatti davanti a sé.

La distinzione non è pedanteria. Un'assistente che risponde a una domanda di giudizio produce una risposta *plausibile*, che è peggiore di nessuna risposta, perché invita qualcuno ad agire su di essa senza aver pensato. Un'assistente che produce i fatti produce qualcosa con cui una persona può pensare.

## Insegnare a un collega

Il documento sul drive condiviso di Riverton era lungo quattro pagine perché qualcuno lo scrisse, e l'atto di scriverlo vale una sezione a parte.

Quando un'azienda adotta questa tecnologia, la conoscenza di come usarla vive in una o due persone, ed è di solito tacita: sanno che *i raccoglitori blu* non funziona e *Raccoglitori con anelli A4, variante blu* sì, e non potrebbero dirvi perché. Quella conoscenza vale più del software, ed evapora quando la persona se ne va.

La cura è la più antica del mondo: tenere un elenco delle istruzioni che funzionavano, nel linguaggio dell'ufficio, con una riga su ciò che ciascuna è per. Non un manuale—un manuale è scritto da qualcuno che ha cessato di fare il lavoro. Un elenco è scritto da qualcuno che lo sta facendo.

L'elenco di Riverton ha tre sezioni, e la terza è quella che conta.

**Istruzioni che funzionano**, raggruppate per dipartimento, una riga ciascuna, con l'output annotato.

**Istruzioni che fallirono**, con ciò che era sbagliato—perché i fallimenti sono dove è l'apprendimento, e perché un elenco di successi non insegna a nessuno nulla.

**Istruzioni che non abbiamo ancora provato**, che è una lista di desideri. *Può darmi notizia di quali clienti sono profittevoli? Può confrontare la fattura di un fornitore con l'ordine senza che io chieda? Può preparare la dichiarazione IVA e conciliarla?* Alcune di quelle funzioneranno e alcune no, e l'elenco è come un'azienda scopre quali.

## Gli anti-patterns, in un'anzianità anziché in un prompt

Quattro abiti appaiono in ogni azienda che adotta un'assistente, ed sono tutti ragionevoli e tutti dannosi.

**L'eroe.** Una persona diventa la persona che sa come chiedere, e tutti gli altri chiedono a lei. L'azienda ora ha un collo di bottiglia con uno stipendio, e la conoscenza è in una testa—che è esattamente la condizione per cui il sistema fu comprato per curare.

**Lo scettico.** Una persona decide che la tecnologia è un giocattolo, e le fa domande progettate per farla fallire, in pubblico. Riusciranno, perché qualsiasi sistema può essere fatto fallire da una domanda che è fuori dai suoi dati. Il costo non è il fallimento; è che il resto dell'ufficio impara a temere di sembrare sciocco.

**La eccessiva fiducia.** Una persona decide che la macchina è sempre corretta, e cessa di controllare. Questo dura finché il primo errore definizione raggiunge un cliente, e poi la reazione è severa—di solito un ritorno alla carta per un mese, che costa più dell'errore.

**Il fantasma.** Il sistema è installato, lodato in una riunione, e mai usato, perché la persona che doveva usarlo era occupata quella settimana e il vecchio modo funzionava ancora. Sei mesi dopo si scopre che la licenza è pagata per un programma che nessuno apre.

L'antidoto per tutti e quattro è lo stesso: una persona *nominata*, un'ora *protetta* a settimana, e una *dimostrazione* una volta al mese in cui qualcuno mostra all'ufficio qualcosa che l'assistente fece che fu utile. Non una sessione di formazione; una dimostrazione. La differenza è che una dimostrazione è sul lavoro, e una sessione di formazione è sul software.

## Il diario dei prompt

C'è un ultimo abito vale la pena adottare, e non costa nulla.

Tenete le istruzioni che digitaste. Non perché dovrete ripeterle—anche se lo farete—ma perché il diario è la registrazione di ciò che l'azienda chiese, e la registrazione di ciò che la macchina comprese.

Odoo tiene il *risultato*: la fattura, l'ordine, il pagamento. Non tiene la frase che la produsse. L'assistente tiene il suo proprio log, ma un log è un artefatto tecnico con timestamp e chiamate di strumenti; non è la storia della giornata.

Un diario è una riga per istruzione, in un file di testo, con la data. Sei mesi dopo risponde a domande che nient'altro può rispondere: *quando iniziammo a inseguire a quindici giorni? Cosa le chiedemmo di fare nella settimana in cui la fatture di Ashfield sbagliò? Qualcuno le chiese mai di confrontare due mesi?*

È la forma più economica di memoria istituzionale che ci sia, e l'unica che una piccola azienda manterrà effettivamente.

## Dove vivono le istruzioni

Il prossimo capitolo è la biblioteca: più di cinquanta istruzioni, raggruppate per dipartimento, ognuna eseguita su un'installazione reale durante la scrittura di questo libro, con il risultato registrato.

Non sono uno script da leggere ad alta voce. Sono un vocabolario. Leggete quelle per il vostro dipartimento, adattate i nomi alla vostra azienda, e aggiungete quelle che mancano—perché la biblioteca che conta è quella che il vostro ufficio scrive per sé stessa, nel linguaggio che effettivamente parla.

C'è un'ultima cosa da dire sui prompt, ed è quella che a Riverton ci mise più tempo a imparare.

La istruzione non è una formula magica. È una *delegazione*, ed porta le stesse oblicazioni di quando si delega a una persona: dite ciò che volete, dite ciò che non volete, date alla persona l'informazione di cui ha bisogno, e controllate il risultato. Le aziende che ottengono valore da questa tecnologia non sono quelle con i prompt più intelligenti. Sono quelle che delegano bene—che, a quanto accade, è anche la differenza tra un buon manager e un cattivo, ed è così da molto prima che ci fossero macchine a cui delegare.
