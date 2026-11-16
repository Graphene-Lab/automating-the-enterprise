# 17. Acheter des marchandises

Acheter constitue la moitié d'une entreprise que personne n'écrit sur des livres.

Vendre a une romance qui l'entoure : des clients, des devis, le frisson de la commande. Acheter, lui, a un bon de commande, un bon de livraison, une facture d'un fournisseur, et un traitement de paiements. Et pourtant chaque livre dépensé par un grossiste arrive par cette porte, et la différence entre une compagnie qui achette bien et une qui achette mal est la différence entre une marge et une habitude.

L'achat chez Riverton était fait par Maggie, par téléphone, par mémoire, pendant onze ans. Elle connaissait le fournisseur de papier, le fournisseur de stylos et le fournisseur de classeurs, et elle savait ce qu'elle avait payé la dernière fois parce qu'elle avait un classeur. Ce qu'elle n'avait pas, c'était un moyen de savoir si le prix avait grimpé, ou si la dernière livraison était réellement arrivée, ou si la facture qu'elle était sur le point de payer correspondait à la commande qu'elle avait passée.

La première tâche d'achat de l'assistant fut une règle de réapprovisionnement qui se déclenchait un mercredi.

---

## La règle de réapprovisionnement, et ce qu'elle propose

Le chapitre onze a posé deux nombres sur chaque produit : un minimum et un maximum. Odoo surveille le stock, et lorsqu'un produit descend sous son minimum, il propose un bon de commande.

Il en proposa un pour les classeurs, le mercredi, dans une liste que Tom regarda avec son café.

> *Trois produits sont sous leur point de réapprovisionnement : Classeur A4 (bleu) 62 disponibles, minimum 100 ; Marqueurs de tableau blanc (assortis) 44 disponibles, minimum 60 ; Papier A4 9 ramettes disponibles, minimum 40.*

Tom regarda la liste, décida que le papier pouvait attendre que le prix de palette soit confirmé, et demanda les deux autres.

> *Créer un bon de commande pour 500 classeurs A4, bleus, et 200 paquets de marqueurs de tableau blanc, assortis, de nos fournisseurs habituels, au dernier prix payé. Ne pas le confirmer encore.*

> *Bon de commande P00008 créé, en brouillon. Deux fournisseurs, car les produits viennent de fournisseurs différents : 500 × Classeur A4 (bleu) de Pennine Paper à £2,10 ; 200 × Marqueurs de tableau blanc (paquet de 4, assortis) de Kestrel Supplies à £6,80. Total net £2 410,00, TVA £482,00, total £2 892,00. Rien n'a été envoyé ; dire « confirmer » pour passer les commandes.*

Deux choses dans cette réponse valent qu'on y remarque, et toutes deux relèvent du système faisant ce qu'une personne aurait dû faire à la main.

La première est *deux fournisseurs*. Tom avait demandé deux produits ; le système savait qu'ils viennent de fournisseurs différents et produisit deux bons de commande. Une personne aurait fait de même, après avoir regardé les fiches produits. La différence est que la personne aurait pu oublier, et commander des classeurs chez le fournisseur de marqueurs.

La deuxième est *le dernier prix payé*. Ce n'est pas une liste de prix ; c'est un fait tiré de l'historique. Le système a regardé l'achat le plus récent de ce produit et a utilisé le prix. Si le fournisseur a augmenté ses prix, la commande sera fausse — mais elle sera fausse d'une manière qu'on peut voir, car le prix précédent est sur la fiche à côté du nouveau.

## Ce que la confirmation fait

Confirmer un bon de commande fait trois choses, et la troisième est celle qui compte.

Elle **engage** la compagnie à acheter, à un prix, à une date — ce qui est une promesse, et donc un document qui doit être regardé avant qu'il soit fait.

Elle **crée une réception attendue** : l'entrepôt sait maintenant que cinq cents classeurs arrivent, et quand. C'est ce qui rend possible la réponse à la question *pouvons-nous promettre ceci à un client la semaine prochaine ?* par quelque chose de mieux qu'un devinements.

Et elle **ouvre une porte à la facture** : lorsque la facture du fournisseur arrive, elle peut être comparée à la commande. Pas parce que le système est soupçonneux, mais parce que la *triple vérification* est le plus vieux contrôle du commerce et reste le meilleur.

## La triple vérification

L'idée est assez simple pour tenir sur une serviette, et elle a fait économiser aux compagnies plus d'argent que toute fonctionnalité de logiciel jamais inventée.

Vous avez commandé cinq cents classeurs à £2,10 l'unité. L'entrepôt a reçu cinq cents classeurs. La facture du fournisseur dit five cents classeurs à £2,10 l'unité. Trois documents, trois nombres, et ils doivent s'accorder avant que la facture soit payée.

Si la facture dit £2,30, quelqu'un demande pourquoi. Si l'entrepôt a reçu quatre-vingts-dix-huit, quelqu'un demande où sont partis vingt. Si la commande était pour cinq cents et la facture pour six cents, quelqu'un demande qui a autorisé les cents supplémentaires — et la réponse est souvent *personne*, ce qui est exactement le point.

Le contrôle est vieux. Les manuels de comptabilité des coûts le décrirent dans les années 1920, et il fut formalisé dans les manuels d'achat des années 1950, lorsque les grands fabricants découvrirent que la différence entre ce qu'ils commandaient et ce qu'ils payaient était une fraction significative de leur profit. Il survit parce qu'il est bon marché : trois documents qui existent déjà, comparés par une machine qui ne s'ennie pas.

Ce qui est nouveau, c'est que la comparaison prend une seconde et peut être *expliquée*.

> *Créer la facture fournisseur pour le bon de commande P00008 et la vérifier contre la commande et la réception.*

> *Facture fournisseur BILL/2026/0031 créée depuis P00008 pour Pennine Paper : 500 × Classeur A4 (bleu) à £2,10, net £1 050,00, TVA £210,00, total £1 260,00. Vérifié : commandé 500, reçu 500, facturé 500. Aucune différence. La facture est en brouillon.*

Aucune différence. Un bon jour, c'est tout le travail : trois nombres qui s'accordent, en une phrase, en une seconde.

Un mauvais jour, il dit quelque chose comme : *commandé 500, reçu 480, facturé 500 — une différence de 20 unités à £2,10.* Et alors une personne doit décider : le fournisseur a-t-il expédié en quantité insuffisante, l'entrepôt a-t-il mal compté, ou quelqu'un a-t-il accepté une livraison partielle et oublié de l'enregistrer ? Le système ne peut pas répondre à ça. Il ne peut faire que la question devienne impossible à éviter.

---

## Payer

Payer un fournisseur est l'image miroir d'être payé, et cela a la même forme : un document (la facture), un paiement, et une correspondance entre eux.

> *Enregistrer un paiement du montant total de BILL/2026/0031, daté d'aujourd'hui, par virement bancaire.*

> *Paiement enregistré pour BILL/2026/0031 : £1 260,00 à Pennine Paper, depuis le journal bancaire, daté du 14 novembre 2026. La facture est maintenant entièrement payée ; le solde du fournisseur est nul.*

Le journal bancaire n'est pas la banque. C'est le *relevé* de la compagnie de ce que la banque a fait, et les deux doivent être réconciliés — ce qui est le rituel mensuel décrit dans le chapitre suivant le prochain. La distinction compte parce que c'est là qu'une compagnie découvre qu'un paiement qu'elle a enregistré n'a jamais été fait, ou un paiement que la banque a fait n'a jamais été enregistré.

## Une courte histoire du bon de commande

Le bon de commande en tant que document est un enfant de l'âge des chemins de fer. Avant les chemins de fer, un marchand achetait à des gens qu'il pouvait voir, et une poignée de main plus une écriture de grand livre suffisait. Les chemins de fer ont créé la distance : un acheteur à Manchester commandant depuis un moulin à Leeds avait besoin d'un document qui disait ce qui était commandé, à quel prix, et quand, car les marchandises arriveraient plusieurs jours plus tard et l'homme qui les avait commandées pourrait ne pas être là.

La forme du bon de commande moderne — numéro, date, fournisseur, lignes, quantités, prix, conditions — fut fixée par le début du XXe siècle et n'a pas changé depuis, car elle encode l'information minimale nécessaire pour résoudre un litige. Le logiciel n'a pas changé le document. Il a changé le coût de production, d'envoi, de vérification et de recherche de celui-ci.

Ce qui est, en une phrase, l'argument de tout ce livre.

## La fiche fournisseur, et ce pour quoi elle est là

Un fournisseur dans un ERP n'est pas une entrée de répertoire. C'est un ensemble de conditions, et les conditions sont ce qui fait fonctionner les papiers.

Les fiches fournisseurs de Riverton furent construites un après-midi, et chacune contient cinq choses qui comptent : les **conditions de paiement** (trente jours à partir de la date de facture, ou fin de mois suivant, qui sont des choses très différentes), la **devise**, le **traitement fiscal** (si le fournisseur facture la TVA et sous quel régime), le **délai de livraison** que l'acheteur attend, et le **contact** qui répond quand quelque chose ne va pas.

Aucune de celles-ci n'est de la décoration. Les conditions de paiement décident de la date d'échéance sur chaque facture, et un fournisseur dont les conditions sont enregistrées comme « 30 jours » quand elles sont en réalité « 60 jours net » sera payé tôt chaque mois pendant un an — ce qui semble inoffensif et est en réalité un petit prêt permanent à un fournisseur qui ne l'a pas demandé. La devise décide si une facture en euros est convertie au taux de la date de facture ou de la date de paiement, ce qui est une différence qui apparaît comme un gain ou une perte. Le délai de livraison décide quand le système attend les marchandises, ce qui est ce qui donne un sens au rapport des « bons de commande en retard ».

L'ancien système n'avait rien de tout cela. Il avait un classeur de factures et un numéro de téléphone écrit à l'intérieur du classeur.

## Ce qu'un bon de commande ne fait pas

Il vaut la peine d'être clair sur les limites, car une compagnie qui attend trop d'un document sera déçue par le logiciel qui le produit.

Un bon de commande ne **négocie** pas. Il enregistre le prix qui fut convenu, et l'assistant peut vous montrer ce que vous avez payé la dernière fois, et ce que vous avez payé avant ça — ce qui est les munitions d'une négociation, pas la négociation.

Il ne **garantit** pas la livraison. Il crée une attente, et l'attente est ce que le rapport des commandes en retard mesure.

Il ne **vérifie** pas les marchandises. C'est la réception, et la réception est une personne avec un classeur.

Et il ne **paye** pas. Le paiement est une décision séparée, faite plus tard, généralement par quelqu'un qui regarde d'abord le solde bancaire.

Ce qu'il fait, c'est rendre ces quatre choses *visibles*, et la visibilité est ce qui transforme une relation conduite par téléphone en une relation qui peut être examinée.

## Le prix qui grimpait

Les frais de palette que Doreen trouva dans le chapitre dix-neuf avaient une contrepartie sur le côté achat, et il fut trouvé par le même genre de question.

> *Quels fournisseurs ont augmenté leurs prix au cours des six derniers mois, et de combien ?*

La réponse listait quatre fournisseurs et onze produits, et l'un d'eux était le papier : le prix d'achat era passé de £2,05 à £2,18 la ramette en juillet, ce qui est six pour cent, sur un produit que Riverton achète par palette.

Six pour cent sur le papier était, aux volumes de Riverton, environ £1 900 par an. Personne n'y avait remarqué, car personne n'avait de liste de ce qu'ils avaient payé avant. L'acheteur — Maggie, dans ce cas — avait remarqué que la facture « semblait un peu plus chère » et avait supposé que c'était son imagination.

C'est le motif que tout ce livre revient constamment à aborder : l'argent n'est pas perdu dans de grandes erreurs dramatiques. Il est perdu dans des changements trop petits pour être remarqués un à un et trop grands pour être ignorés quand ils sont additionnés. Un système qui se souvient du prix précédent les rend remarquables, et remarquer est la plus grande partie du travail.

## La chose unique à bien faire le premier jour

Si une compagnie emporte une seule chose de ce chapitre, ce doit être celle-ci : **enregistrer les conditions de paiement sur le fournisseur, pas sur la facture.**

Une facture avec des conditions tapées dessus est un document qui sera payé selon ces conditions une seule fois. Un fournisseur avec des conditions sur sa fiche est un fournisseur dont chaque facture est à échéance le bon jour, pour toujours, sans que personne n'ait à y penser. La différence est de trente secondes de configuration et une année de plus à ne pas avoir cette conversation :

« Pourquoi payons-nous Pennine en avance ? »
「 Je ne sais pas, le système dit que la facture est à échéance. »
「 La facture est à échéance dans soixante jours, pas trente. »
「 Alors la fiche fournisseur est fausse. »
「 Depuis quand ? »

Depuis le premier jour, généralement, et personne n'y avait remarqué car payer en avance n'est pas une erreur que quelqu'un se plaint — sauf la personne qui regarde le tableau de flux de trésorerie en février.

---

Le verdict de Tom, à la fin du premier mois d'achat par le système, était caractéristiquement pratique.

「 Je pensais qu'un bon de commande c'était des papiers, dit-il. Ce n'est pas le cas. C'est la seule chose qui m'empêche de payer quelque chose que je n'ai pas reçu. »

Maggie lui demanda si le système avait rien capturé.

「 Deux fois. Une fois la facture était pour vingt de plus que ce que nous avions reçu, et une fois le prix était monté sans que personne nous le dise. À chaque fois j'aurais payé, car j'aurais regardé la facture et pensé, oui, c'est à peu près correct. »

« À peu près correct » est la phrase à retenir. La plupart de l'argent perdu dans une petite compagnie est perdu dans l'écart entre *à peu près correct* et *correct*, et l'écart ne se ferme pas en étant plus prudent. Il se ferme en ayant quatre nombres à comparer, et une machine qui les compare à chaque fois.
