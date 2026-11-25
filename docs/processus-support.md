# Processus du support – Néolys

## Cycle de vie d'un ticket

```
 Utilisateur                Support N1                       Support N2
     │                          │                                │
     │  Ticket (portail,        │                                │
     │  mail, téléphone)        │                                │
     ├─────────────────────────►│ Nouveau                        │
     │                          │ Qualification : type,          │
     │                          │ catégorie, urgence, impact     │
     │                          │ → priorité et SLA automatiques │
     │                          │                                │
     │                          │ Traitement possible ?          │
     │                          ├── oui : En cours ── Résolu     │
     │                          │                                │
     │                          └── non : escalade ─────────────►│ En cours
     │                                                           │ Diagnostic
     │◄──────── Suivi et questions (En attente) ─────────────────┤
     │                                                           │ Solution
     │◄─────────────────────────── Résolu ───────────────────────┤
     │ Confirmation ou absence de réponse                        │
     ▼                                                           ▼
   Clos                                       Incident récurrent ? → Problème
                                              Solution durable ?   → Changement
```

## Définitions ITIL

| Objet | Définition | Objectif | Exemple |
|---|---|---|---|
| **Incident** | Quelque chose qui fonctionnait ne fonctionne plus | Rétablir le service le plus vite possible | L'imprimante n'imprime plus |
| **Demande** | Un besoin de service, rien n'est cassé | Livrer le service demandé | Créer le compte d'un intérimaire |
| **Problème** | La cause inconnue d'un ou plusieurs incidents | Supprimer la cause racine | 3 pannes de l'imprimante en un mois |
| **Changement** | Une modification planifiée de l'infrastructure | Modifier sans casser : analyse, validation, retour arrière | Déployer un nouveau pilote |

## Matrice de priorité (urgence × impact)

| Urgence \ Impact | Faible (1 personne) | Moyen (1 service) | Élevé (toute l'entreprise) |
|---|---|---|---|
| **Haute** | Moyenne | Haute | Très haute |
| **Moyenne** | Basse | Moyenne | Haute |
| **Basse** | Très basse | Basse | Moyenne |

- **Impact** : combien de personnes ou quelle partie de l'activité est touchée.
- **Urgence** : à quelle vitesse la situation devient grave (échéance, risque de sécurité).

## Niveaux de service (SLA)

Calendrier : du lundi au vendredi, de 8 h à 18 h.

| Priorité | Prise en charge (TTO) | Résolution (TTR) |
|---|---|---|
| Très haute | 30 min | 4 h |
| Haute | 1 h | 8 h |
| Moyenne | 4 h | 2 jours ouvrés |
| Basse | 8 h | 5 jours ouvrés |

Appliqués automatiquement par 4 règles métier (« si la priorité est X, alors assigner le TTO X et le TTR X »), à la création et à la mise à jour du ticket.

## Répartition N1 et N2

| Support N1 | Support N2 |
|---|---|
| Mots de passe, comptes, droits simples | Réseau, VPN, pare-feu |
| Imprimantes, postes, écrans | Serveurs et applications métier |
| Logiciels bureautiques, installations validées | Incidents de sécurité (phishing, vol) |
| Premier diagnostic et escalade | Problèmes et changements |

## Règles de sécurité du support
- Toujours **vérifier l'identité** avant une réinitialisation de mot de passe (rappeler sur le numéro interne).
- Aucun accès à un dossier sans la **validation** de son responsable, même pour la direction.
- Ne **jamais** demander son mot de passe à un utilisateur.
- Un incident de sécurité (phishing, vol, compromission) est escaladé immédiatement au N2.
