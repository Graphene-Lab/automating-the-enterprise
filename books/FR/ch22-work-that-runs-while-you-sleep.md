# 22. Le travail qui s'exécute pendant votre sommeil

Le premier travail planifié que Riverton a mis en place n'était pas intelligent. C'était la liste du lundi.

Chaque lundi à huit heures, l'assistant produit une page : les factures devenues impayées la semaine précédente, les produits en dessous de leur point de réapprovisionnement, les commandes à livrer dans les sept prochains jours, et toute ajustement de stock sans raison enregistrée. Il l'envoie à Maggie, Priya et Tom par email, et cela prend à l'assistant une quarantaine de secondes.

Personne ne l'avait demandé. C'était l'idée de Sam, et il l'a expliquée avec une phrase qui est restée chez Maggie depuis lors.

« Le but d'un planning n'est pas que la machine travaille pendant que vous dormez. C'est que la *question* soit posée, que quelqu'un se souvienne ou non de la poser. »

---

## Deux sortes de travail planifié

Il existe deux mécanismes dans cette pile, et ils valent la peine d'être distingués car ils répondent à des questions différentes.

**Les planificateurs propres à l'ERP** s'exécutent à l'intérieur d'Odoo. Ce sont les choses qu'un système d'entreprise a toujours faites sur une minuterie : recalculer les points de réapprovisionnement, envoyer les emails de rappel, exécuter l'amortissement, nettoyer les anciennes sessions. Ils sont configurés dans l'ERP, ils s'exécutent que l'assistant soit ouvert ou non, et c'est le bon endroit pour tout ce qui fait partie du *modèle*—ce qui devrait arriver même si personne dans l'entreprise s'y intéressait.

**Le planificateur de tâches de l'assistant** exécut des travaux comme des conversations. Une tâche planifiée est, littéralement, un prompt avec une date attachée : à huit heures le lundi, l'assistant reçoit une instruction, il fait le travail, et il rend compte. C'est le bon endroit pour tout ce qui exige un jugement sur *ce qu'il faut examiner*—un résumé, un balayage, une comparaison, une incitation.

Riverton utilise les deux, et la division entre eux est la partie utile de ce chapitre.

## Ce qui appartient à un planning

La tentation, quand vous découvrez le travail planifié, est de tout planifier. Résistez-y, et utilisez un test facile à appliquer : **un travail appartient à un planning si son absence serait remarquée uniquement quand il est trop tard.**

La liste du lundi passe le test. Sans elle, une facture impayée est remarquée quand quelqu'un pense à regarder—ce qui signifie, quand elle a soixante jours.

Une sauvegarde nocturne passe le test, catastrophiquement.

Un rapport de ventes quotidien échoue généralement au test. Personne ne le lit ; le nombre est dans le tableau de bord ; et un rapport que personne ne lit est une petite taxe quotidienne sur l'attention qui finit par apprendre aux gens à ignorer les messages du système.

Le test a un corollaire : **un travail planifié devrait produire une décision, pas un document.** La liste du lundi produit quatre décisions (poursuivre ceci, réapprovisionner cela, livrer ceci, expliquer cela). Un rapport produit un document, et les documents s'accumulent.

## Les trois travaux que Riverton a conservés

Après un mois d'expérimentation, l'entreprise s'est arrêtée sur trois, et elle les conserve depuis.

**La liste du lundi**, à huit heures. Quatre questions, une page, trois destinataires.

**Le contrôle de stock du vendredi**, à quatre heures. L'assistant liste chaque produit qui est descendu en dessous de son point de réapprovisionnement durant la semaine et propose des commandes d'achat—à l'état de brouillon, jamais confirmées. Tom le lit le vendredi après-midi et décide ; les commandes sont passées le lundi matin, qui est le moment où les fournisseurs répondent au téléphone.

**Le résumé du premier du mois**, à sept heures. Les ventes par client, les ventes par produit, les cinq premiers et les cinq derniers par marge, l'argent entrant et sortant, et les trois clients dont le comportement de paiement a changé. Ce sont deux pages, et c'est le document que Maggie lit avec son premier café du mois.

Tout le reste essayé ce mois-là a été supprimé, et les suppressions sont aussi instructives que les conservations : un résumé quotidien (personne ne le lisait), un contrôle de connexion horaire (il produisait du bruit, pas de l'information), et un travail nocturne de « nettoyage des doublons » qui était une véritable mauvaise idée—une machine décidant laquelle de deux fiches client est réelle, à trois heures du matin, sans personne pour surveiller.

## Ce qui se passe quand un travail échoue

La partie intéressante du travail planifié n'est pas le planning. C'est l'échec.

Un travail peut échouer pour trois raisons, et chacune a sa propre signature.

**La machine était éteinte.** L'ERP ne tournait pas à huit heures, donc le travail ne s'est pas exécuté. Les planificateurs propres d'Odoo gèrent cela en exécutant les travaux manqués au démarrage du serveur ; les tâches planifiées de l'assistant sont stockées comme des plans et s'exécutent au prochain démarrage, avec la date à laquelle ils étaient censés tourner. D'une manière ou de l'autre, le travail a lieu, en retard.

**Le travail s'est exécuté et la réponse était fausse.** C'est le plus dangereux, car rien ne semble cassé. La liste du lundi arrive, et une de ses quatre sections est vide parce qu'un filtre a été laissé activé. La défense est la même qu'ailleurs dans ce livre : la liste dit *ce qu'elle a examiné*, pas seulement ce qu'elle a trouvé. Une section vide qui dit « aucune facture n'est devenue impayée dans la semaine du 14 novembre » est une information ; une section vide sans explication est une question.

**Le travail s'est exécuté et personne ne l'a lu.** C'est l'échec le plus courant et le moins discuté. Un travail planifié qui arrive dans une boîte de réception que personne n'ouvre est pire qu'aucun travail du tout, car il crée l'*impression* de contrôle. La réponse de Riverton a été de faire de la liste du lundi une réunion—quinze minutes, trois personnes, la liste à l'écran—ce qui ressemble à de la bureaucratie et est en réalité le moyen le plus possible de rendre l'automatisation réelle.

## Une courte histoire du travail par lots

Le travail planifié est plus ancien que l'ordinateur personnel, et son vocab vient du mainframe.

Dans les années 1960, un ordinateur était trop coûteux pour laisser une personne s'asseoir devant lui, donc le travail était préparé sur des cartes et exécuté par *lots* la nuit : la paie le 25, les factures le 1, le grand livre en fin de mois. Le lot était une file d'attente, et le travail de l'opérateur était de faire avancer la file. Quand les minicomputers sont arrivés dans les années 1970, le lot a survécu sous forme de `cron`—un programme Unix, écrit en 1975 par Ken Thompson, dont le nom vient de *chronos*, le temps—et `cron` est encore ce qui fait tourner les serveurs du monde, y compris, indirectement, le planificateur à l'intérieur de votre ERP.

Ce qui est nouveau n'est pas la minuterie. C'est *ce qui* s'y exécut. Un travail par lots de 1975 était un programme écrit par un programmeur pour faire exactement une chose. Une tâche planifiée de 2026 est une phrase en anglais, et la machine détermine les étapes à chaque fois qu'elle tourne. C'est une autre sorte d'automatisation, et elle nécessite une autre sorte de supervision : le programme faisait ce pour quoi il avait été écrit, à chaque fois ; la phrase peut être interprétée différemment à mesure que les données changent.

Ce qui fait que la première règle du travail planifié dans ce livre est : **planifiez des questions, pas des actions.** La liste du lundi pose des questions. Le contrôle de stock du周五 propose. Le résumé du premier du mois rend compte. Aucun d'eux ne publie une facture, n'envoie une lettre à un client, ni ne passe une commande, car ce sont des décisions avec des conséquences, et une décision prise à trois heures du matin par une machine que personne ne surveille n'est pas une décision—c'est un pari.

## L'unique exception

Il existe un travail planifié chez Riverton qui agit effectivement, et il vaut la peine de le décrire car il montre où se trouve la limite.

Chaque nuit à deux heures, le système prend une sauvegarde : un dump de la base de données, une copie de la configuration, et une ligne dans un journal. Il agit. Il change le monde, dans le sens où des fichiers apparaissent. Et il a le droit d'agir parce que l'action est *réversible par conception* : une sauvegarde fausse peut être supprimée et reprise, et rien dans l'entreprise n'en dépend jusqu'au jour où quelque chose en dépend.

C'est le test pour toute action planifiée : si cela tourne mal à trois heures du matin, puis-je l'annuler avant que quelqu'un le remarque ? Si oui, elle peut être planifiée. Si non, elle peut proposer, et une personne peut décider.

## Le coût d'un planning que personne ne possède

Un travail planifié est une petite promesse, et les promesses ont besoin d'un propriétaire.

L'échec est discret et il est courant : un travail est mis en place par quelqu'un qui ensuite part, ou change de rôle, ou simplement oublie. Il continue de tourner. Six mois plus tard, il produit un rapport avec un filtre qui était juste en mars, ou propose des commandes pour une gamme de produits que l'entreprise a abandonnée, et personne ne remarque rien car personne ne le lit—jusqu'à ce que quelqu'un le fasse, et y croie.

Le remède est une liste, conservée dans le même fichier que les prompts : chaque travail planifié, ce qu'il fait, qui le lit, et quand il a été revu pour la dernière fois. Quatre colonnes, une page, revue deux fois par an. Un travail pour qui personne ne peut nommer un propriétaire est un travail à supprimer.

La liste de Riverton a trois entrées et une quatrième qui est un rappel pour revoir la liste. C'est le document le moins impressionnant de l'entreprise et il a empêché deux mauvaises décisions, qui auraient toutes deux été prises par une machine faisant exactement ce qu'on lui avait dit.

## Où vit le planning, et ce qui se passe quand la machine est éteinte

Une tâche planifiée est un fichier, et savoir où elle vit fait la différence entre un planning que vous possédez et un planning dont vous êtes à la merci.

L'assistant stocke ses plans sous forme de JSON, dans son propre dossier de données, et ils survivent à un redémarrage. Chaque plan est une phrase, une heure, une récurrence, et une liste de quoi faire du résultat. C'est utile à savoir pour deux raisons : on peut le sauvegarder avec le reste de la configuration, et on peut l'inspecter—ce qui signifie qu'une entreprise peut répondre à la question *ce que fait cette machine à huit heures un lundi ?* en lisant un fichier plutôt qu'en se souvenant.

Les planificateurs propres à l'ERP vivent dans la base de données, dans une table des actions planifiées, et ils sont visibles dans l'interface sous *Paramètres → Techniques → Actions planifiées*. Chacun a un nom, un intervalle, et un compte de combien de fois il a tourné. Ce compte est un diagnostic petit mais excellent : un travail qui a tourné quatre cents fois et un travail qui a tourné zéro fois vous disent des choses différentes, et tous deux valent la peine d'être examinés une fois par trimestre.

Quand la machine est éteinte, trois choses peuvent arriver, et le comportement de l'ERP est le plus sensé.

**Les planificateurs d'Odoo** exécutent les travaux manqués au prochain démarrage, dans l'ordre, et ils enregistrent le fait. Un rappel dû à huit heures partira à neuf heures, et le journal le dira.

**Les tâches de l'assistant** sont vérifiées au démarrage : si le prochain lancement d'un plan est dans le passé, il tourne à la fois et se reschedule. Une liste du lundi manquée parce que la machine était éteinte arrivera le mardi, avec les données telles qu'elles sont le mardi—ce qui est une différence subtile et importante. La liste n'est pas « ce qui s'est passé le lundi » ; c'est « ce qui est vrai maintenant, demandé sur le planning qui était destiné au lundi ».

**Une sauvegarde** qui a été manquée est simplement manquée, et la suivante couvre le trou. C'est acceptable pour une sauvegarde nocturne ; ce n'est pas acceptable pour une hebdomadaire sur une machine souvent éteinte, ce qui est pourquoi le script de sauvegarde écrit une ligne dans un journal et le journal est vérifié mensuellement.

## Quand un travail produit du bruit

Le mode d'échec qui tue le travail planifié n'est pas un crash. C'est le bruit.

Un travail qui produit un message que personne ne lit entraîne les gens à ignorer les messages du système, puis celui qui compte est aussi ignoré. Riverton a essayé quatre planifications dans le premier mois et en a supprimé trois, et les suppressions étaient aussi instructives que les conservations.

**Le résumé quotidien** a été supprimé parce qu'il dupliquait le tableau de bord et arrivait à un moment où personne n'était à un bureau. L'information n'était pas fausse ; la livraison l'était.

**Le contrôle de connexion horaire** a été supprimé parce qu'il rapportait le succès toutes les heures. Un message qui dit *tout est bien* n'est pas une information ; c'est une habitude, et les habitudes sont ce qui fait que les gens cessent de lire.

**Le contrôle des doublons nocturne** a été supprimé parce qu'il était une action que personne n'avait autorisée, tournant à un moment que personne ne surveillait, sur des données que personne n'avait nettoyées. Il n'a rien trouvé pendant trois semaines puis a proposé de fusionner deux clients qui étaient, en fait, deux branches de la même organisation.

Les trois qui ont survécu partagent tous une propriété : ils produisent une *décision* qu'une personne nommée fait à une heure nommée. La liste du lundi est lue à la réunion du lundi. Le contrôle de stock du vendredi est lu par Tom avant qu'il parte. Le résumé mensuel est lu avec le premier café du mois.

Un planning sans lecteur est un job cron avec un passe-temps.

---

La liste du lundi tourne depuis huit mois, et Maggie l'a manquée deux fois—à chaque fois parce qu'elle voyageait, et à chaque fois elle l'a lue le mardi et a regretté de ne pas l'avoir lue le lundi.

« Ce n'est pas l'information, dit-elle. Je pourrais obtenir l'information. C'est que le lundi matin, avant toute autre chose, quelqu'un pose quatre questions devant moi. Et ce sont les quatre bonnes questions. Je n'aurais jamais pensé à les poser à huit heures un lundi. Je penserais à elles à quatre heures un vendredi, quand il est trop tard pour rien faire. »

C'est là la vraie valeur du travail planifié, et elle n'a rien à voir avec les machines qui travaillent pendant que vous dormez. C'est que la *question* a une heure, et l'heure est choisie par quelqu'un qui y a pensé une fois, soigneusement, plutôt que par celui qui arrive à s'inquiéter au moment donné.
