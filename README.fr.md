# Smart-SSI : l'identité prouvée

Une initiative de la Chrome DAO · 5 octobre 2026

[English version](README.md)

## Résumé

Smart-SSI permet à chacun de prouver des faits sur sa vie numérique, sans exposer ses données et sans dépendre d'une plateforme.

**Le problème.** Notre réputation, nos compétences et notre activité sont enfermées dans des plateformes qui ne se parlent pas. Pour prouver quoi que ce soit, il faut soit le déclarer (et on ne nous croit pas), soit tout montrer (et on perd le contrôle). Pendant ce temps, faux profils et bots rendent la confiance en ligne de plus en plus coûteuse.

**La solution.** Smart-SSI combine trois briques :

- **Preuve** : grâce au zkTLS, l'utilisateur prouve qu'une donnée vient bien d'un service réel (Strava, Spotify, une banque, une plateforme freelance), sans transmettre ses identifiants.
- **Interprétation** : une IA transforme ces données prouvées en affirmations simples et utiles, par exemple « coureur régulier depuis 2 ans ».
- **Attestation** : ces affirmations deviennent des attestations liées à l'identité décentralisée de l'utilisateur sur Solana. Les données brutes ne quittent jamais son appareil.

**Pourquoi maintenant.** Le zkTLS est devenu utilisable en production, Solana rend la vérification on-chain rapide et peu coûteuse, et l'Europe déploie son portefeuille d'identité numérique (eIDAS 2.0). L'identité légale aura bientôt son standard. La réputation prouvée, elle, n'en a pas encore.

**Le cadre.** Smart-SSI est une initiative de la [Chrome DAO](https://www.chromedao.xyz/initiatives), financée par les enchères quotidiennes de NFT sur Solana. C'est un bien commun : protocole open source, gouverné par les holders, sans token dédié. Ses premiers usages servent la DAO elle-même : votes anti-sybil, accès au Metaverse, sélection des initiatives.

## Le problème

Aujourd'hui, prouver qui l'on est en ligne oblige à choisir entre ne pas être cru et tout exposer.

**Des identités en silos.** Dix ans de courses sur Strava, des centaines de missions sur une plateforme freelance, une réputation construite sur un réseau social : tout cela existe, mais reste enfermé dans chaque service. Rien n'est portable, et tout disparaît si le compte est fermé ou la plateforme change ses règles.

**La déclaration ne suffit plus.** Un CV, un profil, une bio : ce sont des affirmations que personne ne peut vérifier. Avec l'IA générative, produire un faux profil crédible ne coûte presque plus rien. Les communautés en ligne, les DAO et les campagnes d'airdrop en font les frais : un seul acteur peut se faire passer pour des centaines.

**La vérification coûte trop cher en vie privée.** Pour prouver un revenu, on envoie trois relevés bancaires complets. Pour prouver une expérience, on donne accès à son compte. Le vérificateur récupère bien plus que ce dont il a besoin, et l'utilisateur n'a aucun contrôle sur la suite.

**Les réponses existantes sont partielles.** L'identité auto-souveraine (DID et Verifiable Credentials) donne le bon cadre, mais suppose qu'un émetteur de confiance accepte de délivrer des attestations. Or Strava, Spotify ou une banque n'en délivrent pas. Il manque un pont entre les données qui existent déjà et des attestations vérifiables.

## La solution

Smart-SSI transforme des données qui existent déjà en attestations vérifiables, en trois couches.

### 1. Preuve : la donnée vient bien de la source

L'utilisateur se connecte normalement au service concerné. Grâce au zkTLS, un réseau d'attestors observe l'échange chiffré sans en voir le contenu, puis l'utilisateur génère une preuve que la réponse du serveur contient bien telle donnée. Personne ne récupère ses identifiants, et seule l'information utile est révélée.

### 2. Interprétation : la donnée devient une affirmation utile

Une donnée brute (« 312 activités enregistrées ») dit peu de chose à un vérificateur. Un modèle d'IA la transforme en affirmation lisible et datée : « coureur régulier, 3 sorties par semaine depuis 2 ans ». L'IA produit des **faits dérivés**, jamais des traits de personnalité : chaque affirmation peut être reliée aux données prouvées qui la fondent.

### 3. Attestation : l'affirmation est liée à l'identité

L'affirmation est signée et inscrite sur Solana, rattachée à l'identifiant décentralisé (DID) de l'utilisateur. Seule l'affirmation va on-chain, jamais les données. N'importe quel service peut ensuite la vérifier en quelques millisecondes, sans contacter ni l'utilisateur ni la source.

### Le parcours utilisateur

1. Camille ouvre l'application et crée son identité : un wallet Solana est généré en arrière-plan, sans phrase de récupération à gérer.
2. Elle choisit « Prouver mon activité sportive » et se connecte à Strava dans une fenêtre sécurisée.
3. La preuve est générée sur son téléphone, l'IA propose l'affirmation « coureuse régulière depuis 2 ans ».
4. Camille relit, valide, et l'attestation rejoint son profil.
5. Plus tard, un club de trail lui demande une preuve d'expérience pour une course exigeante : elle partage l'attestation en un clic, rien d'autre.

Pour l'utilisateur, la cryptographie est invisible. Il voit seulement des badges qu'il contrôle, partage et peut retirer de son profil.

## Cas d'usage

Smart-SSI sert d'abord la Chrome DAO elle-même, puis s'ouvre à tout service qui a besoin de confiance.

### Dans la Chrome DAO

- **Votes anti-sybil** : une personne vérifiée, une voix, quel que soit le nombre de wallets qu'elle contrôle. La gouvernance gagne en légitimité.
- **Accès au Metaverse** : le hub 3D réserve déjà une porte aux holders du Ring. Des espaces peuvent s'ouvrir sur preuve : un atelier pour les artistes vérifiés, un club pour les sportifs réguliers.
- **Sélection des initiatives** : un porteur de projet prouve son parcours (missions livrées, audience, régularité sportive ou artistique) au lieu de simplement le déclarer. La DAO finance des talents réels.

### Au-delà de la DAO

| Usage | Ce qui est prouvé | Pour qui |
| --- | --- | --- |
| Airdrops et campagnes | Personne unique, activité réelle sur plusieurs services | Projets Web3 |
| Réputation freelance | Nombre de missions, notes moyennes, ancienneté | Plateformes, clients |
| Preuve de revenus | Revenu supérieur à un seuil, sans montant exact | Bailleurs, prêteurs |
| Communautés sur preuve | Pratique d'une discipline, appartenance à un groupe | Clubs, Discord, événements |
| Recrutement | Compétences démontrées par l'activité (code publié, projets) | Entreprises |

Dans chaque cas, le vérificateur obtient exactement la réponse à sa question, et rien de plus.

## Positionnement

Smart-SSI ne cherche pas à dire qui vous êtes légalement, mais à prouver ce que vous avez fait.

| Solution | Ce qu'elle prouve | Comment | Différence avec Smart-SSI |
| --- | --- | --- | --- |
| Portefeuille européen (eIDAS 2.0) | Identité légale, diplômes, permis | Émetteurs officiels (États, institutions) | Complémentaire : Smart-SSI couvre ce qu'aucune institution n'atteste |
| World ID | Unicité humaine | Scan biométrique de l'iris | Pas de biométrie, et des preuves bien plus riches que « je suis humain » |
| Gitcoin Passport (Human Passport) | Score d'humanité | Agrégation de comptes connectés | Smart-SSI prouve le contenu de l'activité, pas seulement l'existence des comptes |
| Reclaim Protocol | Données Web2 brutes | zkTLS | Brique d'infrastructure que Smart-SSI peut utiliser ; il manque la couche d'interprétation et l'identité |

**Notre angle :** être la couche qui relie les preuves de données (zkTLS) à une identité lisible par des humains et des applications. Les standards du W3C (DID, Verifiable Credentials) sont respectés, ce qui garde la porte ouverte à une interopérabilité avec le portefeuille européen.

## Modèle économique et gouvernance

Smart-SSI est un bien commun financé par la Chrome DAO : pas de token dédié, pas de levée de fonds.

**Financement.** Chaque jour, un Chrome est mis aux enchères sur Solana. Une partie de ces recettes finance les initiatives de la DAO, dont Smart-SSI : développement, audits de sécurité, infrastructure.

**Gouvernance.** Les holders de Chromes votent les décisions structurantes :

- les sources de données prises en charge en priorité ;
- les règles d'émission des attestations (seuils, durée de validité) ;
- le choix et l'élargissement du réseau d'attestors ;
- l'allocation du budget de l'initiative.

**Revenus.** Pour l'utilisateur, Smart-SSI est gratuit. Les vérificateurs professionnels (plateformes, entreprises, projets Web3) peuvent payer une redevance par vérification ou un abonnement. Ces revenus reviennent au trésor de la DAO, qui finance d'autres initiatives.

La boucle est simple : les enchères financent le protocole, le protocole renforce la gouvernance de la DAO, et ses revenus alimentent le trésor.

## Modèle de confiance et vie privée

Chaque attestation Smart-SSI repose sur deux niveaux de confiance distincts, et nous les rendons explicites.

| Niveau | Ce qui est garanti | À qui on fait confiance | Comment on réduit cette confiance |
| --- | --- | --- | --- |
| Preuve de la donnée | La donnée vient bien du service indiqué | Aux attestors zkTLS | Plusieurs attestors indépendants, sélectionnés par la DAO |
| Interprétation | L'affirmation découle correctement de la donnée | À l'émetteur Smart-SSI | Modèle et règles publics, puis exécution en environnement sécurisé (TEE), puis zkML à terme |

**Ce qui ne quitte jamais l'appareil :** identifiants de connexion, données brutes, historique d'activité.

**Ce qui est inscrit on-chain :** l'affirmation, sa date, sa source (« Strava »), sa signature et son statut (valide ou révoquée).

**Le contrôle de l'utilisateur.** Il choisit quelles preuves générer, valide chaque affirmation avant émission, décide avec qui la partager, et peut la révoquer à tout moment. Une révocation ne fait pas disparaître la trace on-chain, mais rend l'attestation invalide pour tout vérificateur.

**Conformité RGPD.** Les affirmations portent sur des faits d'activité et non sur des traits psychologiques, ce qui limite le profilage. Aucune donnée sensible (santé, opinions, religion) n'est interprétée. Le traitement repose sur le consentement explicite de l'utilisateur, étape par étape. Point ouvert : l'articulation entre le droit à l'effacement et l'immuabilité de la blockchain, que nous traitons en ne mettant on-chain aucune donnée personnelle en clair, à valider avec un juriste.

## Roadmap et limites

Le déploiement suit quatre phases, chacune validée par la DAO avant de lancer la suivante.

1. **Phase 1, preuve de concept** : DID sur Solana, une première source (Strava ou GitHub) via un fournisseur zkTLS existant, premières attestations émises pour des membres de la DAO.
2. **Phase 2, usages internes** : votes anti-sybil et accès sur preuve dans le Metaverse, 5 à 10 sources prises en charge.
3. **Phase 3, ouverture** : SDK public pour les vérificateurs externes, premiers partenaires payants, audit de sécurité complet.
4. **Phase 4, décentralisation** : réseau d'attestors multiples, interprétation en environnement sécurisé, travaux d'interopérabilité avec le portefeuille européen.

### Limites assumées

- **Dépendance aux services sources** : si un site change son interface ou bloque l'accès, la source concernée doit être adaptée.
- **Confiance résiduelle** : tant que l'interprétation n'est pas prouvée cryptographiquement, l'émetteur reste un tiers de confiance, encadré par la transparence et la gouvernance.
- **Adoption** : une attestation n'a de valeur que si des vérificateurs l'acceptent. C'est pourquoi les premiers usages sont internes à la DAO.
- **Cadre juridique** : le statut des attestations et leur articulation avec le RGPD doivent être validés avant l'ouverture à des tiers.

## Annexe technique

Cette annexe décrit les choix d'implémentation de la phase 1 ; ils seront révisés à chaque phase.

### Flux complet

1. Le client (application mobile) crée une paire de clés ed25519 et enregistre le DID de l'utilisateur sur Solana.
2. L'utilisateur lance une preuve : le client ouvre une session TLS vers la source via un attestor zkTLS.
3. Le client génère la preuve ZK sur le contenu de la réponse ; l'attestor signe la preuve.
4. Le service d'interprétation vérifie la preuve, applique le modèle et propose une affirmation.
5. L'utilisateur valide ; l'émetteur Smart-SSI signe l'attestation et l'inscrit on-chain, rattachée au DID.
6. Un vérificateur lit l'attestation, contrôle signature, statut et date, sans contacter personne.

### Identité (DID)

Nous nous appuyons sur la méthode **did:sol**, déjà utilisée sur Solana, plutôt que de créer une méthode propriétaire. Le document DID contient les clés de vérification et peut déclarer plusieurs appareils.

### Attestations

Les attestations sont stockées dans des comptes Solana dédiés (par exemple via le Solana Attestation Service), avec un schéma public :

```json
{
  "subject": "did:sol:<identifiant>",
  "claim": "runner.regular",
  "value": { "since": "2024-09", "frequency_per_week": 3 },
  "source": "strava",
  "proof_ref": "<hash de la preuve zkTLS>",
  "model_version": "<hash du modèle et des règles>",
  "issued_at": "2026-10-05",
  "expires_at": "2027-10-05",
  "status": "valid"
}
```

Les données brutes ne sont jamais stockées ; seul le hash de la preuve permet un audit ultérieur.

### Vérification sur Solana

- **Signatures** d'attestors et d'émetteur : vérifiées via les programmes natifs ed25519 ou secp256k1, pour un coût négligeable.
- **Preuves Groth16**, si elles sont vérifiées on-chain : via les syscalls alt_bn128 (bibliothèque groth16-solana).
- Programme principal écrit en Rust avec Anchor.

### Couche zkTLS

Phase 1 : intégration d'un fournisseur existant compatible Solana ([Reclaim Protocol](https://docs.reclaimprotocol.org/solana)), pour aller vite. Phases suivantes : évaluation d'une stack propre basée sur des briques open source (attestor de Reclaim, TLSNotary) pour opérer un réseau d'attestors gouverné par la DAO.

### Pipeline d'interprétation

1. Extraction des champs utiles depuis la donnée prouvée.
2. Application de règles déterministes et publiques quand c'est possible (seuils, fréquences, ancienneté).
3. Recours à un LLM avec sortie structurée uniquement pour les sources textuelles, avec un catalogue fermé d'affirmations possibles.
4. Mesure de fiabilité sur un jeu de test annoté, avec la précision définie ainsi :

```math
P = \frac{\text{prédictions correctes}}{\text{total des prédictions}}
```

Chaque version du modèle et des règles est identifiée par un hash inscrit dans l'attestation, pour que toute affirmation reste traçable.
