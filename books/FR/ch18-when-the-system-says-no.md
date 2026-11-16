# 18. Quand le système dit non

Le premier refus est venu un jeudi après-midi, et c'est le moment où Doreen a cessé d'être méfiante envers le système pour commencer à s'y fier.

Elle avait demandé à l'assistant de corriger une erreur : une facture avait été comptabilisée avec la mauvaise quantité, et elle voulait que ce soit corrigé.

> *Change la quantité sur la facture INV/2026/0007 de 350 à 300.*

> *Je ne peux pas la changer. INV/2026/0007 est comptabilisée, et les factures comptabilisées sont en lecture seule : les écritures de grand livre et le point fiscal sont déjà enregistrés. Pour la corriger, annule la facture et émettons un avoir, ou émettons un avoir pour la différence. Laquelle préfères-tu ?*

Doreen a lu ça deux fois, puis a appelé Maggie.

« Il ne le fait pas », a-t-elle dit.

« Il ne le veut pas ou il ne le peut pas ? »

« Il ne le peut pas. Il dit que le grand livre est déjà écrit. »

Cette distinction—*ne le veut pas* versus *ne le peut pas*—est le sujet de ce chapitre, et c'est la raison pour laquelle un système d'entreprise diffère d'un collègent utile.

---

## Les trois sortes de non

Un ERP refuse pour trois raisons différentes, et il vaut la peine d'apprendre à les distinguer, car chacune appelle une réponse différente.

**Le système ne peut pas le faire parce que le modèle l'interdit.** On ne peut pas comptabiliser une facture sans lignes, livrer des marchandises que l'on ne possède pas, ou modifier un document qui a déjà produit des écritures de grand livre. Ces refus sont structurels : ils protègent l'intégrité du modèle, et il n'y a pas de dérogation, car une dérogation briserait la garantie qui rend le modèle précieux à avoir.

**Le système ne peut pas le faire parce que l'*utilisateur* n'est pas autorisé.** L'assistant est un utilisateur avec un rôle, et si le rôle n'inclut pas la suppression d'enregistrements, la demande est refusée par le système de permissions avant d'atteindre le modèle. Ces refus concernent l'autorité, et ils peuvent être changés—par quelqu'un qui a le droit de les changer, délibérément, et avec une trace du fait de l'avoir fait.

**Le système ne peut pas le faire parce que les *données* ne sont pas là.** Le client n'existe pas, le produit n'a pas de prix, le stock est dans un lieu que l'utilisateur ne peut pas voir. Ces refus concernent l'état du monde, et ce sont généralement les plus utiles, car ils pointent vers quelque chose qui a besoin d'être corrigé plutôt que quelque chose qui a besoin d'être dérogé.

Un bon assistant vous dit quelle sorte de non c'est. C'est ce qui s'est passé ci-dessus : le refus nommait le document, la raison, et deux alternatives légales.

## Les refus qui ont appris quelque chose à Riverton

Au cours des premiers mois, le système disait non d'une poignée de façons qui étaient chacune une petite leçon.

**« Pas assez de stock. »** Tom a demandé une livraison de six cents classeurs quand il y en avait quatre cent douze. Le système a refusé, et a proposé de livrer ce qui était disponible et de créer une commande reportée pour le reste. Tom a choisi la commande reportée, et le client a été téléphoné avant le départ du van—which est tout le point du refus : ça a déplacé la conversation de la quai de chargement vers le téléphone, où elle pouvait encore être utile.

**« La période comptable est close. »** Doreen a essayé de comptabiliser une facture datée du mois précédent, après que le mois ait été verrouillé. Le système a refusé et a expliqué que la période était close. Elle a déplacé la facture vers le mois courant, puis a demandé à l'assistant une liste de tout ce qui a été comptabilisé après la fermeture—which est revenu vide, ce qui est le but d'une période close.

**« Cet utilisateur ne peut pas supprimer d'enregistrements. »** L'assistant, demandé pour supprimer un client en double, a dit qu'il ne pouvait pas, et a proposé d'archiver l'enregistrement à la place. L'archivage garde l'enregistrement et le cache des listes, ce qui est la bonne réponse pour un client en double qui a des documents attachés. Le refus avait été configuré à dessein, au chapitre douze, par quelqu'un qui y avait pensé à l'avance.

**« Ce produit n'a pas de taxe. »** Un nouveau produit avait été créé sans taux de taxe, et la devis refusait de calculer un total. Le refus pointait vers le formulaire du produit, et la correction a pris trente secondes. Sans le refus, la devis serait partie sans TVA—and l'entreprise l'aurait découvert à la fin du trimestre, dans une déclaration qui ne faisait pas le compte.

## Lire le journal

Chaque refus laisse une trace, et apprendre à lire la trace est la compétence qui transforme un assistant d'une boîte noire en un collègent.

L'assistant écrit un journal : ce qui lui a été demandé, quels outils il a choisis, avec quels arguments, ce qui est revenu, et combien de temps ça a pris. Ce n'est pas un document joli—c'est un fichier, dans un dossier, avec des horodateurs—and c'est le premier endroit où regarder quand quelque chose s'est mal passé.

Trois motifs valent la peine d'être reconnus.

**Une boucle.** Le même outil appelé avec les mêmes arguments, trois ou quatre fois. C'est l'assistant essayant de faire marcher quelque chose et échouant de la même façon à chaque fois—généralement parce qu'un document est dans un état qu'il n'attendait pas. Le refus est dans le journal, trois fois, et le lire une fois suffit.

**Un mauvais outil.** L'assistant a choisi *créer* quand il aurait dû choisir *modifier*, et l'ERP a refusé parce que l'enregistrement existait déjà. Le journal montre le choix ; la correction est dans l'instruction, qui ne disait pas *modifier*.

**Un succès silencieux qui n'était pas ce qui était voulu.** Pas d'erreur, pas de refus, et un résultat qui est techniquement correct et pratiquement inutile. C'est le motif le plus dur, rien dans le journal ne semble incorrect. La défense est le contrôle : demander à l'assistant ce qu'il a fait, et comparer ça avec ce que vous vouliez.

Doreen lit le journal chaque vendredi, pour la même raison qu'elle lisait autrefois l'extrait de compte bancaire : pas parce qu'elle attend un problème, mais parce que le lire est comment on apprend ce que la normale ressemble—and donc comment on remarque quand elle ne l'est pas.

## Le refus qui a sauvé un client

Un refus dans la première année de Riverton valait plus que tous les succès, et c'est arrivé au milieu d'un argument.

Un client—un gros client, et un client difficile—avait reçu une facture pour une livraison qu'il affirmait ne jamais avoir reçue. L'avis de livraison était signé, mais la signature était illisible, et le gestionnaire des achats du client insistait sur le fait que les marchandises avaient été refusées à la porte.

Priya a demandé à l'assistant d'émettre un avoir, parce que le client menaçait de porter son ailleurs et que la facture valait 640 £.

L'assistant a refusé, et la raison qu'il a donnée est la raison pour laquelle cette histoire est dans le livre.

> *Je peux créer un avoir, mais tu devrais savoir à quoi ça ressemblera dans les comptes : un avoir sans retour derrière lui enregistre que les marchandises n'ont jamais été fournies. La livraison a été validée le 3 septembre par Tom Beck, et le mouvement de stock montre 40 articles quittant l'étagère A. Si le client a refusé la livraison, les marchandises auraient dû revenir et il n'y a pas de retour enregistré. S'ils ne l'ont pas refusé, l'avoir paierait des marchandises qui ont été livrées. Lequel est-ce ?*

Priya a téléphoné au client, a posé la question que l'assistant avait posée, et a découvert que la livraison avait été acceptée par un gardien de sécurité temporaire qui avait mis la palette dans une salle de stockage et n'avait rien dit à personne. La facture a été payée en entier, et le client s'est excusé.

Le refus n'a pas sauvé 640 £. Il a sauvé une relation, et il l'a fait en refusant de laisser une personne sauter une question—which est ce qu'un bon comptable a toujours fait, et ce que ce système fait parce que quelqu'un l'a configuré pour.

## Les refus qu'une entreprise devrait concevoir à dessein

La plupart des refus viennent avec le logiciel. Quelques-uns devraient être ajoutés, à dessein, et ce sont ceux qui transforment un ERP d'un système d'enregistrement en un système de contrôle.

Quatre valent la peine d'être considérés dans n'importe quelle entreprise qui laisse écrire un assistant.

**Une limite de crédit sur les clients.** Quand une commande prendrait un client au-dessus de sa limite, le système peut refuser de la confirmer, ou exiger une approbation. L'assistant rendrait alors compte du refus et du nombre, ce qui est exactement la conversation qu'un vendeur devrait avoir avec le propriétaire—avant que les marchandises partent, pas après.

**Un discount maximum.** Odoo peut être configuré de sorte qu'un discount au-dessus d'un seuil nécessite une deuxième personne. L'assistant ne peut pas l'accorder, parce que l'assistant est un utilisateur avec un seul rôle ; il ne peut que dire qui pourrait.

**Une période close.** Une fois qu'un mois est verrouillé, rien ne se comptabilise dedans, par personne, y compris l'assistant. C'est le contrôle le plus efficace dans tout le système, et ça coûte un seul réglage.

**Une règle à quatre yeux sur les paiements.** Dans Odoo, c'est une configuration du processus de paiement, pas une fonctionnalité de l'assistant, mais l'effet est le même : l'assistant prépare l'exécution des paiements, une personne les libère.

Aucun de ceux-là n'est une formalité. Chacun encode une décision que l'entreprise a déjà prise sur la façon dont elle veut être gérée, et chacun transforme cette décision en quelque chose qui ne peut pas être oublié un vendredi occupé.

## Ce qu'un refus coûte

Il y a un coût à la rigueur, et il vaut la peine de le nommer parce que les entreprises qui l'ignorent finissent par éteindre les règles.

Un refus arrête le travail. Quelqu'un doit arrêter ce qu'il fait, découvrir pourquoi, et soit corriger les données, soit demander une exception. Dans une petite entreprise, cet quelqu'un est souvent le propriétaire, et le propriétaire est souvent la personne la plus occupée du bâtiment.

Le coût est réel, et le moyen de le garder petit n'est pas d'affaiblir la règle mais de rendre le refus *informatif*. Un message qui dit *limite de crédit dépassée : 2 310 £ sur 2 000 £, client Calder et Fils, dernier examen en mars* dit à la personne quoi faire. Un message qui dit *accès refusé* ne le dit pas.

C'est l'argument pour un assistant devant un ERP en une seule phrase : les règles sont celles de l'ERP, et l'*explication* est celle de l'assistant.

## Pourquoi la rigueur est la fonctionnalité

Il y a une tentation, quand un système refuse quelque chose, de chercher le réglage qui éteint le refus. La plupart des ERPs ont de tels réglages, et la plupart d'entre eux sont une erreur.

Considérez ce que les refus protègent.

Le refus de modifier une facture comptabilisée protège le **système d'audit** : l'enregistrement de ce qui a été envoyé au client, et quand. Une entreprise qui peut modifier sa propre histoire ne peut rien prouver à son sujet.

Le refus de livrer du stock qui n'est pas là protège la **promesse** : le client s'est fait dire une date, et la date dépend de marchandises qui existent.

Le refus de comptabiliser dans une période close protège les **comptes** : une période est close parce que quelqu'un s'en est servi pour faire un rapport—to la banque, au bureau des taxes, aux propriétaires—and la rouvrir silencieusement rendrait le rapport un mensonge.

Le refus de laisser un utilisateur supprimer protège la **responsabilité** : si un document peut disparaître, alors l'absence d'un document ne signifie rien.

Aucun de ceux-là n'est de la propreté. Chacun est de la unique propriété qui rend un ERP vale son coût : que ce qu'il dit est vrai, et peut être montré comme vrai.

## La part de l'assistant dans ceci

Un assistant rend les refus *meilleurs*, d'une façon qui est facile à manquer.

Une personne rencontrant un refus dans un écran voit une boîte rouge avec un code et une phrase. Un assistant rencontrant le même refus peut l'expliquer dans le langage de l'entreprise, offrir les alternatives, et faire le légal si vous êtes d'accord. C'est la différence entre *Erreur : ne peut pas modifier un mouvement comptable comptabilisé* et *la facture est comptabilisée, donc elle ne peut pas être modifiée ; je peux émettre un avoir pour la différence, ou annuler et réémettre—which veux-tu ?*

Il y a un risque dans cette fluidité, et il vaut la peine de le nommer : un assistant qui explique les refus utilement peut les faire sentir négociables. Ils ne le sont pas. L'explication est une courtoisie ; la règle est la règle. L'assistant ne peut pas déroger à l'ERP, parce que l'assistant n'est pas l'autorité—and tout assistant qui prétend le contraire s'est fait donner trop de pouvoir, ce qui est une faute dans l'installation, pas une fonctionnalité du modèle.

## Le seul refus qui n'est pas un refus

Il y a une quatrième sorte de non, et c'est la plus dangereuse parce qu'elle ressemble à un oui.

L'assistant, demandé une question dont la réponse n'est pas dans le système, peut répondre *de façon plausible*. Pas parce qu'il ment, mais parce que c'est ce qu'un modèle de langage fait quand il n'a pas de faits : il produit la phrase la plus probable. C'est le problème de l'hallucination, et la défense est architecturale, pas morale : l'assistant doit être fait pour obtenir ses faits de l'ERP, à travers des outils, et pour le dire quand l'outil ne retourne rien.

La règle de Riverton, sur le mur à côté de la serviette, est une seule phrase : *si elle ne peut pas te montrer d'où vient le nombre, n'utilise pas le nombre.*

Cette règle est pourquoi chaque réponse dans ce livre inclut les documents derrière elle—le numéro de facture, la commande, la liste des mouvements. Ce n'est pas de la décoration. C'est la différence entre un système que tu peux auditer et un système que tu dois croire.

---

Doreen a émis l'avoir, et la facture a tenu.

Ce soir-là, elle a dit quelque chose à Maggie que ni l'une ni l'autre n'attendait.

« J'aime ça qu'il argumente avec moi. »

« Pourquoi ? »

« Parce que mon vieux système faisait tout ce que je tapais. Si je tapais le mauvais nombre, il prenait le mauvais nombre, et il ne me le disait jamais. Celui-ci me fait dire ce que je veux dire. »

Elle a pensé un moment.

« C'est comme avoir un comptable qui le fait depuis six cents ans et qui n'a aucune façon. »

Ce qui est, plus ou moins, exactement ce que sont les règles de Pacioli : aucune façon, aucune mémoire de tes excuses, et aucun intérêt pour le fait que tu sois pressé. Juste les deux côtés de la page, et le refus de leur permettre de désaccorder.
