# 24. Le papier qui sort du bâtiment

Il y a une étagère dans le bureau de Riverton qui contient quatre classeurs, et ce sont les derniers papiers que l'entreprise conserve.

Ce ne sont pas des factures. Les factures sont dans le système et dans les boîtes réception des clients. Les classeurs contiennent les choses qui doivent être signées : les bons de livraison revenus avec les initiales d'un gardien, les avoirs qu'un client a contestés, et les deux contrats qui comptent. Tout le reste est un PDF.

Ce chapitre porte sur le moment où un document quitte le bâtiment, c'est-à-dire le moment où le logiciel rencontre le monde physique—et où un nombre surprenant de systèmes par ailleurs bons échouent.

---

## Ce qui rend un document imprimable

Un document imprimable n'est pas un écran qui aurait été réduit. C'est un objet différent, avec des règles différentes, et le moteur de rapports d'Odoo vaut la peine d'être compris parce qu'il les impose.

**Il a une mise en page fixe.** Un écran se réorganise ; une page ne le fait pas. Le modèle de facture décide où va le logo, quelle est la largeur de la colonne de description, et ce qui se passe quand le nom d'un produit est plus long que la colonne. (La réponse, dans un bon modèle, est qu'il se met en forme—et que la ligne grandit. Dans un mauvais, elle chevauche le prix, et le client voit un nombre qui appartient à une autre ligne.)

**Il a un en-tête et un pied de page qui se répètent.** La page une d'une facture en cinq pages doit dire de quelle facture il s'agit, et la page cinq doit dire qu'il s'agit de la page cinq sur cinq. Ce n'est pas de la vanité : une page qui arrive seule, sans en-tête, est une page qui peut être contestée.

**Il porte l'identité de l'entreprise.** Nom, adresse, numéro fiscal, immatriculation, coordonnées bancaires. Ce ne sont pas des décorations ; ce sont les champs qui font du document une prétention légale, et ils proviennent du record d'entreprise configuré au chapitre neuf.

**Il est reproductible.** La même facture, imprimée un plus tard, doit avoir la même apparence. C'est pourquoi le modèle est un modèle et non un document que quelqu'un a modifié : une facture qui peut être modifiée après coup est une facture qui ne prouve rien.

## Les trois documents qu'un grossiste imprime réellement

Riverton imprime trois choses, et chacune a une tâche différente.

**La facture**, sous forme de PDF joint à un courriel. C'est la demande de paiement et le document fiscal, et c'est celle que le service comptabilité du client classera.

**Le bon de livraison**, imprimé sur la imprimante du camion et signé à la porte. Ce n'est pas un document financier ; c'est la preuve que les marchandises sont arrivées, et c'est la chose qui tranche le débat trois semaines plus tard sur le fait que la palette a été signée pour réception.

**L'état des comptes**, envoyé mensuellement aux clients ayant plusieurs factures ouvertes. C'est une liste, non une demande, et c'est l'outil de recouvrement le plus efficace qui soit—parce qu'il place chaque article ouvert devant la personne qui paie, en une seule page, sans accusation.

Il y a un quatrième, moins évident : le **rapport de stock**. Il n'est envoyé à personne. Il est imprimé parce que Tom le lit dans le camion, et lire une chose sur papier est différent de la lire sur un écran—plus lent, et donc plus susceptible d'être réfléchi.

## Le processus qui a remplacé l'enveloppe

Le vieux processus de Doreen était : imprimer, plier, adresser, timbrer, poster, classer la copie. Cinq étapes, et la dernière était celle qui échouait, parce que le classement est l'étape qui n'a pas de deadline.

Le nouveau processus est : générer, vérifier, envoyer, et laisser le système le classer. Trois étapes, et le classement est automatique—ce qui signifie qu'il se produit, ce qui signifie que lorsqu'un client téléphone en novembre au sujet d'une facture de juin, la réponse est une recherche plutôt qu'une expédition vers la salle des factures.

La vérification est l'étape qui compte, et c'est celle que les entreprises négligent. Un document généré par une machine n'est pas automatiquement correct : il est correct si les données qui le sous-tendent sont correctes, et les données qui le sous-tendent ont été saisies par quelqu'un. L'habitude de Doreen, qu'elle a conservée de l'ère du papier, est de lire la première facture de chaque série—pas toutes, la première—and de regarder le nom du client, l'adresse, le total et la taxe. Si ces quatre éléments sont justes, le reste l'est très probablement.

## Ce que l'assistant fait, et ce qu'il ne fait pas

L'assistant peut produire le PDF et le joindre à un courriel. À Riverton, il ne le fait pas, et la décision vaut la peine d'être consignée parce qu'il s'agit d'un choix, non d'une limitation.

Le rôle de l'assistant est de *préparer* : créer la facture, la valider, produire le document, et dire à Doreen qu'elle est prête. L'envoi est fait par une personne, dans le client de messagerie, parce que l'envoi est l'étape où une erreur atteint un client—et une erreur qui atteint un client coûte plus que la minute qu'il faut pour l'éviter.

C'est un choix prudent, et une entreprise avec cent factures par jour ne peut pas le faire. Riverton en a quinze, et quinze minutes d'attention humaine sont abordables. Le principe qui s'applique à toute échelle, toutefois, est le même à tout volume : **l'étape qui sort du bâtiment est l'étape où un être humain devrait se trouver, jusqu'à ce que vous ayez vu la machine le faire correctement cent fois.**

## Une brève histoire de la forme de facture

La facture imprimée est le enfant du dix-neuvième siècle, et sa forme a été fixée par les chemins de fer et le télégraphe.

Avant que l'impression ne devienne bon marché, une facture était une note manuscrite. Lorsque les entreprises ont grandi, et qu'un même client a commencé à acheter à plusieurs services du même fournisseur, la note est devenue un formulaire : imprimé avec le nom de l'entreprise, avec des lignes numérotées, avec des colonnes pour la quantité, la description, le prix et le montant. Les colonnes ne sont pas arbitraires—elles reflètent la séquence selon laquelle un clerc vérifie le document, de gauche à droite, en terminant par le total.

La forme a survécu à toutes les technologies depuis, y compris celle-ci, parce qu'elle encode l'information minimale nécessaire pour régler un litige : qui, quoi, combien, à quel prix, quelle taxe, au total, pour quelle date. Le logiciel n'a pas changé la forme. Il a changé le coût de la produire, et—plus important encore—le coût de la *trouver* ensuite.

Cette dernière modification est celle que personne ne remarque. En 1975, une copie d'une facture vivait dans un classeur, dans un dossier, sous le nom d'un client, et sa recherche prenait une personne qui connaissait le système. En 2026, elle vit dans une base de données et peut être trouvée par quiconque sait taper le nom d'un client—ce qui signifie qu'elle peut être trouvée par la personne qui est réellement au téléphone, plutôt que par la personne qui sait par hasard où est le dossier.

## L'archive

Chaque document qui sort du bâtiment devrait être trouvable ensuite, et c'est ici qu'une habitude de petite entreprise et une capacité de système divergent généralement.

Odoo conserve chaque document validé et peut régénérer son PDF à tout moment, ce qui signifie que le *fichier* n'a pas besoin d'être archivé séparément : le document est les données, et le PDF est une vue de celles-ci. C'est élégant, et c'est aussi légèrement alarmant la première fois que vous l'entendez—que se passe-t-il si le modèle change et que la facture s'imprime différemment dans un an ?

La réponse est qu'elle le fera, et que c'est acceptable, parce que le *contenu* est ce qui compte et que le contenu est stocké. Si votre juridiction exige le PDF exact tel qu'émis, Odoo peut joindre le PDF généré au record lorsqu'il est validé, et le fichier est alors fixe. Riverton fait cela pour les factures envoyées à l'étranger, où l'autorité fiscale est plus pointilleuse, et pas pour les domestiques.

## La imprimante, et tout ce qui peut mal tourner avec elle

Un chapitre sur l'impression qui ne mentionnerait pas la imprimante serait un chapitre écrit par quelqu'un qui n'a jamais travaillé dans un bureau.

La imprimante est le composant le moins fiable de toute la pile, et c'est celle qui échoue au moment de l'urgence maximale—qui est la nature des imprimantes. Trois choses valent la peine d'être connues.

**Imprimer vers un PDF n'est pas imprimer.** Chaque document décrit dans ce chapitre peut être produit comme un PDF sans qu'une imprimante soit impliquée, et pour les factures et les états des comptes, c'est ce qu'une entreprise devrait faire : générer le PDF, le joindre à un courriel, et garder le papier pour les choses qui nécessitent une signature. La imprimante de Riverton est utilisée pour les bons de livraison et le rapport de stock du vendredi, et pour rien d'autre.

**Un document qui a été imprimé n'est pas un document qui a été envoyé.** Cela semble évidet et c'est la source de la facture Ashfield au début de ce livre. Le système sait que le PDF a été généré ; il ne sait pas si le courriel a été envoyé. Si l'envoi compte, l'envoi doit être enregistré—ce qui est une raison pour laquelle les entreprises finissent par automatiser toute l'étape, afin que l'enregistrement existe.

**Le bourrage de papier est un risque d'entreprise.** Un bon de livraison qui ne peut pas être imprimé est une livraison qui ne peut pas partir, parce que le chauffeur ne partira pas sans le papier que le client signe. Chaque entreprise qui dépend d'une imprimante au quai de chargement devrait en avoir une seconde, ou un moyen d'imprimer la note à l'adresse du client. Riverton a appris cela un samedi, et garde désormais un modèle de rechange dans un placard.

## Les trois choses qui mal tournent avec une série d'impression

Chaque entreprise qui imprime des documents a rencontré ces trois, et chacune a une correction bon marché.

**Le modèle change et personne ne remarque.** Un logo mis à jour, une adresse changée, une coordonnées bancaire corrigée—et le modèle montre encore l'ancien parce que le changement a été fait sur le record d'entreprise et que le modèle lit une copie. Les modèles d'Odoo lisent le record d'entreprise directement, donc ceci est plus rare que dans les systèmes qui copient ; mais un modèle personnalisé peut quand même coder une valeur en dur, et le moyen de le savoir est d'imprimer un document après tout changement et de le lire.

**Le papier est de la mauvaise taille.** Un bon de livraison conçu pour du A4 imprimé sur la imprimante A5 du camion perd sa colonne de droite—qui est celle des quantités. La correction est un deuxième modèle pour le petit format, ou une imprimante qui prend du A4, et il vaut la peine de décider avant la première livraison plutôt qu'après.

**La copie client et la copie de fichier divergent.** Quelqu'un écrit sur la copie imprimée—une note, une correction, une signature—et le fichier conserve la version intacte. C'est correct pour la facture et faux pour le bon de livraison : la note signée *est* l'enregistrement, et elle doit être numérisée ou classée, pas jetée parce qu'« elle est dans le système ».

## Ce qu'une signature signifie

Le bon de livraison revient avec un gribouillage dessus, et le gribouillage est la chose la plus intéressante juridiquement dans toute la pile.

Une signature sur un bon de livraison est une reconnaissance : *j'ai reçu ces marchandises, dans cette quantité*. Ce n'est pas un contrat—le contrat était la commande—et ce n'est pas un reçu pour paiement. C'est une preuve, et sa valeur est qu'elle a été faite au moment de la livraison par quelqu'un qui était présent.

C'est pourquoi le bon de livraison est encore imprimé, et pourquoi l'assistant n'est pas autorisé à marquer une livraison comme signée. La signature est un acte physique par un tiers, et aucune quantité de logiciel ne peut le performer. Ce que le logiciel peut faire est de s'assurer que la note qui est signée est la bonne : la bonne cliente, la bonne commande, les bonnes quantités, et une page que le chauffeur peut réellement lire dans un camion.

Le jour où la note est signée et revient, quelqu'un valide la livraison dans le système—et le papier va dans un dossier pendant six ans, parce que c'est le temps pendant lequel une entreprise peut avoir besoin de prouver que les marchandises sont arrivées.

## L'archive des documents envoyés

Il y a une question qu'une entreprise se pose la première fois qu'un client conteste une facture de il y a deux ans : *pouvons-nous prouver ce que nous avons envoyé ?*

La réponse dépend d'une décision prise bien avant, et elle vaut la peine d'être faite délibérément : le système conserve-t-il le *document* ou les *données* ?

Conserver les données—le record de facture et ses lignes—signifie que le PDF peut être régénéré à tout moment, et qu'il ressemblera au modèle d'aujourd'hui plutôt qu'à celui qui a été utilisé à l'époque. Pour la plupart des usages, c'est suffisant, et c'est ce qu'Odoo fait par défaut.

Conserver le document signifie joindre le PDF généré au record lorsqu'il est validé, afin que le fichier soit fixe. Cela coûte quelques centaines de kilooctets par facture et règle chaque débat sur ce qui a été envoyé, sous la forme sous laquelle il a été envoyé.

Riverton joint le PDF pour les factures aux clients à l'étranger, où l'autorité fiscale est plus pointilleuse, et pour les deux contrats qui comptent. Pour les factures domestiques, elle s'appuie sur les données, ce qui est une décision que Doreen a prise après avoir demandé à son comptable, et qu'elle revisite chaque année.

---

Les classeurs sur l'étagère sont l'exception qui confirme la règle : les choses qui doivent être signées sont encore du papier, parce qu'une signature est encore un acte physique dans la plupart du monde. Tout le reste est devenu un fichier, et l'étagère n'a pas grandi en un an.

Doreen l'a remarqué avant quiconque.

« L'étagère avait tendance à se remplir en juin », dit-elle. « Je devrais commencer un nouveau. Cette année, j'en ai utilisé environ quatre pouces. »

Elle l'a regardé un moment.

« C'est étrange. J'ai passé trente ans à faire du papier, et je ne le regrette pas. Ce dont je m'ennuis, c'est de savoir où sont les choses—et je l'ai retrouvé, d'une manière différente. »

C'est le marché que tout le livre a été en train de décrire, dit par la personne qui l'a conclu : non la disparition du papier, mais le retour de savoir où sont les choses, sans avoir à être la personne qui les a classées.
