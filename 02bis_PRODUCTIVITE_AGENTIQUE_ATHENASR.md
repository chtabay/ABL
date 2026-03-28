# PHASE 2bis - PRODUCTIVITE ET ARCHITECTURE AGENTIQUE

**Cabinet :** Athena Strategie Retraite  
**Date :** 28 mars 2026  
**Documents precedents :** Phase 1 (Audit) / Phase 2 (Offre)  
**Objectif :** Definir les moyens d'optimisation de la productivite par une approche
agentique (IA + outils internes) adaptee a un cabinet de conseil retraite

---

## TABLE DES MATIERES

1. [Pourquoi une approche agentique](#1-pourquoi-une-approche-agentique)
2. [Cartographie des processus metier](#2-cartographie-des-processus-metier)
3. [Architecture agentique proposee](#3-architecture-agentique-proposee)
4. [Detail des sous-agents](#4-detail-des-sous-agents)
5. [Outils internes a developper](#5-outils-internes-a-developper)
6. [Stack technique recommandee](#6-stack-technique-recommandee)
7. [Plan de deploiement progressif](#7-plan-de-deploiement-progressif)
8. [Impact sur la productivite](#8-impact-sur-la-productivite)
9. [Budget et ROI](#9-budget-et-roi)
10. [Risques et garde-fous](#10-risques-et-garde-fous)

---

## 1. POURQUOI UNE APPROCHE AGENTIQUE

### 1.1 Le probleme de productivite d'Athena SR

Aujourd'hui, un dossier retraite complet chez Athena SR mobilise un conseiller
sur des taches de nature tres differente :

| Type de tache | Exemples | Valeur ajoutee humaine |
|---------------|----------|----------------------|
| **Collecte** | Rassembler les bulletins de paie, releves, documents | FAIBLE - repetitif |
| **Saisie / Extraction** | Lire et saisir les donnees de chaque bulletin | FAIBLE - automatisable |
| **Verification** | Croiser les donnees avec les releves de carriere | MOYENNE - pattern matching |
| **Analyse** | Detecter les anomalies, evaluer les options | HAUTE - expertise metier |
| **Calcul** | Simuler les pensions selon differents scenarios | MOYENNE - calculatoire |
| **Redaction** | Ecrire les rapports, courriers aux caisses | MOYENNE - templatable |
| **Relation client** | RDV de restitution, suivi, conseil | TRES HAUTE - relationnel |
| **Administratif** | Suivi des caisses, relances, classement | FAIBLE - automatisable |

**Constat :** Un conseiller passe environ 60-70% de son temps sur des taches
a faible valeur ajoutee (collecte, saisie, verification mecanique, administratif, redaction).
L'objectif est d'inverser ce ratio.

### 1.2 Qu'est-ce qu'une approche agentique ?

Un "agent IA" n'est pas un simple chatbot. C'est un programme autonome capable de :
- **Recevoir un objectif** ("Analyse ce releve de carriere")
- **Decomposer l'objectif** en sous-taches
- **Utiliser des outils** (OCR, bases de donnees, API, calculateurs)
- **Raisonner** sur les resultats intermediaires
- **Decider** de la prochaine action
- **Produire un livrable** (rapport, alerte, recommandation)

Un systeme **multi-agents** (ou agentique) est un ensemble de sous-agents specialises,
coordonnes par un orchestrateur, chacun expert dans un domaine precis.

### 1.3 Analogie pour comprendre

Pensez a votre cabinet comme une equipe humaine ideale :

```
DIRECTRICE (Fatima) = Orchestrateur
    |
    |-- Assistante administrative  = Agent Collecte & Classement
    |-- Analyste carriere junior   = Agent Extraction & Verification
    |-- Analyste carriere senior   = Agent Analyse & Detection d'anomalies
    |-- Actuaire / calculateur     = Agent Simulation
    |-- Redactrice                 = Agent Redaction
    |-- Secretaire juridique       = Agent Veille Reglementaire
    |-- Chargee de suivi           = Agent CRM & Relances
```

L'approche agentique consiste a **emuler numeriquement** chacun de ces postes
pour les taches repetitives, tout en gardant l'humain sur la decision et la relation.

---

## 2. CARTOGRAPHIE DES PROCESSUS METIER

### 2.1 Processus principal : Traitement d'un dossier BILAN COMPLET

```
ETAPE 1 : ONBOARDING CLIENT
  |  - Recuperation des documents (bulletins, releves, attestations)
  |  - Verification de la completude
  |  - Classement et numerisation
  |
ETAPE 2 : EXTRACTION DES DONNEES
  |  - Lecture OCR de chaque bulletin de paie
  |  - Extraction : employeur, periode, salaire brut, cotisations, regime
  |  - Structuration dans un tableau de carriere
  |
ETAPE 3 : RECONSTITUTION DE CARRIERE
  |  - Croisement avec le Releve Individuel de Situation (RIS)
  |  - Detection des ecarts (trimestres manquants, salaires incorrects)
  |  - Identification des periodes assimilees (chomage, maladie, maternite)
  |
ETAPE 4 : ANALYSE ET STRATEGIE
  |  - Evaluation des droits par regime
  |  - Simulations multi-scenarios (age de depart, rachat, cumul)
  |  - Identification des leviers d'optimisation
  |  - Recommandations strategiques
  |
ETAPE 5 : REDACTION DU RAPPORT
  |  - Generation du rapport de reconstitution
  |  - Fiche synthese des anomalies
  |  - Fiches de simulation
  |  - Courriers de regularisation aux caisses
  |
ETAPE 6 : RESTITUTION ET SUIVI
  |  - RDV de restitution avec le client
  |  - Envoi des courriers aux caisses
  |  - Suivi des reponses et relances
  |  - Cloture du dossier
```

### 2.2 Matrice d'automatisabilite

| Etape | Automatisable | Niveau | Agent(s) concerne(s) |
|-------|--------------|--------|---------------------|
| 1. Onboarding | Partiellement | MOYEN | Agent Collecte |
| 2. Extraction donnees | Largement | ELEVE | Agent OCR/Extraction |
| 3. Reconstitution | Partiellement | MOYEN | Agent Verification |
| 4. Analyse strategie | Assistance IA | FAIBLE | Agent Simulation (calcul uniquement) |
| 5. Redaction rapport | Largement | ELEVE | Agent Redaction |
| 6. Restitution/Suivi | Partiellement | MOYEN | Agent CRM/Suivi |

**Resultat :** Les etapes 2 et 5 sont quasi entierement automatisables.
Les etapes 1, 3 et 6 peuvent etre fortement assistees. L'etape 4 reste
principalement humaine (c'est le coeur d'expertise).

---

## 3. ARCHITECTURE AGENTIQUE PROPOSEE

### 3.1 Schema global

```
                    +-----------------------+
                    |                       |
                    |     ORCHESTRATEUR     |
                    |   "Chef de projet"    |
                    |                       |
                    +----------+------------+
                               |
          +--------------------+--------------------+
          |          |          |          |         |
          v          v          v          v         v
    +---------+ +---------+ +---------+ +-------+ +--------+
    | AGENT   | | AGENT   | | AGENT   | | AGENT | | AGENT  |
    | COLLECTE| | OCR /   | | ANALYSE | | REDAC | | VEILLE |
    | & CLASS.| | EXTRACT.| | & SIMUL.| | TION  | | REGL.  |
    +---------+ +---------+ +---------+ +-------+ +--------+
                                                      |
    +---------+                                  +--------+
    | AGENT   |                                  | BASE DE|
    | CRM &   |                                  | CONNAIS|
    | SUIVI   |                                  | SANCES |
    +---------+                                  +--------+

    ============================================================
    |              COUCHE HUMAINE (validation)                  |
    |  Conseiller valide les anomalies, signe les rapports,    |
    |  conduit les RDV, prend les decisions strategiques        |
    ============================================================
```

### 3.2 Principes d'architecture

| Principe | Explication simple |
|----------|--------------------|
| **L'orchestrateur ne fait rien lui-meme** | Il coordonne, decompose les taches, et transmet aux sous-agents. Comme un chef de projet qui ne code pas. |
| **Chaque agent est specialise** | Un agent = un metier. L'agent OCR ne redige pas. L'agent redaction ne calcule pas. |
| **Humain dans la boucle** | Toute decision a impact (anomalie validee, recommandation au client, courrier officiel) doit etre validee par un conseiller avant envoi. |
| **Memoire partagee** | Tous les agents lisent et ecrivent dans une base de donnees commune (le "dossier client numerique"). |
| **Tracabilite** | Chaque action de chaque agent est tracee avec horodatage, pour audit et responsabilite. |

---

## 4. DETAIL DES SOUS-AGENTS

### 4.1 AGENT COLLECTE & CLASSEMENT

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Recevoir les documents du client, verifier la completude, classer et nommer les fichiers |
| **Declencheur** | Le client depose des documents sur l'espace client |
| **Actions** | Identifier le type de document (bulletin, RIS, attestation, etc.), renommer selon une convention, verifier si le dossier est complet, alerter le conseiller si des pieces manquent |
| **Output** | Dossier numerique classe et complet, checklist de completude |
| **Technologie** | Classification de documents par IA (vision) + regles metier |
| **Gain de temps estime** | 30 min a 1h par dossier |

### 4.2 AGENT OCR / EXTRACTION

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Extraire les donnees structurees de chaque document (bulletins de paie, RIS, attestations) |
| **Declencheur** | L'Agent Collecte signale qu'un document est classe |
| **Actions** | OCR du document, extraction des champs cles (employeur, periode, salaire brut, cotisations, trimestres, regime), structuration en tableau de carriere |
| **Output** | Tableau de carriere structure (JSON/Excel) avec source de chaque donnee |
| **Technologie** | OCR specialise (Parseur, Koncile, Mindee) ou modele vision (GPT-4o, Claude) + post-traitement |
| **Precision attendue** | > 95% sur les bulletins modernes, 80-90% sur les anciens formats |
| **Gain de temps estime** | 2 a 4 heures par dossier (vs lecture manuelle de 42 ans de bulletins) |

**C'est l'agent au ROI le plus immediat.** La lecture et saisie de bulletins de paie
est la tache la plus chronophage et la moins valorisante pour un expert retraite.

### 4.3 AGENT VERIFICATION / CROISEMENT

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Croiser les donnees extraites avec le RIS officiel et detecter les anomalies |
| **Declencheur** | L'Agent OCR a termine l'extraction d'un dossier |
| **Actions** | Comparaison trimestre par trimestre entre bulletins et RIS, detection des ecarts (trimestres manquants, salaires incorrects, periodes non declarees), verification des periodes assimilees (chomage, maladie), flagging des anomalies avec un score de confiance |
| **Output** | Tableau d'anomalies avec gravite, source, et action corrective suggeree |
| **Technologie** | Regles metier codees + IA pour les cas ambigus |
| **Validation humaine** | OBLIGATOIRE - le conseiller valide chaque anomalie avant action |
| **Gain de temps estime** | 1 a 2 heures par dossier |

### 4.4 AGENT SIMULATION / CALCUL

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Calculer les pensions estimees selon differents scenarios |
| **Declencheur** | Le conseiller demande des simulations sur un dossier valide |
| **Actions** | Calcul de la pension de base (regime general), calcul des points AGIRC-ARRCO, simulation multi-scenarios (age de depart, avec/sans rachat, cumul emploi-retraite, retraite progressive), calcul du cout de rachat de trimestres vs gain sur la pension |
| **Output** | Tableau de simulations comparatives avec graphiques |
| **Technologie** | Moteur de calcul dedie (base sur les baremes officiels), mis a jour a chaque reforme |
| **Precision** | Estimative (comme les simulateurs officiels), pas de valeur contractuelle |
| **Gain de temps estime** | 1 heure par dossier |

### 4.5 AGENT REDACTION

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Generer les rapports, fiches de synthese, et courriers aux caisses |
| **Declencheur** | Le conseiller valide l'analyse et les recommandations |
| **Actions** | Generation du rapport de reconstitution (30-50 pages) a partir du dossier structure, creation de la fiche synthese, redaction des courriers de regularisation aux caisses (modeles personnalises), generation des fiches de simulation |
| **Output** | Documents PDF prets a etre relus et envoyes |
| **Technologie** | LLM (Claude, GPT-4) + templates Word/PDF + donnees du dossier |
| **Validation humaine** | OBLIGATOIRE - le conseiller relit et signe chaque document |
| **Gain de temps estime** | 2 a 3 heures par dossier |

### 4.6 AGENT VEILLE REGLEMENTAIRE

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Surveiller les evolutions legislatives et reglementaires en matiere de retraite |
| **Declencheur** | Quotidien (automatique) |
| **Actions** | Scraping des sources officielles (CNAV, AGIRC-ARRCO, Journal Officiel, Legifrance), detection des changements (nouveaux decrets, circulaires, baremes), resume des impacts pour le cabinet, mise a jour de la base de connaissances interne |
| **Output** | Briefing hebdomadaire pour l'equipe, alertes en cas de changement majeur |
| **Technologie** | Scraping + RAG (Retrieval Augmented Generation) sur base documentaire |
| **Impact** | Maintient l'expertise du cabinet a jour en permanence, alimente le blog SEO |
| **Gain de temps estime** | 2 a 3 heures par semaine de veille manuelle economisees |

### 4.7 AGENT CRM & SUIVI

| Caracteristique | Detail |
|-----------------|--------|
| **Role** | Gerer le pipeline commercial, les relances, et le suivi des dossiers |
| **Declencheur** | Evenements CRM (nouveau lead, dossier en attente, echeance) |
| **Actions** | Relance automatique des prospects (email personnalise), rappel de documents manquants au client, suivi des reponses des caisses (relance si pas de reponse sous 30 jours), notification au conseiller des actions a mener, reporting d'activite |
| **Output** | Emails de relance, notifications, tableaux de bord |
| **Technologie** | CRM (HubSpot/Pipedrive) + n8n ou Make.com pour l'orchestration |
| **Gain de temps estime** | 3 a 5 heures par semaine |

---

## 5. OUTILS INTERNES A DEVELOPPER

### 5.1 Vue d'ensemble

Au-dela des agents IA, Athena SR a besoin d'outils internes concrets
pour structurer son activite. Voici les 5 outils prioritaires :

### 5.2 OUTIL 1 : Espace Client Securise

| Caracteristique | Detail |
|-----------------|--------|
| **Objectif** | Permettre au client de deposer ses documents, suivre son dossier, et echanger avec son conseiller |
| **Fonctionnalites** | Upload de documents (drag & drop), barre de progression du dossier ("Etape 2/6 : Extraction en cours"), messagerie interne securisee, telechargement des livrables (rapport, simulations), historique des echanges |
| **Acces** | Web (responsive mobile), connexion par email + mot de passe |
| **Securite** | Chiffrement des documents, conformite RGPD, hebergement France |
| **Technologie** | Application web (Next.js ou equivalent) ou solution SaaS existante adaptee |
| **Priorite** | HAUTE - c'est le point de contact principal avec le client dans la V2 |

### 5.3 OUTIL 2 : Tableau de Bord Conseiller ("Cockpit")

| Caracteristique | Detail |
|-----------------|--------|
| **Objectif** | Vue unifiee de tous les dossiers en cours, des actions a mener, et des KPI |
| **Fonctionnalites** | Liste des dossiers avec statut et prochaine action, alertes (documents manquants, relances a faire, echeances), file d'attente des validations humaines (anomalies a confirmer, rapports a relire), KPI : nombre de dossiers en cours, CA genere, delai moyen, taux de conversion |
| **Acces** | Web (desktop), reserve a l'equipe interne |
| **Technologie** | Dashboard integre a l'espace client ou outil separe (Retool, Appsmith, ou custom) |
| **Priorite** | HAUTE |

### 5.4 OUTIL 3 : Base de Connaissances Retraite (RAG)

| Caracteristique | Detail |
|-----------------|--------|
| **Objectif** | Centraliser toute l'expertise reglementaire du cabinet pour que l'equipe (et les agents IA) puissent y acceder |
| **Contenu** | Textes de loi, circulaires, baremes (regime general, AGIRC-ARRCO, MSA, CIPAV, etc.), fiches pratiques par cas (expatrie, multi-regimes, carriere longue, etc.), historique des reformes et leurs impacts, FAQ internes |
| **Fonctionnalites** | Recherche en langage naturel ("Quel est le bareme de rachat de trimestres pour un ne en 1968 ?"), reponses sourcees (avec reference au texte de loi), mise a jour automatique via l'Agent Veille |
| **Technologie** | RAG (Retrieval Augmented Generation) : base vectorielle (Pinecone, Weaviate, ou Supabase pgvector) + LLM |
| **Priorite** | MOYENNE-HAUTE - c'est le "cerveau" du systeme agentique |

### 5.5 OUTIL 4 : Generateur de Rapports

| Caracteristique | Detail |
|-----------------|--------|
| **Objectif** | Produire des rapports professionnels et personnalises a partir des donnees du dossier |
| **Fonctionnalites** | Templates de rapport par type d'offre (Diagnostic, Bilan, Serenite), insertion automatique des donnees (tableau de carriere, anomalies, simulations), generation PDF avec charte graphique Athena SR, versionning des rapports |
| **Technologie** | Templates Docx/PDF + moteur de generation (Carbone.io, ou script Python/Node custom) |
| **Priorite** | HAUTE |

### 5.6 OUTIL 5 : Mini-Simulateur Public (site web)

| Caracteristique | Detail |
|-----------------|--------|
| **Objectif** | Outil d'acquisition : permettre au visiteur du site d'obtenir une estimation rapide et d'entrer dans le tunnel de conversion |
| **Fonctionnalites** | 5-7 questions simples (date de naissance, statut, salaire moyen, nombre d'annees cotisees, age de depart souhaite), estimation indicative de la pension, message de type "Vous pourriez recuperer X EUR/mois en corrigeant les erreurs de votre releve", CTA vers la prise de RDV |
| **Technologie** | Widget web integre au site (React/Next.js), calcul simplifie cote client |
| **Priorite** | HAUTE - c'est le levier d'acquisition principal de la V2 |

---

## 6. STACK TECHNIQUE RECOMMANDEE

### 6.1 Pour une PME : privilegier l'accessibilite

Athena SR n'a pas d'equipe technique interne. La stack doit etre :
- **Maintenable** par un prestataire externe sans expertise rare
- **Evitable** en lock-in : pas de dependance a un seul fournisseur
- **Progressive** : demarrer simple, complexifier au besoin

### 6.2 Stack recommandee

| Couche | Choix recommande | Alternative | Justification |
|--------|-----------------|-------------|---------------|
| **Orchestration workflows** | **n8n** (self-hosted) | Make.com (cloud) | n8n est open-source, gratuit en self-hosted, puissant pour les workflows IA. Make.com est plus simple si pas de technique. |
| **LLM (intelligence)** | **Claude API** (Anthropic) | OpenAI GPT-4o | Meilleur raisonnement sur les textes longs, bon en francais, API fiable |
| **OCR / Extraction** | **Mindee** ou **Parseur** | Claude Vision (GPT-4o vision) | Parseur/Mindee sont specialises bulletins de paie FR. Claude Vision en fallback pour les documents atypiques. |
| **Base de donnees** | **Supabase** (PostgreSQL) | Airtable (no-code) | Supabase offre PostgreSQL + auth + storage + pgvector (RAG). Airtable si 100% no-code. |
| **Base vectorielle (RAG)** | **Supabase pgvector** | Pinecone, Weaviate | Integre a Supabase, pas de service supplementaire a gerer |
| **CRM** | **HubSpot** (gratuit) | Pipedrive | HubSpot a un tier gratuit solide, s'integre bien avec n8n |
| **Espace client** | **Developpement sur mesure** (Next.js) | Notion + Tally (MVP rapide) | Le sur-mesure est necessaire a terme. Un MVP rapide avec Notion est possible pour tester. |
| **Generation rapports** | **Carbone.io** | Docx-templates + Python | Carbone transforme des templates Office en PDF avec injection de donnees |
| **Hebergement** | **Vercel** (front) + **Railway** ou **Render** (back) | OVH VPS | Vercel pour le site, Railway/Render pour n8n et les services backend |
| **Emails transactionnels** | **Resend** ou **Brevo** | Mailgun | Brevo est francais (ex-Sendinblue), bon pour l'emailing + transactionnel |
| **Prise de RDV** | **Cal.com** (open-source) | Calendly | Cal.com est open-source et auto-hebergeable |
| **Signature electronique** | **Yousign** | DocuSign | Yousign est francais, conforme eIDAS, moins cher que DocuSign |

### 6.3 Schema d'integration

```
SITE WEB (Next.js / Vercel)
    |
    |-- Mini-simulateur --> Capture lead --> HubSpot CRM
    |-- Prise de RDV --> Cal.com
    |-- Espace client --> App Next.js (Supabase auth + storage)
    |
    v
n8n (orchestrateur de workflows)
    |
    |-- Nouveau document depose -->  Agent Collecte (classification)
    |                                    |
    |                                    v
    |                               Agent OCR (Parseur/Mindee)
    |                                    |
    |                                    v
    |                               Agent Verification (regles + LLM)
    |                                    |
    |                                    v
    |                               [VALIDATION HUMAINE via Cockpit]
    |                                    |
    |                                    v
    |                               Agent Simulation (moteur calcul)
    |                                    |
    |                                    v
    |                               Agent Redaction (LLM + Carbone)
    |                                    |
    |                                    v
    |                               [VALIDATION HUMAINE : relecture]
    |                                    |
    |                                    v
    |                               Livraison au client (espace client)
    |
    |-- Quotidien --> Agent Veille (scraping + RAG)
    |-- Evenements CRM --> Agent Suivi (relances, notifications)
    |
    v
SUPABASE (base de donnees unifiee)
    |-- Dossiers clients (donnees structurees)
    |-- Documents (stockage fichiers)
    |-- Base de connaissances (pgvector pour RAG)
    |-- Logs d'activite (tracabilite)
```

---

## 7. PLAN DE DEPLOIEMENT PROGRESSIF

### 7.1 Principe : Commencer petit, prouver la valeur, etendre

Le deploiement se fait en **4 vagues** sur 6-9 mois, en partant des gains
les plus immediats :

### 7.2 VAGUE 1 : Fondations (Mois 1-2)

**Objectif :** Poser les bases et obtenir les premiers gains rapides.

| Action | Detail | Effort |
|--------|--------|--------|
| Mettre en place n8n | Installation sur Railway/Render, configuration de base | 2-3 jours |
| Connecter le CRM HubSpot | Import des contacts existants, parametrage du pipeline | 2-3 jours |
| Agent CRM/Suivi (v1) | Automatiser les relances email prospects et les rappels de documents manquants | 3-5 jours |
| Prise de RDV en ligne | Deployer Cal.com, integrer au site actuel | 1 jour |

**Gain immediat :** 3-5 heures/semaine de suivi administratif economisees.

### 7.3 VAGUE 2 : Extraction automatique (Mois 2-4)

**Objectif :** Automatiser la tache la plus chronophage : la lecture des documents.

| Action | Detail | Effort |
|--------|--------|--------|
| Agent OCR/Extraction | Integration Parseur ou Mindee pour les bulletins de paie | 5-7 jours |
| Agent Collecte (v1) | Classification automatique des documents deposes | 3-5 jours |
| Espace client (MVP) | Interface simple de depot de documents + barre de progression | 10-15 jours |
| Tester sur 10 dossiers | Comparer extraction automatique vs manuelle, mesurer la precision | 2 semaines |

**Gain estime :** 2-4 heures par dossier sur l'extraction.

### 7.4 VAGUE 3 : Intelligence et redaction (Mois 4-6)

**Objectif :** Assister l'analyse et automatiser la production de rapports.

| Action | Detail | Effort |
|--------|--------|--------|
| Agent Verification | Croisement automatique des donnees extraites avec le RIS | 5-7 jours |
| Agent Simulation (v1) | Moteur de calcul pension de base + AGIRC-ARRCO | 10-15 jours |
| Agent Redaction (v1) | Templates de rapport + generation assistee par LLM | 7-10 jours |
| Base de connaissances (RAG v1) | Ingestion des textes reglementaires principaux | 5-7 jours |
| Tableau de bord conseiller (v1) | Dashboard simple avec dossiers en cours et actions | 5-7 jours |

**Gain estime :** 3-5 heures supplementaires par dossier.

### 7.5 VAGUE 4 : Optimisation et scale (Mois 6-9)

**Objectif :** Affiner, fiabiliser, et preparer le passage a l'echelle.

| Action | Detail | Effort |
|--------|--------|--------|
| Agent Veille | Scraping automatique des sources reglementaires | 5-7 jours |
| Mini-simulateur public | Widget web pour le site V2 | 7-10 jours |
| Generateur de rapports (v2) | PDF complet avec charte graphique, graphiques, annexes | 5-7 jours |
| Espace client (v2) | Messagerie, historique, signature en ligne | 10-15 jours |
| Optimisation des agents | Affinage des prompts, amelioration de la precision OCR, feedback loop | Continu |

**Resultat final :** Systeme agentique complet, operationnel et mesurable.

---

## 8. IMPACT SUR LA PRODUCTIVITE

### 8.1 Temps par dossier : avant vs apres

| Etape | Temps actuel (estime) | Temps avec agents | Gain |
|-------|----------------------|-------------------|------|
| Onboarding / Collecte | 1h | 15 min | -75% |
| Extraction / Saisie | 4-6h | 30 min + 30 min relecture | -85% |
| Verification / Croisement | 2-3h | 30 min + 30 min validation | -75% |
| Analyse / Strategie | 2h | 2h (reste humain) | 0% |
| Simulations | 1-2h | 15 min + 15 min verification | -80% |
| Redaction rapport | 3-4h | 30 min + 1h relecture/ajustement | -60% |
| Suivi administratif | 2h/dossier/mois | 15 min/dossier/mois | -85% |
| **TOTAL par dossier** | **~16-20h** | **~6-7h** | **~65%** |

### 8.2 Impact sur la capacite du cabinet

| Indicateur | Aujourd'hui | Avec agents |
|------------|------------|-------------|
| Temps moyen par dossier BILAN | ~18h | ~6h |
| Dossiers/mois par conseiller | 8-10 | 20-25 |
| Capacite totale (4 conseillers) | 32-40 dossiers/mois | 80-100 dossiers/mois |
| CA potentiel mensuel (mix d'offres) | ~24 000 EUR | ~60 000 EUR |
| CA potentiel annuel | ~290 000 EUR | ~720 000 EUR |

**Ce n'est pas juste un gain de productivite, c'est un changement de modele economique.**

### 8.3 Impact qualitatif

| Dimension | Amelioration |
|-----------|-------------|
| **Qualite des rapports** | Standardisee, coherente, professionnelle (templates + donnees verifiees) |
| **Delai de traitement** | Divise par 2 a 3 (de 4-8 semaines a 2-3 semaines pour un BILAN) |
| **Taux d'erreur** | Reduit (double verification : agent + humain) |
| **Satisfaction client** | Espace client, suivi en temps reel, communication proactive |
| **Satisfaction equipe** | Moins de saisie repetitive, plus de conseil a haute valeur |
| **Scalabilite** | Recruter un nouveau conseiller = x2,5 au lieu de x1 |

---

## 9. BUDGET ET ROI

### 9.1 Budget de mise en place

| Poste | Cout estime | Recurrence |
|-------|------------|------------|
| **Developpement initial** (Vagues 1-4, prestataire) | 25 000 - 40 000 EUR | Ponctuel |
| **n8n** (self-hosted sur Railway) | ~20 EUR/mois | Mensuel |
| **Supabase** (Pro) | ~25 EUR/mois | Mensuel |
| **API LLM** (Claude/OpenAI) | ~100 - 300 EUR/mois | Mensuel |
| **OCR** (Parseur ou Mindee) | ~50 - 150 EUR/mois | Mensuel |
| **HubSpot CRM** (gratuit) | 0 EUR | - |
| **Cal.com** (self-hosted) | 0 EUR | - |
| **Yousign** | ~25 EUR/mois | Mensuel |
| **Brevo** (email) | ~25 EUR/mois | Mensuel |
| **Hebergement** (Vercel + Railway) | ~50 EUR/mois | Mensuel |
| **TOTAL cout recurrent** | **~300 - 600 EUR/mois** | Mensuel |
| **TOTAL premiere annee** | **~30 000 - 47 000 EUR** | - |

### 9.2 Retour sur investissement

| Scenario | Calcul |
|----------|--------|
| **CA supplementaire annuel** (grace a la capacite accrue) | +430 000 EUR (720k - 290k) |
| **Investissement premiere annee** | ~40 000 EUR |
| **ROI premiere annee** | **x10** |
| **Delai de rentabilite** | **Des la Vague 2** (mois 3-4), l'extraction automatique permet de traiter plus de dossiers |

Meme avec une hypothese prudente (50% du potentiel realise), le ROI reste
de l'ordre de **x5 la premiere annee**.

---

## 10. RISQUES ET GARDE-FOUS

### 10.1 Risques identifies

| Risque | Probabilite | Impact | Mitigation |
|--------|-------------|--------|------------|
| **Erreur d'extraction OCR** non detectee | Moyenne | Eleve (erreur dans le rapport client) | Double validation : agent + humain. Jamais d'envoi sans relecture humaine. |
| **Hallucination LLM** dans les rapports | Moyenne | Eleve (information fausse au client) | Templates structures avec donnees injectees (pas de generation libre). Relecture obligatoire. |
| **Changement reglementaire** non capte | Faible | Eleve (conseil errone) | Agent Veille + veille humaine en parallele. Base de connaissances versionnee. |
| **Dependance a un fournisseur** (API down) | Faible | Moyen (retard de traitement) | Architecture multi-fournisseurs (Claude + OpenAI en fallback). Workflow degrade possible. |
| **Securite des donnees** clients | Faible | Tres eleve (confiance, RGPD) | Hebergement France, chiffrement, acces restreints, audits reguliers. |
| **Resistance au changement** de l'equipe | Moyenne | Moyen (sous-utilisation) | Formation progressive, implication de l'equipe des la conception, demontrer les gains. |
| **Cout de maintenance** sous-estime | Moyenne | Moyen (budget depasse) | Budget de maintenance prevu (20% du cout initial par an). Monitoring des couts API. |

### 10.2 Regles d'or du systeme agentique

1. **Aucun document n'est envoye au client sans validation humaine.**
2. **Aucune demarche administrative n'est lancee sans validation humaine.**
3. **Chaque anomalie detectee par l'IA doit etre confirmee par un conseiller.**
4. **Les donnees clients ne quittent jamais l'infrastructure securisee** (pas de copier-coller dans ChatGPT).
5. **Chaque action agent est tracee** (qui, quoi, quand) pour audit et responsabilite.
6. **L'IA assiste, l'humain decide.** Toujours.

---

## SYNTHESE : LES 7 CHANTIERS DE PRODUCTIVITE

| # | Chantier | Impact | Investissement | Priorite |
|---|----------|--------|----------------|----------|
| 1 | **Agent OCR / Extraction** | Tres eleve (85% de gain sur la saisie) | Moyen | P1 |
| 2 | **Espace client securise** | Eleve (experience client + collecte) | Eleve | P1 |
| 3 | **Agent CRM & Suivi** | Eleve (acquisition + relances) | Faible | P1 |
| 4 | **Agent Redaction + Generateur** | Eleve (60% de gain sur la redaction) | Moyen | P2 |
| 5 | **Base de connaissances RAG** | Moyen-eleve (fiabilite + veille) | Moyen | P2 |
| 6 | **Agent Simulation** | Moyen (gain de temps calcul) | Eleve | P3 |
| 7 | **Mini-simulateur public** | Eleve (acquisition web) | Moyen | P2 |

---

## ANNEXE : GLOSSAIRE POUR NON-TECHNICIENS

| Terme | Explication simple |
|-------|-------------------|
| **Agent IA** | Un programme informatique capable de realiser des taches de maniere autonome, comme un assistant virtuel tres specialise |
| **Orchestrateur** | Le "chef de projet" des agents : il distribue les taches et verifie que tout avance |
| **OCR** | Reconnaissance optique de caracteres : transformer une image de texte (scan, photo) en texte editable et exploitable |
| **LLM** | Large Language Model : le "cerveau" de l'IA (comme ChatGPT ou Claude), capable de comprendre et generer du texte |
| **RAG** | Retrieval Augmented Generation : une technique qui permet a l'IA de chercher dans une base de documents avant de repondre, pour etre plus precise et sourcee |
| **API** | Interface de Programmation : le moyen technique par lequel deux logiciels communiquent entre eux |
| **n8n** | Un outil open-source qui permet de creer des enchainements automatiques de taches (comme des dominos) sans ecrire de code |
| **Supabase** | Une base de donnees moderne qui stocke les informations, les fichiers, et gere les connexions utilisateurs |
| **Workflow** | Un enchainement de taches automatisees, comme une chaine de montage numerique |
| **Self-hosted** | Heberge sur votre propre serveur (vs. utiliser le service cloud d'un fournisseur) |
| **Template** | Un modele pre-formate (de rapport, d'email, etc.) dans lequel on injecte des donnees specifiques |
| **Pipeline** | Le parcours que suit un prospect ou un dossier, etape par etape |

---

*Document genere le 28 mars 2026 - Phase 2bis V1.0*  
*Prochaine etape recommandee : Phase 3 - Analyse legale (RGPD, CGV, cadre reglementaire)*
