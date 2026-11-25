# Lab 2 – Les 15 tickets de Néolys

## Mode d'emploi

1. **Création (côté utilisateur)** : pour chaque ticket, connecte-toi avec le compte du demandeur ou avec `post-only`, ou crée le ticket en tant qu'admin en choisissant le bon demandeur. Copie le titre et le message tels quels.
2. **Traitement (côté technicien)** : connecte-toi avec `tech` (pour le N1) ou `adm-neolys` (pour le N2), puis pour chaque ticket :
   - choisis le **type** (Incident ou Demande) et la **catégorie** ;
   - règle l'**urgence** et l'**impact**, et vérifie la **priorité** calculée et le **SLA** appliqué ;
   - **assigne** le ticket au bon groupe (Support N1 ou Support N2) ;
   - ajoute au moins un **suivi** (une question ou une réponse à l'utilisateur) et une **tâche** (ce que tu as fait, avec la durée) ;
   - rédige la **solution**, puis passe le ticket en **Résolu**.
3. **Ne regarde le corrigé qu'après avoir traité le ticket.**

| # | Demandeur | Canal | Titre |
|---|---|---|---|
| 1 | s.martin (Compta) | Téléphone | Mot de passe expiré |
| 2 | l.bernard (Commercial) | E-mail | L'imprimante du 1er n'imprime plus |
| 3 | c.dubois (Direction) | Téléphone | Plus d'Internet dans tout le bâtiment |
| 4 | t.petit (Production) | Formulaire | Arrivée d'un intérimaire lundi |
| 5 | s.martin (Compta) | E-mail | Excel plante à l'ouverture d'un fichier |
| 6 | l.bernard (Commercial) | Téléphone | Mail suspect reçu, j'ai cliqué sur le lien |
| 7 | c.dubois (Direction) | E-mail | Besoin d'accès au dossier Comptabilité |
| 8 | t.petit (Production) | Formulaire | Écran qui clignote |
| 9 | s.martin (Compta) | Téléphone | Le logiciel de paie est très lent |
| 10 | l.bernard (Commercial) | Formulaire | Installation de Zoom |
| 11 | c.dubois (Direction) | Téléphone | Ordinateur portable volé dans le train |
| 12 | t.petit (Production) | E-mail | L'imprimante du 1er n'imprime plus (encore) |
| 13 | s.martin (Compta) | Formulaire | Calendrier partagé non visible |
| 14 | l.bernard (Commercial) | E-mail | Le VPN ne se connecte pas depuis l'hôtel |
| 15 | c.dubois (Direction) | Formulaire | Imprimante du 1er : 3e panne ce mois-ci |

---

## Énoncés

### Ticket 1 – Mot de passe expiré
> Bonjour, Windows me dit que mon mot de passe a expiré, mais quand je le change il me met une erreur. Je ne peux plus travailler. Sophie

### Ticket 2 – L'imprimante du 1er n'imprime plus
> Bonjour, depuis ce matin, l'imprimante du 1er étage n'imprime plus rien. Mes documents restent bloqués en attente. J'ai un devis à envoyer à un client avant midi. Lucas

### Ticket 3 – Plus d'Internet dans tout le bâtiment
> Personne n'a Internet depuis 10 minutes, ni les mails ni les sites. Les commerciaux ne peuvent plus rien faire. C'est urgent ! Claire Dubois, direction

### Ticket 4 – Arrivée d'un intérimaire lundi
> Un intérimaire, Kevin Moreau, arrive lundi à 8 h en production pour 3 mois. Il lui faut une session sur le poste de l'atelier et l'accès au dossier Production. Merci. Thomas

### Ticket 5 – Excel plante à l'ouverture d'un fichier
> Bonjour, quand j'ouvre le fichier « Budget_2027.xlsx », Excel se ferme tout seul. Les autres fichiers fonctionnent. Sophie

### Ticket 6 – Mail suspect, j'ai cliqué sur le lien
> J'ai reçu un mail de « DHL » pour un colis, j'ai cliqué sur le lien et j'ai entré mon identifiant et mon mot de passe. Après, j'ai trouvé ça bizarre… Lucas

### Ticket 7 – Besoin d'accès au dossier Comptabilité
> Bonjour, pouvez-vous me donner accès au dossier Comptabilité du serveur ? J'ai besoin de voir les factures. Claire Dubois

### Ticket 8 – Écran qui clignote
> Mon écran clignote depuis hier, et parfois il devient noir 2 secondes. Ça me donne mal à la tête. Thomas

### Ticket 9 – Le logiciel de paie est très lent
> Le logiciel de paie met 2 minutes pour ouvrir chaque fiche de salarié. On doit faire les paies avant vendredi. Sophie

### Ticket 10 – Installation de Zoom
> Bonjour, un client veut faire ses réunions sur Zoom. Pouvez-vous l'installer sur mon PC ? Lucas

### Ticket 11 – Ordinateur portable volé
> Je me suis fait voler mon ordinateur portable dans le train Paris-Belfort il y a une heure. Il y avait tous les dossiers de la direction dessus. Que dois-je faire ? Claire Dubois

### Ticket 12 – L'imprimante du 1er n'imprime plus (encore)
> L'imprimante du 1er est encore bloquée, comme la semaine dernière. Thomas

### Ticket 13 – Calendrier partagé non visible
> Je ne vois plus le calendrier partagé « Congés équipe » dans Outlook depuis la mise à jour de mon PC. Sophie

### Ticket 14 – Le VPN ne se connecte pas depuis l'hôtel
> Je suis à l'hôtel pour un salon. Le VPN tourne dans le vide et finit par une erreur. Chez moi, ça marche. Je dois accéder aux tarifs demain matin. Lucas

### Ticket 15 – Imprimante du 1er : 3e panne ce mois-ci
> C'est la 3e fois ce mois-ci que l'imprimante du 1er tombe en panne. Les équipes perdent du temps. Il faut une vraie solution. Claire Dubois

---

## Corrigé (à lire après avoir traité les tickets)

| # | Type | Catégorie | Urgence | Impact | Priorité | Groupe |
|---|---|---|---|---|---|---|
| 1 | Incident | Comptes et accès › Mot de passe | Haute | Faible | Moyenne | N1 |
| 2 | Incident | Matériel › Imprimante | Haute | Moyen | Haute | N1 |
| 3 | Incident | Réseau › Internet | Très haute | Élevé | Très haute | N2 |
| 4 | Demande | Comptes et accès › Nouvel arrivant | Moyenne | Faible | Basse | N1 |
| 5 | Incident | Logiciel › Bureautique | Moyenne | Faible | Basse | N1 |
| 6 | Incident | Sécurité › Virus et phishing | Très haute | Moyen | Haute ou Très haute | N2 |
| 7 | Demande | Comptes et accès › Droits sur dossier | Basse | Faible | Très basse ou Basse | N1 |
| 8 | Incident | Matériel › Poste de travail | Moyenne | Faible | Basse | N1 |
| 9 | Incident | Logiciel › Logiciel métier | Haute | Moyen | Haute | N2 |
| 10 | Demande | Logiciel › Installation | Basse | Faible | Basse | N1 |
| 11 | Incident | Sécurité › Perte ou vol | Très haute | Élevé | Très haute | N2 |
| 12 | Incident | Matériel › Imprimante | Haute | Moyen | Haute | N1 |
| 13 | Incident | Messagerie › Calendrier | Basse | Faible | Basse | N1 |
| 14 | Incident | Réseau › VPN | Haute | Faible | Moyenne | N2 |
| 15 | Incident | Matériel › Imprimante | Haute | Moyen | Haute | N2 |

### Les points clés de chaque ticket

1. **Mot de passe** : vérifier l'**identité** de l'appelant avant toute réinitialisation (rappeler sur son numéro interne). Cause probable : la politique de complexité ou d'historique du mot de passe. Solution : expliquer les règles, réinitialiser avec « changer au prochain logon ».
2. **Imprimante** : vérifier si le problème touche un ou plusieurs utilisateurs, puis vider la file d'attente et redémarrer le spouleur. Le délai « avant midi » augmente l'urgence, pas l'impact.
3. **Internet** : tout le bâtiment est touché, donc impact maximal. Le N2 vérifie le pare-feu (WAN, passerelle, DNS) et le fournisseur d'accès. Informer les utilisateurs (message de communication) pendant l'incident.
4. **Intérimaire** : c'est une **demande**, pas un incident (rien n'est cassé). Créer le compte avec une **date d'expiration** à la fin du contrat (3 mois). Accès au dossier Production uniquement (moindre privilège). Échéance : lundi 8 h.
5. **Excel** : le problème ne concerne qu'un fichier, donc le fichier est probablement corrompu. Essayer « Ouvrir et réparer », puis restaurer une version précédente depuis la sauvegarde.
6. **Phishing** : **incident de sécurité**. Réinitialiser le mot de passe immédiatement, révoquer les sessions, activer ou vérifier le MFA, chercher des connexions suspectes et des règles de transfert de mail ajoutées par l'attaquant, prévenir l'équipe sécurité et sensibiliser l'utilisateur. Ne pas le culpabiliser : il a bien fait de signaler.
7. **Accès au dossier** : ne **jamais** donner l'accès sans **validation** du responsable du dossier (le responsable comptable), même si c'est la direction qui demande. Utiliser l'onglet **Validations** de GLPI. Donner l'accès en lecture seule si c'est suffisant.
8. **Écran** : tester le câble, un autre port, puis un autre écran. S'il est sous garantie, faire un échange. Rattacher le ticket à l'**élément** (l'ordinateur ou l'écran) inventorié.
9. **Logiciel de paie** : impact sur un service avec une échéance. Le N2 vérifie le serveur (CPU, RAM, disque, base de données) et le réseau. Si besoin, contacter l'éditeur. Documenter la cause.
10. **Zoom** : c'est une **demande**. Vérifier qu'il est autorisé (liste des logiciels validés). Sinon, proposer l'outil de visio de l'entreprise, ou ouvrir une demande de **changement** pour ajouter Zoom au catalogue.
11. **Vol de portable** : **incident de sécurité majeur**. Bloquer le compte et réinitialiser le mot de passe, révoquer les sessions et les certificats VPN, vérifier le chiffrement du disque (BitLocker), effacer l'appareil à distance si possible, porter plainte (le récépissé est nécessaire pour l'assurance), évaluer s'il faut une **notification à la CNIL** (données personnelles, 72 h, RGPD). Fournir un poste de remplacement.
12. **Imprimante, encore** : un ticket **identique** au n° 2. Le lier au ticket 2 (onglet **Tickets liés**). Il faut commencer à se demander s'il y a une cause commune.
13. **Calendrier** : reconnecter le calendrier partagé dans Outlook, vérifier les droits de partage. Ajouter la procédure à la base de connaissances.
14. **VPN depuis l'hôtel** : ça marche chez lui, donc ce n'est pas le compte. Les réseaux d'hôtel bloquent souvent les ports du VPN (par exemple UDP pour IPsec ou WireGuard). Solutions : partage de connexion 4G, ou un VPN qui passe par TCP 443. Le traiter avant demain matin.
15. **3e panne** : c'est le moment de créer un **problème** ITIL. Lier les tickets 2, 12 et 15 à ce problème, puis chercher la **cause racine**. C'est l'objet de l'étape 6.

### La différence à retenir
- **Incident** : quelque chose qui marchait ne marche plus. Objectif : rétablir le service vite.
- **Demande** : un besoin de service, rien n'est cassé (compte, accès, installation).
- **Problème** : la **cause** inconnue d'un ou plusieurs incidents. Objectif : qu'ils ne se reproduisent plus.
- **Changement** : une modification planifiée de l'infrastructure, évaluée et validée avant d'être appliquée.
