# 22. Il lavoro che gira mentre dormi

Il primo lavoro programmato che Riverton configurò non era ingegnoso. Era la lista del lunedì.

Ogni lunedì alle otto, l'assistente produce una pagina: le fatture diventate scadute nella settimana precedente, i prodotti scesi sotto il punto di riordino, gli ordini in scadenza per la consegna nei prossimi sette giorni, e qualsiasi rettifica di magazzino senza motivo registrato. La invia a Maggie, Priya e Tom come email, e all'assistente ci vogliono circa quaranta secondi.

Nessuno l'ha richiesta. Era l'idea di Sam, e la spiegò con una frase che è rimasta a Maggie da allora.

"Il punto di una programmazione non è che la macchina lavori mentre dormi. È che la *domanda* venga posta che tu ti ricordi o meno di chiederla."

---

## Due tipi di lavoro programmato

In questo stack ci sono due meccanismi, e valgono la pena di essere distinti perché rispondono a domande diverse.

**I schedulers interni all'ERP** girano dentro Odoo. Sono le cose che un sistema aziendale ha sempre fatto su un timer: ricalcolare i punti di riordino, inviare le email di promemoria, eseguire l'ammodernamento, pulire le vecchie sessioni. Si configurano nell'ERP, girano che tu apra o meno l'assistente, e sono il posto giusto per qualsiasi cosa faccia parte del *modello*—qualunque cosa che avrebbe dovuto succedere anche se nessuno in azienda era interessato.

**Lo scheduler di compiti dell'assistente** gira i lavori come conversazioni. Un compito programmato è, letteralmente, un prompt con una data attaccato: alle otto di lunedì, l'assistente riceve una istruzione, fa il lavoro, e riferisce. Quello è il posto giusto per qualsiasi cosa richieda giudizio su *cosa guardare*—un riassunto, una scorribanda, un confronto, un incitamento.

Riverton usa entrambi, e la divisione tra loro è la parte utile di questo capitolo.

## Cosa appartiene a una programmazione

La tentazione, quando scopri il lavoro programmato, è programmare tutto. Resisti, e usa un test facile da applicare: **un lavoro appartiene a una programmazione se la sua assenza sarebbe notata solo quando è troppo tardi.**

La lista del lunedì supera il test. Senza di essa, una fatture scadente si nota quando qualcuno pensa di guardare—which è dire, quando ha sessanta giorni.

Un backup notturno supera il test, catastroficamente.

Un "rapporto di vendita" quotidiano di solito lo fallisce. Nessuno lo legge; il numero è nella dashboard; e un rapporto che nessuno legge è una piccola tassa quotidiana sull'attenzione che alla fine insegna alle persone a ignorare i messaggi del sistema.

Il test ha un corollario: **un lavoro programmato dovrebbe produrre una decisione, non un documento.** La lista del lunedì produce quattro decisioni (inseguisci questa, riordina quello, consegna questo, spiega quello). Un rapporto produce un documento, e i documenti si accumulano.

## I tre lavori che Riverton tenne

Dopo un mese di esperimenti, la company si è assestata su tre, e le ha mantenuti da allora.

**La lista del lunedì**, alle otto. Quattro domande, una pagina, tre destinatari.

**Il controllo di magazzino del venerdì**, alle quattro. L'assistente elenca ogni prodotto che è sceso sotto il suo punto di riordino durante la settimana e propone ordini di acquisto—in bozza, mai confermati. Tom lo legge il pomeriggio di venerdì e decide; gli ordini vengono piazzati il lunedì mattina, che è quando i fornitori rispondono al telefono.

**Il riassunto del primo del mese**, alle sette. Vendite per cliente, vendite per prodotto, i primi cinque e gli ultimi cinque per margine, cassa in e fuori, e i tre clienti il cui comportamento di pagamento è cambiato. Sono due pagine, ed è il documento che Maggie legge con il primo caffè del mese.

Tutto il resto provato quel mese è stato cancellato, e le cancellazioni sono istruttive quanto i mantenuti: un riassunto quotidiano (nessuno lo leggeva), un controllo di connessione orario (produceva rumore, non informazione), e un lavoro notturno di "pulizia duplicati" che era un'idea genuinamente cattiva—una macchina che decide quale dei due record di cliente è reale, alle tre di notte, con nessuno che guarda.

## Cosa succede quando un lavoro fallisce

La parte interessante del lavoro programmato non è la programmazione. È il fallimento.

Un lavoro può fallire per tre motivi, e ognuno ha una firma diversa.

**La macchina era spenta.** L'ERP non stava girando alle otto, quindi il lavoro non è girato. Gli schedulers interni di Odoo gestiscono questo girando i lavori mancati quando il server parte; i compiti programmati dell'assistente sono salvati come piani e girano al prossimo avvio, con la data per cui avrebbero dovuto girare. In ogni caso, il lavoro succede, in ritardo.

**Il lavoro è girato e la risposta era sbagliata.** Questo è il più pericoloso, perché nulla sembra rotto. La lista del lunedì arriva, e una delle sue quattro sezioni è vuota perché un filtro era rimasto acceso. La difesa è la stessa di ogni altro punto di questo libro: la lista dice *cosa ha guardato*, non solo cosa ha trovato. Una sezione vuota che dice "nessuna fatture è diventata scaduta nella settimana fino al 14 novembre" è informazione; una sezione vuota senza spiegazione è una domanda.

**Il lavoro è girato e nessuno l'ha letto.** Questo è il fallimento più comune e il meno discusso. Un lavoro programmato che arriva in una inbox che nessuno apre è peggiore di nessun lavoro affatto, perché crea l'*impressione* di controllo. La risposta di Riverton è stata di rendere la lista del lunedì una riunione—quindici minuti, tre persone, la lista sullo schermo—which suona come burocrazia ed è in realtà il modo più economico possibile di rendere reale l'automazione.

## Una breve storia del batch job

Il lavoro programmato è più antico del computer personale, e il suo vocabolario viene dal mainframe.

Negli anni sessanta, un computer era troppo costoso per lasciare che una persona ci sedesse davanti, quindi il lavoro era preparato su schede e girato in *batch* durante la notte: stipendi il 25, fatture il 1, il libro mastro a fine mese. Il batch era una coda, e il lavoro dell'operatore era mantenere la coda in movimento. Quando i minicomputer arrivarono negli anni settanta, il batch sopravvisscome `cron`—un programma Unix, scritto nel 1975 da Ken Thompson, il cui nome viene da *chronos*, tempo—e `cron` è ancora ciò che fa girare i server del mondo, incluso, indirettamente, lo scheduler dentro il tuo ERP.

Ciò che è nuovo non è il timer. È *cosa* gira su di esso. Un batch job del 1975 era un programma scritto da un programmatore per fare esattamente una cosa. Un compito programmato del 2026 è una frase in inglese, e la macchina ricava i passi ogni volta che gira. Quello è un tipo diverso di automazione, e ha bisogno di un tipo diverso di supervisione: il programma faceva ciò per cui era stato scritto, ogni volta; la frase può essere interpretata diversamente mentre i dati cambiano.

È per questo che la prima regola del lavoro programmato in questo libro è: **programma domande, non azioni.** La lista del lunedì chiede. Il controllo di magazzino del venerdì propone. Il riassunto del primo del mese riferisce. Nessuno di loro pubblica una fatture, invia una lettera a un cliente, o piazza un ordine, perché quelle sono decisioni con conseguenze, e una decisione fatta alle tre di notte da una macchina che nessuno sta guardando non è una decisione—è una scommessa.

## L'unica eccezione

C'è un lavoro programmato a Riverton che agisce davvero, ed vale la pena descriverlo perché mostra dove si trova la linea.

Ogni notte alle due, il sistema fa un backup: un dump del database, una copia della configurazione, e una riga in un log. Agisce. Cambia il mondo, nel senso che i files appaiono. Ed è permesso che agisca perché l'azione è *reversibile per design*: un backup sbagliato può essere cancellato e rifatto, e nulla in azienda dipende dal fatto che sia successo, fino al giorno in cui qualcosa lo fa.

Quello è il test per qualsiasi azione programmata: se questo gira male alle tre di notte, posso annullarlo prima che qualcuno se ne accorga? Se sì, può essere programmato. Se no, può proporre, e una persona può decidere.

## Il costo di una programmazione che nessuno possiede

Un lavoro programmato è una piccola promessa, e le promesse hanno bisogno di un proprietario.

Il fallimento è silenzioso ed è comune: un lavoro viene configurato da qualcuno che poi se ne va, o cambia ruolo, o semplicemente dimentica. Continua a girare. Sei mesi dopo sta producendo un rapporto con un filtro che era giusto a marzo, o proponendo ordini per una linea di prodotti che la company ha discontinuito, e nessuno se ne accorge perché nessuno lo legge—finché qualcuno non lo fa, e gli crede.

La cura è una lista, tenuta nello stesso file dei prompt: ogni lavoro programmato, cosa fa, chi lo legge, e quando è stato revisionato per l'ultima volta. Quattro colonne, una pagina, revisionato due volte all'anno. Un lavoro che nessuno può nominare un proprietario è un lavoro da cancellare.

La lista di Riverton ha tre voci e una quarta che è un promemoria per revisionare la lista. È il documento meno impressionante in azienda e ha prevenuto due decisioni sbagliate, entrambe le quali sarebbero state fatte da una macchina che faceva esattamente ciò per cui era stata istruita.

## Dove vive la programmazione, e cosa succede quando la macchina è spenta

Un compito programmato è un file, e sapere dove vive è la differenza tra una programmazione che possiedi e una programmazione di cui sei alla mercé.

L'assistente salva i suoi piani come JSON, nella sua cartella dati, e sopravvivono a un riavvio. Ogni piano è una frase, un orario, una ricorrenza, e una lista di cosa fare con il risultato. Quello vale la pena saperlo per due motivi: può essere backed up con il resto della configurazione, e può essere ispezionato—which significa che una company può rispondere alla domanda *cosa sta facendo questa machine alle otto di lunedì?* leggendo un file piuttosto che ricordare.

Gli schedulers interni all'ERP vivono nel database, in una tabella di azioni programmate, e sono visibili nell'interface sotto *Impostazioni → Tecnico → Azioni Programmate*. Ogni una ha un nome, un intervallo, e un conteggio di quante volte è girata. Quel conteggio è un piccolo ma eccellente diagnostico: un lavoro che è girato quattrocento volte e un lavoro che è girato zero volte ti dicono cose diverse, e entrambi valgono la pena di essere guardati una volta al trimestre.

Quando la macchina è spenta, tre cose possono succedere, e il comportamento dell'ERP è quello sensato.

**Gli schedulers di Odoo** girano i lavori mancati al prossimo avvio, in ordine, e registrano il fatto. Un promemoria che era dovuto alle otto uscirà alle nove, e il log lo dirà.

**I compiti dell'assistente** vengono controllati all'avvio: se il prossimo run di un piano è nel passato, gira subito e si riprogramma. Una lista del lunedì che è stata mancata perché la macchina era spenta arriverà il martedì, con i dati come sono il martedì—which è una differenza sottile e importante. La lista non è "cosa è successo il lunedì"; è "cosa è vera ora, chiesta sulla programmazione che era destinata al lunedì".

**Un backup** che è stato mancato è semplicemente mancato, e il prossimo copre il gap. Quello è accettabile per un backup notturno; non è accettabile per uno settimanale su una macchina che è spesso spenta, ed è per questo che lo script di backup scrive una riga in un log e il log viene controllato mensilmente.

## Quando un lavoro produce rumore

La modalità di fallimento che uccide il lavoro programmato non è un crash. È il rumore.

Un lavoro che produce un messaggio che nessuno legge addestra le persone a ignorare i messaggi del sistema, e poi anche quello che conta viene ignorato. Riverton provò quattro programmazioni nel primo mese e ne cancellò tre, e le cancellazioni furono istruttive quanto i mantenuti.

**Il riassunto quotidiano** fu cancellato perché duplicava la dashboard e arrivava a un momento in cui nessuno era alla scrivania. L'informazione non era sbagliata; la consegna sì.

**Il controllo di connessione orario** fu cancellato perché riportava il successo ogni ora. Un messaggio che dice *tutto va bene* non è informazione; è un'abitudine, e le abitudini sono ciò che fanno alle persone smettere di leggere.

**Il controllo di duplicati notturno** fu cancellato perché era un'azione che nessuno aveva autorizzato, che girava a un momento che nessuno stava guardando, su dati che nessuno aveva pulito. Non trovò nulla per tre settimane e poi propose di unire due clienti che erano, di fatto, due diramazioni della stessa organizzazione.

I tre che sopravvisscono condividono tutti una proprietà: producono una *decisione* che una persona nominata fa a un orario nominato. La lista del lunedì viene letta alla riunione di lunedì. Il controllo di magazzino del venerdì viene letto da Tom prima che se ne vada. Il riassunto mensile viene letto con il primo caffè del mese.

Una programmazione senza lettore è un job cron con un hobby.

---

La lista del lunedì gira da otto mesi, e Maggie l'ha saltata due volte—entrambe le volte perché era in viaggio, e entrambe le volte l'ha letta il martedì e ha desiderato averla letta il lunedì.

"Non è l'informazione," dice. "Potrei ottenere l'informazione. È che il lunedì mattina, prima che succeda nient'altro, qualcuno mette quattro domande davanti a me. E sono le quattro domande giuste. Non penserei mai a chiederle alle otto di lunedì. Le penserei alle quattro di venerdì, quando è troppo tardi per fare qualsiasi cosa."

Quello è il vero valore del lavoro programmato, e non ha nulla a che fare con le macchine che lavorano mentre dormi. È che la *domanda* ha un orario, e l'orario è scelto da qualcuno che ci ha pensato una volta, con cura, invece che da chiunque capita di essere preoccupato in quel momento.
