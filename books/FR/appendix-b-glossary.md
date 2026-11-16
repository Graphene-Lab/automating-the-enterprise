# Annexe B — Un glossaire pour celles et ceux qui ne programment pas

Chaque mot ci-dessous est un mot que ce livre a utilisé, ou que quelqu'un emploiera à votre égard pendant que vous installez le système. Les définitions sont volontairement simples et parfois imprécises ; là où une définition précise aurait aidé un programmeur et embrouillé un gestionnaire de bureau, c'est la version simple qui a emporté la décision.

**Agent.** Un programme que l'on peut charger d'une instruction formulée en langage courant et qui peut l'exécuter—rechercher des informations, créer des enregistrements, lancer un traitement—plutôt que de se limiter à répondre par du texte. Dans ce livre, l'agent est AgentBridge, le programme avec lequel vous échangez dans une fenêtre de terminal.

**API.** Application Programming Interface. Une façon documentée pour un programme de demander à un autre programme de faire quelque chose. Imaginez-le comme la trappe de service d'un restaurant : la cuisine ne veut pas que vous entriez en cuisine, mais il existe une façon appropriée de passer une commande et de recevoir un plat.

**Clé API.** Le mot de passe qu'un programme utilise à la place d'un être humain. C'est une longue chaîne de caractères, elle est affichée une seule fois, et elle doit être traitée comme une clé de le coffre-fort : conservée dans un gestionnaire de mots de passe, jamais dans un courriel, jamais dans un document susceptible d'être transmis.

**Sauvegarde.** Une copie des données prise à un instant donné, conservée ailleurs que sur la machine qui détient l'original. Une sauvegarde non vérifiée est un vœu pieux ; une sauvegarde que vous avez ouverte et lue est une sauvegarde.

**Base de données.** Un programme dont la tâche est de stocker des faits et de les restituer fidèlement, même lorsque l'alimentation vient à manquer au milieu d'un changement. Dans ce livre, PostgreSQL.

**Document (dans un ERP).** Pas un morceau de papier : un enregistrement de quelque chose qui s'est produit ou qui va se produire—une commande, une livraison, une facture, un paiement—avec une date, une partie, une liste de lignes et un état. Les documents conservent leur propre copie des faits avec lesquels ils ont été créés, de sorte que la facture du mois dernier montre encore le prix du mois dernier.

**ERP.** Enterprise Resource Planning. Un logiciel qui maintient le client, le produit, la commande, le stock, la facture et le grand livre dans un modèle unique et connecté, de sorte qu'un fait saisi une seule fois soit visible partout. Le nom a été inventé par la firme d'analystes Gartner en 1990.

**Champ.** Une seule pièce d'information dans un enregistrement : le numéro de téléphone du client, le prix d'un produit, la date d'une facture.

**Écriture de journal.** L'enregistrement comptable à double entrée que chaque événement financier produit : un montant dans un compte et le même montant, en sens inverse, dans un autre. Inventée bien avant les logiciels ; codifiée par Luca Pacioli en 1494 ; toujours la raison pour laquelle les livres peuvent être vérifiés.

**JSON.** Une façon d'écrire des données sous forme de texte, de sorte qu'un programme puisse les transmettre à un autre. Vous ne le verrez jamais que dans un fichier journal, où il ressemble à un paragraphe de signes de ponctuation.

**Modèle de langage (LLM).** Un programme entraîné sur une quantité énorme de texte, capable de produire du texte plausible en réponse à une instruction. Il est bon en langage et peu fiable dans les faits, sauf s'il est *ancré*—c'est-à-dire s'il est amené à rechercher les faits plutôt qu'à s'en souvenir.

**MCP.** Model Context Protocol. Une norme ouverte, publiée par Anthropic en novembre 2024, qui permet à un programme de décrire les outils qu'il met à disposition d'un assistant de façon uniforme. C'est la raison pour laquelle un outil écrit pour un assistant peut être utilisé par un autre.

**Modèle (dans ce livre, deux sens).** 1. La représentation d'une entreprise à l'intérieur d'un ERP : parties, produits, documents, argent. 2. L'artefact entraîné derrière un assistant : le « modèle de langage ». Le contexte précise lequel ; lorsqu'il ne le précise pas, c'est généralement le premier sens qui compte.

**Module.** Un paquet qui ajoute une capacité à un ERP—comptabilité, inventaire, fabrication, achats. L'installation d'un module ajoute des écrans, des enregistrements et des règles ; elle ne change pas les données sous-jacentes.

**Odoo.** Un ERP open source, démarré en 2005 sous le nom de TinyERP, rebaptisé OpenERP en 2008 et Odoo en 2014. L'édition Community est gratuite ; l'édition Enterprise est sous licence. La version 20, utilisée dans ce livre, a été publiée en septembre 2026.

**PostgreSQL.** La base de données open source utilisée par Odoo. Elle a commencé comme un projet de recherche à l'Université de Californie à Berkeley dans les années 1980 et est aujourd'hui l'une des bases de données les plus utilisées au monde.

**Invite.** L'instruction que vous tapez pour l'assistant, en langage courant. Une bonne invite dit ce que vous voulez, pour qui, et pour quand ; une mauvaise invite dit « fais les factures » et espère.

**Enregistrement.** Une seule ligne dans une table : un client, un produit, une facture.

**Schéma.** La liste des tables et des champs qu'une base de données contient, ainsi que les règles concernant ce qui peut y figurer. Quand quelqu'un dit « le schéma impose qu'un client ait un nom », il veut dire que la base de données refusera de sauvegarder un client sans nom.

**Mouvement de stock.** L'enregistrement de marchandises se déplaçant d'un lieu vers un autre : d'un fournisseur vers un entrepôt, d'une étagère vers une fourgonnette, d'une fourgonnette vers une étagère parce que la porte de l'école était verrouillée. Le niveau de stock d'un produit est la somme de ses mouvements ; il n'est jamais saisi directement.

**Jetons.** L'unité dans laquelle le travail d'un modèle de langage est mesuré. Grossièrement, un jeton vaut trois quarts d'un mot. Les fournisseurs facturent au jeton, ce qui fait qu'un document très long coûte plus cher à traiter qu'une question brève.

**Outil (dans le contexte d'un assistant).** Une seule action que l'assistant est autorisé à réaliser, avec un nom et une description : *rechercher des clients*, *créer une facture*, *publier un paiement*. Un assistant sans outils ne peut que parler. Un assistant avec des outils peut travailler.

**Transaction.** Un changement qui se produit soit complètement, soit pas du tout. C'est la promesse qui rend une base de données digne de confiance : il n'existe aucun état dans lequel une facture existerait à moitié.

**Variante.** Une version d'un produit qui diffère par un seul attribut—taille, couleur, tension. Un seul produit avec douze variantes n'est pas douze produits, et le modéliser correctement fait la différence entre un rapport utile et un rapport inutile.

**Interface web (ou interface web, UI).** Les écrans que vous voyez dans un navigateur. L'interface web d'Odoo est l'endroit où vous configurez l'entreprise, où vous consultez les enregistrements et où vous imprimez des documents ; l'assistant est une seconde façon d'atteindre les mêmes enregistrements.

**Flux de travail.** La série d'états par lesquels un document passe—brouillon, confirmé, livré, facturé, payé—et les règles concernant qui peut le faire passer d'un état à l'autre. Dans un bon ERP, le flux de travail est la politique de l'entreprise, écrite et appliquée.
