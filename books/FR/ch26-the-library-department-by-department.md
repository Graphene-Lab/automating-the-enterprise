# 26. La bibliothèque, département par département

Ce chapitre est une liste, et il est destiné à être utilisé plutôt que lu.

Chaque instruction ci-dessous a été exécutée sur l'installation décrite dans ce livre, contre une entreprise
avec des clients, des produits, des stocks, des commandes et des factures. Le résultat est noté là où il
n'est pas évident, et celles qui ont échoué à la première tentative sont marquées, avec ce qui a dû changer—car une
bibliothèque de prompts qui ne contient que ceux qui ont fonctionné est une bibliothèque de mensonges.

Adaptez les noms. Les produits de Riverton sont des classeurs et du papier; les vôtres ne le sont pas. La *forme* de chaque
instruction est ce qui vaut la peine d'être copié : un verbe, un objet, une étendue, et une contrainte.

---

## Clients

**1.** *Combien de clients avons-nous, et combien d'entre eux ont passé commande au cours des quatre-vingt-dix derniers jours ?* — Deux nombres, et le second est celui qui compte. Une liste de clients qui ne fait que croître est une
liste de personnes qui ont cessé d'acheter.

**2.** *Trouvez le client appelé Ashfield Academy et montrez-moi leur adresse, leur numéro de téléphone et leurs conditions de paiement.* — La première chose que fait quiconque au téléphone. Elle a remplacé trois écrets et une recherche.

**3.** *Créez un nouveau client appelé Northgate Library Service, 14 Mill Lane, Northgate, avec les mêmes conditions de paiement que Ashfield Academy.* — *Identiques à* est la partie utile : elle copie une configuration réelle plutôt qu'une devinée.

**4.** *Quels clients n'ont commandé quoi que ce soit au cours des six derniers mois, et quelle fut leur dernière commande ?* — La liste qui a sauvé le centre jardinier au chapitre vingt.

**5.** *Ajoutez un second contact à Ashfield Academy : Carol Whitfield, bureau des finances, et faites-en le contact facturé.* — Une petite instruction qui exigeait autrefois de savoir où se trouvaient les contacts dans le menu.

**6.** *Montrez-moi les dix clients ayant le montant facturé total le plus élevé cette année.* — Un classement, avec les nombres derrière.

## Ventes

**7.** *Créez un devis pour Ashfield Academy pour 400 classeurs et 20 boîtes de marqueurs pour tableau blanc, aux prix standards.* — Le premier vrai morceau de travail, au chapitre quatorze.

**8.** *Montrez-moi le devis que j'ai créé pour Ashfield Academy aujourd'hui, avec ses lignes et son total.* — Le contrôle. Demandez toujours le contrôle.

**9.** *Confirmez le devis Ashfield Academy et dites-moi le numéro de commande de vente.* — La transition de la proposition à la promesse.

**10.** *Créez un devis pour Northgate Library Service pour 12 boîtes de papier A4 et 6 paquets de stylos, livraison lundi prochain.* — *Lundi prochain* est interprété et repris sous forme de date, ce qui est comment vous découvrez que la machine et vous désaccordez sur quel lundi.

**11.** *Quel est le valeur totale de tous les devis encore ouverts, et pour qui sont-ils ?* — Le pipeline, sans module CRM.

**12.** *Quels produits avons-nous vendus le plus en nombre le mois dernier, par quantité ?* — Le rapport utile le plus simple dans n'importe quelle entreprise de gros.

**13.** *Changez la date de livraison sur la commande Ashfield Academy ouverte jusqu'à la fin du mois.* — Un changement à un document confirmé, que l'ERP n'autorise que tant qu'elle n'est pas encore livrée.

**14.** *Annulez le devis pour Northgate Library Service et dites-moi dans quel état elle est maintenant.* — *Dans quel état est-elle maintenant* est la vérification, et c'est ce qui rend une annulation sûre.

## Facturation

**15.** *Créez une facture depuis la commande de vente Ashfield Academy confirmée.* — Le lien entre la commande et la facture, qui est la raison entière de l'existence d'un ERP.

**16.** *Comptabilisez la facture Ashfield Academy et dites-moi son numéro et son total.* — La comptabilisation, le moment où le grand livre change.

**17.** *Quelles factures sont impayées et âgées de plus de trente jours ? Montrez-moi le client, le numéro de facture, la date et le montant restant dû.* — Le rapport de vieillissement, en une phrase.

**18.** *Enregistrez un paiement du montant intégral contre la facture Ashfield Academy, daté d'aujourd'hui, par virement bancaire.*

**19.** *Montrez-moi l'état de paiement de chaque facture pour Northgate Library Service.* — Un relevé client, sans en générer un.

**20.** *Créez un avoir pour Ashfield Academy pour 20 classeurs qui ont été retournés endommagés, et comptabilisez-le.* — La correction qui ne récrit pas l'histoire.

**21.** *Combien d'argent est dû au total, et combien d'entre est en retard ?* — Les deux nombres qu'un propriétaire d'entreprise regarde en premier.

**22.** *Envoyez un rappel de paiement poli à chaque client ayant une facture plus de quinze jours en retard.* — À Riverton, cela produit des brouillons, pas des emails : l'envoi est une décision de personne. L'instruction fonctionne des deux manières; c'est la configuration qui décide laquelle.

## Entrepôt

**23.** *Combien de classeurs avons-nous en stock en ce moment, et où sont-ils ?* — La question qui a fait croire à Tom au système.

**24.** *Quels produits sont en dessous de leur point de réapprovisionnement ?* — La liste qui devient une commande d'achat.

**25.** *Confirmez la livraison de la commande Ashfield Academy et dites-moi quels mouvements de stock elle a créés.* — Les mouvements sont la preuve que le stock est parti.

**26.** *Enregistrez un ajustement de stock de moins 5 boîtes de marqueurs pour tableau blanc, raison : endommagés dans la pluie.* — La raison n'est pas optionnelle; c'est ce qui rend l'ajustement vérifiable.

**27.** *Quel est le valeur totale du stock dans l'entrepôt au coût ?* — Un nombre que la plupart des petites entreprises ne peuvent produire, et qui change la façon dont elles achètent.

**28.** *Montrez-moi chaque mouvement de stock pour les classeurs au cours des trente derniers jours.* — L'audit d'un seul produit, ce qui est comment une divergence s'explique.

**29.** *Quels produits n'ont bougé du tout au cours de l'année dernière ?* — Le stock mort, qui est de l'argent endormi.

## Achats

**30.** *Créez une commande d'achat pour 500 classeurs de notre fournisseur habituel, au dernier prix payé.* — *Dernier prix payé* est un fait de l'histoire, pas une liste.

**31.** *Confirmez la commande d'achat et dites-moi quand les marchandises sont attendues.* — La confirmation crée la réception prévue, ce qui est ce qui rend la prochaine livraison responsable.

**32.** *Récevez les marchandises pour la commande d'achat et montrez-moi le stock qu'elles ont ajouté.*

**33.** *Créez la facture fournisseur pour cette commande d'achat et comptabilisez-la.* — La troisième jambe du contrôle en trois voies.

**34.** *Quels fournisseurs ont relevé leurs prix au cours des six derniers mois, et de combien ?* — La question qui a trouvé les frais de palette au chapitre dix-neuf.

**35.** *Combien devons-nous à chaque fournisseur en ce moment ?* — Le miroir du rapport de vieillissement.

**36.** *Quelles commandes d'achat sont en retard, et de combien de jours ?* — Les fournisseurs en retard sont un problème d'achats, pas un problème d'entrepôt, et la distinction compte.

## Comptabilité

**37.** *Montrez-moi le bilan de vérification pour ce mois.* — Le rapport le plus ancien en comptabilité, produit en une seconde.

**38.** *Quel est le solde du compte bancaire aujourd'hui, selon les livres ?* — *Selon les livres* est le qualifiant honnête : la banque et les livres s'accordent après réconciliation, pas avant.

**39.** *Montrez-moi chaque écriture comptable comptabilisée au cours des sept derniers jours, avec le document dont elles viennent.* — La trace d'un nombre jusqu'à un document.

**40.** *Quel est notre chiffre d'affaires pour ce mois jusqu'à présent, et comment se compare-t-il au mois dernier ?*

**41.** *Listez les taxes configurées pour cette entreprise et le taux de chacune.* — Le contrôle qui empêche qu'un quatrième taux de TVA soit inventé au comptoir.

**42.** *Quels comptes de charges n'ont aucune activité cette année ?* — Soit un plan de comptes trop gros, soit une charge qui a été comptabilisée ailleurs. Les deux valent la peine d'être connus.

## Rapports

**43.** *Donnez-moi un résumé d'une page de l'entreprise cette semaine : ventes, factures, argent en retard, alertes de stock.* — La liste du lundi, à la demande.

**44.** *Quels cinq produits ont le meilleure marge, et quels cinq ont la pire ?* — Le rapport qui change une liste de prix.

**45.** *Montrez-moi les ventes par mois pour cette année, sous forme de tableau.*

**46.** *Quel vendeur a facturé le plus ce trimestre ?* — Seulement significatif si les factures portent un vendeur, ce qui est une décision de configuration prise à la première semaine.

**47.** *Quel pourcentage de nos factures sont payées en retard, et quel est le délai moyen ?* — La mesure qui a transformé le « on est payé in fine » de Riverton en douze jours de chiffre d'affaires.

**48.** *Comparez le nombre de commandes ce mois avec le même mois l'année dernière.*

**49.** *Quels clients nous doivent de l'argent et ont aussi cessé de commander ? C'est la liste de risque.* — L'instruction qui a sauvé le centre jardinier. Nommer la liste dans l'instruction—*c'est la liste de risque*—dit à l'assistant ce pour quoi la liste sert, et la réponse revient annotée.

## Entretien

**50.** *Trouvez n'importe quels clients en double avec le même nom et montrez-les à moi.* — Montrez, ne fusionnez pas. Une machine ne devrait pas décider lequel de deux fichiers est réel.

**51.** *Quels produits n'ont pas de prix fixé ?* — L'erreur qui arrête un devis.

**52.** *Listez les produits dont le nom ne correspond pas à leur référence interne.* — Un petit contrôle de cohérence qui attrape des années de négligence accumulée.

**53.** *Y a-t-il des devis plus vieux que quatre-vingt-dix jours qui sont encore ouverts ? Archivez-les.*

**54.** *Vérifiez la connexion à Odoo et dites-moi quelle version tourne.* — La première instruction que quiconque devrait taper, sur n'importe quelle installation, jamais.

## Travail récurrent

**55.** *Chaque lundi à huit heures, envoyez-moi une liste de factures qui sont devenues en retard la semaine précédente.*

**56.** *Chaque vendredi après-midi, dites-moi quels produits sont descendus en dessous de leur point de réapprovisionnement pendant la semaine, et proposez les commandes d'achat en brouillon.*

**57.** *Le premier jour ouvrable du mois, produisez le résumé des ventes du mois précédent par client.*

**58.** *Chaque matin, vérifiez la connexion à Odoo et dites-moi si quelque chose ne va pas.* — Utile seulement si la réponse est silencieuse quand tout est bon; un « tout est bon » quotidien entraîne les gens à ignorer les messages.

**59.** *Chaque jeudi, listez les commandes d'achat qui sont en retard et les fournisseurs qui sont responsables.*

---

## Comment utiliser cette liste dans la première semaine

Un lecteur qui essaie de travailler ce chapitre dans l'ordre échouera, et il vaut la peine de dire pourquoi.

Les instructions supposent une entreprise avec des données à l'intérieur : clients, produits, stock, commandes. Sur une installation fraîche, la plupart d'entre elles ne renvoient rien, ce qui est correct et démoralisant. L'ordre qui fonctionne est l'ordre suivi par le livre : créez un client, créez un produit, mettez du stock sur une étagère, faites un devis, confirmez-le, livrez-le, facturez-le, comptabilisez-le, payez-le. Après cela, chaque instruction de ce chapitre a quelque chose sur quoi travailler.

La deuxième semaine est celle où la liste devient utile : choisissez un département, lisez ses instructions, et essayez celles qui décrivent le travail que vous faites chaque semaine. Écartez le reste. Une entreprise n'a pas besoin d'une bibliothèque de cinquante-neuf instructions; elle a besoin des huit qu'elle utilise réellement, écrites, dans ses propres mots.

La troisième semaine est celle où l'entreprise écrit la sienne. C'est le moment où la technologie a cessé d'être quelque chose qui a été installé et est devenu quelque chose qui est utilisé—et le test est simple : la liste contient-elle une instruction qui n'est pas dans ce chapitre ? Si elle le fait, le bureau a commencé à penser dans la langue du système, ce qui est le seul résultat durable de tout ceci.

## Celles qui ont nécessité une deuxième tentative

Quatre instructions ont échoué à la première tentative pendant les tests derrière ce livre, et chaque échec vaut la peine d'être enregistré car c'est le même type d'échec.

**« Montrez-moi les produits que nous n'avons jamais vendus. »** — Ambigu, comme le chapitre treize le décrit : pas de ligne de commande de vente, ou pas de mouvement de quel que ce soit ? La version corrigée nomme le test : *produits sans ligne de commande de vente et sans livraison directe au cours de l'année dernière.*

**« Envoyez la facture au client. »** — À Riverton, l'assistant n'a pas d'outil email, par conception. L'instruction a été refusée, correctement, et la version fonctionnelle est *produisez le PDF de la facture et dites-moi qu'elle est prête.*

**« Supprimez le client en double. »** — Refusée : l'utilisateur Agent ne peut pas supprimer. La version fonctionnelle est *archivez le client en double*, ce qui est aussi la bonne réponse.

**« Combien avons-nous gagné le mois dernier ? »** — Ambigu entre chiffre d'affaires, marge brute et profit. La version corrigée est *quel a été notre profit net le mois dernier, et de quoi est-il composé ?* — et la réponse revient avec les composants, ce qui est plus utile que le nombre.

Le motif dans les quatre : l'assistant était littéral, la personne était vague, et la correction consistait à dire ce qui était voulu. Ce n'est pas une limitation de la technologie. C'est la même exigence que la gestion a toujours eue envers les gens à qui elle délègue, et c'est la raison pour laquelle ce chapitre est organisé de cette façon—par département, dans la langue du travail, avec les contrôles attachés.

---

Une dernière note, à propos de la bibliothèque comme *document*.

Riverton conserve sa propre version de cette liste dans un fichier partagé, et elle croît d'environ une instruction par mois. Chaque instruction en elle a été essayée, et celles qui n'ont pas fonctionné ont été supprimées plutôt que conservées « au cas où ». Le fichier fait quatre pages, et c'est le document le plus lu dans l'entreprise après la liste de prix.

C'est ce qu'une bibliothèque de prompts devrait être : pas un manuel, pas une liste de tours de passe-passe, mais le vocabulaire accumulé d'une entreprise qui a appris à dire ce qu'elle veut.
