# Annexe C — Quand quelque chose se passe mal

Cette annexe est organisée par symptôme, car c'est ainsi que les problèmes arrivent. Chaque entrée indique ce que vous verrez, ce que cela signifie généralement, et quoi faire. Les marques *observé* désignent des échecs survenus lors de la rédaction de ce livre, sur l'installation qui a produit ses captures d'écran ; ils ne sont pas hypothétiques.

Avant tout, une habitude. Quand quelque chose se passe mal, ne réinstallez pas. Lisez les vingt dernières lignes du journal, et regardez laquelle des trois boîtes sur le mouchoir est mécontente : la mémoire (la base de données), le modèle (l'ERP) ou l'assistant. Neuf fois sur dix, la réponse vous dit quoi faire, et réinstaller détruit les preuves.

---

## L'installateur s'arrête avec « psql was not found »

**Ce que vous voyez.** L'installateur signale que PostgreSQL n'est pas installé, tente `winget`, puis tente de télécharger l'installateur officiel directement, et s'arrête enfin avec un message indiquant que `psql` n'a pas été trouvé et que rien d'après cette étape ne fonctionnerait.

**Ce que cela signifie.** PostgreSQL n'est pas sur la machine. L'installateur a tenté de l'installer et n'y a pas réussi : soit `winget` n'a pas réussi à atteindre sa source, soit le téléchargement depuis le site du vendeur ne s'est pas terminé. Sur une connexion lente ou instable, c'est l'échec le plus courant de toute la procédure.

**Ce qu'il faire.** Relancez l'installateur. Il reprend là où il s'est arrêté et réutilise ce qui est déjà là ; un téléchargement partiel est repris plutôt que redémarré, donc chaque tentative avance plus loin que la précédente. Si vous êtes sur une connexion plus lente qu'environ un demi-mégabit par seconde, téléchargez l'installateur PostgreSQL vous-même, avec un navigateur, depuis le site du vendeur, et placez-le dans le dossier que l'installateur signale ; la prochaine exécution le trouvera et l'utilisera. Si vous préférez installer PostgreSQL à la main, toute version 16.x convient, et l'installateur le détectera à la prochaine exécution — y compris son port, qu'il lit dans le propre fichier de configuration du serveur.

*Observé lors de la rédaction de ce livre :* la première exécution a échoué exactement à ce point, après trois tentatives de téléchargement, sur une connexion tournant à environ soixante kilo-octets par seconde. La deuxième exécution a repris le fichier partiel et s'est terminée.

---

## « TCP port 5432 is already in use »

**Ce que vous voyez.** Tôt dans l'exécution, un avertissement indiquant que le port 5432 est pris et que PostgreSQL écoutera sur le 5433 à la place.

**Ce que cela signifie.** Quelque chose d'autre sur la machine utilise le port de base de données standard. Souvent, c'est une base de données à l'intérieur du Sous-système Windows pour Linux, transmise vers le côté Windows, ou un conteneur Docker.

**Ce qu'il faire.** Rien. L'installateur choisit le premier port libre et le fait traverser à toute la pile — le rôle de base de données, la base de données, l'ERP et le lanceur. Ce n'est pas une erreur ; c'est l'installateur faisant la bonne chose sur une machine occupée. Notez le port si vous prévoyez de vous connecter à la base de données avec d'autres outils.

---

## `winget` ne peut installer rien

**Ce que vous voyez.** Un message indiquant que `winget` s'est terminé avec une erreur de connexion, suivi par l'installateur recourant à un téléchargement direct.

**Ce que cela signifie.** La source du paquet n'a pas pu être atteinte. Les réseaux d'entreprise, les réseaux d'hôtel et certains produits antivirus interfèrent avec le Gestionnaire de paquets Windows.

**Ce qu'il faire.** Laissez le recours faire son travail. Si les deux routes échouent, installez le composant à la main (PostgreSQL et Python sont les seuls que l'installateur nécessite de l'extérieur), puis relancez l'installateur.

---

## La page qui s'ouvre n'est pas celle de connexion

**Ce que vous voyez.** Vous double-cliquez sur **AI Odoo**, ou vous ouvrez `http://localhost:8069`, et
le navigateur montre autre chose que la carte blanche de connexion : une page sur Odoo, un site web
avec un logo factice, ou une liste de bases de données.

**Ce que cela signifie.** L'adresse demandée n'est pas celle de votre ERP, ou c'est une adresse à
laquelle plusieurs choses peuvent répondre. Il y a exactement trois cas, et chacun a sa cause.

*C'est la documentation d'Odoo, sur odoo.com, dans la langue de votre navigateur.* C'est une page sur
le produit, pas sur votre machine : rien de ce qu'elle contient n'est vos données et elle ne fait pas
partie de l'installation. C'est ce qu'une version précédente de l'installateur ouvrait à la fin, et
elle est encore imprimée à la fin comme lien à lire plus tard. Fermez-la et ouvrez la page de
démarrage depuis l'icône.

*C'est un site web avec un logo que vous n'avez pas choisi, un menu et un lien « Se connecter » dans
un coin.* C'est l'application **website** d'Odoo : un module qui sert un site public à l'adresse
racine. Une fois installé, `http://localhost:8069` montre le site au lieu de la page de connexion, et
l'ERP se cache derrière le petit lien de connexion. Rien n'est cassé et aucune donnée n'est perdue. La
page de connexion a sa propre adresse, et elle fonctionne toujours :
`http://localhost:8069/web/login?db=odoo_agent`. La page de démarrage et l'icône utilisent cette
adresse pour cette raison.

*C'est une liste de bases de données, ou un formulaire qui demande quelle base vous voulez dire.* La
machine garde plus d'une base Odoo—une copie de test, une ancienne installation—et l'adresse n'en
nommait aucune. Ajoutez `?db=odoo_agent` à l'adresse, ou utilisez la page de démarrage, qui la nomme.

---

## L'identifiant et le mot de passe imprimés à la fin ne fonctionnent pas

**Ce que vous voyez.** Les identifiants du résumé de l'installateur sont refusés, et la page de
connexion dit que le nom d'utilisateur ou le mot de passe sont faux.

**Ce que cela signifie.** À une première installation, l'installateur crée l'administrateur et imprime
ce qu'il a créé, donc les deux coïncident. À une seconde exécution, le compte existe déjà et garde son
identifiant et son mot de passe : imprimer là un mot de passe fraîchement inventé serait imprimer un
mot de passe qui n'a jamais été appliqué. Maintenant l'installateur relit le compte dans la base et
dit soit le mot de passe qu'il a posé, soit que le mot de passe est inchangé depuis la première
installation.

**Que faire.** Si le résumé dit *inchangé*, utilisez le mot de passe de la première installation. S'il
est perdu, posez-en un nouveau exprès : relancez l'installateur avec `ADMIN_PASS` dans
l'environnement, et il appliquera et imprimera ce mot de passe. Rien d'autre dans la base n'est
touché.

---

## La fenêtre noire a disparu

**Ce que vous voyez.** Odoo répond encore dans le navigateur, mais il n'y a plus de fenêtre où taper.

**Ce que cela signifie.** La fenêtre noire *est* l'assistant : la fermer arrête l'assistant, et
seulement l'assistant. L'ERP tourne comme un programme séparé, et c'est pourquoi le navigateur
continue de fonctionner.

**Que faire.** Double-cliquez de nouveau sur **AI Odoo**. Il démarre ce qui manque et ne démarre pas
une seconde copie de ce qui tourne déjà.

---

## La page qui s'ouvre n'est pas celle de connexion

**Ce que vous voyez.** Vous double-cliquez sur **AI Odoo**, ou vous ouvrez `http://localhost:8069`, et
le navigateur montre autre chose que la carte blanche de connexion : une page sur Odoo, un site web
avec un logo factice, ou une liste de bases de données.

**Ce que cela signifie.** L'adresse demandée n'est pas celle de votre ERP, ou c'est une adresse à
laquelle plusieurs choses peuvent répondre. Il y a exactement trois cas, et chacun a sa cause.

*C'est la documentation d'Odoo, sur odoo.com, dans la langue de votre navigateur.* C'est une page sur
le produit, pas sur votre machine : rien de ce qu'elle contient n'est vos données et elle ne fait pas
partie de l'installation. C'est ce qu'une version précédente de l'installateur ouvrait à la fin, et
elle est encore imprimée à la fin comme lien à lire plus tard. Fermez-la et ouvrez la page de
démarrage depuis l'icône.

*C'est un site web avec un logo que vous n'avez pas choisi, un menu et un lien « Se connecter » dans
un coin.* C'est l'application **website** d'Odoo : un module qui sert un site public à l'adresse
racine. Une fois installé, `http://localhost:8069` montre le site au lieu de la page de connexion, et
l'ERP se cache derrière le petit lien de connexion. Rien n'est cassé et aucune donnée n'est perdue. La
page de connexion a sa propre adresse, et elle fonctionne toujours :
`http://localhost:8069/web/login?db=odoo_agent`. La page de démarrage et l'icône utilisent cette
adresse pour cette raison.

*C'est une liste de bases de données, ou un formulaire qui demande quelle base vous voulez dire.* La
machine garde plus d'une base Odoo—une copie de test, une ancienne installation—et l'adresse n'en
nommait aucune. Ajoutez `?db=odoo_agent` à l'adresse, ou utilisez la page de démarrage, qui la nomme.

---

## L'identifiant et le mot de passe imprimés à la fin ne fonctionnent pas

**Ce que vous voyez.** Les identifiants du résumé de l'installateur sont refusés, et la page de
connexion dit que le nom d'utilisateur ou le mot de passe sont faux.

**Ce que cela signifie.** À une première installation, l'installateur crée l'administrateur et imprime
ce qu'il a créé, donc les deux coïncident. À une seconde exécution, le compte existe déjà et garde son
identifiant et son mot de passe : imprimer là un mot de passe fraîchement inventé serait imprimer un
mot de passe qui n'a jamais été appliqué. Maintenant l'installateur relit le compte dans la base et
dit soit le mot de passe qu'il a posé, soit que le mot de passe est inchangé depuis la première
installation.

**Que faire.** Si le résumé dit *inchangé*, utilisez le mot de passe de la première installation. S'il
est perdu, posez-en un nouveau exprès : relancez l'installateur avec `ADMIN_PASS` dans
l'environnement, et il appliquera et imprimera ce mot de passe. Rien d'autre dans la base n'est
touché.

---

## La fenêtre noire a disparu

**Ce que vous voyez.** Odoo répond encore dans le navigateur, mais il n'y a plus de fenêtre où taper.

**Ce que cela signifie.** La fenêtre noire *est* l'assistant : la fermer arrête l'assistant, et
seulement l'assistant. L'ERP tourne comme un programme séparé, et c'est pourquoi le navigateur
continue de fonctionner.

**Que faire.** Double-cliquez de nouveau sur **AI Odoo**. Il démarre ce qui manque et ne démarre pas
une seconde copie de ce qui tourne déjà.

---

## L'ERP ne répond pas sur son port

**Ce que vous voyez.** Après l'installation, le navigateur ne peut pas atteindre l'adresse imprimée à la fin (le défaut est `http://localhost:8069`), ou le lanceur ouvre une page blanche.

**Ce que cela signifie.** Le processus ERP ne tourne pas, ou il a démarré puis s'est arrêté à cause d'une erreur dans son propre journal.

**Ce qu'il faire.** Ouvrez le fichier appelé `odoo.log` dans le dossier que l'installateur a créé (par défaut sous vos données d'application locales, dans `odoo-tool-stack`). Les dernières lignes disent pourquoi. Les trois causes courantes sont : le service de base de données ne tourne pas ; le mot de passe de la base de données dans la configuration ne correspond plus à la base de données ; et le port est pris par un autre programme. Les trois sont réparables sans réinstaller.

---

## L'assistant répond, mais ne peut pas trouver l'ERP

**Ce que vous voyez.** Vous demandez « liste les clients » et l'assistant répond qu'il ne peut pas se connecter, ou que la configuration est manquante.

**Ce que cela signifie.** Le connecteur de l'assistant n'a pas d'adresse, pas de clé, ou une clé que l'ERP n'accepte plus. Le connecteur lit ses paramètres depuis l'environnement ou depuis un petit fichier dans le dossier de données de l'assistant.

**Ce qu'il faire.** Vérifiez d'abord que l'ERP tourne et est atteignable dans un navigateur. Puis vérifiez la clé : dans l'ERP, ouvrez le menu utilisateur, allez à la page de sécurité du compte, et créez une nouvelle clé API. Collez-la dans la configuration du connecteur. Si vous avez changé le mot de passe de l'utilisateur ERP, les clés existantes survivent généralement ; si vous avez supprimé et recréé l'utilisateur, elles ne survivent pas.

---

## L'assistant crée un client en double

**Ce que vous voyez.** Deux clients appelés presque de la même façon : « Ashfield Academy » et « Ashfield Academy Ltd. »

**Ce que cela signifie.** L'assistant a été demandé de créer un client et a fait ce qu'on lui a dit. Il ne décide pas automatiquement qu'un nom similaire est la même entreprise, et il ne devrait pas : deux branches d'même organisation peuvent légitimement être deux enregistrements.

**Ce qu'il faire.** Formulez l'instruction pour chercher d'abord — « trouve le client Ashfield et ajoute un contact » — ou demandez à l'assistant de vous montrer les correspondances avant de créer quoi que ce soit. Quand un double apparaît, fusionnez ou archivez-le dans l'ERP plutôt que de le supprimer, afin que l'histoire des factures reste intacte.

---

## Un document ne peut pas être validé

**Ce que vous voyez.** L'ERP refuse de valider une facture, ou une livraison, et montre un message au sujet d'un compte manquant, d'un taxe manquant, ou d'une période qui est close.

**Ce que cela signifie.** Le modèle est incomplet. Un produit n'a pas de compte de revenus, ou l'entreprise n'a pas de taxe configurée, ou la période comptable a été verrouillée.

**Ce qu'il faire.** Lisez le message ; il nomme le champ. Réparez la configuration dans les paramètres de l'ERP, puis validez à nouveau. C'est l'ERP faisant son travail : il refuse d'écrire une écriture que Pacioli ne reconnaîtrait pas.

---

## Tout est lent

**Ce que vous voyez.** Les écrans prennent des secondes à charger ; l'assistant prend beaucoup de temps à répondre.

**Ce que cela signifie.** Deux choses différentes, souvent confondues. Si les écrans ERP sont lents, le problème est local : la base de données, le disque, ou la mémoire de la machine. Si seul l'assistant est lent, le problème est le modèle de langage — soit le service distant, soit le modèle local si vous en faites tourner un.

**Ce qu'il faire.** Regardez d'abord la mémoire et le disque de la machine. Puis regardez le journal de l'assistant : il enregistre combien de temps chaque requise a pris et quels outils ont été appelés. Une seule requise qui prend trente secondes parce qu'elle a fait douze appels d'outils n'est pas une faute ; c'est une requise qui aurait dû être formulée plus étroitement.

---

## Vous avez perdu le mot de passe administrateur

**Ce que cela signifie.** Le mot de passe imprimé à la fin de l'installation n'a pas été noté.

**Ce qu'il faire.** Sur une installation auto-hébergée, vous êtes le propriétaire de la machine, donc vous pouvez le réinitialiser depuis la base de données. Arrêtez l'ERP, connectez-vous à la base de données avec le propre compte administrateur de la base de données, et fixez un nouveau hachage de mot de passe pour l'utilisateur administrateur. La procédure est documentée dans la propre documentation de l'ERP sous « reset the administrator password », et elle prend deux minutes. Ne supprimez pas la base de données pour résoudre un problème de mot de passe.

---

## La seule règle

Quoi qui arrive, gardez deux choses : le fichier journal, et une copie de la base de données d'avant le changement. Avec ces deux-là, presque tout problème peut être diagnostiqué et la plupart peut être annulé. Sans eux, chaque problème devient un argument sur ce qui était autrefois vrai.
