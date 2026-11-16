# 16. L'entrepôt répond

La question qui a changé le travail de Tom Beck a été posée un mardi, et ce n'était pas une question sur les ordinateurs.

> *Combien avons-nous de classeurs A4 à annexes, et où sont-ils ?*

Il l'avait posée mille fois en dix-neuf ans, et la réponse venait toujours d'une personne : de lui-même, ou de qui que soit sur la ligne de préparation, ou d'un carnet dont l'information était parfois exacte. Maintenant, il la tapait dans une fenêtre et obtenait ceci :

> *Classeur A4 : 412 au total en stock. 350 réservés pour la commande S00012 (Ashfield Academy). 62 disponibles. Emplacements : Stock/Etagère A — 380, Stock/Retours — 24, Stock/Quarantaine — 8.*

Il lut la réponse trois fois. Puis il sortit vers l'Etagère A et comptea, ce qui prit onze minutes et prouva que le système avait raison sur les trois chiffres.

「Bon, dit-il en revenant. Maintenant, je le crois.」

---

## Qu'est-ce qu'un mouvement de stock

Le chiffre 412 n'est stocké n'importe où. C'est la première chose à comprendre, et c'est ce qui sépare un vrai système d'inventaire d'un tableur avec une colonne de quantité.

Ce qui est stocké, c'est une liste de *mouvements* : deux cents reçus du fournisseur en mars, trois cents cinquante préparés pour Ashfield en juin, vingt retournés en juillet, huit transférés en quarantaine en août. Le niveau de stock est la somme de ces mouvements, calculée quand vous demandez. Si vous redemandez dans une minute, et que rien n'a bougé, vous obtenez la même réponse. Si quelque chose a bougé, vous obtenez une réponse différente, et la différence est *le mouvement lui-même* — qui a une date, un utilisateur, une raison et un document.

Cela a trois conséquences qu'un tableur ne peut pas reproduire.

**On peut toujours savoir pourquoi.** Quand un chiffre semble faux, les mouvements l'expliquent. Pas « quelqu'un a changé la quantité » mais « vingt sont allés en quarantaine le 3 août parce que la palette a été écrasée ».

**Deux personnes ne peuvent pas désapprouver silencieusement.** Si Tom compte 380 et que le système dit 412, la différence est un document : un ajustement, avec une raison, approuvé par quelqu'un. Le comptage n'écrase pas le système ; il produit un mouvement qui les réconcilie.

**L'histoire survit à un changement d'unité, de prix ou de fournisseur.** Les mouvements conservent les quantités dans lesquelles ils ont été faits. Réorganiser le catalogue ne réécrit pas le passé.

## Réservé, disponible, et la différence qui compte

La deuxième chose que Tom apprit fut la différence entre *en stock* et *disponible*, et c'est la différence entre un entrepôt qui promet et un entrepôt qui tient ses promesses.

**En stock** c'est ce qui est physiquement dans le bâtiment : 412 classeurs.

**Réservé** c'est ce qui a été promis à une commande précise : 350 classeurs, pour Ashfield, attendant le camion.

**Disponible** c'est en stock moins réservé : 62 classeurs qu'on peut promettre à quelqu'un d'autre.

Une entreprise qui suit seulement *en stock* promettra les mêmes 350 classeurs deux fois — une fois pour Ashfield et une fois pour Northgate — et découvrira le problème le matin de la livraison, quand il n'y a qu'une seule palette. Une entreprise qui suit les réservations le découvre au moment de la seconde promesse, quand le système dit *62 disponibles* et que le vendeur doit prendre une décision.

Cette décision — livrons-nous Northgate en retard, ou achetons-nous plus, ou partageons-nous la commande — est une décision commerciale, et le point du système n'est pas de la prendre. Le point est de la placer devant une personne *avant* qu'elle ne devienne une excuse.

## La livraison

La livraison elle-même est le document le plus simple de tout le système et celui qui a le plus de conséquences.

> *Livrez la commande S00012 et montrez-moi les mouvements de stock qu'elle a créés.*

> *Livraison WH/OUT/00004 validée pour la commande S00012. Mouvements : 350 × Classeur A4 (bleu) de Stock/Etagère A vers Clients ; 20 × Marqueurs de tableau (paquet de 4) de Stock/Etagère A vers Clients. Stock après le mouvement : 62 classeurs en stock, 0 réservés ; marqueurs 44 en stock.*

Trois choses se produisirent à la fois, et elles valent la peine d'être séparées.

Le **stock** a bougé : 350 classeurs ont quitté l'Etagère A. La **réservation** a disparu, car elle avait été exécutée. Et la **commande** a changé d'état : elle est maintenant *livrée*, ce qui signifie que la facture peut être créée contre elle.

Si la livraison avait été partielle — deux cents classeurs au lieu de trois cents cinquante — Odoo aurait créé un *sous-commande* : un second document de livraison pour le reste, lié au premier. Ce seul mécanisme est la raison pour laquelle une entreprise peut promettre *nous enverrons le reste vendredi* sans que quiconque ait à se souvenir de ce qu'était le reste.

## Les emplacements, en pratique

Un emplacement ressemble à une technicité jusqu'à la première fois que quelque chose se perd, puis alors c'est la seule chose qui compte.

Les quatre emplacements de Riverton — deux étagères, les retours, la quarantaine — furent mis en place en une heure et utilisés correctement pendant environ un mois avant que quiconque les apprécie.

L'emplacement des retours fut le premier à gagner son maintien. Un client renvoie vingt classeurs parce qu'ils sont de la mauvaise couleur ; le camion les amène au quai de chargement ; Tom doit décider s'ils retournent sur l'Etagère A (ce sont, après tout, vendables) ou en quarantaine (ce ne le sont pas). Sur l'ancien système, la décision était prise là où la boîte était posée, et la boîte était posée là où il y avait de la place. Sur le nouveau système, la décision est un mouvement de stock, et le mouvement a une raison attachée.

La conséquence apparut dans le rapport de marge trois mois plus tard : l'emplacement des retours contenait quarante-et-un articles qui avaient été « retournés » et jamais vérifiés, dont certains endommagés, dont certains étaient en réalité un produit différent. Chacun d'eux avait été compté comme stock vendable. C'est quarante-et-un articles de stock que l'entreprise croyait avoir et ne pouvait pas vendre — un petit nombre, et une illustration parfaite du principe général : **la valeur d'un emplacement est qu'il force une décision à être enregistrée.**

## Le triplement de conformité, du côté de l'entrepôt

Le chapitre dix-sept décrit le triplement de conformité du point de vue du comptable. Du côté de Tom, ça difère et ça vaut un paragraphe.

Quand une livraison arrive, le travail de l'entrepôt est d'enregistrer ce qui est réellement venu : combien, de quel produit, dans quelle condition, quelle date. Ce document est la *réception*, et c'est la jambe centrale du triplement. S'il est faux — si Tom enregistre quarante palettes au lieu de quarante rameaux, ou s'il valide la réception avant de compter — alors le triplement « réussira » contre un chiffre faux, et l'erreur survivra jusqu'au fond dans les comptes.

C'est pourquoi la réception est un document avec un utilisateur et une horodate, et pourquoi l'assistant n'est pas autorisé à valider une réception de sa propre initiative. Il peut en créer une à partir d'une commande d'achat, qui est une proposition ; la valider signifie *j'ai compté ceci*, et c'est une affirmation sur le monde physique que seule une personne debout devant la palette peut faire.

La règle de Tom, écrite sur le tableau blanc : *le système peut deviner ce qui devrait être là. Seul je peux dire ce qui est.*

## Le coût d'un mauvais comptage

Ça vaut la peine de mettre un nombre sur le comptage trimestriel, parce que « nous devrions le faire plus souvent » est le genre de conseil qui meurt dans un mois chargé.

Le stock de Riverton valait environ 180 000 £ au coût. Le premier comptage trouva une différence nette de 1,8 pour cent — environ 3 200 £ — répartie sur onze produits. Ce n'est pas du vol ; c'est l'effet accumulé de quarante petites erreurs : une palette enregistrée comme quarante palettes, un retour remis sans vérification, une livraison validée avant qu'elle soit comptée.

Un comptage coûte deux personnes un jour, deux fois par an, ce qui est environ 1 200 £ de salaire. Il trouva 3 200 £ d'erreur la première fois et 900 £ la seconde. L'arithmétique n'est pas subtile : une entreprise qui compte deux fois par achète une police d'assurance de 1 200 £ contre une erreur de 3 000 £, et l'erreur qu'elle empêche est celle qui rend les comptes faux à la fin de l'année.

Ce qui changea avec le système ne fut pas l'arithmétique mais la *forme* du comptage. Au lieu de compter tout et de réconcilier une liste, le système propose ce qu'il croit et le compteur confirme ou corrige. Les corrections sont alors investiguées, une à une, et chaque investigation répare une habitude plutôt qu'un chiffre. C'est là la différence entre compter le stock et le gérer.

## L'avis de livraison, et les trois signatures

Une livraison dans un grossiste a trois moments, et chacun a une signature d'un genre.

**La préparation :** quelqu'un prend les marchandises sur l'étagère et les pose sur une palette. La signature est la liste de préparation, signée ligne par ligne, et c'est l'entrepôt disant *c'est ce que j'ai assemblé*.

**Le chargement :** les marchandises montent sur le camion. La signature est celle du chauffeur, et c'est l'entreprise disant *ça est sorti du bâtiment*.

**La livraison :** le gardien du client signe l'avis. La signature est la leur, et c'est le client disant *ça est arrivé*.

Dans Odoo, les trois moments se réduisent à deux documents — l'ordre de livraison et sa validation — et c'est une simplification qui vaut la peine d'être comprise, parce que c'est là que naissent la plupart des écarts. Une palette qui est préparée, chargée et jamais livrée a quitté le stock du système mais pas la cour de l'entreprise ; une palette qui est livrée et jamais validée a quitté la cour mais pas le système.

L'habit de Tom, après la première année, fut de traiter la validation comme le moment de vérité : la livraison est validée quand l'avis signé revient, pas quand le camion part. Ça rend le rapport de stock en retard d'un jour et ça le rend juste, et il préférerait avoir un chiffre juste le mercredi qu'un chiffre faux le mardi.

## Ce que l'entrepôt sait que le système ne sait pas

Il y a une limite à tout ceci, et Tom est le premier à la décrire.

Le système connaît les quantités, les emplacements et les dates. Il ne sait pas que le coin de l'Etagère B est là où l'humidité entre, que la palette de papier de la livraison d'août est plus lourde que celle de février parce que le fournisseur a changé le poids du rameau, ou que le chauffeur qui livre le vendredi n'attendera pas pendant que vous comptez.

Un gestionnaire d'entrepôt porte cette connaissance, et la valeur du système n'est pas qu'il le remplace mais qu'il le *libère* : une personne qui n'a pas à se souvenir où sont quatre cents douze classeurs peut dépenser l'attention sur pourquoi la palette d'août semble fausse.

「C'est la même chose que dans le bureau, dit Tom. Le système fait le comptage. Moi je fais la remarque.」

## Le comptage

Une fois par trimestre, Riverton compte.

Ce n'est pas un après-midi agréable. Ça implique un porte-plume, deux personnes, une torche, et un entrepôt plus froid qu'il n'en a l'air. Mais c'est différent maintenant, d'une façon qui prit à Tom un moment à articuler.

「La première fois, j'ai compté tout et tapé ça dans le système, et le système m'a dit où j'étais faux, dit-il. La seconde fois, j'ai seulement compté les choses que le système disait que j'aurais dû avoir, et il m'a dit où *lui* était faux. C'est un travail différent. Le premier est une corvée. Le second est une conversation.」

Ce qu'il voulait dire est ceci : avec un comptage de stock, le système propose une liste de produits et les quantités qu'il croit être sur l'étagère, et le compteur confirme ou corrige. Les corrections sont alors revues, et chacune est une petite investigation : était-ce une erreur de préparation, une livraison signée pour mais non enregistrée, un retour qui n'est jamais revenu sur l'étagère ?

Cette investigation est là où est l'argent. Dans la première année de Riverton, le comptage trimestriel trouva trois problèmes récurrents, et aucun d'eux n'était du vol :

- Un produit dont l'unité de mesure avait été mal configurée en 2022, de sorte que chaque réception était enregistrée comme une palette au lieu de quarante rameaux. Le système « perdait » du papier depuis trois ans.
- Un avis de livraison qui fut signé à l'école mais jamais validé dans le système, de sorte que les marchandises étaient sur l'étagère et aussi dans le placard du client.
- Un processus de retour qui remettait les marchandises retournées en stock sans les vérifier, de sorte que des articles endommagés étaient vendus deux fois.

Chacun de ceux-là fut trouvé en comparant ce que le système croyait avec ce qui était vrai, et chacun fut réparé en changeant une habitude, pas en achetant quelque chose.

---

## Une note sur le mot « entrepôt »

L'entrepôt de Tom est une pièce avec des étagères, un quai de chargement, et un coin où vont les choses endommagées. Dans Odoo, c'est une *location*, et les locations peuvent être imbriquées : un entrepôt contient une zone de stock, qui contient des étagères, qui contiennent des cases.

Une entreprise avec une seule pièce n'a pas besoin de l'imbriquage, et Riverton ne l'utilisa pas au début. Mais la structure était là, et dans la seconde année, quand l'entreprise loua l'unité à côté, ajouter un second entrepôt fut une affaire de création d'une location et de déplacement de stock — pas d'achat d'un second système ou de démarrage d'un second tableur.

C'est l'avantage discret de modeler la réalité au lieu de l'enregistrer. Un tableur qui dit « 412 classeurs » ne peut pas faire pousser une seconde étagère sans être reconstruit. Un système qui dit « 412 classeurs, voici les mouvements qui les ont mis là » peut faire pousser un second bâtiment en un après-midi.

---

Le rapport de Tom, à la fin de ce premier trimestre, faisait quatre pages et il le lut dans le camion.

「La chose à laquelle je reviens toujours, dit-il en le rapportant, c'est que j'utilisais *savoir* des choses et je ne pouvais pas les *montrer*. Maintenant je peux les montrer. C'est le fait de les montrer qui change la conversation.」

Maggie lui demanda ce qu'il voulait dire.

「Avant, si je disions que nous avions trop de papier, c'était l'opinion de Tom. Maintenant c'est un nombre sur une page avec une date dessus. Personne ne dispute avec un nombre sur une page. Ils disputent avec Tom.」

Il sourit. « C'est très reposant.」
