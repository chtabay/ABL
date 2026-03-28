# AUDIT APPROFONDI - ATHENA STRATEGIE RETRAITE

**Site audité :** https://athenasr.com/  
**Date de l'audit :** 28 mars 2026  
**Commanditaire :** Direction Athena SR  
**Objectif :** Préparer la refonte complète (V2) du site et de l'offre

---

## TABLE DES MATIERES

1. [Synthese executive](#1-synthese-executive)
2. [Audit technique](#2-audit-technique)
3. [Audit editorial et contenu](#3-audit-editorial-et-contenu)
4. [Audit de l'offre et des prestations](#4-audit-de-loffre-et-des-prestations)
5. [Audit UX / Parcours utilisateur](#5-audit-ux--parcours-utilisateur)
6. [Audit SEO](#6-audit-seo)
7. [Benchmark concurrentiel](#7-benchmark-concurrentiel)
8. [Matrice SWOT](#8-matrice-swot)
9. [Recommandations prioritaires pour la V2](#9-recommandations-prioritaires-pour-la-v2)
10. [Prochaines etapes du projet V2](#10-prochaines-etapes-du-projet-v2)

---

## 1. SYNTHESE EXECUTIVE

### Contexte

Athena Strategie Retraite est un cabinet de conseil specialise dans l'accompagnement
retraite, base a Toulouse avec une antenne a Bordeaux. Le site actuel (athenasr.com)
presente des faiblesses techniques et strategiques majeures qui limitent sa capacite
a convertir des visiteurs en clients et a refleter le niveau d'expertise du cabinet.

### Constats cles

| Domaine | Niveau de criticite | Resume |
|---------|-------------------|--------|
| Technique | CRITIQUE | WordPress mal maintenu, sitemap en erreur 500, URLs inconstantes, pages lentes/timeout |
| Contenu | ELEVE | Textes generiques, presence de contenu spam/IA non relu, pas de preuve de valeur chiffree |
| Offre | ELEVE | 4 services identiques repetes sur chaque segment, pas de tarification, pas de differenciation |
| UX | ELEVE | Parcours de conversion faible, pas d'espace client, pas de simulateur |
| SEO | CRITIQUE | Sitemap casse, indexation tres faible, pas de blog structure, meta-donnees insuffisantes |
| Image de marque | MOYEN | Positionnement flou entre cabinet premium et cabinet generaliste |

### Verdict global

Le site actuel fonctionne comme une vitrine statique basique. Il ne rend pas justice
a l'expertise reelle du cabinet. Une refonte complete (technique + offre + communication)
est non seulement justifiee mais necessaire pour soutenir la croissance du cabinet.

---

## 2. AUDIT TECHNIQUE

### 2.1 Stack technologique identifie

| Composant | Technologie | Observation |
|-----------|------------|-------------|
| CMS | **WordPress** | Confirme par la structure `/index.php/` dans les URLs et `/wp-content/` pour les medias |
| SEO Plugin | **Yoast SEO** | Confirme par le fichier `robots.txt` (bloc Yoast) |
| Page Builder | Probablement **Elementor** ou **Divi** | Sections accordion "Voir plus", mise en page typique |
| Hebergement | Non identifie precisement | Performances tres faibles (timeouts frequents) |
| SSL | Oui (HTTPS actif) | Certificat en place |
| CDN | Non detecte | Pas de Cloudflare ni autre CDN visible |
| Cookies/RGPD | Bandeau de consentement present | Plugin WordPress de gestion du consentement |

### 2.2 Problemes techniques critiques

#### Sitemap XML casse (Severite : CRITIQUE)
- `https://athenasr.com/sitemap.xml` retourne une **erreur 500 (Internal Server Error)**
- `https://athenasr.com/wp-sitemap.xml` retourne egalement une **erreur 500**
- `https://athenasr.com/sitemap_index.xml` retourne une **erreur 500**
- **Impact :** Google ne peut pas decouvrir et indexer correctement les pages du site.
  C'est la raison probable pour laquelle le site est quasi invisible dans les resultats de recherche.

#### Structure d'URLs inconstante (Severite : HAUTE)
- Certaines pages utilisent `/index.php/slug/` (ex : `/index.php/dirigeant/`)
- D'autres semblent repondre directement sur `/slug/` (d'apres le menu)
- Le menu du site pointe vers des URLs **sans** `/index.php/`, qui retournent des **erreurs 404**
- Les pages reelles vivent sous `/index.php/slug/`
- **Impact :** Navigation cassee pour les visiteurs, liens internes brises, confusion pour les moteurs de recherche.

#### Performances serveur catastrophiques (Severite : HAUTE)
- La page d'accueil genere regulierement des **timeouts** au chargement
- La page `/index.php/devis-gratuit-simulation-retraite/` est egalement en timeout
- **Impact :** Taux de rebond tres eleve. Google penalise les sites lents dans ses classements.

#### Pages manquantes / Erreurs 404 (Severite : HAUTE)
- `/index.php/entreprise/` : 404
- `/index.php/qui-sommes-nous/` : 404
- `/index.php/nos-formations/` : 404
- Plusieurs liens du menu principal menent vers des pages inexistantes
- **Impact :** Experience utilisateur degradee, perte de credibilite, signaux negatifs pour le SEO.

### 2.3 Architecture des pages identifiees

**Pages fonctionnelles (confirmees) :**
| URL | Contenu |
|-----|---------|
| `/` (accueil) | Page d'accueil avec presentation generale |
| `/index.php/dirigeant/` | Offre pour les dirigeants |
| `/index.php/particulier/` | Offre pour les particuliers |
| `/index.php/expatrie/` | Offre pour les expatries |
| `/index.php/une-entreprise/` | Offre pour les entreprises (formations, webinaires, offres groupees) |
| `/index.php/nos-services/` | Liste des 4 services |
| `/index.php/faq/` | Foire aux questions (11 questions) |
| `/index.php/evenements-retraite-toulouse/` | Page evenements |
| `/index.php/nos-partenaires/` | Formulaire de demande de partenariat |
| `/index.php/recrutement-conseiller-retraite-toulouse/` | Formulaire de recrutement |
| `/index.php/devis-gratuit-simulation-retraite/` | Page de contact/devis (en timeout) |

**Pages confirmees en erreur 404 :**
| URL tentee | Statut |
|------------|--------|
| `/index.php/entreprise/` | 404 |
| `/index.php/qui-sommes-nous/` | 404 |
| `/index.php/nos-formations/` | 404 |
| Toutes les URLs sans `/index.php/` | 404 |

### 2.4 Securite et conformite technique

| Point | Statut | Commentaire |
|-------|--------|-------------|
| HTTPS | OK | Certificat SSL actif |
| RGPD / Cookies | Partiel | Bandeau de consentement present, mais declaration de confidentialite en 404 |
| Mentions legales | Non identifie | Pas de page de mentions legales trouvee |
| robots.txt | OK | Present et correctement configure (Yoast) |
| Sitemap | KO | En erreur 500 |
| Sauvegardes | Non verifiable | A investiguer |

---

## 3. AUDIT EDITORIAL ET CONTENU

### 3.1 Qualite redactionnelle

#### Contenu generique et repetitif
Les pages par segment (dirigeant, particulier, expatrie) repetent largement les memes
contenus avec des variations mineures. Les 4 services listes (audit, optimisation fin
de carriere, rachat de trimestres, liquidation) sont repris quasiment a l'identique
sur chaque page de segment.

#### Contenu spam / IA non relu (Severite : CRITIQUE pour la credibilite)
Plusieurs pages contiennent des **phrases hors sujet manifestement generees par IA
et non relues** :

- Page Expatries : *"L'elimination des dechets est un element important de la protection
  de l'environnement urbain. Les coquelicots sont colores et symbolisent les reves
  et les espoirs."*
- Page FAQ : *"Les immeubles de grande hauteur de la ville temoignent d'une atmosphere
  moderne."*
- Page FAQ : *"Les oies forment un V lors de leur migration pour economiser de l'energie."*
- Page Accueil : *"La culture ecologique met l'accent sur la coexistence harmonieuse
  de l'homme et de la nature."*

**Impact :** Ces passages detruisent la credibilite du cabinet. Un prospect qui lit ces
phrases remettra en question le serieux de l'entreprise. C'est un probleme URGENT
a corriger meme avant la refonte V2.

#### Absence de preuve sociale structuree
- Les avis Google (21 avis, note "Excellent") sont affiches via un widget Trustindex
  mais ne sont pas mis en valeur strategiquement
- Pas d'etude de cas
- Pas de temoignages developpes
- Pas de chiffres cles mis en avant (nombre de dossiers traites, montant recupere, etc.)

### 3.2 Tonalite et positionnement editorial

| Aspect | Constat |
|--------|---------|
| Ton general | Professionnel mais impersonnel, tres "plaquette commerciale" |
| Storytelling | Quasi absent. Pas d'histoire fondatrice, pas de parcours client |
| Chiffres d'impact | Un seul chiffre frappant utilise : "84% des releves comportent des erreurs" |
| Appels a l'action | Repetitifs ("Profitez de notre diagnostic retraite gratuit") sans urgence ni personnalisation |
| Differenciation | Le texte ne dit pas clairement pourquoi choisir Athena SR plutot qu'un concurrent |

---

## 4. AUDIT DE L'OFFRE ET DES PRESTATIONS

### 4.1 Cartographie de l'offre actuelle

#### Services identifies (page /nos-services/)

| Service | Description | Tarif affiche |
|---------|------------|---------------|
| **Audit et optimisation retraite** | Bilan de carriere complet, analyse des trimestres, points, droits | Non communique |
| **Optimisation de fin de carriere** | Strategie sur mesure, prise en compte des evolutions legislatives | Non communique |
| **Rachat de trimestres** | Analyse du cout, des avantages fiscaux, accompagnement administratif | Non communique |
| **Liquidation des dossiers** | Gestion complete de la liquidation des droits et pensions | Non communique |

#### Offre B2B (page /une-entreprise/)

| Prestation | Description | Tarif affiche |
|------------|------------|---------------|
| **Formation 2 jours** | Sensibilisation des dirigeants et salaries a la preparation retraite | Non communique |
| **Webinaire retraite** | Sessions en ligne interactives pour les collaborateurs | Non communique |
| **Offres groupees** | Accompagnement personnalise a conditions avantageuses pour les collaborateurs | Non communique |

#### Point d'entree commercial
- **Diagnostic retraite gratuit** : Mentionne sur chaque page comme CTA principal
- **Premier rendez-vous offert** pour les entreprises
- **Evenements/Afterwork** : Organisation mensuelle d'evenements de networking et sensibilisation

### 4.2 Analyse critique de l'offre

#### Forces de l'offre
- **Specialisation claire** : Uniquement les regimes obligatoires, pas de placement financier
  (element differenciateur fort, bien mentionne dans un avis Google)
- **Expertise technique** : Connaissance des 42 regimes de retraite francais
- **Multi-segments** : Couverture dirigeants, salaries, expatries, entreprises
- **Capacite a traiter les dossiers complexes** : Mentionne dans les medias comme element
  distinctif du cabinet

#### Faiblesses majeures de l'offre

| Faiblesse | Detail |
|-----------|--------|
| **Pas de tarification visible** | Aucun prix, fourchette, ou logique de tarification n'est communique. Le prospect ne peut pas se projeter. |
| **Offre indifferenciee par segment** | Les 4 services sont les memes pour dirigeants, particuliers et expatries. Seule la page entreprise se distingue avec des prestations specifiques (formation, webinaire). |
| **Pas de niveaux d'offre** | Pas de formules (Essentiel / Premium / Sur-mesure) qui permettraient de structurer le parcours d'achat |
| **Pas de livrables explicites** | Le prospect ne sait pas ce qu'il recevra concretement (rapport, document, nombre de RDV, delais) |
| **Valeur ajoutee mal quantifiee** | Le site ne dit jamais combien les clients recuperent en moyenne, quel est le ROI du service |
| **Processus client opaque** | Les "4 etapes vers une retraite sereine" sont mentionnees en bas de la FAQ mais non detaillees |

### 4.3 Segmentation client

| Segment | Page dediee | Proposition de valeur specifique | Evaluation |
|---------|-------------|--------------------------------|------------|
| **Dirigeants** | Oui | "Chute de 70% des revenus" comme accroche, accompagnement global | Faible : le contenu est generique au-dela de l'accroche |
| **Particuliers** | Oui | "84% des releves comportent des erreurs" comme accroche | Faible : meme structure que dirigeant |
| **Expatries** | Oui | CFE, conventions bilaterales, demarches internationales | Moyen : le plus specifique des 3, mais reste superficiel |
| **Entreprises** | Oui | Formation, webinaire, offres groupees | Moyen : offre distincte mais mal structuree, pas de lien avec la loi Partage de la Valeur |

### 4.4 Benchmark tarifaire (marche)

D'apres l'analyse du marche, les cabinets concurrents affichent ces fourchettes :

| Service | Fourchette marche |
|---------|-------------------|
| Audit / reconstitution de carriere (simple) | 960 EUR - 1 290 EUR |
| Audit / reconstitution de carriere (complexe) | 1 490 EUR - 3 600 EUR+ |
| Aide a la liquidation | A partir de 2 160 EUR |
| Bilan retraite complet (audit + strategie + liquidation) | 2 500 EUR - 5 000 EUR+ |

---

## 5. AUDIT UX / PARCOURS UTILISATEUR

### 5.1 Parcours de conversion actuel

```
Visiteur arrive sur le site
    |
    v
Page d'accueil (souvent en timeout)
    |
    v
Choix du segment (Dirigeant / Particulier / Expatrie / Entreprise)
    |
    v
Page segment (contenu generique, memes services)
    |
    v
CTA "Diagnostic retraite gratuit" --> Page de devis (en timeout)
    |
    v
FIN - Pas de parcours alternatif
```

### 5.2 Points de friction identifies

| Point de friction | Impact | Priorite |
|-------------------|--------|----------|
| Page d'accueil en timeout | Le visiteur part avant meme de voir le contenu | CRITIQUE |
| Liens du menu menant vers des 404 | Perte de confiance immediate | CRITIQUE |
| CTA principal (devis) en timeout | Le parcours de conversion est totalement bloque | CRITIQUE |
| Pas de numero de telephone cliquable en hero | Frein a la prise de contact rapide | HAUTE |
| Pas de simulateur en ligne | Pas d'outil interactif pour engager le visiteur | HAUTE |
| Pas de chatbot ou FAQ interactive | Le visiteur ne trouve pas de reponse rapide | MOYENNE |
| Pas d'espace client | Pas de suivi de dossier en ligne | MOYENNE |
| Pas de prise de RDV en ligne (Calendly ou equivalent) | Le prospect doit envoyer un formulaire et attendre | HAUTE |

### 5.3 Experience mobile

Non testable en profondeur dans cet audit, mais les signes suivants suggerent
des problemes :
- Le page builder WordPress genere typiquement un rendu mobile correct mais sous-optimal
- Les timeouts affectent encore plus les utilisateurs mobiles (connexion plus lente)
- Les formulaires de contact ne semblent pas optimises pour le mobile

---

## 6. AUDIT SEO

### 6.1 Etat de l'indexation

| Indicateur | Constat |
|------------|---------|
| Sitemap XML | **CASSE** - Erreur 500 sur toutes les variantes |
| robots.txt | OK - Correctement configure via Yoast |
| Indexation Google | **Tres faible** - Le site n'apparait quasiment pas dans les resultats de recherche |
| Resultats `site:athenasr.com` | Aucun resultat retourne dans nos tests |
| Structure d'URLs | **Problematique** - `/index.php/` dans les URLs est un signal negatif |

### 6.2 Analyse des facteurs SEO

| Facteur | Etat | Detail |
|---------|------|--------|
| **Balises title** | Partiellement OK | Les pages ont des titles descriptifs (ex : "Retraite de chefs d'entreprise : Eviter une chute de vos revenus") |
| **Meta descriptions** | Non verifiable | Probablement generees par Yoast mais non testables |
| **Structure Hn** | Correcte | Les pages utilisent H2/H3 de facon hierarchique |
| **Maillage interne** | Faible | Peu de liens entre les pages, pas de blog pour creer du contenu |
| **Contenu duplique** | OUI | Les memes blocs de texte sont copies entre les pages segments |
| **Vitesse de chargement** | Tres mauvaise | Timeouts frequents |
| **URLs propres** | NON | Presence de `/index.php/` dans les URLs |
| **Blog / Contenu frais** | Absent | Quelques posts d'evenements mais pas de strategie de contenu |
| **Backlinks** | Non mesure | A analyser avec un outil dedie (Ahrefs, SEMrush) |

### 6.3 Mots-cles strategiques non exploites

Le site ne se positionne probablement sur aucun de ces termes pourtant strategiques :

| Mot-cle | Volume estime | Concurrence |
|---------|---------------|-------------|
| "cabinet conseil retraite" | Moyen | Moyenne |
| "audit retraite" | Moyen | Moyenne |
| "reconstitution carriere retraite" | Faible | Faible |
| "expert retraite toulouse" | Faible | Faible |
| "preparation retraite dirigeant" | Faible | Faible |
| "retraite expatrie france" | Faible | Faible |
| "rachat trimestres retraite" | Moyen | Moyenne |
| "erreur releve carriere" | Faible | Tres faible |
| "liquidation retraite aide" | Faible | Faible |
| "formation retraite entreprise" | Faible | Faible |

---

## 7. BENCHMARK CONCURRENTIEL

### 7.1 Concurrents identifies

| Cabinet | Localisation | Positionnement | Points forts |
|---------|-------------|----------------|--------------|
| **Analyse-Retraite.fr** | National | Leader historique, reconnu MEDEF | Forte credibilite institutionnelle, tarifs affiches |
| **Retraite Conseil** | Paris | Premium, cadres et dirigeants | Offres structurees (bilan, strategie, exit strategy, liquidation), ciblage haut de gamme |
| **Retraite & Conseils** | National | Generaliste, accompagnement individualise | Tarification claire, segmentation par statut |
| **Cabinet Odysseus** | National | Specialise audit retraite | Simulations detaillees, focus optimisation timing |
| **Pedagogie-Retraite** | National | Expert audit exhaustif | Reconstitution de carriere tres detaillee |
| **Acces-Retraite** | National | Expert multi-profils | Bonne segmentation, preuve sociale forte |

### 7.2 Ce que font mieux les concurrents

| Pratique | Concurrents qui le font | Athena SR |
|----------|------------------------|-----------|
| Tarifs affiches clairement | Retraite & Conseils, Pedagogie-Retraite | Non |
| Offres packagées (Essentiel/Premium/Sur-mesure) | Retraite Conseil | Non |
| Blog SEO regulier | Analyse-Retraite, Acces-Retraite | Non |
| Simulateur en ligne | Plusieurs | Non |
| Etudes de cas / temoignages developpes | Analyse-Retraite | Tres basique (widget Google) |
| Prise de RDV en ligne | La plupart | Non |
| Livrables explicites (rapport PDF, nombre de RDV) | Retraite Conseil, Odysseus | Non |

### 7.3 Avantage concurrentiel d'Athena SR (a exploiter)

- **Specialisation regimes obligatoires exclusivement** (pas de placement financier) :
  c'est un positionnement rare et de confiance
- **Capacite a traiter les dossiers complexes** (multi-regimes, expatries, carrieres longues)
- **Presence physique bi-ville** (Toulouse + Bordeaux) : proximite client
- **Strategie evenementielle active** : afterworks, conferences, partenariats (Allianz, MPL, Dynabuy)
- **Equipe en croissance** : signal de dynamisme

---

## 8. MATRICE SWOT

### Forces (Strengths)
- Expertise pointue et exclusive sur les regimes obligatoires
- Equipe qualifiee et en croissance
- Presence physique a Toulouse et Bordeaux
- Bons avis clients (4.9/5 sur Google, 21 avis)
- Reseau de partenaires actif (AXA, Allianz, etc.)
- Strategie evenementielle reguliere
- Capacite a traiter les dossiers complexes

### Faiblesses (Weaknesses)
- Site web techniquement defaillant (timeouts, 404, sitemap casse)
- Contenu spam/IA detruisant la credibilite
- Offre non structuree (pas de packages, pas de tarifs)
- Visibilite SEO quasi nulle
- Pas de strategie de contenu (blog, guides, simulateur)
- Processus de conversion casse (formulaire en timeout)
- Absence de mentions legales et politique de confidentialite fonctionnelle
- Communication indifferenciee entre segments

### Opportunites (Opportunities)
- Reforme des retraites 2023 : augmentation de la demande d'accompagnement
- Afflux de liquidations attendu en 2026 (Cnav)
- Loi Partage de la Valeur : nouveau levier B2B
- Faible concurrence SEO locale ("expert retraite toulouse")
- Possibilite de creer un positionnement premium clair
- Digitalisation du parcours client (simulateur, espace client, prise de RDV)
- Contenu educatif a fort potentiel (guides, calculateurs, blog)

### Menaces (Threats)
- Concurrents nationaux mieux structures et mieux references
- Informations retraite gratuites (info-retraite.fr, sites officiels)
- Risque d'image si le contenu spam reste en ligne
- Dependance a l'evenementiel physique pour l'acquisition
- Evolution reglementaire permanente necessitant une veille continue

---

## 9. RECOMMANDATIONS PRIORITAIRES POUR LA V2

### 9.1 Actions immediates (AVANT la V2)

Ces actions doivent etre realisees immediatement, sans attendre la refonte :

| # | Action | Priorite | Difficulte |
|---|--------|----------|------------|
| 1 | **Supprimer les phrases spam/IA** sur toutes les pages | URGENTE | Facile |
| 2 | **Corriger le sitemap XML** (desactiver/reactiver Yoast ou regenerer) | URGENTE | Facile |
| 3 | **Corriger les permaliens** WordPress pour supprimer `/index.php/` | URGENTE | Moyenne |
| 4 | **Creer les pages manquantes** (mentions legales, politique de confidentialite) | URGENTE | Facile |
| 5 | **Reparer les liens du menu** pour pointer vers les bonnes URLs | URGENTE | Facile |

### 9.2 Piliers de la V2

#### Pilier 1 : Nouvelle plateforme technique
- Migrer vers une solution moderne (Next.js + CMS headless, ou WordPress refait proprement)
- Hebergement performant avec CDN
- Temps de chargement < 2 secondes
- Score Lighthouse > 90 sur tous les criteres

#### Pilier 2 : Refonte de l'offre
- Structurer l'offre en **packages clairs avec tarification**
  (ex : Bilan Essentiel / Accompagnement Premium / Solution Complete)
- Definir des **livrables concrets** pour chaque prestation
- Creer une **offre B2B structuree** avec la loi Partage de la Valeur comme levier commercial
- Introduire un **simulateur de retraite** en ligne comme outil d'acquisition

#### Pilier 3 : Nouvelle communication
- Definir un **positionnement clair** : expert technique independant vs. conseiller patrimonial
- Creer un **storytelling fondateur** autour de la mission du cabinet
- Produire des **etudes de cas** et temoignages clients detailles
- Mettre en avant des **chiffres d'impact** (montant moyen recupere, nombre d'erreurs corrigees)

#### Pilier 4 : Strategie d'acquisition digitale
- Blog SEO avec calendrier editorial (2-4 articles/mois)
- Landing pages par mot-cle strategique
- Integration d'un outil de prise de RDV en ligne
- Strategie LinkedIn pour le B2B (Fatima Lalouch + equipe)

#### Pilier 5 : Experience client digitale
- Espace client pour le suivi de dossier
- FAQ interactive / chatbot
- Processus d'onboarding digitalise
- Notifications d'avancement

---

## 10. PROCHAINES ETAPES DU PROJET V2

Le projet de refonte complete suivra ces phases :

| Phase | Livrable | Description |
|-------|----------|-------------|
| **Phase 1** (actuelle) | Audit approfondi | Ce document. Etat des lieux technique, editorial et strategique. |
| **Phase 2** | Analyse de l'offre | Redefinition des prestations, packaging, tarification, proposition de valeur par segment. |
| **Phase 3** | Analyse legale | Conformite RGPD, mentions legales, CGV, cadre reglementaire du conseil en retraite. |
| **Phase 4** | Business plan | Modele economique de la V2, projections, ROI de la refonte, budget. |
| **Phase 5** | Specifications fonctionnelles | Parcours utilisateur, fonctionnalites, arborescence, contenus. |
| **Phase 6** | Specifications techniques | Architecture, stack, hebergement, integrations, securite. |
| **Phase 7** | Maquettes (wireframes + UI) | Design de l'interface, prototypage interactif. |
| **Phase 8** | Developpement & mise en ligne | Realisation, tests, migration, lancement. |

---

## ANNEXES

### A. Liste complete des URLs testees

| URL | Statut |
|-----|--------|
| `https://athenasr.com/` | Timeout (contenu recupere via cache/search) |
| `https://athenasr.com/robots.txt` | 200 OK |
| `https://athenasr.com/sitemap.xml` | 500 Internal Server Error |
| `https://athenasr.com/wp-sitemap.xml` | 500 Internal Server Error |
| `https://athenasr.com/sitemap_index.xml` | 500 Internal Server Error |
| `https://athenasr.com/index.php/dirigeant/` | 200 OK |
| `https://athenasr.com/index.php/particulier/` | 200 OK |
| `https://athenasr.com/index.php/expatrie/` | 200 OK |
| `https://athenasr.com/index.php/une-entreprise/` | 200 OK |
| `https://athenasr.com/index.php/nos-services/` | 200 OK |
| `https://athenasr.com/index.php/faq/` | 200 OK |
| `https://athenasr.com/index.php/evenements-retraite-toulouse/` | 200 OK |
| `https://athenasr.com/index.php/nos-partenaires/` | 200 OK |
| `https://athenasr.com/index.php/recrutement-conseiller-retraite-toulouse/` | 200 OK |
| `https://athenasr.com/index.php/devis-gratuit-simulation-retraite/` | Timeout |
| `https://athenasr.com/dirigeant/` | 404 |
| `https://athenasr.com/particulier/` | 404 |
| `https://athenasr.com/nos-services/` | 404 |
| `https://athenasr.com/qui-sommes-nous/` | 404 |
| `https://athenasr.com/nos-formations/` | 404 |
| `https://athenasr.com/nos-partenaires/` (sans index.php) | 404 |
| `https://athenasr.com/faq/` (sans index.php) | 404 |
| `https://athenasr.com/recrutement/` | 404 |
| `https://athenasr.com/index.php/entreprise/` | 404 |
| `https://athenasr.com/index.php/qui-sommes-nous/` | 404 |
| `https://athenasr.com/index.php/nos-formations/` | 404 |
| `https://athenasr.com/declaration-de-confidentialite/` | 404 |

### B. Citations de contenu spam identifie

1. **Page Expatries** : "L'elimination des dechets est un element important de la protection
   de l'environnement urbain. Les coquelicots sont colores et symbolisent les reves et les espoirs."
2. **Page FAQ (documents)** : "Les oies forment un V lors de leur migration pour economiser
   de l'energie."
3. **Page FAQ (caisses)** : "Les immeubles de grande hauteur de la ville temoignent
   d'une atmosphere moderne."
4. **Page Accueil** : "La culture ecologique met l'accent sur la coexistence harmonieuse
   de l'homme et de la nature."

### C. Equipe identifiee

| Nom | Role | Localisation |
|-----|------|-------------|
| Fatima Lalouch | Gerante | Toulouse |
| Vanessa Reynaert | Developpement commercial & Partenariats | Bordeaux |
| Sarrah Aacha | Conseillere retraite | Toulouse |
| Julie Malet | Conseillere (mentionnee dans un avis) | Non precise |

### D. Partenaires affiches

Bonjour Patrimoine, AXA, Audit Courtage, Origami, PASS Formation,
Federation Toulouse, Allianz, MPL, Unis-Vers, Beaubourg

---

*Document genere le 28 mars 2026 - Audit V1.0*
*Prochaine etape recommandee : Phase 2 - Analyse et restructuration de l'offre*
