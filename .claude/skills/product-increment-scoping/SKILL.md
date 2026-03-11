---
name: product-increment-scoping
description: Guides the user through an interactive Q&A process to write a complete product increment scope (EPIC) following a standardized product management structure. Collects information section by section in chronological order and generates a structured final document. Use when the user wants to scope a feature, write an EPIC, define a product increment, or structure a product initiative. Triggers include mentions of 'EPIC', 'feature scope', 'product increment', 'scoping', 'product initiative', 'feature spec', or 'rédiger une EPIC'.
---

# Product Increment Scoping

Ce skill guide l'utilisateur à travers la rédaction d'un Product Increment Scope (EPIC) en posant des questions ciblées pour chaque section du document, dans l'ordre chronologique.

## Objectif

Créer un document de scope produit complet en guidant l'utilisateur section par section.  
Le document final suivra la structure standardisée ci-dessous.

## Processus

### 1. Introduction

Accueillez l'utilisateur et expliquez brièvement :

- Vous allez poser des questions section par section, dans l'ordre  
- L'utilisateur peut répondre de manière détaillée ou concise  
- Il peut passer des sections s'il n'a pas encore l'information  
- Un document final sera généré à la fin  

### 2. Collecte des Informations — Ordre chronologique

Procédez **section par section**, dans l'ordre ci-dessous.  
Ne posez **jamais toutes les questions d'un coup**. Attendez la réponse avant de passer à la section suivante.

---

#### Section 1 — Customer Tweet

**Rôle :** Exercice marketing. Formuler le pitch de valeur en une phrase percutante.

**Question :**

> "Si tu devais tweeter à tes utilisateurs pour leur pitcher la valeur de cette feature — le problème que tu résous pour eux — que dirais-tu ? (Un tweet court, authentique, orienté bénéfice utilisateur)"

---

#### Section 2 — Opportunity (User Problem)

**Rôle :** Décrire le problème concret à craquer et expliquer pourquoi maintenant.

**Questions :**

> "Quel est le problème utilisateur exact que nous voulons résoudre ?"  
> "Pourquoi priorisons-nous cette feature maintenant ? Qu'est-ce qui rend ce timing important ?"

⚠️ Ne pas redemander la valeur (déjà couverte par le Customer Tweet). Se concentrer sur le problème et le timing.

---

#### Section 3 — Target Audience

**Rôle :** Identifier les personas cibles.

**Questions :**

> "Pour qui construisons-nous cette feature ? Décris le profil type de l'utilisateur cible."  
> "Y a-t-il des segments secondaires qui pourraient en bénéficier ?"

---

#### Section 4 — Customer Insights

**Rôle :** Données terrain, verbatims, frictions observées chez les utilisateurs actuels.

**Questions :**

> "Que savons-nous de l'expérience utilisateur actuelle sur ce sujet ? Quelles frictions ou frustrations as-tu observées ?"  
> "As-tu des données, retours clients ou verbatims qui supportent ce besoin ?"

⚠️ Ne pas redemander le problème (déjà couvert en Section 2). Se concentrer sur les preuves et observations.

---

#### Section 5 — Competitive Insights

**Rôle :** Apprentissages clés tirés de la concurrence.

**Questions :**

> "Comment la concurrence aborde-t-elle ce problème ?"  
> "Quels apprentissages clés peut-on en tirer ?"

---

#### Section 6 — Success Metrics

**Rôle :** KPIs de succès et contribution business.

**Questions :**

> "Quels indicateurs devraient bouger si on réussit ?"  
> "Comment cette feature contribue-t-elle au revenu ou aux objectifs business ?"

---

#### Section 7 — User Journey

**Rôle :** Décrire le parcours utilisateur complet : comment il arrive dans la feature (onboarding), et où on l'attend ensuite dans le produit.

**Questions :**

> "Comment l'utilisateur découvre et arrive sur cette feature ? Quel est le parcours d'onboarding ?"  
> "Une fois qu'il a utilisé la feature, où l'attends-tu ensuite dans le produit ? Quelle est la prochaine étape naturelle pour lui ?"

Formuler cette section comme un vrai parcours narratif : étape d'arrivée → activation → destination suivante.

---

#### Section 8 — Product Parts

**Rôle :** Détails fonctionnels sous forme de user stories. C'est ici que vivent les jobs to be done.

**Consigne :**

> "Quels sont les éléments fonctionnels concrets de cette feature ? Décris-les moi, je les formulerai en user stories."

**Format de chaque user story :**

```text
En tant que <persona>, <où dans le produit>, quand <trigger/condition>, alors <résultat visible>
```

**Exemples :**

- En tant que gestionnaire de patrimoine, sur le dashboard client, quand je clique sur "Nouveau rapport", alors un rapport pré-rempli avec les données du client s'affiche  
- En tant que client investisseur, sur la page de mon portefeuille, quand une alerte de marché est déclenchée, alors je vois une notification avec la recommandation de mon conseiller  

**Regroupement :**  
Si les user stories sont nombreuses (>5), les organiser par zone d'impact dans le produit (ex : "Dashboard", "Onboarding", "Notifications").

**🔪 Challenge du scope — OBLIGATOIRE :**

Après avoir listé les user stories, l'agent DOIT :

1. Identifier les stories qui sont du "nice to have" vs "must have"  
2. Proposer une version lean : quelles stories retirer pour un MVP qui délivre 80 % de la valeur ?  
3. Suggérer des alternatives plus simples pour les stories complexes (ex : "Au lieu d'un système de notifications temps réel, est-ce qu'un email récapitulatif quotidien suffirait pour la V1 ?")  
4. Présenter la comparaison : scope complet vs scope lean, avec le ratio effort/valeur de chaque  

L'utilisateur décide, mais l'agent challenge systématiquement.

---

#### Section 9 — Pending Questions

**Rôle :** Questions en suspens, à clarifier plus tard.

**Question :**

> "Quelles questions restent en suspens ? Des zones de flou à investiguer avant ou pendant le développement ?"

---

#### Section 10 — Wireframes / Design

**Rôle :** Liens vers les maquettes.

**Question :**

> "Générer des maquettes ASCII et faire valider les écrans clés à l'utilisateur"

---

#### Section 11 — Engineering

**Rôle :** Notes techniques pertinentes.

**Questions :**

> "Y a-t-il un contexte technique existant qui influence cette feature ? Des contraintes ou dépendances ?"  
> "Des réflexions techniques intéressantes à documenter ? Quelle est la stratégie d'implémentation ? Quels sont les trade-off techniques à décider ?"

---

### 3. Validation à mi-parcours

Après la Section 6 (Success Metrics), faire un résumé rapide de ce qui a été collecté et demander confirmation avant de continuer avec le User Journey et les Product Parts.

### 4. Génération du Document Final

Une fois toutes les sections complétées, générer un document markdown structuré comme suit :

```markdown
# EPIC : [Nom de la Feature]

## Context
> 🕊️ **Customer Tweet**
> "[Le tweet pitch de valeur]"

## Opportunity (User Problem)
[Problème à craquer + pourquoi maintenant]

## Target Audience
[Personas cibles + segments secondaires]

## Customer Insights
[Données terrain, verbatims, frictions observées]

## Competitive Insights
[Apprentissages concurrence]

## Success Metrics
[KPIs + contribution business]

## User Journey
**Arrivée →** [Comment l'utilisateur découvre la feature]  
**Activation →** [Ce qu'il fait dedans]  
**Destination →** [Où on l'attend ensuite dans le produit]

## Product Parts

### [Zone d'impact 1]
**US-001 : [Titre court]**  
En tant que [persona], [où dans le produit], quand [trigger/condition], alors [résultat visible]

**US-002 : [Titre court]**  
En tant que [persona], [où dans le produit], quand [trigger/condition], alors [résultat visible]

### [Zone d'impact 2]
**US-003 : [Titre court]**  
...

---

> 🔪 **Scope Challenge**
> **Version lean proposée :** [Stories à garder pour le MVP]  
> **Stories décalées :** [Stories retirées + justification]  
> **Alternatives suggérées :** [Simplifications proposées]

## Pending Questions
- [ ] [Question 1]
- [ ] [Question 2]

## Wireframes / Design
Produire des écrans en utilisant ASCII

## Engineering
[Notes techniques, contraintes, dépendances]
```

## Notes Importantes

- Suivre strictement l'ordre chronologique des sections  
- Ne jamais poser les questions de plusieurs sections en même temps  
- Éviter les redondances entre sections : chaque section a un rôle unique  
- Le challenge de scope dans Product Parts est **obligatoire**, pas optionnel  
- Les user stories suivent **toujours** le format : `En tant que <persona>, <où dans le produit>, quand <trigger/condition>, alors <résultat visible>`  
- Si des sections sont incomplètes, indiquer clairement "[À compléter]" dans le document final  
- Être conversationnel et professionnel dans le ton  
