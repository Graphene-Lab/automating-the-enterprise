# Annexe A — Installation de la pile, étape par étape

Cette annexe présente l'installation sans le récit : le même procédé que le chapitre sept, écrit sous forme de liste que vous pouvez suivre, le livre fermé. Elle suppose Windows 10 ou 11 ; la procédure sous Linux est le même script sous un autre nom, et l'installateur est conçu pour se comporter de façon identique.

## Avant de commencer

| Exigence | Pourquoi | Comment vérifier |
|---|---|---|
| Windows 10 ou 11, 64 bits | le moteur de base de données et l'assistant sont des programmes Windows | Paramètres → Système → À propos |
| Environ 12 Go de disque libre | base de données, source ERP, paquets Python, assistant | Explorateur de fichiers → Ce PC |
| Un compte administrateur | la base de données installe un service Windows | l'installateur le dit à la fin s'il manque le droit requis |
| Une connexion Internet | les composants sont téléchargés une seule fois | n'importe quel navigateur |
| Un nom d'entreprise | il apparaît sur vos documents | décidez-en maintenant |

Vous **n'**avez **pas** besoin : d'un mot de passe de base de données, d'un numéro de port, de .NET, de Git, de Docker, d'une installation de Python ou de quelconne connaissance de la ligne de commande.

## Étape 1 — Se procurer l'installateur

Téléchargez `install.bat` depuis la page des publications d'OdooTool et placez-le dans un dossier vide, par exemple `C:\Users\<vous>\Downloads\odoo-install\`.

Le fichier fait quelques kilo-octets. Il télécharge le reste de lui-même s'il en a besoin, de sorte qu'il fonctionne même lorsqu'il arrive seul.

## Étape 2 — L'exécuter

Double-cliquez sur `install.bat`. Une fenêtre de console s'ouvre, intitulée *Installateur OdooTool*.

Si Windows demande l'autorisation d'apporter des modifications, autorisez-le : la base de données doit enregistrer un service.

## Étape 3 — Répondre aux questions

Lors d'une exécution normale, l'installateur demande le **nom d'entreprise** et accepte la valeur par défaut suggérée pour le reste en appuyant sur Entrée. Lors d'une exécution non surveillée, les réponses peuvent être données à l'avance au moyen de variables d'environnement, et l'installateur ne demande rien du tout.

L'installateur imprime un titre appelé *Questions* avec les réponses qu'il va utiliser, de sorte que vous puissiez voir ce qu'il a décidé avant qu'il ne commence à travailler.

## Étape 4 — Suivre les quatre étapes

L'écran imprime un titre par étape. Chaque titre est suivi de lignes qui indiquent ce qui se produit ; rien n'a à être tapé.

1. **Espace libre.** Il refuse de commencer en dessous de douze gigabytes.
2. **Vérification de PostgreSQL, Python et Git.** Il rend compte de ce qu'il a trouvé et de ce qu'il va installer.
3. **Installation.** La partie longue : la base de données, le runtime Python si nécessaire, la source ERP, les paquets Python, la base de données elle-même, l'assistant, le connecteur.
4. **Résumé.** Adresses, identifiants et ce qui manque encore, s'il y a lieu.

Deux messages lors de l'étape 2 sont normaux et ne sont pas des défauts :

- *Le port TCP 5432 est déjà utilisé ; le nouveau PostgreSQL écoutera sur le 5433 à la place.* Quelque chose d'autre sur la machine détient le port standard. L'installateur choisit le port libre suivant et l'utilise partout.
- *PostgreSQL n'est pas installé. Il est installé maintenant avec le mot de passe du superutilisateur 'postgres' réglé sur 'odoo'.* Le mot de passe est attribué par l'installateur, est local à cette machine, et est imprimé à la fin. Rien n'a à être retenu ou recherché.

## Étape 5 — Si le téléchargement est lent

L'installateur de base de données fait environ 390 Mo et provient du site propre du vendeur. Sur une ligne lente, le téléchargement peut prendre une heure ou échouer. L'installateur conserve le fichier partiel et le reprend à l'exécution suivante, de sorte que **le relancer est la bonne réponse** — il continue là où il s'est arrêté et réutilise ce qui est déjà là.

Si la machine ne peut pas atteindre le vendeur du tout, téléchargez vous-même l'installateur de PostgreSQL 16 pour Windows depuis enterprisedb.com, laissez-le dans le dossier que l'installateur indique, et relancez `install.bat`. Il le trouvera et vérifiera sa taille avant de s'en servir.

## Étape 6 — Conserver le résumé

À la fin, la fenêtre imprime quelque chose comme ceci. Notez-le, ou photographiez l'écran.

```
  Odoo (l'ERP, dans le navigateur) :  http://localhost:8069
  Identifiant : admin@yourcompany.example
  Mot de passe : (celui que l'installateur a généré, ou celui que vous lui avez donné)
  Assistant (parlez-lui ici) :  http://localhost:5290/OfficeManager
```

Si le compte administrateur existait déjà depuis une exécution précédente, l'installateur imprime
l'identifiant qui se trouve réellement dans la base et dit que le mot de passe est inchangé, au lieu
d'en inventer un nouveau qui ne fonctionnerait pas.

Le navigateur ouvre la **page de démarrage** : un fichier sur cet ordinateur avec l'adresse, le compte
et un lien. Cette page est le début de la configuration, et non la fin de l'installation.

## Étape 7 — L'icône, et les trois fenêtres

Double-cliquez sur l'icône **AI Odoo** du bureau. Trois choses se produisent :

1. l'ERP démarre, s'il n'était pas en cours d'exécution ;
2. la page de démarrage s'ouvre dans le navigateur ;
3. l'assistant s'ouvre dans sa propre fenêtre noire.

*Ouvrir Odoo* sur la page de démarrage mène à la page de connexion sur
`http://localhost:8069/web/login?db=odoo_agent`. L'assistant est la fenêtre noire, et c'est là qu'on
tape ; il faut la laisser ouverte pendant que vous travaillez, car la fermer arrête l'assistant, alors
qu'Odoo continue de tourner.

À son premier démarrage, l'assistant demande le fournisseur d'IA : choisissez le service, collez la
clé, et il récupère la liste des modèles de ce service. Rien d'autre n'est nécessaire — l'adresse de
l'ERP et la clé d'accès ont été écrites par l'installateur.

## Étape 8 — Vérifier que cela fonctionne

Trois vérifications, dans l'ordre, et chacune vous indique laquelle des trois machines est mécontente
si elle échoue.

1. **L'ERP.** Cliquez sur *Ouvrir Odoo* sur la page de démarrage, ou ouvrez
   `http://localhost:8069/web/login?db=odoo_agent` dans un navigateur, et connectez-vous. Si la page
   ne se charge pas, l'ERP ou la base de données n'est pas en cours d'exécution ; le fichier
   `odoo.log` dans le dossier d'installation explique pourquoi.
2. **Le connecteur.** Dans l'assistant, demandez : *vérifiez la connexion à Odoo et dites-moi quelle
   version est en cours d'exécution.* Un numéro de version signifie que la clé et l'adresse sont
   justes.
3. **Le modèle.** Demandez : *combien de clients avons-nous ?* Un nombre signifie que l'assistant peut
   lire les données de l'ERP en tant qu'utilisateur, avec les permissions de cet utilisateur.

Si les trois répondent, l'installation est complète.

## Désinstallation

Deux scripts annulent l'installation, et c'est la manière prise en charge : `uninstall.bat` sous
Windows et `uninstall.sh` sous Linux. Ils se trouvent à côté de l'installateur dans la même version,
et chacun peut être téléchargé et exécuté seul.

Ce qu'ils suppriment :

- la base de données Odoo, avec chaque client, produit, commande, facture et mouvement de stock ;
- le dossier d'installation (`%LOCALAPPDATA%\odoo-tool-stack`, ou `~/odoo-tool-stack`) ;
- les raccourcis **AI Odoo** et la règle de pare-feu.

Ils demandent deux fois, et la seconde question n'est pas une formalité. La première est un oui/non qui
énumère ce qui disparaît. La seconde exige la phrase **DESTROY ALL**, tapée en majuscules. Si la
phrase n'est pas exacte, rien n'est touché—pas un fichier, pas une ligne. La suppression est
irréversible et le désinstalleur ne fait aucune sauvegarde : une copie de la base prise avant est le
seul chemin de retour.

AgentBridge est demandé à part, parce qu'il peut héberger d'autres outils et garde ses propres
réglages et clés d'API : répondre *non* le conserve et ne retire que la moitié Odoo.

PostgreSQL reste installé. C'est un service que d'autres programmes peuvent partager, et il se retire
dans *Applications et fonctionnalités* comme n'importe quel programme, quand plus rien n'en a besoin.
Le rôle de base `odoo` reste et il est inoffensif : une future installation le réutilise.
