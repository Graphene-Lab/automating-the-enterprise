# 23. L'ufficio in fondo al corridoio

L'assistente ha due porte d'ingresso, e la maggior parte delle aziende ne usa una per un mese prima di scoprire l'altra.

La prima è la finestra del terminale: sfondo nero, un prompt, e la risposta sottostante. È la porta che questo libro ha stato usando, perché è quella che mostra il lavoro—le chiamate agli strumenti, i passaggi intermedi, il log. È un laboratorio.

La seconda è una pagina web, all'indirizzo `http://localhost:5290/OfficeManager`, e non è un laboratorio. È un ufficio.

---

## Cosa mostra la pagina

La pagina disegna una piccola stanza. Ci sono scrivanie, una porta, una pianta, e diverse piccole figure che camminano, si sedono, si alzano, e occasionalmente si riuniscono alla macchinetta del caffè. Una di esse è il tuo agente. Sotto la stanza c'è una casella di chat.

![L'ufficio: una stanza, un lavoratore, e una casella di chat in fondo](../../assets/screens/assistant-01-office.png)

Quando arriva una istruzione, una figura appare alla porta e prende una scrivania, il pannello a destra mostra cosa sta facendo—*recuperare il contesto*, *cercare*, *creare*—e il log della chat registra lo scambio.

![La istruzione mentre arriva: l'agente ha preso una scrivania e sta lavorando](../../assets/screens/assistant-02-prompt.png)

Se questo sembra fantasioso, lo è—ed è anche l'interfaccia più efficace per questo genere di lavoro che Riverton abbia provato. Il motivo vale la pena di essere compreso, perché non riguarda la carinezza.

Una finestra di terminale mostra *una conversazione alla volta*, e mostra tutto: ogni chiamata agli strumenti, ogni risultato intermedio, ogni linea di ragionamento. Questo è esattamente ciò che vuoi quando stai costruendo o debuggando un compito. È esattamente ciò che non vuoi quando sei un responsabile d'ufficio con un cliente al telefono.

La pagina d'ufficio mostra *una cosa sola*: l'agente, e se è occupato. Le figure camminano quando l'agente sta pensando e si sedono quando è inattivo. Puoi vedere, dall'altra parte della stanza, se l'assistente sta lavorando—che sembra banale e in realtà è l'unica informazione più utile dell'intero sistema.

"Si capisce se è occupato senza leggere nulla," disse Priya. "Nel terminale devo guardare l'ultima riga. Qui basta guardare."

## Quando usare quale

Dopo un mese, le abitudini di Riverton si sono assestate in una semplice divisione.

**Il terminale per qualsiasi cosa che tocchi i soldi o cambi un documento.** Creare una fattura, pubblicare un conto, confermare un ordine. Il motivo non è che la pagina web non possa farla—può—ma che il terminale mostra i *passaggi*, e una persona che può vedere i passaggi può fermarli. Sul terminale, osservi l'assistente cercare il cliente, leggere il prodotto, creare il documento, e puoi vedere il momento in cui va sbagliato. Sulla pagina web vedi una bolla che dice "fatto", e devi fidarti.

**La pagina web per domande e operazioni rapide.** *Quante fatture scadute abbiamo? Quali prodotti sono bassi? Cosa abbiamo venduto la scorsa settimana?* Non si cambia nulla, la risposta è breve, e la metafora d'ufficio rende tutto ciò simile a chiedere a un collega piuttosto che a operare una macchina.

**La pagina web per chiunque non sia Maggie.** Tom la usa, Priya la usa, e Doreen—dopo qualche resistenza—la usa. Il terminale è intimidatorio in un modo che non ha nulla a che fare con il lavoro: sembra l'interno di una macchina, e la maggior parte dello personale d'ufficio è stata istruita, per trenta anni, che l'interno di una macchina non è per loro. La pagina d'office sembra un luogo dove qualcuno lavora.

Quell'ultimo punto non è decorazione. È la differenza tra uno strumento che usano quattro persone e uno strumento che una persona usa per conto di quattro.

## Le piccole figure

Le figure nell'ufficio non sono avatar dello personale. Sono *agenti*: l'installazione può farne correre diversi, ciascuno con il proprio compito, e la pagina li mostra tutti. Riverton ne fa correre uno, perché la macchina ha un modello e una scheda grafica, e agenti paralleli su una macchina non aggiungono velocità—fanno a turni, e possono esaurire la memoria.

La pagina è onesta su questo se la osservi: le figure condividono la stanza, e la stanza ha un unico telefono. Due agenti che provano a rispondergli insieme non è una funzionalità.

C'è una tentazione, quando vedi l'ufficio, a popolarlo—dare a ogni dipartimento la propria piccola figura con le proprie istruzioni. È una brutta idea per una piccola azienda, e il motivo è lo stesso che attraversa tutto questo libro: un agente è buono solo quanto il modello che sta dietro a lui, e un modello che risponde a quattro conversazioni sono quattro conversazioni lente. L'ufficio è una finestra su un unico lavoratore, non uno personale.

## La terza porta, che non è una porta affatto

C'è un terzo modo per entrare, e non è uno schermo: l'assistente risponde alle richieste HTTP.

Sulla stessa macchina, all'indirizzo `http://localhost:5290/v1/chat/completions`, parla lo stesso protocollo dei grandi servizi cloud. Qualsiasi cosa possa parlare con un endpoint compatibile con OpenAI può parlare con lui—uno script, una macro di foglio di calcolo, un altro programma, un sistema telefonico, il modulo di contatto di un sito web.

Riverton non ha usato questo, ed vale la pena spiegare perché, perché la tentazione è forte e il rischio è sottile.

La tentazione è ovvia: un cliente invia una email con una richiesta, il sito web la inoltra all'assistente, l'assistente crea un record di cliente e una bozza di preventivo, e Priya trova il lavoro fatto quando apre il proprio schermo. Questo è un vero flusso di lavoro, ed è esattamente il genere di cosa in cui questa tecnologia è brava.

Il rischio è che ogni porta nel sistema è una porta, e la porta su `localhost:5290` è aperta a qualsiasi cosa corra sulla macchina—inclusa una scheda del browser che è stata indotta a fare una richiesta. L'API non ha autenticazione di default, perché è stata progettata per essere raggiunta dalla stessa macchina da programmi che il proprietario controlla. Questo è un design ragionevole per un laboratorio. Non è un design ragionevole per una azienda che un giorno la collegherà a internet.

La regola che Riverton ha adottato, e quella che questo libro raccomanda: **l'API resta sulla macchina finché qualcuno non ha una necessità specifica e un piano specifico.** Quando quel giorno arriva, il piano è lungo tre righe—mettilo dietro un proxy che richiede un token, limitarlo a un unico endpoint, e registrare ogni richiesta. Fino ad allora, due porte d'ingresso bastano, e entrambe hanno una persona che le presidia.

## Il pomeriggio di Tom

Il giorno in cui la pagina d'ufficio si è guadagnata il proprio posto nell'azienda era un giovedì di febbraio, e la storia è piccola.

Tom era nel magazzino con una clipboard, a fare il conteggio trimestrale, e doveva sapere se una palletta di carta era stata ricevuta contro un ordine o era ancora "in transito" nel sistema. Sul terminale, quella domanda significa camminare fino all'ufficio, sedersi alla macchina che fa correre l'assistente, e digitare. Sulla pagina d'ufficio, significa aprire una scheda del browser sul laptop del magazzino—which è una macchina economica che esiste per cercare codici di prodotto—e digitare la domanda lì.

*La palletta di carta A4 di Pennine sull'ordine P00008 è stata ricevuta?*

*Ricevuta: 40 risme il 12 novembre, validate da Tom Beck, movimento scorte WH/IN/00031. L'ordine è interamente ricevuto; il conto non è ancora stato creato.*

Ebbe la propria risposta in nove secondi, in piedi accanto alla palletta. La vecchia versione di quella risposta era una camminata all'ufficio, una conversazione, e una nota su una clipboard.

Questo è il beneficio meno drammatico di tutto il libro e forse il più importante: la distanza tra una domanda e la propria risposta, misurata in passi. Un magazzino che può chiedere qualcosa al sistema senza lasciare il magazzino è un magazzino che verifica le cose.

## Cosa l'ufficio non può fare

Tre limiti valgono la pena di essere conosciuti prima che un'azienda costruisca una abitudine attorno alla pagina.

**Non può far correre due conversazioni insieme, utilmente.** L'ufficio disegna diverse figure, e la tentazione è assunere un dipartimento per figura. Su una macchina con un unico modello, sono quattro conversazioni che fanno a turni, e le figure si sederanno alle proprie scrivanie sembrando occupate mentre nulla finisce. La pagina è onesta su questo se la osservi: il pannello a destra elenca le sessioni, e solo una di esse è *in lavoro* in qualsiasi momento.

**Non può mostrarti il ragionamento.** Il terminale mostra le chiamate agli strumenti mentre accadono; l'ufficio mostra un'etichetta (*cercare*, *creare*, *recuperare il contesto*) e poi una risposta. Questo è il giusto livello di dettaglio per un responsabile d'ufficio e il livello sbagliato per qualcuno che debugga un compito. Le due entrate non sono intercambiabili, e un'azienda che usa solo la pagina web alla fine avrà bisogno del terminale—solitamente il giorno in cui qualcosa va sbagliato.

**Non può essere lasciata aperta su uno schermo in una stanza pubblica.** La chat mostra i dati dell'azienda: nomi, importi, fatture. Un laptop su una scrivania in un negozio è una finestra sul libro mastro. La pagina non ha un proprio accesso, perché è servita dall'assistente su `localhost` e presume che la macchina sia tua. Questa presumizione è corretta a una scrivania e sbagliata in una sala d'attesa.

## Il suono, e l'interruttore che lo spegne

La pagina emette piccoli rumori: una tastiera quando l'agente sta digitando, una campana quando un compito è fatto. È affascinante per una settimana e assordante per un mese, e l'interruttore è nell'angolo in basso a destra della pagina, etichettato *SUONO: ON*.

Il fatto che questo valga un paragrafo è in sé una lezione sull'software d'ufficio. Le funzionalità che decidono se uno strumento sopravvive sono raramente quelle nel volantino. Sono quelle che toccano i nervi dell'ufficio: se fa rumore, se può essere lasciata aperta, se la cosa che mostra è vera.

## Una breve storia della metafora d'ufficio

Mettere le persone in un'immagine per rappresentare il lavoro è un'idea antica nel computing, ed ha un buon record.

Nel 1984, il Macintosh di Apple introdusse la metafora del desktop—file, cartelle, un cestino—e funzionava perché permetteva alle persone di usare conoscenze che avevano già. Nel 1987, il progetto Information Visualizer alla Xerox PARC andò oltre e disegnava uffici, con stanze e documenti, come modo di navigare grandi spazi informativi. Nel 1993, il gioco *Doom* insegnò a una generazione che una vista in prima persona di uno spazio è più leggibile di un suo diagramma.

Ciò che tutti e tre scoprirono è la stessa cosa: **una metafora spaziale trasporta lo stato.** Non hai da leggere una linea di stato per sapere che una stanza è occupata; puoi vederla. La pagina d'ufficio a Riverton è un diretto discendente di quella idea, ed esiste per lo stesso motivo—non per essere affascinante, ma per rispondere alla domanda *cosa sta succedendo?* senza richiedere all'utente di leggere.

## La chat, e la stessa disciplina

La casella di chat in fondo alla pagina prende le stesse istruzioni del terminale, e produce lo stesso lavoro. Tutto nel capitolo venticinque sui prompt si applica invariato.

Due cose sono diverse, e entrambe sono conseguenze dell'interfaccia.

**Le risposte sono più brevi.** La pagina web mostra una conversazione, non un log, quindi l'assistente sintetizza. Questo è buono per la lettura e cattivo per il controllo: il numero di fattura può essere nella sintesi, ma l'elenco dei passaggi che l'ha prodotto non lo è. Quando un risultato conta, chiedi un seguito—*mostrami i documenti dietro quel numero*—e la risposta sarà un elenco.

**La tentazione al multitasking è più forte.** Una finestra di chat invita a una seconda domanda mentre la prima è ancora in corso, e una seconda domanda mentre la prima è in corso è la cosa che fa sentire a pezzi un'installazione a modello unico. La pagina non lo impedisce. L'abitudine lo impedisce.

---

L'uso che Maggie stessa ne ha fatto si è assestate in qualcosa che non si aspettava: usa la pagina web al mattino e il terminale al pomeriggio.

"Al mattino voglio sapere delle cose," dice. "Voglio l'elenco di ciò che è in ritardo, ciò che è basso, ciò che è arrivato durante la notte. Quella è una conversazione, e l'ufficio è dove l'ho. Al pomeriggio voglio *fare* delle cose—publicare le fatture, inseguire i tre conti, sistemare la cosa che Tom ha trovato—e per quello voglio vedere girare le ruote."

Ci ha pensato per un momento.

"È come la differenza tra chiedere a qualcuno una domanda nel corridoio e sedersi con lui a una scrivania. Stessa persona. Stanza diversa."

Quello è una buona descrizione quanto questo libro può offrire delle due interfacce, ed suggerisce il principio dietro di esse: l'interfaccia deve corrispondere al *genere di attenzione* che il lavoro richiede, non al genere di tecnologia dietro di esso. Una domanda richiede una conversazione. Una pubblicazione richiede un testimone.
