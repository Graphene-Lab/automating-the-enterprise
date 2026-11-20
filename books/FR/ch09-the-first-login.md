# 9. La première connexion

L'icône a ouvert deux fenêtres, soit une de plus que la plupart des programmes.

La première était une page dans le navigateur : la page de démarrage du chapitre précédent, avec sa porte unique et le compte. La seconde était une fenêtre noire avec un curseur et une courte question sur le fournisseur d'IA. Ensemble, elles étaient tout le système—la page était l'endroit où les données seraient regardées, la fenêtre noire l'endroit où elles seraient demandées.

Avant de cliquer quoi que ce soit, Maggie s'est posé la question qui arrête la plupart des gens à ce point, et il vaut la peine d'y répondre lentement, parce que tout le reste de ce livre suppose la réponse.

« Qu'est-ce que je regarde ? »

## Un programme qui vit dans un navigateur

Odoo est une **application web**. La formule couvre deux dispositions différentes du même logiciel, et la différence décide qui en est responsable.

Dans la disposition familière—celle du cloud—le programme tourne sur un ordinateur qui appartient à quelqu'un d'autre, dans un bâtiment où vous n'êtes jamais entré, et votre navigateur est une fenêtre sur lui. Vous tapez une adresse comme `riverton.odoo.com`, la demande voyage sur internet, et une machine dans un centre de données répond. Rien n'est installé sur votre bureau. Vous louez le programme au mois, quelqu'un d'autre le maintient en marche, et en échange votre liste de clients vit sur son disque.

Dans la disposition que ce livre utilise, le programme tourne sur l'ordinateur devant vous. Il n'y a pas de bâtiment et pas de facture mensuelle : il y a un dossier sur votre disque, une base de données sur le même disque, et un petit programme qui écoute les demandes et y répond. Le navigateur est toujours l'écran, mais la machine derrière l'écran est à vous.

C'est pourquoi l'adresse paraît étrange. `localhost` est le nom qu'un ordinateur utilise pour **lui-même** : `localhost:8069` signifie *le programme sur cette machine, à l'écoute de la porte 8069*. Ce n'est pas une société, ce n'est pas un site web, et cela ne s'ouvre depuis l'ordinateur de personne d'autre—ce qui est exactement le point. L'adresse est la porte, et la porte est dans votre bureau.

Deux conséquences en découlent, et toutes deux surprennent les personnes qui n'ont utilisé que des logiciels en cloud.

La première est que **le programme doit tourner**. Un service en cloud est toujours actif parce que quelqu'un est payé pour le maintenir ; votre copie est active quand la fenêtre noire, ou un processus caché en arrière-plan, la fait tourner. Si la machine est éteinte, ou si le programme a été arrêté, le navigateur affiche une page qui ne peut pas se connecter—pas une panne dans vos données, juste une porte sans personne derrière. Un nouveau double-clic sur l'icône le démarre, et c'est la réponse à la plupart des questions de ce chapitre.

La seconde est que **l'adresse n'est pas facultative**. Il n'y a pas d'entrée de menu qui ouvre Odoo directement, parce qu'Odoo n'a pas de fenêtre à lui : sa fenêtre est un onglet du navigateur, et un onglet du navigateur a besoin d'une adresse. C'est la petite connaissance que l'édition précédente de ce livre supposait acquise, et le récit d'un lecteur a prouvé que c'était faux. Une personne qui n'a jamais administré de serveur n'a aucune raison de savoir qu'une application web s'atteint en tapant son adresse, et aucun moyen de deviner `localhost:8069` depuis une icône de bureau qui ouvre autre chose.

C'est toute la raison d'être de la page de démarrage. Ce n'est pas de la décoration : c'est l'adresse, écrite, avec le compte à côté.

## La fenêtre noire est l'assistant

La seconde fenêtre n'a ni titre, ni menus, ni boutons : un rectangle noir avec un curseur. C'est l'assistant, et c'est le seul endroit où l'on peut taper une phrase.

Elle paraît inachevée parce que ce n'est pas un programme grand public. C'est un *terminal*—la surface de texte simple que les programmes utilisent depuis avant la souris—et l'assistant y parle parce que c'est là qu'une conversation avec une machine coûte le moins cher et reste la plus claire : aucune mise en page à maintenir, aucun bouton à chercher, et la réponse imprimée dans l'ordre où elle a été produite, erreurs comprises.

Les trois fenêtres ont trois propriétaires différents, et savoir laquelle peut être fermée, c'est l'essentiel de ce dont un nouvel utilisateur a besoin :

| Fenêtre | Ce que c'est | Si vous la fermez |
|---|---|---|
| La page de démarrage | un fichier sur votre disque, ouvert par le navigateur | rien ne se passe ; l'icône la rouvre |
| L'onglet du navigateur avec Odoo | l'ERP, servi par le programme de cette machine | rien ne se passe ; les données restent et le programme continue de tourner |
| La fenêtre noire | l'assistant | l'assistant s'arrête. Odoo continue de tourner, et l'icône relance l'assistant |

Maggie a laissé la page de démarrage ouverte, parce que l'adresse s'y trouvait, et a cliqué sur *Ouvrir Odoo*.

## La page de connexion, et la partie de l'adresse qui compte

Le navigateur est allé sur `http://localhost:8069/web/login?db=odoo_agent`, et la page était presque vide : une carte blanche, un logo composé de deux formes violettes, et deux champs.

![La page de connexion de l'ERP. La barre d'adresse fait partie de la figure : c'est un programme sur cet ordinateur, à la porte 8069](../../assets/screens/odoo-01-login.png)

La partie `db` de l'adresse nomme la base de données. `odoo_agent` est celle que l'installateur a créée, et la nommer signifie que le navigateur ne peut pas tomber sur une autre par accident—une machine peut garder plusieurs bases, une copie de test et une réelle, et sans le nom Odoo demande laquelle vous voulez dire. Ce n'est pas un réglage à retenir : la page de démarrage et l'icône l'écrivent pour vous.

Une chose sur cette page est un piège, et il vaut la peine de la nommer avant qu'elle soit cliquée. En bas, en petites lettres grises, il y a un lien appelé *Gérer les bases de données*. Il ouvre le gestionnaire de bases d'Odoo, qui peut créer, dupliquer, sauvegarder et **supprimer** des bases, et il demande un mot de passe principal qui n'a rien à voir avec votre identifiant. L'installateur a déjà créé la base ; le gestionnaire est un outil pour un administrateur qui sait pourquoi il l'a ouvert. Rien dans ce livre n'en a besoin.

Maggie a tapé l'adresse administrateur que l'installateur avait imprimée, ainsi que le mot de passe, puis a appuyé sur Entrée.

Si la page de votre navigateur n'est pas celle-ci, c'est l'une de trois choses, et aucune ne signifie que l'installation a échoué : une page sur Odoo sur le site du fournisseur, un site web avec un logo que vous n'avez pas choisi, ou une liste de bases de données. L'annexe C les prend une par une.

Rien de spectaculaire ne s'est produit. C'est là la première chose à dire sur l'ERP : il ne vous accueille pas. Il ne vous félicite pas. Il ouvre une page avec un menu en haut et quelques cartes colorées, et attend qu'on lui dise ce qu'il est.

![Le premier écran après la connexion : la公司 n'a encore aucune donnée](../../assets/screens/odoo-02-dashboard.png)

C'est le moment où une petite entreprise perd généralement courage. Le système paraît vide, les cartes sont dépourvues de sens, et l'on est tenté de conclure que quelque chose s'est mal passé—ou, pis que tout, de commencer à cliquer, ce qui fait qu'une entreprise se retrouve avec quatre entrepôts, trois devises et un client appelé « test ».

La page vide n'est pas une faute. C'est la vérité. Le système ne sait encore rien de Riverton : ni son nom, ni son argent, ni ce qu'il vend. Ce qu'il sait, c'est comment *être* une entreprise. L'heure qui suit est celle pendant laquelle il apprend quelle entreprise.

---

## La première chose à modifier : la langue de la machine

Odoo parle de nombreuses langues, et l'installateur a pris celle de la machine, qui sur ce PC était l'italien. Une entreprise située dans une ville de marché en Angleerre souhaite ses factures en anglais, les noms de ses taxes en anglais, et ses messages d'erreur en anglais, de sorte que la langue est le premier paramètre à modifier, avant que quoi que ce soit ait été nommé.

Le paramètre se trouve dans les préférences de l'utilisateur—le petit cercel en haut à droite, *Mon profil*, *Préférences*—et il est propre à l'utilisateur, pas à l'entreprise. Cette distinction mérite d'être comprise tôt : Odoo est rempli de paramètres qui vous sont propres (langue, fuseau horaire, quelles notifications vous souhaitez) et de paramètres qui sont propres à *l'entreprise* (devise, taxes, plan de comptes). Modifier votre langue ne change rien pour autrui ; modifier la devise change tout pour tous.

## La deuxième chose : l'entreprise elle-même

Sous *Paramètres*, la première entrée est l'entreprise. C'est un formulaire avec un nom, une adresse, un numéro de taxes, une devise, un pays et un logo, et c'est le formulaire le plus important de tout le système, car tout document qui sort du bâtiment est estampé de ce qu'il contient.

![Le formulaire de l'entreprise : nom, adresse, devise, pays](../../assets/screens/odoo-03-company.png)

Trois champs de ce formulaire méritent chacun un paragraphe.

**Le nom** est ce qui apparaît sur les factures. Ce n'est pas nécessairement le nom que l'entreprise utilise dans la conversation ; c'est le nom que le service comptable du client verra et le nom que l'administration des taxes mettra en correspondance avec une immatriculation. S'ils diffèrent, utilisez le nom immatriculé.

**Le pays** décide d'une quantité surprenante de choses : quel plan de comptes le système propose, quelles taxes existent, le format des adresses, la façon dont les dates sont imprimées. Le choisir tardivement est possible et douloureux ; le choisir en premier est gratuit.

**La devise** est celle dans laquelle l'entreprise tient ses livres. Pas la devise de chaque transaction—Odoo gère les devises étrangères, avec des taux de change et des gains et des pertes—mais la devise du grand livre. Pour Riverton, c'est la livre.

Il y a un warning attaché à la modification de la devise une fois que des documents existent, et ce n'est pas une formalité : le grand livre y est dénommé, et le modifier rétroactivement, c'est comme modifier l'unité de mesure d'un entrepôt une fois les étagères pleines. Faites-le maintenant, sur un système vide, et ce sera un menu déroulant.

## La troisième chose : les personnes

Odoo vient avec un seul utilisateur—l'administrateur—et la tentation est de continuer à s'en servir pour tout, parce que c'est le seul qui existe.

Résistez-y, et résistez-y pour une raison qui n'a rien à voir avec le théâtre de sécurité. Chaque enregistrement dans l'ERP se souvient de qui l'a créé et de qui l'a modifié. Si tout le monde travaille en tant qu'administrateur, cette mémoire devient inutile : le système dira que *admin* a créé la facture, *admin* a approuvé la remise et *admin* a supprimé le client, et la question « qui a fait ceci ? » n'aura pas de réponse. La piste d'audit ne vaut quelque chose que si les personnes sont distinctes.

Pour Riverton, quatre utilisateurs suffisaient pour commencer :

| Utilisateur | Rôle | Pourquoi |
|---|---|---|
| Administrateur | droits complets | configuration, et rien d'autre |
| Doreen | comptabilité, facturation | son travail, et sa signature sur le grand livre |
| Priya | vente | devis, commandes, clients |
| Tom | inventaire | réceptions, livraisons, ajustements de stock |

Chacun d'eux a un identifiant, un mot de passe et un rôle. Chacun d'eux apparaît dans la piste d'audit par son nom. Et chacun d'eux peut se voir accorder plus ou moins de droits sans toucher à ceux d'autrui.

Il y a un cinquième utilisateur, comme lequel personne ne se connecte : l'assistant. Il a été créé par l'installateur, il possède sa propre clé, et il a exactement les droits nécessaires pour faire le travail décrit dans ce livre. Nous le rencontrerons proprement au chapitre douze.

## La quatrième chose : ce que l'entreprise fait

La dernière question de la première heure est celle qui décide quelles parties de l'ERP sont allumées. Odoo est modulaire : il peut être un programme de facturation, ou un entrepôt, ou une usine, ou un magasin, et la différence tient à quelles applications sont installées.

Pour un grossiste, la réponse est courte : *Vente*, *Achats*, *Inventory*, *Facturation*, et *Comptabilité*. Pas *Fabrication* (Riverton ne fabrique rien), pas *Point de vente* (il n'y a pas de magasin), pas *Site web* (la boutique en ligne est une chose à part et peut être connectée plus tard). Chaque application installée ajoute des menus, et chaque menu est une invitation à la confusion si personne n'en a besoin.

Maggie a installé cinq applications dans la première heure et a résisté aux vingt autres. Cette retenue vaut plus que toute configuration : un système avec cinq applications que tout le monde utilise vaut plus qu'un système avec vingt que personne ne fait confiance.

## Le tableau de bord, et pourquoi il est vide dessein

Les cartes colorées du premier écran sont la tentative d'Odoo de répondre à la question *à quoi dois-je regarder ?* avant que vous en sachiez assez pour la poser. Il y a une carte pour la vente, une pour les factures, une pour le stock, et chacune montre un nombre et un petit graphique.

Sur une nouvelle entreprise, chaque carte montre zéro, et les graphiques sont des lignes plates. Ce n'est pas un bug et ce n'est pas une mauvaise première impression ; c'est la seule chose honnête que le système pouvait afficher. Un tableau de bord qui aurait inventé un nombre plausible pour une entreprise vide serait un tableau de bord que l'on ne pourrait plus jamais faire confiance.

Les cartes deviennent utiles à des moments différents, et savoir lesquelles ignorer fait partie du premier mois.

**Vente** est utile dès le premier devis. Elle montre le pipeline en argent : devis envoyés, commandes confirmées, factures à établir.

**Facturation** est utile dès la première facture publiée, et c'est la carte que Maggie regardait chaque matin : combien est dû, combien est en retard.

**Inventory** est inutile tant que les produits existent et que le stock a été compté, ce qui est pourquoi le chapitre onze vient avant l'assistant.

**Comptabilité** est utile uniquement une fois le plan de comptes configuré et les premières écritures publiées.

Une entreprise qui tenterait de rendre les quatre cartes significatives dès la première semaine passera une quinzaine de jours en configuration et perdra son courage. Une entreprise qui en ignore trois et en rend une utile aura un système qui sera utile dici vendredi.

## La première personne qui n'est pas la propriétaire

Priya s'est connectée le deuxième après-midi, depuis son propre bureau, avec le compte que Maggie avait créé pour elle, et la première chose qu'elle a dite fut : « Où est tout ? »

L'écran qu'elle voyait n'était pas l'écran sur lequel Maggie regardait. Les menus étaient plus courts. Il n'y avait pas de *Paramètres*, pas d'*Utilisateurs*, pas de *Comptabilité* au-delà des factures qu'elle avait le droit de voir. Il y avait *Vente*, avec les devis et les commandes, et *Clients*, et une boîte de recherche.

C'est là tout le point d'un utilisateur, et ça vaut la peine de regarder quelqu'un le rencontrer pour la première fois. Pendant trente ans, Priya avait travaillé dans un système où tout le monde pouvait tout faire, parce que le système était un dossier partagé et un ensemble de fichiers. L'idée qu'un programme lui montrerait *moins*, dessein, a pris environ dix minutes pour cesser de paraître une insulte et commencer de paraître un soulagement.

「 Je ne peux rien casser », a-t-elle dite, à la fin de l'après-midi.

「 Tu peux casser un devis », a dit Maggie. « Tu ne peux pas casser le grand livre. »

Il y a un point plus profond dans cet échange, et c'est la raison pour laquelle les utilisateurs ont été configurés avant qu'aucune donnée n'ait été saisie. Dans un système où tout le monde peut tout faire, personne n'est responsable de rien : quand un prix est faux, c'est parce que quelqu'un, quelque part, l'a tapé. Dans un système où chaque personne a un rôle, le prix est faux parce que Priya l'a tapé—ce qui paraît plus sévère et est en fait plus aimable, parce que cela signifie que le prix peut être corrigé, et que la personne qui l'a corrigé peut être remerciée.

L'assistant, lorsqu'il est arrivé, s'est vu donner exactement le même traitement. C'est un utilisateur dans cette liste, avec un rôle, et il apparaît dans la piste d'audit comme tout le monde.

## La page qui vous dit quoi faire ensuite

Le premier écran après la connexion n'est pas le tableau de bord. C'est une page appelée *Premières étapes*, et c'est la chose la plus réflchie de toute l'application.

Elle liste cinq choses : choisir le pays de votre entreprise, configurer votre plan de comptes, ajouter vos produits, ajouter vos clients, et inviter vos collègues. Chacune est un lien, et chacune disparaît une fois faite. Quand les cinq sont faites, la page disparaît aussi.

Il y a un principe de conception dans tout ça, et ça vaut la peine de le nommer parce que la plupart des logiciels le ratent : **le système doit savoir ce qu'il ne sait pas encore.** Un tableau de bord qui montre des zéros est un tableau de bord qui ne vous dit rien. Une liste de contrôle qui dit *vous n'avez pas de clients* est une liste de contrôle qui vous dit exactement quoi faire ensuite, dans l'ordre qui a du sens.

L'ordre compte aussi. Le pays d'abord, parce qu'il décide le plan de comptes ; le plan de comptes avant les produits, parce que les produits ont besoin de comptes de revenus ; les produits avant les clients, parce qu'un devis a besoin des deux. Une entreprise qui commencerait par les clients—ce qui est l'instinct naturel, parce que les clients sont ce qu'une entreprise a pour objet—découvrirait en une heure qu'elle ne peut citer rien.

Maggie a fait les cinq étapes en un seul après-midi, dans l'ordre donné, et la seule qu'elle a ignorée fut *inviter vos collègues*, parce qu'elle voulait une journée pour faire ses propres erreurs avant que quiconque regarde.

Ça a été une bonne décision, et c'est le seul bout de conseil dans ce chapitre qui ne soit pas dans le logiciel.

---

À la fin de l'après-midi, la page paraissait différente. Il y avait des menus : *Vente*, *Achats*, *Inventory*, *Comptabilité*. Il y avait quatre utilisateurs. Il y avait une entreprise avec un nom, une devise et un pays. Il n'y avait encore aucune donnée—pas de clients, pas de produits, pas de factures—mais le système savait maintenant pour quel genre d'entreprise il travaillait, ce qui fait la différence entre une page blanche et un grand livre vide.

Doreen est venue à quatre heures et demie, comme convenu, et s'est assise devant lui.

Elle a regardé l'écran un moment sans rien dire. Puis elle a dit : « C'est très vide. »

「 L'est. »

「 Et ceci va en savoir plus sur cette entreprise que moi. »

Maggie attendait la question sous une forme ou une autre, et avait décidé de y répondre honnêtement.

「 Ceci va *se souvenir* de plus que toi, a-t-elle dite. Ce n'est pas pour en savoir plus. Il ne sait pas que l'officier des finances d'Ashfield s'appelle Carol, ou que la porte de l'école est verrouillée avant huit heures, ou que le gestionnaire là-b préfère un appel téléphonique à un courriel. Il ne sait pas que les classeurs bleus sont ceux qui se vendent, ou que le fournisseur de papier est peu fiable en août. Il sait ce que nous lui disons, et il n'oublie jamais ce qu'il a été dit. »

Doreen a considéré ceci.

「 Alors c'est moi celle qui le lui dit, a-t-elle dite.

「 C'est toi celle qui décide ce qui est vrai. C'est un travail différent de celui que tu avais lundi. »

Ça l'était, et ça lui a pris quelques semaines pour cesser de sentir que le système la surveillait. Mais elle fut la première à admettre, d'ici le printemps, que le grand livre era devenu un endroit où l'on pouvait *demander*—et que demander est un meilleur emploi du matin que de chercher.

Le lendemain matin, ils ont commencé par l'argent, parce que l'argent est là où commencent tous les débats d'une entreprise.
