# 11. Étagères, Cartons et Noms

Tom Beck travaillait dans l'entrepôt de Riverton depuis dix-neuf ans, et il avait une seule règle concernant les ordinateurs, qu'il annonça le matin du quatrième jour, debout dans l'encadrement de la porte de la petite pièce, les bras croisés.

« Je ne vais pas saisir onze mille produits. »

« Personne ne te le demande, » dit Maggie. « Nous allons en saisir quarante. »

Tom décroisa les bras, ce qui représentait le degré maximum d'enthiasme qu'il atteignait avant le déjeuner.

---

## Pourquoi quarante et pas onze mille

Le catalogue d'un grossiste n'est pas la même chose que son *rayon*. Riverton listait onze mille références parce qu'en plus de trente ans elle avait acheté tout ce que les clients demandaient, et la liste avait grandi comme se développe une haie. Parmi ces onze mille, quatre cents avaient vendu plus de dix unités au cours de l'année dernière. quatre cents, c'est encore trop pour les saisir en une semaine, et la plupart partagent une forme : une marque, une taille, une couleur, une quantité en pack.

Le plan n'était donc pas de copier le catalogue. Le plan était de bien modéliser les *familles* et de laisser aux variantes faire le travail.

Le tableau blanc dans le bureau de l'entrepôt finit par contenir quatre lignes :

| Famille | Variantes | Unité de vente | Unité d'achat |
|---|---|---|---|
| Classeurs | 2 tailles × 3 couleurs | l'unité | carton de 20 |
| Marqueurs pour tableau blanc | 4 couleurs | pack de 4 | carton de 12 packs |
| Papier A4 | 1 | ramette | palette de 40 ramettes |
| Stylos à bille | 2 couleurs | carton de 50 | carton de 50 |

Quatre familles, et entre elles une demi-douzaine de variantes. Voilà ce qu'un ERP moderne appelle une liste de produits : pas une liste de tout ce que vous avez jamais acheté, mais un modèle des choses que vous vendez, avec les différences exprimées comme variantes plutôt que comme entrées séparées.

La différence n'est pas cosmétique. Si « Classeur A4 bleu » et « Classeur A4 rouge » sont deux produits, alors le système ne peut pas répondre à « combien de classeurs A4 avons-nous vendus ? » sans que quelqu'un sache que les deux sont liés. S'il s'agit d'un seul produit avec une variante de couleur, la question est triviale—et la question est tout le sujet.

## Les catégories, et pourquoi un rapport en a besoin

Une catégorie de produit est un dossier, et les dossiers sont ennuyeux tant que quelqu'un ne pose pas de question.

Dans Odoo, une catégorie fait trois choses : elle regroupe les produits pour les rapports, elle peut porter des comptes par défaut (de sorte que chaque produit de la catégorie affecte ses ventes au même compte de produits, et elle peut porter une unité de mesure par défaut et une méthode de coût.

Les catégories de Riverton finirent par être six : *Papier*, *Classeurs et classement*, *Instruments d'écriture*, *Encre et toner*, *Mobilier*, et *Services*. Six suffisent pour répondre à la question *quelle partie de l'affaire a fait de l'argent ce mois-ci ?* et sont assez peu pour que personne ne dispute du lieu où un produit appartient.

L'alternative—une seule catégorie appelée *Tous les produits*—est ce qu'une compagnie obtient si elle ne décide pas, et cela signifie que chaque rapport de marge est un rapport sur la compagnie dans son ensemble. C'est un bon rapport, et ce n'est pas celui qu'un grossiste nécessite, car le profit d'un grossiste se gagne et se perd dans le mélange entre les catégories, pas dans le total.

Il y a une seconde raison de s'en soucier, et c'est la comptabilité. Si la catégorie porte le compte de produits, alors un nouveau produit est affecté correctement par défaut, et la personne qui le crée n'a pas à rien savoir du plan comptable. Si elle ne le porte pas, chaque nouveau produit est une petite décision comptabilité prise par quelqu'un qui pense au papier.

## Les unités de mesure, et l'arithmétique de l'entrepôt

La seconde chose à bien faire est l'unité.

Riverton achète les classeurs par cartons de vingt et les vend à l'unité. Si le système ne sait pas qu'un carton fait vingt, alors chaque réception, chaque comptage et chaque livraison est un argument, et quelqu'un finira par convertir dans sa tête au mauvais moment.

Odoo gère ceci avec deux unités par produit : l'unité de mesure utilisée pour acheter et stocker (le carton), et l'unité de vente (l'unité), avec un facteur de conversion. L'entrepôt compte les cartons ; le client commande des unités ; la facture est en unités ; le stock est en cartons. Un seul nombre, trois vues.

Il y a ici un piège qui a coûté plus d'argent aux compagnies que tout autre réglage unique : **l'unité de mesure sur un produit existant ne peut pas être changée après qu'il a bougé.** Une fois une centaine de réceptions enregistrées en « unité », dire au système que le produit est réellement acheté en « cartons de vingt » ne convertit pas l'historique ; elle le corrompt. Le moment de bien faire ceci est avant la première réception, ce qui explique pourquoi Tom y passa une heure et pourquoi cette heure valait plus que les deux jours qu'il aurait passés plus tard à réconcilier un comptage de stock.

## L'entrepôt lui-même

Un ERP n'a pas « l'entrepôt ». Il a des *emplacements*, et un emplacement est tout endroit où le stock peut être.

Odoo installe deux par défaut : un emplacement virtuel appelé *Partenaires* (où les marchandises viennent et vont, car un fournisseur n'est pas une étagère) et *Stock*, l'entrepôt physique. De là, une compagnie ajoute ce qu'elle a réellement : *Stock/Étagère A*, *Stock/Étagère B*, *Stock/Retours*, *Stock/Dommagés*.

![Les emplacements de l'entrepôt : un endroit pour tout, y compris les endroits où les marchandises ne sont pas](../../assets/screens/odoo-06-locations.png)

Riverton en ajouta quatre : deux étagères, une zone de retour et une zone de quarantaine pour les marchandises endommagées. La dernière importe plus qu'il n'y paraît. Sans elle, le stock endommagé reste dans l'emplacement principal et est compté comme vendable, et la compagnie découvre le problème quand un client ouvre un carton de classeurs écrasés. Avec elle, le dommage est un *mouvement*—un document, avec une date et une raison—et le rapport de stock dit la vérité.

## Les premiers produits

Les produits furent saisis en un après-midi, par Priya et Tom ensemble, ce qui est le seul façon dont cela fonctionne : le vendeur sait comment le client l'appelle, l'entrepôt sait comment le fournisseur l'appelle, et l'enregistrement du produit a besoin des deux.

Six champs sur ce formulaire décident de presque tout ce qui arrive plus tard.

**Type de produit.** *Marchandises* pour les choses qu'on peut poser sur une étagère ; *Service* pour les choses qu'on ne peut pas. Un service n'a ni stock ni livraison ; une marchandise a les deux. Se tromper ici rend un produit définitivement non-livable ou définitivement non-comptable.

**Prix de vente et prix d'achat.** Les valeurs par défaut. Le vrai prix pour un client donné peut être différent—c'est pour ça que servent les nomenclatures de prix—mais la valeur par défaut est ce que le vendeur voit quand il est pressé.

**Taxe.** Le taux qui s'applique à ce produit. Comme le disait le chapitre dix : configuré ici, une seule fois, et hérité par chaque document.

**Unité de mesure.** Comme ci-dessus.

**Référence interne.** Le code que l'entrepôt utilise. C'est le champ qui fait la différence entre un système que les humains peuvent utiliser et un qu'ils ne peuvent pas, car c'est ce que les gens disent à haute voix quand ils se tiennent devant une étagère.

**Code-barres.** Optionnel, et transformateur si vous avez un lecteur : une livraison peut être vérifiée en bippant chaque carton plutôt qu'en lisant une liste.

## Le premier stock

Un système qui croit que l'entrepôt est vide refusera de livrer quoi que ce soit, ce qui est correct et incommode. Donc le premier stock doit être saisi, et il y a deux façons honnêtes de le faire.

La première est une *inventaire initial* : vous dites au système combien de chaque produit vous avez, à une date donnée, et il crée le stock correspondant. C'est ce que Riverton fit, sur deux soirs, avec un porte-plume et une lampe torche.

La seconde est un *comptage de stock* : le système vous demande de compter, et vous saisissez ce que vous trouvez, et il enregistre la différence entre ce qu'il croyait et ce qui est vrai. C'est ce que Riverton fait tous les trimestres maintenant, et c'est une opération différente avec un but différent.

Toutes deux sont des documents. Ni l'une ni l'autre n'est un nombre saisi dans un champ. C'est là la discipline qui fait fonctionner tout le système : **le stock n'est jamais un nombre que vous fixez ; c'est la somme des mouvements que vous avez enregistrés.** Si cela semble pédant, considerez ce qui arrive quand un nombre peut être fixé : quelqu'un le fixe, quelqu'un d'autre le remet, et l'entrepôt et les comptes restent en désordre pour toujours.

## Les choses qui ne sont pas des choses

Il y a une catégorie de produit qui cause plus de confusion que toute autre, et elle mérite une page à elle seule : les produits qui ne sont pas physiques.

Riverton en a trois, et chaque grossiste a les mêmes trois.

**Le transport.** La frais que le client paie pour la livraison. Il n'a ni stock ni réception, et il doit être facturé. Dans Odoo, c'est un produit de type *Service*, avec un taux de taxe et un prix, et la seule chose qui le distingue d'un carton de stylos est qu'il n'apparaît jamais dans une livraison.

**La remise.** Pas un produit du tout, dans la plupart des systèmes : une ligne négative sur la commande, ou une règle de nomenclature de prix. Mais une compagnie qui émet des notes de crédit pour des rabais de volume a besoin d'un produit à mettre sur la note de crédit, et on l'appelle généralement quelque chose comme *Rabais de volume* et on le saisit comme un service.

**L'échantillon.** Un produit donné gratuitement. Il a du stock, il quitte l'entrepôt, et il ne doit pas être facturé. S'il est modélisé comme un produit normal avec un prix zéro, les rapports de marge montreront une perte de cent pour cent sur une centaine d'unités ; s'il est modélisé comme un service, le stock ne partira jamais. La façon propre est une *livraison* du produit sans commande derrière, avec une raison, ce qui est aussi le seul moyen dont le coût finit par arriver au bon endroit.

Aucune de celles-ci n'est difficile. Toutes sont invisibles le premier jour et produisent des nombres étranges le trentième, ce qui explique pourquoi la personne qui configure le système devrait s'asseoir avec la personne qui facture et poser une question simple : *qu'est-ce que nous mettons sur une facture qui n'est pas sur une étagère ?*

## Les quatre cents produits que personne n'achète

Chacun grossiste les a : le catalogue de choses qui furent achetées une seule fois pour un client qui demanda, puis jamais de nouveau. Les onze mille références de Riverton contenaient, selon l'estimation de Tom, environ quatre cents de celles-là.

La tentation est de les nettoyer dans la première semaine, et c'est le premier mauvais mouvement pour deux raisons. Le nettoyage prend des semaines, et il enseigne au bureau que le nouveau système est une corvée avant qu'il ne leur ait appris que le nouveau système est utile.

Le bon mouvement est d'amener les quatre cents lignes qui comptent—celles avec de l'activité dans l'année dernière—et de laisser le reste dans l'ancien système, archivé, aussi longtemps que la loi l'exige. Un produit qui n'a pas bougé depuis 2019 n'a pas besoin d'un record dans le nouveau système le jour un ; il a besoin d'une décision, et la décision peut attendre jusqu'à ce que quelqu'un ait du temps.

Il y a un second bénéfice à attendre. Après trois mois du nouveau système, le rapport *produits sans mouvement dans l'année dernière* est une liste exactement des candidats à la retraite, produite en une seconde, avec la valeur de stock attachée. Le nettoyage devient une décision avec des nombres, plutôt qu'une semaine de saisie.

## La règle de réapprovisionnement

La dernière chose que Tom configura fut la règle de réapprovisionnement, et c'est le premier endroit où le système commence à être utile plutôt que simplement précis.

Pour chaque produit, il fixa deux nombres : un *minimum* (en dessous de ceci, nous sommes à risque) et un *maximum* (commander jusqu'à ceci). Odoo surveille le stock, et quand un produit tombe en dessous du minimum, il propose une commande d'achat pour la différence. Il ne l'envoie pas. Il la propose, dans une liste, et une personne décide.

Cette distinction—proposer, n'agir pas—est la même distinction qui importera énormément quand l'assistant arrivera dans la Partie III. Une machine qui propose est un collègue. Une machine qui agit sans demander est un risque avec une prise.

---

Le vendredi de cette semaine, Tom fit quelque chose qu'il n'avait pas fait en dix-neuf ans : il imprima un rapport de stock et le lut dans la fourgonnette, sur le chemin vers une livraison.

« Quatre cents douze lignes, » dit-il quand il revint. « Je les connais toutes. Mais je ne les ai jamais vues sur une seule page avant. Je les ai vues dans ma tête, une à la fois, quand quelqu'un demandait. »

Il posa le rapport sur le bureau de Maggie.

« Regarde le papier, » dit-il. « Nous avons onze cents ramettes et nous vendons environ quatre-vingt-dix la semaine. C'est trois mois de papier. Ce n'est pas exactement faux, mais c'est beaucoup d'argent assis sur une étagère. »

C'en était ainsi, et c'était la première fois que quelqu'un à Riverton pouvait le dire avec un nombre attaché. Le stock avait toujours été là ; le *fait* sur le stock était dans la tête de Tom, et la tête de Tom était dans une fourgonnette.

Voilà ce qu'un entrepôt devient quand il est modélisé correctement : pas un endroit où les choses sont, mais un endroit où les choses sont *connues*. Et le savoir, une fois qu'il existe, commence immédiatement à poser des questions que personne n'avait pensé à poser—à propos du papier, de l'argent liquide, des onze cents ramettes qui auraient pu être quatre cents.

Maggie écrivit le nombre au dos du rapport de stock et le mit dans le tiroir avec le mouchoir et la carte de Gerald. Le tiroir devenait plein. Cela, décida-t-elle, était un bon signe.
