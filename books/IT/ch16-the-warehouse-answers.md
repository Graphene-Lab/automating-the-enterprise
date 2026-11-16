# 16. Il magazzino risponde

La domanda che cambiò il lavoro di Tom Beck fu posta un martedì, e non era una domanda sui computer.

> *Quanti raccoglitori A4 con anelli abbiamo, e dove sono?*

L'aveva fatta mille volte in diciannovi anni, e la risposta arrivava sempre da una persona:
da lui, o da chi era in linea di prelievo, o da un taccino che a volte aveva ragione. Ora la digitò
in una finestra e ottenne questo:

> *Raccoglitore A4: 412 in totale in magazzino. 350 riservati per l'ordine S00012 (Ashfield Academy). 62
> disponibili. Posizioni: Stock/Shelf A — 380, Stock/Returns — 24, Stock/Quarantine — 8.*

La lesse tre volte. Poi uscì verso la Shelf A e contò, cosa che gli fece undici minuti e
dimostrò che il sistema aveva ragione su tutti e tre i numeri.

"Giusto," disse, quando tornò. "Ora ci credo."

---

## Cosa è uno spostamento di magazzino

Il numero 412 non è memorizzato da nessuna parte. Questa è la prima cosa da capire, ed è ciò che
separa un vero sistema di inventario da un foglio di calcolo con una colonna delle quantità.

Ciò che è memorizzato è una lista di *spostamenti*: duecento ricevuti dal fornitore a marzo, trecento
cinquanta prelevati per Ashfield a giugno, venti resi a luglio, otto spostati in quarantina a
agosto. Il livello di magazzino è la somma di quegli spostamenti, calcolata quando la si chiede. Se la
si chiede di nuovo un minuto dopo, e nulla si è spostato, si ottiene la stessa risposta. Se qualcosa si
è spostato, si ottiene una diversa, e la differenza è *lo spostamento stesso*—che ha una data, un
utente, una ragione e un documento.

Questo ha tre conseguenze che un foglio di calcolo non può riprodurre.

**Si può sempre scoprire il perché.** Quando un numero sembra sbagliato, gli spostamenti lo spiegano.
Non "qualcuno ha cambiato la quantità" ma "venti sono finiti in quarantina il 3 agosto perché il pallet
era schiacciato".

**Due persone non possono dissentire in silenzio.** Se Tom conta 380 e il sistema dice 412, la
differenza è un documento: un aggiustamento, con una ragione, approvato da qualcuno. Il conteggio non
sovrascrive il sistema; produce uno spostamento che li riconcilia.

**La storia sopravvive al cambio di unità, prezzo o fornitore.** Gli spostamenti mantengono le
quantità con cui sono stati fatti. Riorganizzare il catalogo non riscrive il passato.

## Riservato, disponibile, e la differenza che conta

Il secondo cosa che Tom imparò è la differenza tra *in magazzino* e *disponibile*, ed è la
differenza tra un magazzino che promette e un magazzino che mantiene le promesse.

**In magazzino** è ciò che è fisicamente nell'edificio: 412 raccoglitori.

**Riservato** è ciò che è stato promesso a un ordine specifico: 350 raccoglitori, per Ashfield, in
attesa del furgone.

**Disponibile** è in meno riservato: 62 raccoglitori che possono essere promessi a qualcun altro.

Una compagnia che traccia solo *in magazzino* prometterà le stesse 350 raccoglitori due volte—una
per Ashfield e una per Northgate—e scoprirà il problema la mattina della consegna, quando c'è un
solo pallet. Una compagnia che traccia le prenotazioni la scopre al momento della seconda promessa,
quando il sistema dice *62 disponibili* e il commesso deve prendere una decisione.

Quella decisione—consegniamo Northgate in ritardo, o compriamo di più, o dividiamo l'ordine—è una
decisione commerciale, e il punto del sistema non è farla. Il punto è porla davanti a una persona
*prima* che diventi una scusa.

## La consegna

La consegna in sé è il documento più semplice di tutto il sistema e quello con più
conseguenze.

> *Consegna l'ordine S00012 e mostrami gli spostamenti di magazzino che ha creato.*

> *Consegna WH/OUT/00004 validata per l'ordine S00012. Spostamenti: 350 × Raccoglitore A4 (blu) da
> Stock/Shelf A a Clienti; 20 × Marcatori per lavagna (confezione da 4) da Stock/Shelf A a Clienti.
> Stock dopo lo spostamento: 62 raccoglitori in magazzino, 0 riservati; marcatori 44 in magazzino.*

Tre cose succedero insieme, e valgono la pena di essere separate.

Lo **stock** si è spostato: 350 raccoglitori hanno lasciato la Shelf A. La **prenotazione** è
scomparsa, perché era stata soddisfatta. E l'**ordine** è cambiato di stato: ora è *consegnato*, che
significa che la fattura può essere creata contro di esso.

Se la consegna fosse stata parziale—duecento raccoglitori invece di trecento cinquanta—Odoo avrebbe
creato un *backorder*: un secondo documento di consegna per il resto, collegato al primo. Quel
singolo meccanismo è la ragione per cui una compagnia può promettere *inviiamo il resto venerdì*
senza che qualcuno debba ricordare cosa fosse il resto.

## Le posizioni, in pratica

Una posizione sembra una tecnicità fino alla prima volta che qualcosa si perde, e allora è l'unica
cosa che conta.

Le quattro posizioni di Riverton—due scaffali, resi, quarantina—erano state impostate in un'ora e
usate correttamente per circa un mese prima che qualcuno le apprezzasse.

La posizione dei resi è stata la prima a guadagnarsi il proprio spazio. Un cliente rimanda venti
raccoglitori perché sono del colore sbagliato; il furgone li porta al piano di carico; Tom deve
decidere se tornano sulla Shelf A (dopotutto, sono vendibili) o in quarantina (non lo sono). Sul
vecchio sistema, la decisione era fatta da dove veniva messa la scatola, e la scatola veniva messa
ovunque ci fosse spazio. Sul nuovo sistema, la decisione è uno spostamento di magazzino, e lo
spostamento ha una ragione allegata.

La conseguenza apparve nel report sui margini tre mesi dopo: la posizione dei resi conteneva
quarantuno articoli che erano stati "resi" e mai controllati, alcuni danneggiati, alcuni in realtà un
prodotto diverso. Ognuno di loro era stato contato come stock vendibile. Questo è quarantuno articoli
di stock che la compagnia credeva di avere e non poteva vendere—un numero piccolo, e una
illustrazione perfetta del principio generale: **il valore di una posizione è che forza una decisione
a essere registrata.**

## Il controllo a tre vie, dal lato del magazzino

Il capitolo diciassette descrive il controllo a tre vie dal punto di vista del contabile. Dal lato di
Tom, sembra diverso ed vale un paragrafo.

Quando arriva una consegna, il lavoro del magazzino è registrare ciò che è realmente arrivato: quanti,
di quale prodotto, in che condizione, in che data. Quel registro è la *ricevuta*, ed è la gamba
centrale del controllo. Se è sbagliata—se Tom registra quaranta pallet invece di quaranta risme, o se
valida la ricevuta prima di contare—allora il controllo "riuscirà" contro un numero sbagliato, e l'errore
sopravviverà fino alle contabilità.

Questo è il perché la ricevuta è un documento con un utente e un timestamp, e perché l'assistente non
è autorizzato a validare una ricevuta per propria iniziativa. Può crearne una da un ordine di
acquisto, che è una proposta; validarla significa *ho contato questo*, ed è una affermazione sul mondo
fisico che solo qualcuno in piedi davanti al pallet può fare.

La regola di Tom, scritta sulla lavagna: *il sistema può indovinare cosa dovrebbe esserci. Solo io
posso dire cosa c'è.*

## Il costo di un conteggio sbagliato

Vale la pena mettere un numero sul conteggio trimestrale, perché "dovremmo farlo più spesso" è il
tipo di consiglio che muore in un mese affollato.

Lo stock di Riverton valeva circa £180.000 al costo. Il primo conteggio trovò una differenza netta di
1,8 per cent—circa £3.200—sparsi su undici prodotti. Questo non è furto; è l'effetto accumulato di
quaranta piccoli errori: un pallet registrato come quaranta pallet, un reso rimesso senza controllo, una
consegna validata prima che fosse contata.

Un conteggio costa due persone un giorno, due volte all'anno, che sono circa £1.200 di salari. Trovò
£3.200 di errore la prima volta e £900 la seconda. L'aritmetica non è sottile: una compagnia che
conta due volte all'anno sta comprando una polizza assicurativa da £1.200 contro un errore da £3.000,
e l'errore che previene è quello che rende sbagliate le contabilità alla fine dell'anno.

Ciò che cambiò con il sistema non fu l'aritmetica ma la *forma* del conteggio. Invece di contare
tutto e riconciliare una lista, il sistema propone ciò che crede e il conteggiatore conferma o
corregge. Le correzioni sono poi investigate, una alla volta, e ogni indagine ripara un'abitudine più
che un numero. Questa è la differenza tra contare lo stock e gestirlo.

## La nota di consegna, e le tre firme

Una consegna in un grossista ha tre momenti, e ognuno ha una firma di un certo tipo.

**La prelievo:** qualcuno prende la merce dallo scaffale e la mette su un pallet. La firma è la lista
di prelievo, firmata riga per riga, ed è il magazzino che dice *questo è ciò che ho assemblato*.

**Il carico:** la merce va sul furgone. La firma è quella del conducente, ed è la compagnia che dice
*questo è uscito dall'edificio*.

**La consegna:** il custode del cliente firma la nota. La firma è la loro, ed è il cliente che dice
*questo è arrivato*.

In Odoo i tre momenti collassano in due documenti—l'ordine di consegna e la sua validazione—ed è una
semplificazione vale la pena capire, perché è da dove nascono la maggior parte delle discrepanze. Un
pallet che è prelevato, carico e mai consegnato ha lasciato lo stock del sistema ma non il cortile della
compagnia; un pallet che è consegnato e mai validato ha lasciato il cortile ma non il sistema.

L'abitudine di Tom, dopo il primo anno, era di trattare la validazione come il momento della verità: la
consegna è validata quando torna la nota firmata, non quando il furgone parte. Rende il report di stock
in ritardo di un giorno e lo rende giusto, e preferirebbe avere un numero giusto di mercoledì che un
sbagliato di martedì.

## Ciò che il magazzino sa e il sistema non

C'è un limite a tutto questo, e Tom è il primo a descriverlo.

Il sistema conosce quantità, posizioni e date. Non sa che l'angolo della Shelf B è dove entra l'umidità,
che il pallet di carta della consegna di agosto è più pesante di quello di febbraio perché il fornitore
ha cambiato il peso della rima, o che il conducente che consegna il venerdì non aspetterà mentre tu
conti.

Un responsabile di magazzino porta quella conoscenza, e il valore del sistema non è che la sostituisce
ma che la *libera*: una persona che non deve ricordare dove sono quattrocento dodici raccoglitori può
spendere l'attenzione sul perché il pallet di agosto sembri sbagliato.

"È uguale all'ufficio," dice Tom. "Il sistema conta. Io noto."

## Il conteggio

Una volta trimestrale, Riverton conta.

Non è un pomeriggio piacevole. Coinvolge una clipboard, due persone, una torcia, e un magazzino che
è più freddo di quanto sembri. Ma ora è diverso, in un modo che ha preso a Tom un po' di tempo per
articolare.

"La prima volta, ho contato tutto e l'ho digitato, e il sistema mi ha detto dove sbagliavo,"
 disse. "La seconda volta, ho contato solo le cose che il sistema diceva che avrei dovuto avere, e mi
ha detto dove *era* sbagliato. Questo è un lavoro diverso. Il primo è un'abitudine. Il secondo è una
conversazione."

Ciò che intendeva è questo: con un conteggio di stock, il sistema propone una lista di prodotti e le
quantità che crede siano sullo scaffale, e il conteggiatore conferma o corregge. Le correzioni sono poi
esaminate, e ognuna è una piccola indagine: è stato un errore di prelievo, una consegna firmata ma non
registrata, un reso che non è mai tornato sullo scaffale?

Quella indagine è dove sono i soldi. Nel primo anno di Riverton, il conteggio trimestrale trovò tre
problemi ricorrenti, e nessuno era furto:

- Un prodotto la cui unità di misura era stata impostata male nel 2022, in modo che ogni ricevuta fosse
  registrata come un pallet invece di quaranta risme. Il sistema stava "perdendo" carta da tre anni.
- Una nota di consegna firmata alla scuola ma mai validata nel sistema, in modo che la merce fosse
  sullo scaffale e anche nell'armadio del cliente.
- Un processo di resi che rimetteva la merce resa nello stock senza controllarla, in modo che gli
  articoli danneggiati fossero venduti due volte.

Ognuna di quelle fu trovata confrontando ciò che il sistema credeva con ciò che era vero, e ognuna fu
riparata cambiando un'abitudine, non comprando qualcosa.

---

## Una nota sulla parola "magazzino"

Il magazzino di Tom è una stanza con scaffali, un piano di carico, e un angolo dove vanno le cose
danneggiate. In Odoo è una *posizione*, e le posizioni possono essere annidate: un magazzino contiene
una area di stock, che contiene scaffali, che contengono cassetti.

Una compagnia con una sola stanza non ha bisogno dell'annidamento, e Riverton non lo usò all'inizio.
Ma la struttura c'era, e nel secondo anno, quando la compagnia affittò l'unità accanto, aggiungere un
secondo magazzino fu questione di creare una posizione e spostare lo stock—non di comprare un secondo
sistema o iniziare un secondo foglio di calcolo.

Questo è il vantaggio silenzioso del modellare la realtà invece di registrarla. Un foglio di calcolo
che dice "412 raccoglitori" non può far crescere un secondo scaffale senza essere ricostruito. Un
sistema che dice "412 raccoglitori, eccovi gli spostamenti che li hanno messi là" può far crescere un
secondo edificio in un pomeriggio.

---

Il report di Tom, alla fine di quel primo trimestre, era lungo quattro pagine e lo lesse nel furgone.

"La cosa a cui torno sempre," disse, quando lo riportò, "è che una volta *conoscevo* le cose e non
potevo *mostrarle*. Ora le posso mostrare. È il mostrarle che cambia la conversazione."

Maggie gli chiese cosa intendesse.

"Prima, se dicevo che avevamo troppo carta, era l'opinione di Tom. Ora è un numero su una pagina con
una data sopra. Nessuno discute con un numero su una pagina. Discutono con Tom."

Lui sorrise. "È molto riposante."
