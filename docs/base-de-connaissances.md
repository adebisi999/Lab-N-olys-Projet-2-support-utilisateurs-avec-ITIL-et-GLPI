# Base de connaissances – Néolys

Les 4 articles à créer dans GLPI : **Outils › Base de connaissances › + Ajouter**.

---

## Article 1 – Redémarrer le spouleur d'impression
**Catégorie** : Matériel › Imprimante · **Cible** : techniciens (Support N1, N2) · **Lié au problème** : « Pannes répétées de l'imprimante du 1er étage »

**Symptôme** : les documents restent « en attente » dans la file d'impression, et l'imprimante ne sort rien.

**Procédure (2 minutes)**
1. Sur le poste de l'utilisateur, touche Windows, tape `services.msc`, puis **Entrée**.
2. Trouve le service **Spouleur d'impression**, puis clic droit › **Arrêter**.
3. Ouvre l'Explorateur et va dans `C:\Windows\System32\spool\PRINTERS`, puis supprime tout le contenu de ce dossier (pas le dossier lui-même).
4. Retourne dans les services : **Spouleur d'impression** › clic droit › **Démarrer**.
5. Demande à l'utilisateur de relancer son impression.

**En PowerShell (administrateur)** :
```powershell
Stop-Service Spooler -Force
Remove-Item C:\Windows\System32\spool\PRINTERS\* -Force
Start-Service Spooler
```

⚠️ C'est une **solution de contournement**. La solution définitive est le changement « Déploiement du nouveau pilote de l'imprimante du 1er ». Lie chaque nouveau ticket au problème.

---

## Article 2 – Changer son mot de passe Windows
**Catégorie** : Comptes et accès › Mot de passe · **Cible** : tous les utilisateurs (FAQ)

**Quand ?** Windows vous demande de changer votre mot de passe tous les 90 jours.

**Comment ?**
1. Appuyez sur **Ctrl + Alt + Suppr**, puis choisissez **Modifier un mot de passe**.
2. Tapez l'ancien mot de passe, puis deux fois le nouveau.

**Les règles de votre nouveau mot de passe**
- 12 caractères minimum ;
- au moins une majuscule, une minuscule, un chiffre et un caractère spécial ;
- différent de vos 5 derniers mots de passe ;
- sans votre prénom, votre nom ni le nom de l'entreprise.

💡 **Astuce** : une phrase est plus facile à retenir. Par exemple : `MonChat-Mange3Croquettes!`

**Ça ne marche pas ?** Si Windows refuse le mot de passe, il ne respecte pas l'une des règles ci-dessus. Si vous êtes bloqué, appelez le support : nous vérifierons votre identité avant de réinitialiser votre mot de passe.

🔒 Le support ne vous demandera **jamais** votre mot de passe, ni par téléphone ni par mail.

---

## Article 3 – Reconnaître un mail de phishing
**Catégorie** : Sécurité › Virus et phishing · **Cible** : tous les utilisateurs (FAQ)

**Les 5 signes qui doivent vous alerter**
1. **L'expéditeur** : l'adresse ne correspond pas à l'entreprise (`dhl-livraison@gmail.com` au lieu de `@dhl.com`).
2. **L'urgence** : « Votre colis sera renvoyé sous 24 h », « Votre compte sera bloqué ».
3. **Le lien** : passez la souris dessus **sans cliquer**. L'adresse affichée est étrange ou ne correspond pas au site.
4. **La demande** : on vous demande votre mot de passe, vos coordonnées bancaires ou d'ouvrir une pièce jointe inattendue.
5. **Les fautes** : orthographe, mise en page ou logo approximatifs.

**Le bon réflexe : je signale, je ne clique pas.**
- Ne cliquez sur rien et ne répondez pas.
- Signalez le mail au support (bouton « Signaler » ou ticket dans GLPI).
- Supprimez-le ensuite.

**Vous avez déjà cliqué ou saisi votre mot de passe ?**
Pas de panique et pas de honte : **appelez immédiatement le support**. Plus vous réagissez vite, plus on limite les dégâts (changement du mot de passe, vérification du compte).

---

## Article 4 – Perte ou vol de votre ordinateur ou téléphone
**Catégorie** : Sécurité › Perte ou vol · **Cible** : tous les utilisateurs (FAQ)

**Dans l'heure qui suit**
1. **Prévenez le support informatique**, par téléphone de préférence. Nous allons :
   - bloquer votre compte et changer votre mot de passe ;
   - couper l'accès VPN et la messagerie de l'appareil ;
   - effacer l'appareil à distance si c'est possible.
2. **Prévenez votre responsable.**

**Dans les 24 heures**
3. **Portez plainte** au commissariat ou à la gendarmerie (ou en pré-plainte en ligne). Le récépissé est nécessaire pour l'assurance.
4. **Envoyez une copie de la plainte** au support, dans le ticket.

**Ensuite**
5. Le support vous prête un **poste de remplacement**.
6. Si l'appareil contenait des données personnelles (clients, salariés), l'entreprise évalue s'il faut **déclarer l'incident à la CNIL dans les 72 heures** (RGPD).

💡 Nos ordinateurs sont chiffrés (BitLocker) : sans votre mot de passe, les données sont illisibles. C'est pour ça qu'il ne faut **jamais** coller votre mot de passe sur l'ordinateur.
