# 25. Les instructions qui fonctionnent

Au printemps, Riverton disposait d'un document sur le lecteur partagé intitulé *Comment demander*, et il faisait quatre pages. Personne ne l'avait écrit comme un manuel ; il était né d'une filière d'emails dans laquelle les gens publiaient les instructions qui avaient fonctionné, et celles qui n'avaient pas fonctionné, et quand Maggie l'a imprimé, il era devenu le document le plus lu de l'entreprise.

Ce chapitre est ce document, réécrit.

---

## Les quatre parties d'une instruction

Toute instruction qui a fonctionné, dans les mois de test qui précèdent ce livre, avait quatre parties, que la personne qui l'écrivait en soit consciente ou non.

**Un verbe.** Que faire. *Lister. Créer. Changer. Annuler. Totaliser. Comparer. Envoyer.* Une instruction sans verbe est un sujet, et l'assistant y répond par un paragraphe de conversation plutôt que par du travail.

**Un objet.** À quoi le faire, nommé comme l'entreprise le nomme. *Les factures pour Ashfield Academy. Les classeurs à anneaux. La commande d'achat de mardi.* Si l'objet est ambigu—*la commande*—l'assistant doit deviner, et il devinera de façon plausible plutôt que correcte.

**Un périmètre.** Lesquelles, combien, sur quelle période. *Les factures impayées de plus de trente jours. Les commandes du mois dernier. Les cinq produits au stock le plus bas.* Le périmètre est là où la plupart des instructions échouent, car un être humain demandant à un collègue s'appuierait sur un contexte partagé, et l'assistant n'en a aucun, sauf s'il est donné.

**Une contrainte, quand il y en a une.** *Aux prix standards. Livraison lundi prochain. Ne pas l'encoder pour le moment.* Une contrainte est la différence entre un brouillon et un engagement, et c'est la partie que les gens oublient, puis blâment la machine pour avoir fait ce qu'on lui a demandé.

Comparez :

> *Faire les factures.*

> *Créer des factures à partir de toutes les commandes de vente confirmées datant de la semaine dernière, les laisser en brouillon, et me donner le total.*

La première est ce que les gens tapent quand ils sont pressés, et la réponse qu'ils reçoivent est soit une question, soit un devinements. La seconde est quarante secondes de frappe et elle produit du travail.

## La différence entre une question et une action

L'assistant peut faire deux choses tout à fait différentes, et les mêmes mots peuvent déclencher l'une ou l'autre.

Une **question** produit une réponse : *combien de clients nous doivent de l'argent ?* Rien dans l'ERP ne change.

Une **action** produit un document : *créer la facture.* L'ERP change, définitivement, avec un horodateur et un nom d'utilisateur attachés.

La différence compte car les deux ont des coûts d'erreur différents. Une réponse erronée coûte une minute ; une facture erronée coûte un après-midi. L'habitude sûre—et celle que le livre recommande depuis le premier jour—is de poser d'abord la question, puis d'agir sur la réponse :

> *Quelles factures sont en retard de plus de trente jours ? Listez-les avec le montant et le client.*

puis, après avoir lu la liste :

> *Créer un rappel pour les trois plus grosses, en brouillon, et me montrer le texte avant d'envoyer.*

Cette habitude en deux temps n'est pas de la timidité. C'est comment un bon employé travaille avec un nouveau système : regarder, puis agir.

## Nommer les choses comme l'entreprise les nomme

Un ERP a trois noms pour tout : le nom sur la fiche, la référence interne, et le nom que les gens utilisent. L'assistant travaille avec les deux premiers, et le troisième est celui qui est dans votre tête.

Riverton a découvert cela la première semaine. Quelqu'un a demandé *les classeurs bleus* et a obtenu une liste de rien, car le produit s'appelle *Classeur à anneaux A4*, avec une variante de couleur, et le mot « bleu » vit dans la variante, pas dans le nom. Une fois la demande devenue *classeurs à anneaux A4, variante bleue*, ça a fonctionné.

La solution n'est pas d'apprendre des synonymes à l'assistant. La solution est une habitude d'entreprise : quand un produit, un client ou un document a un nom dans le système, utilisez ce nom dans l'instruction. C'est la même discipline que l'utilisation du numéro de compte du client quand vous téléphonez à la banque.

## Les instructions qui fonctionnent le mieux

Quatre sortes d'instruction ont produit les meilleurs résultats dans les tests, et elles valent la peine d'être apprises délibérément.

**Le balayage.** *Listez tout ce qui correspond à cette condition.* Les balayages sont là où l'assistant bat une personne carrément, car une personne doit ouvrir des écrans et l'assistant, non. *Toute facture impayée depuis plus de trente jours. Tout produit en dessous de son point de réapprovisionnement. Tout client qui n'a pas commandé depuis janvier.*

**La chaîne.** *Faites ceci, puis cela, puis donnez-moi le résultat.* Les chaînes sont la seconde grande force de l'assistant : elle ne perd pas le fil entre les étapes. *Créez la commande, confirmez-la, livrez-la, factez-la, et donnez-moi le numéro de facture.*

**La comparaison.** *Comparez cette période à celle-là.* Les comparaisons sont là où une personne devrait exporter deux feuilles de calcul. *Comparez les ventes de ce mois au même mois de l'année dernière, par produit.*

**L'exception.** *Donnez-moi seulement ce qui est incorrect.* C'est la plus précieuse et la moins utilisée. *Montrez-moi les ajustements de stock dont la raison est manquante. Montrez-moi les factures dont le total ne correspond pas à la commande.*

## Ce qu'il ne faut pas demander

Quatre sortes d'instruction n'ont rien produit d'utile, et les échouements sont assez réguliers pour valoir la peine d'être nommés.

**Le verbe vague.** *Gérez les factures. Débrouillez-vous pour le stock. Occupez-vous des comptes en retard.* L'assistant demandera ce que tu veux dire, ce qui est le comportement correct et un gaspillage d'une minute.

**La demande de jugement qu'elle ne peut pas faire.** *Quels clients valent la peine d'être conservés ?* Elle peut vous donner les chiffres—revenu, marge, comportement de paiement, depuis combien de temps ils sont silencieux—et elle peut les classer. Elle ne peut pas vous dire ce que votre entreprise valorise, car ce n'est pas dans la base de données.

**L'instruction qui dépend de quelque chose qui n'est pas dans le système.** *Facture le travail que nous avons fait pour l'école jeudi dernier.* Si le travail n'a jamais été enregistré, l'assistant ne trouvera rien, et la réponse correcte est rien. Ce n'est pas une limitation de l'assistant ; c'est la même limitation qu'a un nouvel employé, et le remède est le même : écrivez-le.

**L'instruction qui la demande de deviner.** *Créez le client à partir de cet email.* Elle peut lire l'email si vous lui donnez l'email ; elle ne peut pas lire votre boîte de réception sauf si quelqu'un lui a donné cet outil, et elle n'inventera pas une adresse pour être utile. Si vous voulez qu'elle extraie, dites-le : *lis cet email et propose la fiche client, mais ne la crée pas avant que je le dise.*

## L'habitude de vérification

Toute instruction qui produit une action doit être suivie d'un contrôle, et le contrôle doit être la réponse de l'assistant à une question sur ce qu'elle a fait.

> *Confirmez la commande.*
>
> *Quelle commande avez-vous confirmée, et quel est son total ?*

La seconde instruction coûte cinq secondes et comble l'écart entre ce que vous vouliez et ce qui s'est passé. Dans les mois de test, cette habitude a capturé chacune des erreurs qui comptaient, et les erreurs qu'elle a capturées étaient presque toujours des *définitions*, pas de l'arithmétique : l'assistant avait fait exactement ce qui était demandé, et ce qui était demandé n'était pas ce qui était voulu.

## L'instruction qui demande un jugement

Il existe une catégorie d'instruction que les gens écrivent constamment et qui presque jamais ne fonctionne, et elle valant la peine d'être nommée car elle semble si raisonnable : l'instruction qui demande à l'assistant de décider.

*Quels clients devons-nous relancer ? Quels produits devons-nous cesser ? Ce fournisseur est-il trop cher ?*

Chacune de celles-là est une décision, et une décision nécessite trois choses que l'assistant n'a pas : ce que l'entreprise valorise, quelles sont les alternatives, et qui porte les conséquences. Ce que l'assistant a, c'est des données, et la version utile de chaque question lui donne les données et garde la décision :

*Listez les clients avec une facture en retard et aucune commande dans quatre-vingt-dix jours, avec le montant et la date de la dernière commande.* La décision—relancer, attendre, ou passer en perte—est alors prise par une personne, en une minute, avec les faits devant eux.

La distinction n'est pas de la pedanterie. Un assistant qui répond à une question de jugement produit une réponse *plausible*, ce qui est pire qu'aucune réponse, car elle invite quelqu'un à agir sans avoir réfléchi. Un assistant qui produit les faits produit quelque chose avec quoi une personne peut réfléchir.

## Former un collègue

Le document sur le lecteur partagé de Riverton faisait quatre pages parce que quelqu'un l'a écrit, et l'acte de l'écrire vaut une section à lui seul.

Quand une entreprise adopte cette technologie, la connaissance de comment s'en servir vit dans une ou deux personnes, et c'est généralement tacite : elles savent que *les classeurs bleus* ne fonctionne pas et que *classeurs à anneaux A4, variante bleue* fonctionne, et elles ne pourraient pas vous dire pourquoi. Cette connaissance vaut plus que le logiciel, et elle s'évapore quand la personne part.

Le remède est le plus ancien au monde : gardez une liste des instructions qui ont fonctionné, dans la langue de l'office, avec une ligne sur ce que chacune est pour. Pas un manuel—un manuel est écrit par quelqu'un qui a cessé de faire le travail. Une liste est écrite par quelqu'un qui le fait.

La liste de Riverton a trois sections, et la troisième est celle qui compte.

**Les instructions qui fonctionnent**, groupées par département, une ligne chacune, avec le résultat noté.

**Les instructions qui ont échoué**, avec ce qui était incorrect—car les échouements sont là où est l'apprentissage, et car une liste de succès n'enseigne à personne rien.

**Les instructions que nous n'avons pas encore essayées**, qui est une liste de souhaits. *Peut-elle me dire quels clients sont rentables ? Peut-elle comparer la facture d'un fournisseur à la commande sans que je demande ? Peut-elle préparer la déclaration de TVA et la réconcilier ?* Certaines de celles-là fonctionneront et d'autres non, et la liste est comment une entreprise découvre lesquelles.

## Les anti-modèles, dans une entreprise plutôt qu'un prompt

Quatre habitudes apparaissent dans chaque entreprise qui adopte un assistant, et elles sont toutes raisonnables et toutes nuisibles.

**Le héros.** Une personne devient la personne qui sait comment demander, et tout le monde le leur demande. L'entreprise a maintenant un goulot d'étranglement avec un salaire, et la connaissance est dans une tête—ce qui est exactement la condition que le système a été acheté pour guérir.

**Le sceptique.** Une personne décide que la technologie est un jouet, et lui pose des questions conçues pour la faire échouer, en public. Elles réussiront, car tout système peut être fait échouer par une question qui est en dehors de ses données. Le coût n'est pas l'échouement ; c'est que le reste de l'office apprend à avoir peur de paraître ridicule.

**La sur-confiance.** Une personne décide que la machine a toujours raison, et cesse de vérifier. Cela dure jusqu'à ce que la première erreur définitionnelle atteigne un client, et alors la réaction est sévère—généralement un retour au papier pendant un mois, qui coûte plus que l'erreur.

**Le fantôme.** Le système est installé, félicité à une réunion, et jamais utilisé, car la personne qui était censée s'en servir était occupée cette semaine et l'ancienne façon fonctionnait encore. Six mois plus tard, on découvre que la licence est payée pour un programme que personne n'ouvre.

L'antidote à tous les quatre est le même : une personne *nommée*, une heure *protégée* par semaine, et une *démonstration* une fois par mois dans laquelle quelqu'un montre à l'office quelque chose que l'assistant a fait qui était utile. Pas une session de formation ; une démonstration. La différence est qu'une démonstration est à propos du travail, et qu'une session de formation est à propos du logiciel.

## Le journal des prompts

Il y a une dernière habitude valeureuse à adopter, et elle ne coûte rien.

Gardez les instructions que vous avez tapées. Pas parce que vous aurez besoin de les répéter—bien que vous le ferez—mais parce que le journal est le record de ce que l'entreprise a demandé, et le record de ce que la machine a compris.

Odoo garde le *résultat* : la facture, la commande, le paiement. Il ne garde pas la phrase qui l'a produite. L'assistant garde son propre journal, mais un journal est un artefact technique avec des horodateurs et des appels d'outil ; ce n'est pas l'histoire de la journée.

Un journal est une ligne par instruction, dans un fichier texte, avec la date. Six mois plus tard, il répond à des questions que rien d'autre ne peut : *quand avons-nous commencé à relancer à quinze jours ? Qu'avions-nous demandé de faire dans la semaine où la facture Ashfield a mal tourné ? Quelqu'un a-t-il jamais demandé de comparer deux mois ?*

C'est la forme la plus bon marché de mémoire institutionnelle qui soit, et la seule qu'une petite entreprise gardera réellement.

## Où vivent les instructions

Le chapitre suivant est la bibliothèque : plus de cinquante instructions, groupées par département, chacune exécutée sur une installation réelle pendant l'écriture de ce livre, avec le résultat enregistré.

Ce ne sont pas un script à faire lire à voix haute. Ce sont un vocabulaire. Lisez celles pour votre département, adaptez les noms à votre entreprise, et ajoutez celles qui manquent—car la bibliothèque qui compte est celle que votre office écrit pour elle-même, dans la langue qu'elle parle réellement.

Il y a une dernière chose à dire sur les prompts, et c'est celle qui a pris le plus longtemps à Riverton à apprendre.

L'instruction n'est pas une formule magique. C'est une *délégation*, et elle porte les mêmes obligations que de déléguer à une personne : dire ce que vous voulez, dire ce que vous ne voulez pas, donner à la personne l'information dont elle a besoin, et vérifier le résultat. Les entreprises qui tirent de cette technologie de la valeur ne sont pas celles avec les prompts les plus intelligents. Ce sont celles qui déléguent bien—ce qui, par ailleurs, est aussi la différence entre un bon manager et un mauvais, et l'a été depuis longtemps avant qu'il y ait des machines à déléguer.
