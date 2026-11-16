# 29. L'arithmétique de ne pas le faire

Gerald Pryce, le comptable au-dessus du magasin de produits chimiques, avait une règle concernant les investissements : *montrez-moi le coût de la chose pour laquelle vous payez déjà.*

Maggie era venue le voir au printemps, avec les factures de l'année et une question qui la gênait un peu, car elle ressemblait à la question de quelqu'un qui avait déjà décidé. « Est-ce que ça valait le coup ? »

Gerald posa ses lunettes, ce qui signifiait qu'il allait s'amuser.

« Pas encore », dit-il. « D'abord, nous faisons l'arithmétique de ne pas le faire. »

---

La plupart des études de cas pour les logiciels sont écrites à l'envers. Elles listent le coût de la nouvelle chose — la licence, le matériel, la formation, le consultant — puis elles listent les avantages dans le langage de l'espoir : efficacité, visibilité, agilité. Les chiffres du côté du coût sont précis, parce que quelqu'un les a chiffrés. Les chiffres du côté des avantages sont des adjectifs.

L'arithmétique de ne pas le faire est l'inverse. Elle part de la position selon laquelle l'entreprise paye déjà son mode de fonctionnement actuel, jour après jour, et que ce paiement n'apparaît dans aucun compte parce qu'il est fait en heures.

Ainsi, Gerald et Maggie passèrent une matinée avec un tableur — l'outil qui a remplacé l'arithmétique du comptable et n'a pas remplacé le comptable — et ils comptèrent.

**La première ligne était la course des factures.** Riverton produisait, en moyenne, quatre-vingts-cent factures par mois. Chacune prenait, du moment où la livraison était confirmée au moment où l'enveloppe était à la poste, entre quatre et six minutes du temps de quelqu'un : impression, vérification par rapport au bon de livraison, pliage, adresse, timbre. Appelez ça cinq minutes, ce qui fait soixante heures par mois, ce qui est la plupart d'une semaine de travail et demie.

Après le changement, la course prenait onze minutes au total, car les documents étaient générés et envoyés par courriel, et la vérification se faisait en regardant une liste plutôt que chaque morceau de papier. Les soixante heures ne devinrent pas zéro ; une partie d'entre elles devinrent de la vérification, et une partie devinrent le travail que Doreen avait toujours voulu faire. Mais quarante heures par mois revinrent à l'entreprise.

**La deuxième ligne était la recherche.** Personne n'avait jamais mesuré ceci, car personne ne mesure la recherche. Doreen l'estima à une heure par jour, ce qui était probablement une sous-estimation, car les gens ne comptent pas les interruptions. Twenty heures par mois, disparues. Après le changement, c'était peut-être trois, surtout passé à regarder des choses qui nécessitaient une décision plutôt qu'un emplacement.

**La troisième ligne était les erreurs.** Douze notes de crédit l'année précédente, causées par des prix faux, des quantités fausses ou des adresses fausses, à une moyenne de cent quarante livres chacune, plus le temps à les corriger et le petit dommage à la relation. Le changement n'éliminait pas les erreurs, mais il supprimait la classe d'erreurs causées par la retapage, car rien n'était retapé.

**La quatrième ligne était l'argent qui arrivait tard.** C'est la ligne qui surprit Maggie, car ce n'est pas un coût dans les comptes ; c'est un coût dans la banque. Le temps moyen de la facture au paiement avait été de cinquante-trois jours. Après six mois de factures envoyées à temps, et d'un rappel poli que l'assistant produisait chaque lundi sans qu'on le lui demande, c'était quarante-et-un. Douze jours de chiffre d'affaires d'une entreprise, assis dans la banque plutôt que dans les comptes des clients, valent plus que le coût entier du système, et cela n'apparaît nulle part dans un compte de profits et pertes.

---

Contre cela, les coûts.

Le logiciel était gratuit. Odoo Community, la base de données, l'assistant et le connecteur sont tous open source, et la licence pour tout cela est zéro. Ce n'est pas un tour et ce n'est pas un essai : c'est le modèle économique de l'open source, et c'est pourquoi une entreprise de la taille de Riverton peut se permettre un système qui aurait été impensable en 1995.

Le matériel était un ordinateur que l'entreprise possédait déjà, avec assez de mémoire et de disque pour lancer trois programmes à la fois. Si une entreprise doit en acheter un, c'est une dépense en capital du même ordre que le service annuel d'une fourgonne de livraison, et il dure plus longtemps.

Le modèle linguistique était un service, payé à l'usage. Le montant dépend du fournisseur et de combien l'assistant est demandé à faire, et c'est la seule ligne qu'une entreprise devrait surveiller, de la façon dont elle surveille l'électricité. Ce qui compte, c'est le ratio : l'assistant est demandé à faire des choses qui autrement prendraient à une personne des minutes, et le coût d'une requête est mesuré en fractions d'un centime, donc le ratio n'est pas proche.

Les coûts honnêtes étaient les deux que personne ne chiffre.

La première était *le temps à installer*, qui fut une journée de l'attention de Sam Okafor et une semaine de celle de Maggie, étalées sur un mois, surtout le soir. La deuxième était *la discipline*, qui n'est pas un coût que vous payez une fois. Quelqu'un doit garder la liste de produits propre, décider ce que l'assistant est autorisé à faire, lire le journal, et dire non à la requête d'ajouter une exception de plus. C'est un travail permanent, petit, sans glamour, et c'est le prix de tout le système.

---

Il y a un piège dans cette arithmétique, et ça vaut la peine de le nommer car il attrape les entreprises intelligentes.

Le piège est d'automatiser la partie qui est facile à automatiser plutôt que la partie qui coûte le plus. Un assistant peut être enseigné, en un après-midi, à produire un beau rapport hebdomadaire. Le rapport prend dix minutes à produire à la main. Pendant ce temps, le processus qui coûte quarante heures par mois — la course des factures, la réconciliation, le suivi des comptes en retard — est laissé seul, car il est plus salissant et parce qu'il touche à l'argent et parce que quelqu'un devrait prendre une décision sur comment il devrait fonctionner.

Les entreprises qui obtiennent un retour sont celles qui commencent par le processus cher, ennuyeux, répétitif, et acceptent que la première version sera imparfaite. Les entreprises qui obtiennent une démonstration sont celles qui commencent par le rapport.

Il y a un deuxième piège, qui est l'image miroir : automatiser quelque chose qui ne devrait pas être fait du tout. Un assistant produira joyeusement un rapport que personne ne lit, à une vitesse qui rend impossible d'argumenter qu'il n'est pas produit. Avant d'automatiser une tâche, la question n'est pas « peut-elle être automatisée ? » mais « si ceci arrivait automatiquement, chaque jour, quelqu'un serait-il mieux loti ? » Un nombre surprenant de tâches de bureau échouent à ce test, et l'automatisation correcte pour eux est la suppression.

## Les nombres qui sont faciles à se tromper sur

Trois erreurs sont faites dans presque chaque étude de cas pour ce genre de système, et chacune d'elles vaut la peine d'être évitée car chacune détruit la crédibilité de tout le calcul.

**Compter les heures sauvées comme si c'était de l'argent.** Une heure sauvée n'est pas une heure payée. Si l'entreprise ne réduit les heures de personne, l'économie est *la capacité*, pas le cash — et la capacité n'est valeureuse en argent que si quelqu'un l'utilise pour quelque chose qui rapporte. La version honnête de Riverton du calcul était : quarante heures par mois de capacité, dont environ la moitié était utilisée pour du travail qui autrement aurait été fait par une agence ou pas du tout, et la moitié était simplement un bureau moins fatigué. La deuxième moitié est réelle et elle n'apparaît pas dans un tableur.

**Ignorer le coût du changement.** Installation, configuration, le premier mois de corrections, la formation, la résistance. Une étude de cas qui suppose que le nouveau système fonctionne dès le premier jour est une étude de cas qui sera fausse d'une semaine du temps de quelqu'un. Celle de Riverton fut deux mois de l'attention de Doreen à environ demi-temps, ce qui est la plus grande seule ligne dans tout le calcul et que aucun vendeur ne mentionne jamais.

**Supposer que l'avantage est permanent.** Un système qui n'est pas maintenu se dégrade : la liste de produits se remplit de ferraille, les codes fiscaux dérivent, les permissions de l'assistant s'élargissent « juste cette fois ». La dégradation est lente et elle est invisible jusqu'à ce que quelqu'un essaie de répondre à une question et obtienne une réponse fausse avec confiance. L'heure par semaine dans le calendrier est le coût de maintenance, et elle appartient au calcul.

## Ce que l'arithmétique dit réellement

Avec les erreurs évitées, l'arithmétique de la première année de Riverton ressemble à ceci.

| Ligne | Montant |
|---|---|
| Licences de logiciel | 0 £ |
| Matériel (une machine que l'entreprise possédait déjà) | 0 £ |
| Usage du modèle linguistique pour l'année | environ 90 £ |
| Installation et configuration (temps de Sam) | 1 200 £ |
| Temps interne à configurer et corriger (deux mois, demi-temps) | environ 4 000 £ |
| **Coût total** | **environ 5 300 £** |
| Heures retournées au travail productif | environ 480 |
| Valeur de ces heures aux taux de salaire de Riverton | environ 9 600 £ |
| Collecte plus tôt des créances (douze jours de chiffre d'affaires) | environ 14 000 £ de fonds de roulement |
| Erreurs évitées (notes de crédit, prix faux, recharges manquées) | environ 3 400 £ |
| **Avantage total, première année** | **environ 27 000 £, dont 13 000 £ est du cash** |

La ligne des fonds de roulement est celle qui surprend les gens, et ça vaut la peine de l'expliquer car ce n'est pas du profit. Douze jours de chiffre d'affaires arrivant plus tôt ne rend pas l'entreprise plus riche ; elle rend l'entreprise *plus sûre*, car l'argent est dans la banque quand la facture du fournisseur arrive. Pour une entreprise avec un cash serré, c'est valeureux plus que la ligne de profit, et elle est invisible dans un compte de profits et pertes.

Le calcul de la deuxième année est bien meilleur, car le coût d'installation est parti et il ne reste que la maintenance : environ 500 £ de coût contre les mêmes avantages. C'est la forme de tout bon investissement en logiciel : cher à la première année, gratuit ensuite, et ne valant tout à fait rien si personne ne le maintient.

## La comparaison qui compte

La comparaison qu'une entreprise devrait faire n'est pas entre ce système et aucun système. C'est entre ce système et *le mode de fonctionnement de l'entreprise maintenant*, avec tous ses coûts comptés — y compris ceux qui n'apparaissent pas dans les comptes.

Le vieux mode de Riverton coûtait, par an : soixante heures par mois de facturation et de classement (environ 18 000 £ aux taux de salaire chargés), une quantité inconnue de recherche et de demande (probablement 6 000 £), douze notes de crédit des erreurs de retapage (1 700 £), et douze jours de créances permanentement dans les comptes des clients (ce qui est un prêt permanent d'environ 14 000 £ de fonds de roulement, à ce que coûte le découvert).

Contre cela, le nouveau mode coûte 500 £ par an après le premier, plus une heure par semaine d'attention.

La comparaison n'est pas proche, et elle ne l'est jamais — pour n'importe quelle entreprise qui produit des documents et veut savoir ce qui est vrai. Ce qui emp les entreprises n'est pas l'arithmétique. C'est le changement, et la peur de lui, et aucun tableur ne s'adresse à cela.

---

Gerald additionna les colonnes, retira ses lunettes, et donna à Maggie la réponse de la façon dont les comptables le font : pas un nombre, mais une phrase avec un nombre à l'intérieur.

« Les heures que vous avez retournées valent environ trente-et-un mille livres par an aux salaires que vous payez », dit-il. « L'argent qui arriva douze jours plus tôt vaut plus que cela, et ce n'est pas un revenu, c'est de l'oxygène. Les erreurs valent quatre mille. Contre cela, vos coûts sont la machine, le modèle et votre propre temps, que vous n'avez pas facturés et devriez. »

« Donc ça valait le coup. »

« Ça valait le coup *si vous continuez la discipline* », dit-il. « Si vous arrêtez, le système dérivera vers le fait d'être un classeur très coûteux en un an. J'ai vu ça arriver. Le logiciel ne échoue pas. Les habitudes, si. »

C'est la phrase à retenir de ce chapitre, et c'est la phrase la moins commerciale du livre. L'arithmétique de ne pas le faire est favorable, décisivement ainsi, pour presque chaque entreprise qui produit des documents et veut savoir ce qui est vrai. Mais l'arithmétique ne tient que tant que quelqu'un garde le modèle honnête, et ce quelqu'un est une personne, et cette personne doit se voir donner le temps.

---

Maggie écrivit les nombres sur une carte et le mit dans le tiroir avec le mouchoir en papier. Puis elle fit quelque chose que Gerald n'avait pas suggéré, et qu'approuva quand elle le lui dit.

Elle donna un titre à Doreen.

Ce n'était pas un titre grand — *systèmes de bureau et exceptions* — et il ne venait pas avec plus d'argent, car Riverton est une petite entreprise et l'argent est réel. Mais il venait avec une heure par jour qui était protégée, dans le calendrier, pour le travail de remarque : vérifier les prix, lire le journal, demander à l'assistant des questions dont les réponses pourraient être inconfortables.

La carte dans le tiroir disait ce que le système valait. L'heure dans le calendrier était ce qui rendait la carte vraie.
