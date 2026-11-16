# 8. Ce qui s'est passé pendant que le bar bougeait

L'installation a pris quarante minutes, dont la plupart ont été consacrées à regarder un écran qui ne changeait pas.

Ce chapitre explique ce qui s'est passé pendant ces quarante minutes, pour quelqu'un qui n'aura jamais besoin de le faire à la main mais qui mérite de savoir ce qui tourne désormais sur la machine—car un système que vous ne comprenez pas est un système que vous ne pouvez pas faire confiance, et un système que vous ne pouvez pas faire confiance est un système que vous abandonnerez en mars.

Il y a cinq choses à expliquer : la base de données, l'environnement Python, l'ERP, le connecteur et l'assistant. Ils vivent dans un seul dossier, et connaître ce dossier, c'est connaître l'installation.

---

## Le dossier

Tout ce que l'installateur crée va en un seul endroit :

```
%LOCALAPPDATA%\odoo-tool-stack
```

Sur une machine Windows typique, c'est `C:\Users\<vous>\AppData\Local\odoo-tool-stack`. À l'intérieur, quatre sous-dossiers, un par composant, plus les fichiers journaux. Rien n'est éparpillé sur le disque, aucun fichier n'est placé dans `Windows`, et rien n'est enregistré sauf le service de base de données et deux raccourcis.

C'est une décision de design délibérée et elle a une conséquence pratique énorme : **désinstaller, c'est supprimer un dossier.** Une entreprise qui essaie le système en janvier et l'abandonne en février ne laisse pas de fossile dans la machine pour les cinq prochaines années. Elle supprime un répertoire et désinstalle la base de données.

Les données propres à l'utilisateur—les paramètres de l'assistant, ses conversations, la configuration du connecteur—vivent séparément, dans `%LOCALAPPDATA%\agent`, de façon à ce que la mise à jour ou la réinstallation de la pile ne les détruise pas.

## La base de données

PostgreSQL est installé de la façon dont PostgreSQL est destiné à être installé sur Windows : comme un service, avec un répertoire de données qui lui appartient, à l'écoute sur un port. Le service signifie qu'il démarre avec la machine et fonctionne sans qu'on se connecte ; le répertoire de données signifie que la mémoire de l'entreprise est un ensemble de fichiers situés dans un endroit connu, ce qui rend une sauvegarde possible.

L'installateur a choisi le port. Il voulait le 5432, l'a trouvé pris par la base de données à l'intérieur du Sous-système Windows pour Linux, et a pris le 5433. Puis il a fait trois choses qu'une personne devrait sinon faire à la main :

1. Il a créé un utilisateur de base de données appelé `odoo`, avec un mot de passe, de façon que l'ERP ne se connecte jamais en tant qu'utilisateur super. C'est la différence entre donner à le comptable une clé du bureau et lui donner la clé maîtresse de l'immeuble.
2. Il a créé une base de données appelée `odoo`, appartenant à cet utilisateur.
3. Il a écrit le port et les identifiants dans le fichier de configuration de l'ERP.

Le mot de passe de l'utilisateur super est `odoo` sauf si la personne qui installe a choisi autrement, et l'installateur le imprime dans le résumé. C'est un compte local. Il n'a rien à voir avec quel que ce soit sur internet, et c'est le mot de passe dont vous aurez besoin si un jour vous devez restaurer une sauvegarde à la main.

## L'environnement Python

Odoo est écrit en Python, et les programmes Python ont besoin de bibliothèques. L'installateur crée un environnement isolé—une *virtual environment*—à l'intérieur du dossier de la pile, et y installe exactement les bibliothèques dont Odoo a besoin, aux versions qu'Odoo attend.

Le mot « isolé » fait ici un vrai travail. Sans lui, l'installation d'Odoo modifierait le Python que les autres programmes de la machine utilisent, et un jour quelque chose d'étranger au sujet cesserait de fonctionner. Avec lui, la pile porte son propre Python et ne peut rien casser en dehors de son dossier.

Si la machine n'avait aucun Python utilisable, l'installateur en installait un d'abord—et il vérifiait en le lançant, pas en le cherchant, car sur une machine Windows moderne la commande `python` est souvent une publicité pour le Microsoft Store plutôt qu'un programme.

## L'ERP

Odoo lui-même est un dossier de source Python et un large ensemble de modules. L'installateur a récupéré la version en cours d'installation, a créé le schéma de base de données, et a chargé les modules de base—ceux qui fournissent le modèle d'une entreprise : les partenaires, les produits, les documents, le grand livre, l'interface web.

C'est l'étape qui prend le plus de temps et qui ressemble le plus à rien qui se passe. Une base de données est en train de se construire : des centaines de tables, des milliers de règles, le plan comptable d'une entreprise générique, les taxes d'un pays générique, les menus d'un utilisateur générique. Quand elle termine, l'ERP est un programme fonctionnel qui sait comment être une entreprise mais ne sait pas encore quelle entreprise c'est. C'est pour ça que la page des premiers pas existe.

## Le connecteur

Le connecteur est le petit programme qui traduit entre l'assistant et l'ERP. Il est installé comme un plugin—un dossier de fichiers que l'assistant charge au démarrage—et il est configuré avec deux faits : l'adresse de l'ERP (`http://localhost:8069`) et une clé.

La clé est générée pendant l'installation et écrite dans la configuration du connecteur. C'est une clé d'API Odoo : un identifiant qui appartient à un utilisateur, qui peut être révoqué sans changer le mot de passe de cet utilisateur, et qui porte les permissions de cet utilisateur. Quand l'assistant demande à Odoo de créer une facture, c'est cette clé qui voyage avec la requête, et Odoo la vérifie exactement comme il vérifierait la connexion d'une personne.

C'est la partie de l'architecture qu'un auditeur d'entreprise posera, et la réponse est rassurante : l'assistant est un *utilisateur*. Il apparaît dans la liste des utilisateurs de l'ERP. Il a un rôle. Enregistrements qu'il crée sont tous estampillés de son nom. On peut le désactiver en un clic, et la piste d'audit montrera toujours ce qu'il a fait.

## L'assistant

L'assistant arrive en tant que version publique : un exécutable, un dossier de outils, et le client de chat de bureau. L'installateur le décompacte, installe le connecteur en lui, et crée le raccourci **AI Odoo**.

Le raccourci est la pièce qui fait sentir au système qu'il est un produit plutôt qu'un projet scientifique. Double-cliquer dessus démarre l'ERP s'il ne tourne pas, ouvre la page de l'ERP dans le navigateur, et ouvre l'assistant dans une fenêtre de terminal. Une icône, trois fenêtres, et le travail peut commencer.

La configuration propre à l'assistant—quel fournisseur d'IA, quel modèle, quelle clé—est demandée à son premier démarrage, par l'assistant lui-même, dans la même fenêtre de terminal où vous taperez vos instructions. C'est un bon endroit pour demander, car c'est le seul endroit où la clé peut réellement être testée : l'assistant récupère la liste des modèles du fournisseur avec la clé que vous avez collée, et si la liste revient, la clé fonctionne.

---

## Ce qui aurait pu mal tourner

Tout ce qui précède a fonctionné à la deuxième tentative. Il vaut la peine de lister ce qui a mal tourné à la première, car chaque élément est un endroit où une entreprise installant ceci pour de vrai perdra un après-midi, et chacun a été corrigé plutôt que documenté comme un problème connu.

**Le téléchargement qui redémarrait.** Décrit dans le chapitre précédent : l'installateur supprimait son téléchargement partiel avant chaque nouvelle tentative, donc une ligne lente signifiait trois échecs au lieu d'un seul succès lent. Corrigé en gardant le fichier partiel, en le nommant d'après sa version, et en le reprenant.

**Une liste de versions qui périt.** L'installateur connaissait les noms de fichiers de trois builds récents de PostgreSQL. Le vendeur en avait publié une quatrième, qui n'était pas sur la liste. Un installateur dans six mois aurait heurté une liste de fichiers qui n'existent plus. Corrigé en ajoutant le build actuel et en faisant dire exactement au message d'échec quel fichier récupérer à la main.

**Le message du gestionnaire de paquets dans la langue de la machine.** Quand `winget` échoue, il explique pourquoi dans la langue de Windows. L'installateur répétait les deux cents derniers caractères de cette explication, et sur une console dont la page de codes n'est pas de l'UTF-8, les lettres accentuées arrivaient en pagaille—donc l'écran montrait un fragment d'italien, haché, au milieu d'une installation en anglais. Corrigé deux fois : la console est désormais réglée en UTF-8, et l'installateur ne répète plus du tout le texte du gestionnaire de paquets. Le code de sortie est le fait ; la ligne suivante dit ce qui se passe à la place.

**Le silence pendant l'installation de la base de données.** L'installateur de la base de données lui-même tourne sans sortie, donc l'écran reste immobile pendant plusieurs minutes. Celle-ci n'est pas corrigée, car la correction consisterait à inventer une barre de progression qui ment. Elle est documentée à la place, ici et dans l'annexe : si l'écran n'a pas changé depuis cinq minutes, regardez le dossier `C:\Program Files\PostgreSQL`—s'il grandit, l'installation fonctionne.

Aucun de ceux-là n'est dramatique. Ensemble, ils font la différence entre une procédure qu'une personne non technique peut terminer sur une mauvaise connexion et une qui se termine par un ticket de support.

---

## Les deux fichiers qui valent la peine d'être compris

À l'intérieur du dossier du connecteur il y a deux petits fichiers, et ce sont les seuls qu'une entreprise est susceptible de toucher.

**`odoo.json`** contient l'adresse de l'ERP, le nom de la base de données et la clé. Ce sont quatre lignes de texte. Si l'ERP passe sur un autre port, c'est ce fichier qui change ; si la clé est révoquée, c'est ce fichier qui reçoit la nouvelle.

**`toolset.json`** contient la liste des outils que l'assistant a le droit d'utiliser. C'est le fichier qui décide si l'assistant peut toucher un fichier, naviguer sur le web, ou seulement parler à l'ERP. C'est le réglage de sécurité le plus important de toute l'installation, et c'est une seule ligne de texte.

La première semaine de Riverton a produit une leçon à propos de ce second fichier qui vaut la peine d'être racontée, car c'est le genre de chose qu'aucun manuel ne prévoit.

L'installateur avait activé quatre outils : le connecteur ERP, un outil fichier, un outil web et un outil de contrôle de versions. C'est un défaut raisonnable pour un assistant à usage général. Mais la première instruction que l'entreprise a donnée—*créer un client appelé Ashfield Academy, Mill Lane, Ashfield*—a été répondue par l'assistant allant chercher l'adresse sur le web, car un outil web était disponible et une adresse est une chose qu'on recherche.

Ce n'était pas exactement faux. C'était peu utile, c'était lent, et ça utilisait un outil que l'entreprise n'avait pas pensé. La correction a pris une seule ligne : le jeu d'outils a été réduit au connecteur et à l'outil fichier, et l'assistant a cessé de naviguer et a commencé à demander à l'ERP.

C'est une décision de design que chaque entreprise doit prendre, et le défaut devrait être le plus étroit. Un assistant avec un outil dont il n'a pas besoin est un assistant qui finira par l'utiliser, au pire moment possible, pour une raison qui a paru sensée à un modèle de langage.

Il y a une meilleure réponse que l'étreinte de la liste, pourtant, et c'est celle que ce livre recommande.

Un modèle de langage choisit un outil en lisant ce que l'outil dit servir à. Si le connecteur ERP se décrit comme *requêter et gérer les données de l'ERP Odoo* et rien de plus, alors une instruction contenant les mots « client » et « adresse » est un bon appariement pour une recherche web—une adresse est, après tout, une chose qu'on recherche. Le modèle n'est pas bête ; il est littéral à propos de deux descriptions également plausibles.

La correction est une seule phrase dans la description de l'outil lui-même, à l'endroit où le modèle lit réellement : *cet outil est le système de référence de l'entreprise : pour toute question ou action concernant les clients, les fournisseurs, les produits, les prix, les ventes, les achats, les factures, les paiements ou le stock, utilisez ces méthodes plutôt qu'une recherche web, un fichier ou des connaissances générales ; recherchez d'abord ici un enregistrement nommé, et dites-le quand il n'y est pas.*

Cette phrase a été ajoutée, les quatre outils ont été remis, et le comportement a changé : la même installation, avec l'outil fichier, l'outil web et l'outil de contrôle de versions tous activés, répond désormais « combien de clients avons-nous » depuis l'ERP, en une seconde, avec le critère qu'il a utilisé et les enregistrements derrière le nombre.

Deux leçons, et elles point en directions opposées.

**Pour l'entreprise :** ne pas résoudre un problème de routage en retirant des outils. Un vrai bureau a besoin du web, des fichiers et de l'ERP à la fois ; un assistant qui a été mutilé pour bien se comporter est un assistant qui échouera le jour où le travail aura besoin de l'outil que vous avez retiré.

**Pour qui que ce soit qui écrit l'outil :** la description est l'interface. Elle est lue par le modèle à chaque tour, elle ne coûte rien, et une seule phrase sur *quand utiliser ceci et quand ne pas l'utiliser* vaut plus que n'importe quelle quantité de génie d'instruction dans la commande. Les règles qui comptent appartiennent au résumé de l'outil, en courtes lignes impératives—pas dans un manuel, et pas dans une remarque que le modèle ne voit jamais.

## La forme de la chose

Quand l'installateur a terminé, Riverton avait cinq programmes là où elle avait autrefois un classeur.

Une base de données, qui se souvient. Un ERP, qui sait ce que les faits signifient. Un environnement Python, qui fait tourner l'ERP. Un connecteur, qui traduit. Un assistant, qui agit. Et un dossier, qui contient tout cela et peut être supprimé.

Maggie a écrit le chemin du dossier sur la feuille de papier, sous le mot de passe, et l'a regardé un moment. C'était une sensation étrange, d'avoir remplacé trente-et-ans de papier par un répertoire dans son profil utilisateur—comme si la mémoire de l'entreprise era venue une chose qui pouvait être copiée sur une clé mémoire en quatre minutes.

Ça pouvait, en fait, être copiée sur une clé mémoire en quatre minutes. C'est ce qu'est une sauvegarde, et c'est le sujet d'une conversation qu'elle aurait avec Sam trois semaines plus tard, après la première alerte.

Mais avant les sauvegardes, avant les factures, avant n'importe quel travail, il y avait une page dans le navigateur demandant quelle devise l'entreprise utilise.

---

## La première alerte, et ce qu'est réellement une sauvegarde

L'alerte est venue un jeudi, trois semaines plus tard, et ce n'était pas un crash.

Maggie avait demandé à l'assistant une question—combien avons-nous facturé le mois dernier ?—et la réponse était plus petite qu'elle ne s'y attendait. Pas exactement fausse : plus petite. Elle a vérifié la liste des factures, et il y avait moins de factures qu'elle ne s'en souvenait avoir approuvées.

La cause, quand Sam l'a trouvée, était innocente : Doreen expérimentait avec un filtre dans la liste des factures, et le filtre era resté activé. L'assistant a répondu à la question qu'on lui avait posée, contre la liste qu'on lui avait donnée, et la liste était filtrée. Rien n'avait été supprimé. Rien n'avait été perdu.

Mais pendant vingt minutes, Maggie a cru que trois semaines de facturation avaient disparu, et la sensation de ces vingt minutes est ce dont cette section parle. Parce que la deuxième question qu'elle a posée, avant de demander quoi que ce soit à Sam, était : *avons-nous une sauvegarde ?*

La réponse, ce jour-là, était : pas vraiment. Il y avait une copie du dossier du jour de l'installation, faite par l'installateur lui-même, et rien depuis.

Ce qu'est une sauvegarde, dans un système comme celui-ci, ce sont trois choses et pas une.

**La base de données.** Un dump de tout ce que l'ERP sait, pris avec l'outil propre de la base de données, sur un calendrier. C'est un seul fichier, on peut le restaurer dans une installation vide, et c'est la seule copie qui compte pour le grand livre.

**Le dossier.** La source de l'ERP, la configuration, les paramètres de l'assistant, la clé du connecteur. Petit, et fastidieux à recréer à la main, ce qui est exactement pourquoi ça vaut la peine d'être copié.

**Le contrôle.** Une fois par mois, restaurer la sauvegarde dans une installation de test et la regarder. Une sauvegarde qui n'a jamais été restaurée est un fichier avec un nom plein d'espoir. La règle de Sam—*une sauvegarde non vérifiée est un vœu*—vient d'avoir vu une entreprise découvrir, au pire moment possible, que son travail nocturne écrivait sur un disque qui était plein.

Les outils pour les trois sont dans le dossier de la pile : un script qui dump la base de données, un dossier à copier, et un document avec les quatre commandes pour restaurer. La version de Riverton tourne à deux heures du matin, garde trente jours, et écrit dans un dossier que OneDrive synchronise. Ça a pris une heure à Sam pour le mettre en place et c'est, de loin, l'assurance la moins chère que l'entreprise ait jamais achetée.
