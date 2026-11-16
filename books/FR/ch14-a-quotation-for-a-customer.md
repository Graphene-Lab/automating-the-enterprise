# 14. Un devis pour un client

Le premier vrai travail que l'assistant a réalisé à Riverton fut un devis, et il concernait le client dont la facture avait commencé toute l'histoire.

L'Académie Ashfield souhaitait quatre-vingts classeurs à anneaux et vingt boîtes de marqueurs pour tableaux blancs, pour le début du trimestre d'été. Priya avait la demande dans un courriel, qu'elle avait lu deux fois, car les quantités étaient inhabituelles : quatre-vingts classeurs représentaient un trimestre entier, et vingt boîtes de marqueurs dépassaient ce que l'école avait jamais commandé à la fois.

Sur l'ancien système, cela lui aurait pris douze minutes : ouvrir le programme de comptabilité, trouver le client, créer un devis, ajouter deux lignes, rechercher les prix dans le tableau qui contenait les prix contractuels, appliquer la réduction, l'imprimer, l'envoyer par courriel, l'archiver. Sur le nouveau système, cela prit quarante secondes, et les douze minutes allèrent ailleurs, plus utilement—dans un appel téléphonique à Carol à Ashfield pour savoir si les marqueurs étaient pour toute l'école ou pour le département des arts, ce genre de question qui empêche un retour.

Voici ce que Priya a tapé.

> *Créer un devis pour l'Académie Ashfield pour 400 classeurs A4 à anneaux, bleus, et 20 boîtes de marqueurs pour tableaux blancs, couleurs assorties, aux prix contractuels. Livraison à l'école, fin de semaine prochaine.*

Et voici ce qui est revenu.

> *Devis S00012 créé pour l'Académie Ashfield : 400 × Classeur A4 (bleu) à 3,40 £, 20 × Marqueurs pour tableaux blancs (paquet de 4, assortis) à 11,40 £. Net 1 588,00 £, TVA 317,60 £, total 1 905,60 £. Date de livraison fixée au vendredi 27 juin. Le devis est brouillon—dites « confirmer » quand vous voulez qu'il devienne commande.*

Quarante secondes, et chaque nombre qui s'y trouvait était vérifiable.

---

## La liste de prix, et pourquoi le prix contractuel n'est pas une réduction

Le prix que l'assistant a utilisé pour Ashfield—3,40 £ pour un classeur affiché à 3,95 £—ne provenait ni du record produit ni d'une réduction. Il provenait d'une *liste de prix*, et la distinction est une que les entreprises prennent à tort depuis des années.

Une liste de prix dans Odoo est un ensemble de règles attachées à un client (ou à un groupe de clients, ou à une devise) : pour ce produit, ou cette catégorie, ou tout, appliquer ce prix, ou ce pourcentage de réduction, ou cette formule. Ashfield possède une liste de prix contractuelle depuis janvier, convenue lors d'une réunion, signée sur une seule page, et elle indique ce que l'école paie pour les douze produits qu'elle achète régulièrement.

La différence entre une liste de prix et une réduction n'est pas cosmétique.

Une **réduction** est un ajustement à un prix, appliqué à un document, par une personne, au moment de la vente. Elle est visible sur le devis, elle est vérifiable, et c'est une décision que quelqu'un a prise.

Une **liste de prix** est le prix. Ce n'est pas un ajustement ; c'est ce que le client paie, et le prix liste est un autre nombre que ce client ne voit jamais. Un devis pour Ashfield qui afficherait 3,95 £ avec une réduction de quinze pour cent serait *correct* et serait aussi une petite insulte : il dirait au client que le vrai prix de l'entreprise est plus élevé et qu'on leur accorde une faveur.

Il existe une troisième possibilité, qui est ce que font réellement la plupart des petites entreprises : un tableau contenant les prix contractuels, consulté par une personne, et tapé à la main sur le devis. Cela fonctionne jusqu'à ce que la personne soit en vacances, que le tableau soit périmé, ou que le contrat soit renégocié et que le tableau ne le soit pas.

## Ce qui se passe quand le prix est erroné

Chaque entreprise a une histoire sur un prix erroné sur un devis, et toutes les histoires ont la même forme : l'erreur a été trouvée après confirmation de la commande, le client a été téléphoné, et quelqu'un a dû décider s'il fallait honorer le prix ou expliquer l'erreur.

La décision est généralement de l'honorer—la différence est petite et la relation pas—et le coût est écrit comme une leçon. Ce que l'entreprise apprend de cette leçon est généralement la chose fausse : *être plus prudent*, plutôt que *faire du prix un fait plutôt qu'une mémoire*.

Une liste de prix fait du prix un fait. Elle vit en un seul endroit, elle est datée, elle s'applique à chaque document pour ce client, et quand le contrat est renégocié, quelqu'un le change une fois. L'assistant le lit de la même façon qu'une personne, sauf qu'il ne peut pas oublier quel tableau est actuel.

La seule chose qu'une liste de prix ne peut pas faire est *décider*. Si Ashfield obtient une réduction de quinze pour cent sur le prix liste, ou un prix fixe, ou un prix qui augmente avec l'indice du papier, c'est une décision commerciale prise par des personnes. Le travail du système est de l'appliquer exactement, à chaque fois, et de le rendre visible quand il change—ce qui est le sujet de la section suivante.

## Le devis qui a changé un prix

Trois mois plus tard, Priya a posé une question qui n'avait jamais été possible auparavant.

*Quels clients paient un prix qui n'a pas changé depuis janvier, et quel serait le coût de son augmentation de trois pour cent ?*

La réponse fut une liste de neuf clients et un nombre : environ 4 100 £ par an de revenus supplémentaires, avec l'arithmétique par client. Les prix n'avaient pas changé parce que personne n'avait regardé, et personne n'avait regardé parce que regarder ouvrait neuf listes de prix et les comparait aux prix d'achat, ce qui aurait pris un après-midi.

S'il faut augmenter les prix est une décision commerciale, et Riverton les a augmentés pour quatre des neuf et a laissé les autres tranquilles pour des raisons qui n'avaient rien à voir avec l'arithmétique. Mais la décision a été prise avec un nombre devant elle, en dix secondes, plutôt que remise à une autre année.

C'est à nouveau le motif : la machine ne décide pas. Elle rend la décision assez bon marché pour la prendre.

---

## Ce qui s'est réellement passé

Il vaut la peine de ralentir cela, car la vitesse n'est pas la partie intéressante.

L'assistant ne savait pas ce qu'était un classeur à anneaux. Il n'avait jamais vu le contrat de l'Académie Ashfield, et il n'avait aucune idée de ce qu'était un trimestre scolaire. Ce qu'il avait, c'était un ensemble d'outils et une description de ce que chacun faisait, et un modèle de l'entreprise que quelqu'un d'autre avait construit.

Ainsi, quand l'instruction de Priya est arrivée, l'assistant a fait ce qu'un nouvel employé fait son premier jour : il a recherché des choses.

Il a recherché dans les clients un nom correspondant à *Ashfield Academy* et en a trouvé un—et, parce qu'il est prudent par conception, il aurait demandé s'il en avait trouvé deux. Il a recherché dans les produits *ring binder* et a trouvé un produit avec variantes, et il a choisi le bleu parce que Priya avait dit bleu. Il a recherché les marqueurs et a trouvé le paquet de quatre, assortis. Il a demandé à l'ERP le prix de chacun, pour ce client, à cette date, ce qui est une question différente de « quel est le prix de ce produit » et la différence est tout le chapitre dix.

Puis il a créé le devis : un document avec un client, une date, deux lignes, un calcul de taxe et un état. Et puis il s'est arrêté, car un devis en brouillon n'est pas un engagement, et il l'a dit.

Cette dernière phrase est la chose la plus importante que l'assistant ait faite. Il n'a pas confirmé la commande. Il n'a pas réservé le stock. Il n'a rien envoyé à personne. Il a produit une *proposition*, et il a dit à Priya que la proposition attendait qu'elle.

---

## La machine à états, et pourquoi elle importe

Un devis, une commande et une facture ne sont pas trois documents. Ce sont trois états de la même intention, et les transitions entre eux sont les moments où une entreprise s'engage.

**Brouillon.** Une proposition. Rien n'a été promis, aucun stock n'est réservé, le prix peut changer. Dans Odoo, on l'appelle un devis, et il a une date de validité, car un prix cité en juin n'est pas nécessairement un prix en septembre.

**Confirmé.** Une commande. L'entreprise a promis de livrer, à un prix, d'une date. Le stock est réservé (ou, dans une entreprise qui ne réserve pas, au moins l'intention est enregistrée), et le document obtient un nombre qui apparaîtra sur le bon de livraison et la facture.

**Livré.** Les marchandises sont parties. Maintenant il y a un mouvement de stock, et un bout de papier que le client a signé.

**Facturé.** L'argent a été demandé. Maintenant il y a une écriture de grand livre, et un point fiscal.

**Payé.** L'argent est arrivé. Maintenant il y a une transaction bancaire qui doit être appariée à la facture, ce qui est l'étape où la plupart des petites entreprises perdent la trace de leur trésorerie.

Chaque transition est une décision, et le travail de l'ERP est de s'assurer que la décision est prise délibérément. Un devis qui devient commande sans que personne ne décide est une promesse que l'entreprise ne savait pas avoir faite. Une commande qui devient facture avant que les marchandises ne partent est un point fiscal qui a bougé sans permission.

Priya a lu le devis, a changé une chose—elle a réduit les classeurs à trois cent cinquante, car le département des arts avait trouvé une armoire pleine—et l'a confirmé.

> *Changer la quantité de classeurs à 350 et confirmer la commande.*

> *Commande de vente S00012 confirmée : 350 × Classeur A4 (bleu), 20 × Marqueurs pour tableaux blancs. Total 1 712,40 £. Date de livraison vendredi 27 juin. Stock réservé : 350 classeurs disponibles, marqueurs disponibles.*

Remarquez ce que l'assistant a ajouté à la fin : *stock réservé, disponible*. On ne le lui avait pas demandé. Il a vérifié, car la prochaine chose qui arriverait serait une livraison, et une livraison qui ne peut pas être faite est pire qu'un devis qui ne peut pas être confirmé.

![La même opération sur l'installation de démonstration : commande S00002 confirmée, avec les totaux, l'état et deux choses que l'assistant pensait que vous deviez savoir](../../assets/screens/assistant-06-order.png)

La figure ci-dessus vaut la peine d'être lue attentivement, car c'est le comportement que ce chapitre a défendu, capturé plutôt que décrit. L'assistant rapporte le numéro de commande, l'état (*brouillon → vente*), le montant non taxé, la taxe et le total ; puis il propose deux choses qui n'avaient pas été demandées—que la taxe a été appliquée automatiquement à quinze pour cent, et qu'affirmer une commande ne crée ni une livraison ni une facture. Et il termine en disant comment il a vérifié : *J'ai vérifié le record en le relisant après confirmation.*

Cette dernière phrase est la différence entre un assistant et un formulaire. Un formulaire vous dit ce qu'il a enregistré. Un collègue vous dit ce qu'il a fait et comment il sait que ça a fonctionné.

---

## Une courte histoire du devis

Le mot *devis* vient du latin *quotare*, numéroter—la même racine que *quote* au sens de citer un passage. Dans le commerce, il signifie, depuis au moins quatre cents ans, une déclaration de prix offerte à un acheteur, et son statut juridique a été débattu dans les salles d'audience depuis lors.

Le débat est toujours le même : un devis est-il une offre, qui devient contrat quand il est accepté, ou une invitation au traité, qui est simplement une position d'ouverture ? La réponse dépend de la formulation, du contexte et de la juridiction, et c'est la raison pour laquelle un formulaire de devis porte généralement une ligne comme *ce devis est valide trente jours* et *sous réserve de disponibilité*.

Un ERP ne règle pas la question juridique, mais il fait quelque chose de lié et d'utile : il enregistre *quel* devis a été envoyé, *quand*, *à qui*, et *ce qu'il disait*. Quand un client téléphone en septembre et dit « vous m'avez cité quatre cents livres », l'entreprise peut trouver le document et voir s'il disait quatre cents ou quatre cents cinquante, et à quelle date, et pour combien.

Ce n'est pas une petite chose. Dans l'ancien système, la réponse vivait dans un fil de courriel, dans une copie imprimée dans un plateau, et dans la mémoire de Priya—dans cet ordre de fiabilité.

---

## Ce que l'assistant n'a pas fait

Trois choses valent la peine d'être remarquées dans ce qui n'est *pas* arrivé.

Il n'a pas appliqué une réduction. Ashfield a un prix contractuel, qui est un mécanisme différent d'une réduction, et l'assistant a utilisé le prix contractuel parce que c'est ce que dit le record du client. Si Priya avait voulu une réduction, elle aurait dû en demander une, et la réduction aurait été enregistrée—ce qui est la différence entre un prix et une faveur.

Il n'a pas choisi la date de livraison de lui-même. Il a pris *fin de semaine prochaine* et l'a tournée en date, ce qui est un petit acte d'interprétation, et il a dit quelle date il avait choisie afin que Priya puisse la corriger.

Et il n'a pas envoyé le devis. Envoyer est une action avec un client à l'autre bout, et l'assistant n'a pas d'outil pour le courriel dans la configuration de Riverton—délibérément. Le devis a été imprimé vers un PDF par l'ERP et joint à un courriel par une personne, ce qui a pris à Priya trente secondes et a gardé la dernière étape, celle où un document quitte le bâtiment, dans les mains humaines.

Certaines entreprises voudront automatiser cette étape, et le système peut le faire. Riverton a décidé, au premier mois, que rien ne serait envoyé à un client sans qu'une personne le regarde. C'est une décision qu'une entreprise peut reconsidérer ; ce n'est pas une décision qu'une entreprise devrait faire par accident.

---

La commande est restée dans le système deux jours, attendant la date de livraison.

Le jeudi, Tom a demandé à l'assistant une question que Priya n'avait pas pensé à demander.

> *Quelles commandes sont dues pour livraison dans les trois prochains jours, et le stock est-il présent pour toutes d'entre elles ?*

La réponse fut une liste de quatre commandes et une phrase qui a changé la semaine : les classeurs pour Ashfield étaient là, les marqueurs étaient là, mais la commande pour Northgate Library Service nécessitait douze boîtes de papier A4 et il y en avait neuf.

Neuf boîtes, et une promesse de livrer le lundi. C'est le genre de fait qui autrefois était découvert par un conducteur au quai de chargement, et il a été découvert à la place un jeudi après-midi par quelqu'un qui a pensé à demander.
