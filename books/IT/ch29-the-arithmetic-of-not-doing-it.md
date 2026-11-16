# 29. L'aritmetica di non farlo

Gerald Pryce, il contabile sopra il negozio di chimica, aveva una regola sugli investimenti: *mostrami il costo della cosa per cui stai già pagando.*

Maggie era andata a trovarlo in primavera, con le fatture dell'anno e una domanda di cui era leggermente imbarcata, perché suonava come la domanda di chi aveva già deciso. "Ne è valso la pena?"

Gerald si mise gli occhiali, il che significava che si sarebbe divertito.

"Non ancora," disse. "Prima facciamo l'aritmetica di non farlo."

---

La maggior parte dei casi aziendali per il software sono scritti al contrario. Elencano il costo della cosa nuova—la licenza, l'hardware, la formazione, il consulente—ed poi elencano i benefici nel linguaggio della speranza: efficienza, visibilità, agilità. I numeri dal lato del costo sono precisi, perché qualcuno li ha preventivati. I numeri dal lato dei benefici sono aggettivi.

L'aritmetica di non farlo va al contrario. Parte dalla posizione che l'azienda sta già pagando il suo modo attuale di lavorare, ogni singolo giorno, e che questo pagamento non compare in alcun bilancio perché avviene in ore.

Così Gerald e Maggie passarono una mattina con un foglio di calcolo—lo strumento che ha sostituito l'aritmetica del contabile e non ha sostituito il contabile—e contarono.

**La prima riga era la corsa delle fatture.** Riverton produceva, in media, quattrocento ottanta fatture al mese. Ognuna richiedeva, dal momento in cui la consegna era confermata al momento in cui la busta era nella posta, tra i quattro e i sei minuti del tempo di qualcuno: stampa, controllo contro la nota di consegna, piegatura, indirizzamento, affrancatura. Chiamiamolo cinque minuti, che sono sessanta ore al mese, che sono quasi mezza settimana lavorativa.

Dopo il cambiamento, la corsa richiedeva undici minuti in totale, perché i documenti erano generati ed inviati per email, e il controllo era fatto guardando una lista piuttosto che ogni singolo pezzo di carta. Le sessanta ore non diventarono zero; alcune diventarono controllo, e altre il lavoro che Doreen aveva sempre voluto fare. Ma quaranta ore al mese tornarono all'azienda.

**La seconda riga era la ricerca.** Nessuno aveva mai misurato questo, perché nessuno misura la ricerca. Doreen la stimò a un'ora al giorno, che probabilmente era un sottostima, perché le persone non contano le interruzioni. Vant'ore al mese, sparite. Dopo il cambiamento erano forse tre, per la maggior parte passate a guardare cose che richiedevano una decisione piuttosto che una posizione.

**La terza riga era gli errori.** Dodici note di credito nell'anno precedente, causate da prezzi sbagliati, quantità sbagliate o indirizzi sbagliati, in media centoquaranta sterline l'una, più il tempo per correggerli e il piccolo danno alla relazione. Il cambiamento non eliminò gli errori, ma rimosse la classe di errori causati dalla rigitura, perché nulla era ri-digitato.

**La quarta riga era i soldi che arrivavano in ritardo.** Questa è la riga che sorprese Maggie, perché non è un costo nei conti; è un costo in banca. Il tempo medio dalla fattura al pagamento era di cinquantatre giorni. Dopo sei mesi di fatture inviate in tempo, e di un promemorso gentile che l'assistente produceva ogni lunedì senza essere richiesta, era quarantuno. Dodici giorni di fatturato di un'azienda, seduti in banca invece che nei conti dei clienti, valgono più dell'intero costo del sistema, e compaiono ovunque in un conto economico.

---

Contro questo, i costi.

Il software era gratuito. Odoo Community, il database, l'assistente e il connettore sono tutti open source, e la licenza per tutto ciò è zero. Questo non è un trucco e non è una prova: è il modello di business dell'open source, ed è il motivo per cui un'azienda delle dimensioni di Riverton può permettersi un sistema che sarebbe stato inimmaginabile nel 1995.

L'hardware era un computer che l'azienda possedeva già, con abbastanza memoria e disco per tre programmi in una volta. Se un'azienda deve comprarne uno, è una spesa in conto capitale dello stesso ordine del servizio annuale di un furgone di consegna, e dura più a lungo.

Il modello linguistico era un servizio, pagato in base all'uso. L'importo dipende dal fornitore e da quanto si chiede all'assistente, ed è l'unica riga che un'azienda dovrebbe tenere d'occhio, nel modo in cui tiene d'occhio l'elettricità. Ciò che conta è il rapporto: si chiede all'assistente di fare cose che altrimenti richiederebbero a una persona minuti, e il costo di una richiesta è misurato in frazioni di sterlina, quindi il rapporto non è vicino.

I costi onesti erano i due che nessuno preventiva.

Il primo era *il tempo per installare*, che era una giornata di attenzione di Sam Okafor e una settimana di Maggie, distribuita in un mese, per la maggior sera nelle serate. Il secondo era *la disciplina*, che non è un costo che si paga una volta. Qualcuno deve tenere pulita la lista dei prodotti, decidere cosa l'assistente è autorizzato a fare, leggere il log, e dire di no alla richiesta di aggiungere un'altra eccezione. È un lavoro permanente, piccolo, senza fascino, ed è il prezzo di tutto il resto.

---

C'è una trappola in quest'aritmetica, ed vale la pena nominarla perché cattura le aziende intelligenti.

La trappola è automatizzare la parte facile da automatizzare piuttosto che la parte che costa di più. Un assistente può essere insegnato, in un pomeriggio, a produrre un bellissimo report settimanale. Il report richiede dieci minuti per essere prodotto a mano. Nel frattempo il processo che costa quaranta ore al mese—la corsa delle fatture, la riconciliazione, il sollecitare i conti in ritardo—viene lasciato solo, perché è più disordinato e perché tocca i soldi e perché qualcuno dovrebbe prendere una decisione su come dovrebbe funzionare.

Le aziende che ottengono un ritorno sono quelle che partono dal processo costoso, noioso, ripetitivo, e accettano che la prima versione sarà imperfetta. Le aziende che ottengono una dimostrazione sono quelle che partono dal report.

C'è una seconda trappola, che è l'immagine speculare: automatizzare qualcosa che non dovrebbe essere fatto per niente. Un assistente produrrà felicemente un report che nessuno legge, a una velocità che rende impossibile sostenere che non viene prodotto. Prima di automatizzare un compito, la domanda non è "può essere automatizzato?" ma "se questo fosse accaduto automaticamente, ogni giorno, qualcuno sarebbe stato più avvantaggiato?" Un numero sorprendente di compiti da ufficio falliscono questo test, e l'automazione corretta per loro è l'eliminazione.

## I numeri facili da sbagliare

Tre errori sono fatti in quasi ogni caso aziendale per questo tipo di sistema, e ciascuno vale la pena evitare perché ciascuno distrugge la credibilità dell'intero calcolo.

**Contare le ore salvate come se fossero soldi.** Un'ora salvata non è un'ora pagata. Se l'azienda non riduce le ore di nessuno, il risparmio è *capacità*, non cassa—e la capacità vale soldi solo se qualcuno la usa per qualcosa che guadagna. La versione onesta di Riverton al calcolo era: quaranta ore al mese di capacità, di cui circa metà usate per lavoro che sarebbe altrimenti stato fatto da un'agenzia o non affatto, e metà semplicemente un ufficio meno stanco. La seconda metà è reale e non compare in un foglio di calcolo.

**Ignorare il costo del cambiamento.** Installazione, configurazione, il primo mese di correzioni, la formazione, la resistenza. Un caso aziendale che presuppone che il nuovo sistema funzioni dal primo giorno è un caso aziendale che sarà sbagliato di una settimana del tempo di qualcuno. Quello di Riverton era due mesi di attenzione di Doreen a circa mezza carica, che è la singola riga più grande di tutto il calcolo e che nessun fornitore menziona mai.

**Presupporre che il beneficio sia permanente.** Un sistema che non è mantenuto decade: la lista dei prodotti si riempie di spazzatura, i codici fiscali derivano, i permessi dell'assistente si allargano "solo questa volta". La decadenza è lenta ed è invis finché qualcuno cerca di rispondere a una domanda e ottiene una risposta sbagliata con sicurezza. L'ora a settimana nell'agenda è il costo di manutenzione, ed appartiene al calcolo.

## Cosa dice realmente l'aritmetica

Con gli errori evitati, l'aritmetica del primo anno di Riverton sembra così.

| Riga | Importo |
|---|---|
| Licenze del software | £0 |
| Hardware (una macchina che l'azienda possedeva già) | £0 |
| Uso del modello linguistico per l'anno | circa £90 |
| Installazione e configurazione (tempo di Sam) | £1.200 |
| Tempo interno per configurare e correggere (due mesi, part-time) | circa £4.000 |
| **Costo totale** | **circa £5.300** |
| Ore tornate al lavoro produttivo | circa 480 |
| Valore di quelle ore ai tassi salariali di Riverton | circa £9.600 |
| Raccolta precedente dei crediti (dodici giorni di fatturato) | circa £14.000 di capitale circolante |
| Errori evitati (note di credito, prezzi sbagliati, ricarichi mancati) | circa £3.400 |
| **Beneficio totale, primo anno** | **circa £27.000, di cui £13.000 è cassa** |

La riga del capitale circolante è quella che sorprende le persone, ed vale la pena spiegarla perché non è profitto. Dodici giorni di fatturato che arrivano prima non rendono l'azienda più ricca; rendono l'azienda *più al sicuro*, perché i soldi sono in banca quando arriva il conto del fornitore. Per un'azienda con liquidità stretta, questo vale più della riga del profitto, ed è invisibile in un conto economico.

Il calcolo del secondo anno è molto migliore, perché il costo di installazione è sparito e resta solo la manutenzione: circa £500 di costo contro gli stessi benefici. Quella è la forma di ogni buon investimento in software: costoso nel primo anno, economico in seguito, e che vale tutto zero se nessuno lo mantiene.

## Il confronto che conta

Il confronto che un'azienda dovrebbe fare non è tra questo sistema e nessun sistema. È tra questo sistema *il modo in cui l'azienda lavora ora*, con tutti i suoi costi contati—inclusi quelli che non compaiono nei conti.

Il vecchio modo di Riverton costava, per anno: sessanta ore al mese di fatturazione e archiviazione (circa £18.000 ai tassi salariali completati), una quantità sconosciuta di ricerca e domande (probabilmente £6.000), dodici note di credito da errori di rigitura (£1.700), e dodici giorni di crediti permanentemente nei conti dei clienti (che è un prestito permanente di circa £14.000 di capitale circolante, a qualsiasi costo abbia il conto in rosso).

Contro questo, il nuovo modo costa £500 all'anno dopo il primo, più un'ora a settimana di attenzione.

Il confronto non è vicino, e non lo sarà mai—per qualsiasi azienda che produce documenti e vuole sapere cosa è vero. Ciò che ferma le aziende non è l'aritmetica. È il cambiamento, e la paura di esso, e nessun foglio di calcolo affronta ciò.

---

Gerald addizionò le colonne, si tolse gli occhiali, e diede a Maggie la risposta nel modo in cui i contabili fanno: non un numero, ma una frase con un numero al suo interno.

"Le ore che hai ottenuto tornate valgono circa trentamila sterline all'anno ai salari che paghi," disse. "I soldi che sono arrivati dodici giorni prima valgono più di quello, e non sono reddito, sono ossigeno. Gli errori valgono quattromila. Contro questo, i tuoi costi sono la macchina, il modello e il tuo tempo, che non hai addebitato e che dovresti."

"Quindi ne è valso la pena."

"Ne è valso la pena *se continui a fare la disciplina*," disse. "Se ti fermi, il sistema deriverà tornando a essere un archivio molto costoso dentro un anno. L'ho visto accadere. Il software non fallisce. Le abitudini sì."

Quella è la frase da ricordare da questo capitolo, ed è la frase meno commerciale del libro. L'aritmetica di non farlo è favorevole, decisivamente tale, per quasi ogni azienda che produce documenti e vuole sapere cosa è vero. Ma l'aritmetica tiene solo finché qualcuno mantiene il modello onesto, e quel qualcuno è una persona, e quella persona deve ricevere il tempo.

---

Maggie scrisse i numeri su una scheda e la mise nel cassetto con il fazzoletto. Poi fece qualcosa che Gerald non aveva suggerito, e che approvò quando lei glielo disse.

Diede a Doreen un titolo.

Non era un titolo grandioso—*sistemi d'ufficio ed eccezioni*—e non veniva con più soldi, perché Riverton è un'azienda piccola e i soldi sono reali. Ma veniva con un'ora al giorno che era protetta, nell'agenda, per il lavoro di notare: controllare i prezzi, leggere il log, fare all'assistente domande le cui risposte potrebbero essere scomode.

La scheda nel cassetto diceva quanto valeva il sistema. L'ora nell'agenda era ciò che rendeva vera la scheda.
