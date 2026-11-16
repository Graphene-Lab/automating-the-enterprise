# 12. La clé qui n'ouvre qu'une seule porte

Le dernier élément de configuration avant de laisser l'assistant agir était le moins intéressant
et le plus important : la clé.

Sam l'a expliquée au tableau blanc, de la façon dont il expliquait tout, avec un diagramme qui prenait
une trenteaine de secondes et tranchait un débat qui prend d'habitude une semaine.

« Chaque serrure de ce bâtiment a une clé, dit-il en dessinant un rectangle pour l'ERP. « La question
n'est pas de savoir si l'assistant obtient une clé. La question est quelle porte il ouvre, et ce qu'il
peut faire une fois à l'intérieur. »

---

## Ce qu'est une clé API

Une clé API est un mot de passe qu'un programme utilise à la place d'une personne. C'est une longue
chaîne de caractères, elle s'affiche une seule fois, et elle appartient à un *utilisateur*—pas au
programme, et pas à la machine.

Ce dernier point constitue toute la conception. Lorsque l'assistant se connecte à Odoo, il ne se
connecte pas en tant que superutilisateur avec une porte dérobée spéciale. Il se connecte en tant que
compte utilisateur appelé, dans le cas de Riverton, *Agent*, avec un mot de passe et une clé, et avec
un ensemble de permissions qu'une personne aurait pu donner à un nouvel employé le premier jour.

Ce qui signifie trois choses, et chacune d'elles vaut plus que la commodité qu'elle coûte.

**Les règles de l'ERP s'appliquent à l'assistant.** Si l'utilisateur *Agent* n'est pas autorisé à
supprimer des factures, l'assistant ne peut pas supprimer de factures—pas parce qu'on lui a dit de ne
pas le faire, mais parce que l'ERP refusera la demande. L'intelligence est nouvelle ; les règles sont
anciennes ; la chose nouvelle fonctionne à l'intérieur de la chose ancienne.

**L'assistant apparaît dans la piste d'audit.** Chaque enregistrement qu'il crée indique *Agent* dans
le champ « créé par », et chaque modification qu'il effectue est journalisée. Si une facture apparaît
à quatre heures du matin avec une étrange remise, le système ne dira pas « c'est la machine qui l'a
faite » ; il dira quel utilisateur, à quelle heure, et avec quelles valeurs.

**La clé peut être révoquée sans rien changer d'autre.** Si la clé fuit, ou si l'assistant est
remplacé, ou si quelqu'un part, la clé est supprimée et l'assistant s'arrête. L'ERP ne change pas, les
utilisateurs ne changent pas, et rien n'a à être réinstallé.

## Où vit la clé

L'installateur a généré la clé pendant l'installation et l'a écrite dans la configuration du
connecteur, dans le propre dossier de l'assistant. Elle n'est pas dans le livre, pas dans un courriel,
et pas dans un document qui est transmis. Elle est dans un seul fichier, sur une seule machine, avec
les permissions de fichier de l'utilisateur qui l'a installée.

La même clé peut être créée à la main, et chaque utilisateur peut en créer une pour soi-même : elle se
trouve dans le menu utilisateur, *Mon Profil*, *Sécurité du compte*, *Nouvelle clé API*. L'ERP l'affiche
une seule fois, dans une boîte, avec un avertissement selon lequel elle ne sera plus jamais affichée—ce
qui n'est pas une menace, mais un fait sur la façon dont les clés sont stockées : le système conserve un
hachage, et non la clé, donc il ne peut pas vous le rappeler plus tard.

![La liste des utilisateurs : l'assistant est un utilisateur comme les autres, avec un rôle et une
piste d'audit](../../assets/screens/odoo-08-users.png)

## Ce que l'assistant était autorisé à faire

L'utilisateur *Agent* de Riverton s'est vu attribuer un rôle, et le rôle a été choisi selon une règle
qui vaut la peine d'être répétée : **donner à l'assistant les droits du salarié le moins puissant qui
aurait pu faire le travail.**

Pour Riverton, cela signifiait :

| Domaine | Droits | Pourquoi |
|---|---|---|
| Clients | lire, créer, modifier | il prend des commandes et ajoute des contacts |
| Produits | lire | il fait des devis ; il n'invente pas de produits |
| Ventes | lire, créer, confirmer | il rédige des devis et confirme des commandes |
| Factures | lire, créer, valider | il facture ; la validation est l'acte qui crée le grand livre |
| Paiements | lire, créer | il enregistre ce que la banque indique |
| Achats | lire, créer, confirmer | il réapprovisionne ce que l'entrepôt demande |
| Stock | lire, ajuster | il déplace du stock et consigne les dégâts |
| Paramètres de comptabilité | aucun | la configuration est le travail d'une personne |
| Utilisateurs et permissions | aucun | jamais, en aucune circonstance |
| Suppression de documents | aucun | si quelque chose est erroné, il est annulé, pas effacé |

Les deux dernières lignes sont celles qu'il faut défendre. Une machine qui peut changer de permissions
peut s'attribuer elle-même tout ce qu'elle veut ; une machine qui peut supprimer peut détruire la piste
d'audit qui prouverait ce qu'elle a fait. Toutes deux sont exclues non pas parce que l'assistant est
peu fiable en un sens dramatique, mais parce que le coût de leur exclusion est nul et que le coût d'une
erreur ne l'est pas.

## La conversation sur la confiance

Doreen, qui avait été silencieuse pendant la majeure partie de cet exposé, posa la question qui
comptait.

« Qu'est-ce qui l'empêche de faire une bêtise ? »

« Rien ne l'empêche, dit Sam. C'est la réponse honnête. Elle peut créer un client avec un nom ridicule,
ou valider une facture au mauvais destinataire, ou commander quatre cents cartons du mauvais papier. Ce
qui empêche que cela devienne une catastrophe, c'est que vous pouvez le voir, et l'annuler, et qu'elle
ne peut pas faire les choses qui ne se désfont pas. »

« Ce n'est pas très réassurant. »

« Non, admit-il. Mais c'est la même assurance que l'on a avec un nouvel employé. On ne l'empêche pas de
faire une erreur ; on lui donne un travail avec une limite, on vérifie le travail du premier mois, et on
s'assure que les erreurs sont du genre que l'on peut corriger. »

La différence—et c'est la différence qui rend le système utilisable—est que les erreurs de l'assistant
sont *visibles d'une façon dont ne le sont pas celles d'une personne*. Une personne qui entend mal une
quantité l'écrit sur une commande et personne ne remarque quelque chose tant que le client ne se
plaint pas. La version de l'assistant de la même erreur est un enregistrement avec une horodate, un
utilisateur, l'outil qu'elle a appelé et les arguments qu'elle a transmis, et on peut le trouver dans un
journal par quiconque pense à chercher.

C'est pourquoi le journal n'est pas un détail technique. C'est la chose qui rend un agent acceptable dans
une entreprise où l'argent bouge : non qu'il n'erre jamais, mais que ses erreurs sont *trouvables*.

## Le premier test

Avant de laisser l'assistant faire quoi que ce soit, Sam lui demanda de ne rien faire.

« Vérifie la connexion, tapilla-t-il. « Dis-moi quelle version d'Odoo est en cours d'exécution. »

La réponse revint en une seconde : la version, le nom de la base de données, l'utilisateur auquel elle
était connectée, et la compagnie vers laquelle elle était orientée. Quatre faits, tous corrects, tous
qui pourraient être vérifiés par un humain dans l'ERP en environ le même temps.

« Bien, dit Sam. « Maintenant, demande-lui combien de clients il y a. »

Il n'y en avait pas, parce que personne n'en avait encore saisi. L'assistant dit zéro, ce qui était
vrai, et ce qui est une réponse plus intéressante qu'il n'y paraît : un système qui peut dire *zéro* est
un système qui lit la base de données, et non un système qui invente quelque chose. Un modèle qui
devinerait aurait produit un nombre plausible.

« D'accord, dit Sam en fermant son ordinateur portable. « C'est le tien. Donne-lui un travail. »

## La permission que tout le monde oublie

Il y a une permission dans chaque ERP que les entreprises accordent sans réfléchir, et c'est celle qui
annule toutes les autres : la capacité de changer la *configuration*.

Un utilisateur qui peut modifier le plan comptable peut valider n'importe quoi n'importe où. Un
utilisateur qui peut modifier les codes fiscaux peut faire disparaître une vente. Un utilisateur qui peut
changer les droits d'accès peut s'attribuer lui-même tout ce qui lui manque. Les règles qui protègent le
grand livre sont elles-mêmes des données, et quiconque peut changer les données peut changer les règles.

L'assistant est donc exclu des paramètres entièrement—non pas parce qu'il en abuserait, mais parce que la
compétence d'un agent réside précisément dans le *faire des choses*, et que la configuration est le seul
domaine où faire la mauvaise chose est indiscernable de faire la bonne chose jusqu'à l'arrivée de
l'auditeur.

La règle se généralise : **automatisez le travail, jamais les règles.** Une entreprise qui laisse un
assistant changer ses propres permissions a, en réalité, aucune permission du tout ; elle a une boîte à
suggestions.

## Le premier contrôle après la création d'une clé

Au moment où une clé est créée, il y a un contrôle qui vaut la peine d'être fait, et qui prend dix
secondes.

Dans l'assistant, demandez : *vérifie la connexion à Odoo et dis-moi quelle version est en cours
d'exécution.*

Un numéro de version et un nom de base de données signifient que la clé fonctionne, que l'adresse est
correcte, et que l'utilisateur peut atteindre l'ERP. Une erreur signifie que l'un des trois est erroné,
et le message d'erreur dit d'habitude lequel.

Ce contrôle vaut la peine d'être répaprès tout changement à la configuration—une nouvelle clé, un nouveau
port, une nouvelle machine—parce qu'il isole la connexion de tout le reste. Quand quelque chose plus
tard tourne mal, la première question est toujours *est-ce la connexion ou est-ce la question ?*, et cet
ordre y répond en une seconde.

Doreen l'a écrit sur une carte et l'a collée au moniteur. C'est l'instruction la moins intéressante de
ce livre et celle qui a fait gagner le plus de temps.

## Quand la clé fuit

Une clé écrite dans un fichier de configuration sur une machine peut fuir de trois façons, et les trois
se sont produites pour des entreprises qui n'étaient pas négligentes.

Elle peut être copiée dans une sauvegarde qui est ensuite partagée. Elle peut être collée dans une
demande de support par quelqu'un qui essaie d'être utile. Et elle peut être lue par un autre programme
sur la même machine, ce qui est la raison pour laquelle un ordinateur partagé par cinq personnes n'est
pas un bon endroit pour une clé qui peut valider des factures.

Le remède n'est pas de garder la clé avec cérémonie. Le remède est que la clé est *bon marché à
remplacer* :

1. Dans l'ERP, ouvrez la page de sécurité du compte de l'utilisateur et supprimez la clé.
2. Créez-en une nouvelle et collez-la dans la configuration du connecteur.
3. Redémarrez l'assistant.

Trois minutes, aucune perte de données, aucune réinstallation. La vieille clé cesse de fonctionner à
l'instant où elle est supprimée, ce qui est la propriété qui rend cela sûr : une clé fuyée est une
gêne plutôt qu'un incident, pourvu que quelqu'un le remarque et la révoque.

La chose qui en fait un incident est une clé appartenant à un utilisateur qui peut tout faire. Ce qui est
pourquoi l'utilisateur *Agent* a un rôle, et pourquoi la clé de l'administrateur n'est jamais celle qui
est donnée à un programme.

## Un agent à la fois

Il y a une limite supplémentaire à connaître, et elle n'a rien à voir avec les permissions.

L'assistant s'exécute sur la même machine que tout le reste, et le modèle de langage—qu'il s'agisse d'un
service dans un autre bâtiment ou d'un modèle sur votre propre carte graphique—répond à une demande à la
fois. Une entreprise qui démarre quatre agents dans quatre fenêtres n'obtiendra pas quatre fois le
travail ; elle obtiendra quatre agents qui prennent leur tour, et une machine sans mémoire restante.

L'installateur est conçu autour de ceci : un assistant, une fenêtre, un lanceur qui en ouvre exactement
une. La tentation d'en ouvrir une seconde, de faire autre chose pendant que le premier réfléchit, est la
façon la plus commune pour une petite installation de tomber en panne—et le remède n'est pas technique.
C'est d'attendre, ou de demander moins à la fois.

Riverton l'a apprise à la deuxième semaine, quand Tom a ouvert une seconde fenêtre pour demander du stock
pendant que la facture de Priya était rédigée. La machine ne s'est pas crashée. Elle est simplement
devenue lente, puis plus lente, puis les deux fenêtres ont répondu à la fois avec deux moitiés du même
travail, et Doreen a passé vingt minutes à déterminer quelle facture était réelle.

La règle qui en est sortie est sur le mur de la salle des factures, à côté de la serviette : *une seule
question à la fois, et lisez la réponse.*

---

Ce soir-là, Maggie s'est assise devant la fenêtre de l'assistant pendant un moment sans taper quoi que ce
soit.

La fenêtre était simple : une invite, un endroit pour la réponse, et une petite ligne en bas disant à
quel modèle elle parlait. Elle ressemblait aux fenêtres de terminal que son père avait utilisées dans les
années soixante-dix, ce qui était soit réassurant soit alarmant selon votre point de vue sur les années
soixante-dix.

Elle tapilla : *Que peux-tu faire ?*

La réponse fut une liste. Elle pouvait lire clients, produits, commandes, factures, stock ; elle pouvait
créer et modifier des enregistrements ; elle pouvait appeler les actions qui font passer un document d'un
état à un autre ; elle pouvait grouper et sommer et compter. Elle ne pouvait pas changer les paramètres de
la compagnie, gérer des utilisateurs, ou supprimer quoi que ce soit.

Elle le lut deux fois, puis elle tapilla la phrase qui était dans sa tête depuis le lundi de novembre
quand elle avait traversé la ville avec une facture.

*Montre-moi tous les clients qui nous doivent de l'argent et qui n'ont commandé quoi que ce soit depuis
six mois.*

La réponse prit quatre secondes. Il n'y avait pas encore de clients, donc la réponse fut une phrase
polie le disant—mais la phrase comprenait les deux choses qu'elle avait cherchées et l'endroit où elle
avait cherché, ce qui est ce qu'un bon employé fait quand la réponse est « rien ».

Maggie ferma la fenêtre et rentra chez elle.

Le lendemain matin, elle commença à saisir les clients.
