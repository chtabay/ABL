# SPRINT 1 - SPECIFICATIONS FONCTIONNELLES DU SITE V2

**Cabinet :** Athena Strategie Retraite  
**Date :** 28 mars 2026  
**Objectif :** Definir l'integralite du site V2 (arborescence, parcours, fonctionnalites, contenus)  
**Cible de livraison :** Semaine 2-3 du Sprint 1

---

## 1. ARBORESCENCE DU SITE

### 1.1 Plan de site (sitemap)

```
athenasr.com/
|
|-- /                                 PAGE D'ACCUEIL
|
|-- /offres/                          VUE D'ENSEMBLE DES OFFRES
|   |-- /offres/diagnostic/           Offre DIAGNOSTIC (690 EUR)
|   |-- /offres/bilan-complet/        Offre BILAN COMPLET (1 890 EUR+)
|   |-- /offres/serenite/             Offre SERENITE (2 990 EUR+)
|   |-- /offres/urgence/              Offre URGENCE (990 EUR+)
|
|-- /dirigeant/                       PAGE SEGMENT - Dirigeants / TNS
|-- /particulier/                     PAGE SEGMENT - Salaries / Particuliers
|-- /expatrie/                        PAGE SEGMENT - Expatries
|-- /entreprise/                      PAGE SEGMENT - Entreprises (B2B)
|
|-- /simulateur/                      MINI-SIMULATEUR RETRAITE
|
|-- /a-propos/                        QUI SOMMES-NOUS (equipe, histoire, valeurs)
|-- /temoignages/                     ETUDES DE CAS ET TEMOIGNAGES
|
|-- /blog/                            BLOG SEO
|   |-- /blog/[slug]/                 Articles individuels
|
|-- /faq/                             FOIRE AUX QUESTIONS
|-- /evenements/                      EVENEMENTS & AFTERWORKS
|-- /partenaires/                     DEVENIR PARTENAIRE
|-- /recrutement/                     NOUS REJOINDRE
|
|-- /contact/                         CONTACT + PRISE DE RDV
|-- /rendez-vous/                     PRISE DE RDV DIRECTE (Cal.com embed)
|
|-- /mentions-legales/                MENTIONS LEGALES
|-- /cgv/                             CONDITIONS GENERALES DE VENTE
|-- /politique-confidentialite/       POLITIQUE DE CONFIDENTIALITE
```

### 1.2 Navigation principale (header)

```
[LOGO ATHENA SR]     Nos Offres v    Vous etes v    Simulateur    A propos    Blog    [PRENDRE RDV]
                      |                |
                      |-- Diagnostic   |-- Dirigeant
                      |-- Bilan        |-- Particulier
                      |-- Serenite     |-- Expatrie
                      |-- Urgence      |-- Entreprise
```

- Le CTA principal "PRENDRE RDV" est toujours visible en haut a droite (bouton plein)
- Le numero de telephone est visible dans le header (cliquable sur mobile)
- Navigation sticky au scroll

### 1.3 Footer

```
ATHENA SR                OFFRES              RESSOURCES          CONTACT
Expert independant       Diagnostic          Blog                55 av. Louis Breguet
en retraite              Bilan Complet       FAQ                 31400 Toulouse
obligatoire              Serenite            Evenements          05 34 42 17 84
                         Urgence             Temoignages
[Logo]                   Entreprise          Simulateur          Bordeaux : 06 51 36 02 38

[Avis Google 4.9/5]     Mentions legales | CGV | Confidentialite | © 2026
```

---

## 2. SPECIFICATIONS PAGE PAR PAGE

### 2.1 PAGE D'ACCUEIL (/)

**Objectif :** Capter l'attention en 5 secondes, qualifier le visiteur, l'orienter vers l'action.

#### Section HERO

| Element | Contenu |
|---------|---------|
| **Titre principal (H1)** | "Vos droits de retraite meritent un expert independant" |
| **Sous-titre** | "Nous ne vendons aucun produit financier. Notre seul metier : verifier, corriger et optimiser vos droits de retraite obligatoire." |
| **CTA principal** | [Estimer ma retraite gratuitement] --> /simulateur/ |
| **CTA secondaire** | [Prendre rendez-vous] --> /rendez-vous/ |
| **Element de preuve** | "4.9/5 sur Google - 21 avis" + "Plus de X dossiers traites" |
| **Visuel** | Photo professionnelle de l'equipe ou illustration sobre |

#### Section PROBLEME (hook emotionnel)

```
"84% des releves de carriere comportent des erreurs.
 Chaque erreur, c'est de l'argent perdu. Chaque mois. A vie."

 [Verifier mon releve gratuitement] --> /simulateur/
```

#### Section OFFRES (3 colonnes + 1)

Presentation visuelle des 4 offres en cards :

| Card | Titre | Accroche | Prix | CTA |
|------|-------|----------|------|-----|
| DIAGNOSTIC | "Savoir ou j'en suis" | Votre premier etat des lieux complet | A partir de 690 EUR | En savoir plus |
| BILAN COMPLET | "Securiser mes droits" | Reconstitution exhaustive + corrections | A partir de 1 890 EUR | En savoir plus |
| SERENITE | "De A a Z" | Accompagnement integral jusqu'au 1er versement | A partir de 2 990 EUR | En savoir plus |
| URGENCE | "Rattraper un dossier" | Reprendre en main un dossier bloque | A partir de 990 EUR | En savoir plus |

Le BILAN COMPLET est mis en avant visuellement (badge "Le plus demande" ou equivalent).

#### Section VOUS ETES (segmentation)

4 blocs cliquables :

| Bloc | Accroche | Lien |
|------|----------|------|
| Dirigeant / TNS | "Evitez la chute de 70% de vos revenus" | /dirigeant/ |
| Salarie | "Recuperez les droits oublies par les caisses" | /particulier/ |
| Expatrie | "Vos annees a l'etranger comptent" | /expatrie/ |
| Entreprise | "La retraite, votre prochain levier RH" | /entreprise/ |

#### Section METHODE (process en 4 etapes)

```
1. DIAGNOSTIC        2. ANALYSE          3. ACTION           4. RESULTAT
Nous recevons vos    Nous reconstituons  Nous corrigeons     Vous recevez
documents et         votre carriere      les erreurs et      votre rapport
analysons votre      trimestre par       engageons les       et vos droits
situation            trimestre           demarches           sont securises
```

#### Section PREUVE SOCIALE

- Widget Google Reviews (21 avis, 4.9/5)
- 2-3 temoignages mis en avant avec photo + prenom + situation
- Logos partenaires (AXA, Allianz, MPL, etc.)
- Chiffres cles : "X erreurs corrigees" / "X dossiers traites" / "X EUR recuperes en moyenne"

#### Section BLOG (3 derniers articles)

3 cards d'articles recents avec image + titre + extrait + lien

#### Section CTA FINAL

```
"Pret a securiser votre retraite ?"

[Simuler ma retraite]     [Prendre rendez-vous]     [Appeler : 05 34 42 17 84]
```

---

### 2.2 PAGE OFFRES (/offres/)

**Objectif :** Permettre au visiteur de comparer les 4 offres et choisir.

#### Tableau comparatif

```
                        DIAGNOSTIC    BILAN COMPLET    SERENITE         URGENCE
                        690 EUR       1 890 EUR+       2 990 EUR+       990 EUR+

Analyse du releve          x              x               x              x
Reconstitution         partielle      complete         complete       selon dossier
Detection anomalies        x              x               x              x
Correction erreurs         -              x               x              x
Etude rachat trim.         -              x               x         si applicable
Simulations                -              x               x              -
Liquidation                -              -               x         si applicable
Suivi                      -           3 mois          9-12 mois      variable
Rapport                synthetique    detaille         detaille         flash
Nombre de RDV              1              2            mensuel       selon besoin
Demarches admin            -         regularisations   tout inclus   correctives

                       [Choisir]      [Choisir]       [Choisir]      [Choisir]
                                    RECOMMANDE
```

#### Sous le tableau

- FAQ courte (3-4 questions : "Comment choisir ?", "Peut-on changer de formule ?", etc.)
- CTA : "Pas sur de votre choix ? Appelez-nous ou prenez RDV, on vous conseille."

---

### 2.3 PAGES OFFRE INDIVIDUELLES (/offres/diagnostic/, etc.)

**Structure commune pour chaque page d'offre :**

| Section | Contenu |
|---------|---------|
| **Hero** | Nom de l'offre + baseline + prix + CTA "Prendre RDV" |
| **Pour qui** | Description du profil type en 2-3 phrases |
| **Ce que vous obtenez** | Liste detaillee des livrables avec icones |
| **Comment ca se passe** | Timeline du processus (etapes + durees) |
| **Tarification** | Prix clair + mention "dossier complexe sur devis" si applicable + facilites de paiement |
| **Temoignage** | 1 temoignage client pertinent pour cette offre |
| **FAQ specifique** | 3-4 questions propres a cette offre |
| **CTA** | [Prendre RDV] + [Appeler] + [Simuler ma retraite] |

---

### 2.4 PAGES SEGMENT (/dirigeant/, /particulier/, /expatrie/)

**Objectif :** Parler le langage du segment, puis orienter vers les offres.

**Structure commune :**

| Section | Contenu |
|---------|---------|
| **Hero** | Accroche specifique au segment + chiffre choc |
| **Problemes specifiques** | 3-4 problemes typiques de ce profil |
| **Notre approche** | Comment Athena SR repond specifiquement a ce profil |
| **Offre recommandee** | Mise en avant de l'offre la plus pertinente pour ce segment |
| **Toutes les offres** | Lien vers /offres/ pour voir le comparatif |
| **Temoignage** | 1 temoignage d'un client de ce segment |
| **CTA** | [Prendre RDV] + [Simuler] |

**Differences par segment :**

| Segment | Accroche hero | Problemes specifiques | Offre recommandee |
|---------|---------------|----------------------|-------------------|
| **Dirigeant** | "En moyenne, un dirigeant perd 70% de ses revenus a la retraite" | Cotisations TNS sous-optimales, multi-statuts, pas le temps de s'en occuper | SERENITE |
| **Particulier** | "84% des releves de carriere comportent des erreurs" | Erreurs non detectees, surestimation de la pension, complexite administrative | BILAN COMPLET |
| **Expatrie** | "Vos annees a l'etranger ne doivent pas etre perdues" | Conventions bilaterales, CFE, coordination internationale, demarches complexes | BILAN COMPLET (complexe) |

---

### 2.5 PAGE ENTREPRISE (/entreprise/)

**Objectif :** Presenter l'offre B2B et generer des leads entreprise.

| Section | Contenu |
|---------|---------|
| **Hero** | "La retraite, votre prochain levier RH" + "Accompagnez vos collaborateurs et renforcez votre marque employeur" |
| **Contexte** | Encart sur la loi Partage de la Valeur (obligation 2025) |
| **3 offres B2B** | Cards : Webinaire (890 EUR HT) / Formation 1 jour (1 800 EUR HT) / Formation 2 jours (3 200 EUR HT) |
| **Offre groupee** | Explication des offres DIAGNOSTIC et BILAN a tarif preferentiel pour les collaborateurs |
| **Partenariat** | Encart "Devenir partenaire" pour les CGP, courtiers, cabinets comptables |
| **Logos clients/partenaires** | AXA, Allianz, etc. |
| **CTA** | [Demander une presentation] --> formulaire specifique B2B |

---

### 2.6 SIMULATEUR & ANALYSE RIS (/simulateur/)

**Objectif :** Outil d'acquisition principal a 2 volets. Engager le visiteur avec
un resultat personnalise, puis l'orienter vers un echange avec une conseillere.

**Principe cle :** Le simulateur ne remplace PAS l'interaction humaine. C'est un
outil de pre-qualification et d'engagement. La valeur est dans l'accompagnement.

#### ONGLET 1 : Estimation rapide (4 etapes)

```
ETAPE 1 : Votre profil
  - Annee de naissance (select 1956-1985)
  - Nombre d'enfants (0, 1, 2, 3+)

ETAPE 2 : Votre carriere
  - Statut principal (Salarie / TNS / Fonctionnaire / Multi-statuts)
  - Age de debut d'activite (select 16-26+)
  - Interruptions / etranger (Non / Interruptions / Etranger / Les deux)

ETAPE 3 : Vos revenus et objectif
  - Salaire brut mensuel actuel (input number, aide net->brut)
  - Age de depart souhaite (slider 60-67 avec labels)

ETAPE 4 : Resultats enrichis
  - Pension mensuelle estimee (base + complementaire AGIRC-ARRCO)
  - Barre de taux de remplacement (pension vs salaire net)
  - Trimestres acquis estimes vs trimestres requis (generation)
  - Indicateur decote / taux plein / surcote avec explication
  - Comparaison multi-scenarios (3-4 ages de depart)
  - Avertissement sur les erreurs de releve (84%)
  - CTA : [Echanger avec une conseillere] --> /contact/
  - CTA secondaire : [Analyser votre RIS] --> bascule onglet 2
```

#### ONGLET 2 : Analyse de releve (RIS) - PISTE 1 VALIDEE

**Methode retenue :** Upload PDF + text parsing (extraction de texte natif, pas d'OCR).
Les RIS telecharges depuis info-retraite.fr sont des PDFs numeriques dont le texte
est directement extractible.

```
PARCOURS :
  1. Instructions pour obtenir son RIS (4 etapes via info-retraite.fr / FranceConnect)
  2. Zone de drop / upload (PDF uniquement)
  3. Barre de progression (parsing cote client)
  4. Pre-analyse : nombre de regimes, trimestres enregistres, anomalies potentielles
  5. CTA : [Echanger avec une conseillere] --> /contact/

IMPORTANT :
  - La pre-analyse est indicative. Elle detecte des SIGNAUX, pas des certitudes.
  - Le document est analyse localement (pas d'envoi serveur en Sprint 1)
  - Le parsing reel sera implemente en Sprint 2 (pdf.js ou pdf-parse)
  - En Sprint 1 : maquette fonctionnelle avec simulation du resultat
```

#### Precision et disclaimers

- Estimation **indicative uniquement**, basee sur les baremes officiels simplifies
- Disclaimer clair : "Ne constitue pas un engagement. Seul un bilan realise par
  nos conseilleres peut determiner vos droits reels."
- Le simulateur n'a PAS besoin d'etre ultra-precis. Son role est d'**engager**
  le visiteur et de l'amener vers un echange, pas de remplacer un bilan.

#### Donnees techniques

- Calcul simplifie cote client (JavaScript, pas besoin de backend)
- Formules basees sur les baremes 2026 du regime general + AGIRC-ARRCO
- Pas de stockage de donnees personnelles sans consentement
- Sprint 2 : integration pdf.js pour le parsing reel du RIS

#### Ce que le simulateur ne fait PAS (choix explicite)

- Pas de generation automatique de bilan ou audit
- Pas de remplacement du conseil humain
- Pas de connexion FranceConnect (reserve aux organismes publics)
- Pas d'OCR (les RIS de info-retraite.fr sont des PDFs natifs)

---

### 2.7 PAGE A PROPOS (/a-propos/)

**Objectif :** Humaniser le cabinet, creer la confiance, raconter l'histoire.

| Section | Contenu |
|---------|---------|
| **Hero** | "Votre retraite merite mieux qu'un formulaire" |
| **Notre histoire** | Storytelling fondateur : pourquoi Fatima a cree Athena SR, qu'est-ce qui l'a revoltee dans le systeme actuel, quelle mission |
| **Nos valeurs** | Independance / Expertise / Transparence / Prise en charge complete |
| **L'equipe** | Photo + nom + role + 1 phrase personnelle pour chaque membre |
| **Nos chiffres** | X dossiers traites / X erreurs corrigees / X EUR recuperes / 4.9/5 Google |
| **Nos partenaires** | Logos + explication du role de chaque partenariat |
| **Medias** | Reprendre l'article sur "la croissance fulgurante" du cabinet |
| **CTA** | [Prendre RDV] |

---

### 2.8 PAGE TEMOIGNAGES (/temoignages/)

**Objectif :** Preuve sociale detaillee. Compenser l'absence de bouche a oreille naturel.

**Structure :**
- 3-5 etudes de cas detaillees (anonymisees si necessaire)
- Format par etude de cas :
  - Profil du client (age, statut, situation)
  - Probleme rencontre
  - Ce qu'Athena SR a fait
  - Resultat concret (trimestres recuperes, montant de pension corrige, etc.)
  - Citation du client
- Widget Google Reviews en complement
- CTA : "Vous aussi, securisez votre retraite"

---

### 2.9 PAGE FAQ (/faq/)

**Objectif :** Repondre aux objections, reduire la friction, capter du SEO longue traine.

**Structure :** Accordeon par categorie

| Categorie | Questions |
|-----------|-----------|
| **Generales** | Quand commencer a preparer sa retraite ? / Combien ca coute ? / Combien de temps ca prend ? / Pourquoi faire appel a un cabinet ? |
| **Nos services** | Quelle difference entre Diagnostic et Bilan ? / Que contient le rapport ? / Peut-on changer de formule en cours ? / Comment se passe le premier RDV ? |
| **Technique retraite** | Combien de regimes existent ? / Comment verifier son releve ? / Qu'est-ce que le rachat de trimestres ? / Qu'est-ce que la decote ? |
| **Administratif** | Quels documents fournir ? / Qui s'occupe des demarches ? / Comment suivre mon dossier ? |
| **Tarifs** | Les tarifs sont-ils fixes ? / Peut-on payer en plusieurs fois ? / Y a-t-il un premier RDV gratuit ? |

Chaque reponse contient un lien interne vers la page pertinente (offre, simulateur, contact).

---

### 2.10 PAGE BLOG (/blog/)

**Objectif :** Acquisition SEO + demonstration d'expertise.

**Structure :**
- Liste d'articles avec pagination
- Filtres par categorie (Reforme, Dirigeants, Expatries, Conseils pratiques, Actualites)
- Sidebar : simulateur mini-CTA + dernieres actus + newsletter

**Premiers articles cibles (Sprint 1) :**
1. "Comment lire et verifier son releve de carriere"
2. "Retraite des dirigeants : les 5 erreurs les plus couteuses"
3. "Expatries : comment ne pas perdre vos droits acquis en France"
4. "Reforme des retraites 2026 : ce qui change pour vous"
5. "Rachat de trimestres : est-ce rentable ?"

---

### 2.11 PAGES CONTACT ET RDV

#### Page Contact (/contact/)

- Formulaire simple : nom, email, telephone, message, segment (dropdown)
- Coordonnees Toulouse + Bordeaux (adresse, tel, email)
- Carte Google Maps des 2 agences
- Horaires d'ouverture
- CTA : "Ou prenez directement RDV en ligne"

#### Page RDV (/rendez-vous/)

- Embed Cal.com pleine page
- Choix du type de RDV :
  - "Appel decouverte gratuit (20 min)" = premier contact, qualification
  - "RDV de lancement Diagnostic (45 min)" = pour ceux qui ont deja choisi
  - "RDV entreprise (30 min)" = pour les leads B2B
- Confirmation automatique par email + rappel J-1

---

## 3. FONCTIONNALITES TRANSVERSALES

### 3.1 Barre de confiance flottante (trust bar)

Visible sur toutes les pages, sous le header :

```
✓ Expert independant    ✓ Aucun produit financier    ✓ 4.9/5 Google    ✓ Toulouse & Bordeaux
```

### 3.2 Pop-up de sortie (exit intent)

Quand le visiteur s'apprete a quitter le site :

```
"Avant de partir...
 Savez-vous que 84% des releves de carriere comportent des erreurs ?
 Estimez votre retraite en 2 minutes.
 [Lancer le simulateur]"
```

### 3.3 Chat / WhatsApp

- Bouton flottant en bas a droite
- Lien vers WhatsApp Business (Fatima ou accueil)
- Pas de chatbot IA dans un premier temps (Sprint 1 = simplicite)

### 3.4 Bandeau evenement

Quand un evenement est a venir, bandeau en haut du site :

```
[EVENEMENT] Afterwork Retraite - Jeudi 15 avril a Toulouse - Places limitees [S'inscrire]
```

### 3.5 SEO technique

| Element | Implementation |
|---------|---------------|
| Balises title | Unique par page, incluant le mot-cle principal |
| Meta description | Unique par page, incluant le CTA |
| URLs | Propres, sans /index.php/, en minuscules, avec tirets |
| Schema.org | LocalBusiness + FAQPage + Service + Review |
| Sitemap XML | Genere automatiquement, fonctionnel |
| Open Graph | Image + titre + description pour chaque page |
| Canonical | Sur chaque page |
| Alt images | Descriptifs sur chaque image |
| Performance | Lighthouse > 90 sur les 4 criteres |

### 3.6 Analytics et tracking

| Outil | Usage |
|-------|-------|
| Google Analytics 4 | Trafic, comportement, conversions |
| Google Search Console | Indexation, mots-cles, performances SEO |
| Hotjar ou equivalent | Heatmaps, enregistrements de sessions (Sprint 2) |
| HubSpot tracking | Identification des leads, attribution |

**Evenements a tracker :**
- Simulation completee
- RDV pris
- Formulaire contact soumis
- Clic sur numero de telephone
- Telechargement de guide (si Lead Magnet)
- Temps passe sur page offre

---

## 4. PARCOURS DE CONVERSION DETAILLES

### 4.1 Parcours principal : Prospect froid → Client

```
GOOGLE / LINKEDIN / PARTENAIRE
        |
        v
  PAGE D'ACCUEIL ou ARTICLE BLOG
        |
        v
  SIMULATEUR (engagement, resultat personnalise)
        |
        v
  PAGE OFFRE (comprehension de la valeur + tarifs)
        |
        v
  PRISE DE RDV (Cal.com, appel decouverte 20 min)
        |
        v
  APPEL DECOUVERTE (qualification, recommandation d'offre)
        |
        v
  PROPOSITION COMMERCIALE (email avec devis)
        |
        v
  SIGNATURE + PAIEMENT (Yousign + paiement en ligne)
        |
        v
  ONBOARDING (depot de documents via espace client)
        |
        v
  TRAITEMENT DU DOSSIER
        |
        v
  RESTITUTION + AVIS GOOGLE
```

### 4.2 Parcours segment : "Je suis dirigeant"

```
  /dirigeant/ (accroche "70% de chute de revenus")
        |
        v
  "Notre approche pour les dirigeants" (confiance)
        |
        v
  Offre recommandee : SERENITE (2 990 EUR+)
        |
        v
  [Prendre RDV] --> Cal.com
```

### 4.3 Parcours B2B : Entreprise

```
  /entreprise/ (accroche "Levier RH + Partage de la Valeur")
        |
        v
  Offre : Webinaire / Formation / Offre groupee
        |
        v
  [Demander une presentation] --> Formulaire B2B
        |
        v
  Appel de presentation (30 min)
        |
        v
  Proposition commerciale
```

### 4.4 Parcours retargeting : Visiteur non converti

```
  Visiteur quitte le site sans RDV
        |
        v
  Exit intent popup --> Simulateur
        |
        v
  Si email capture (simulateur) --> Sequence email (3 emails sur 10 jours)
        |
        Email 1 (J+1) : "Votre estimation + les 3 erreurs les plus courantes"
        Email 2 (J+4) : "Temoignage : comment [prenom] a recupere X EUR/mois"
        Email 3 (J+10) : "Votre RDV decouverte gratuit vous attend"
```

---

## 5. KIT D'INTEGRATION NOUVELLES RECRUES

### 5.1 Documents a fournir aux 3 nouvelles recrues

| Document | Contenu | Statut |
|----------|---------|--------|
| **Fiche offre synthetique** | Les 4 offres en 1 page recto-verso avec prix, livrables, cibles | A produire |
| **Argumentaire par segment** | Pitch de 2 min par segment (Dirigeant / Particulier / Expatrie / Entreprise) | A produire |
| **Process de traitement** | Les 6 etapes d'un dossier, qui fait quoi, quels outils utiliser | A produire |
| **Script appel decouverte** | Trame de l'appel de 20 min (questions, qualification, recommandation) | A produire |
| **FAQ interne** | Les 20 questions les plus frequentes des prospects + reponses | A produire |
| **Charte qualite** | Les engagements du cabinet (delais, relecture, validation) | A produire |

---

## 6. SPECIFICATIONS TECHNIQUES CLES

### 6.1 Stack recommandee pour le site V2

| Composant | Technologie | Justification |
|-----------|------------|---------------|
| **Framework** | Next.js (App Router) | Performance, SEO natif (SSR/SSG), ecosysteme riche |
| **Styling** | Tailwind CSS | Rapidite de developpement, coherence visuelle |
| **CMS / Contenu** | Markdown + MDX (blog) ou Sanity.io | Blog geerable par l'equipe sans toucher au code |
| **Formulaires** | React Hook Form + validation | Fiable, leger |
| **RDV** | Cal.com (embed) | Open-source, personnalisable |
| **Analytics** | Google Analytics 4 + Search Console | Standard marche |
| **Hebergement** | Vercel | Deploiement auto, CDN mondial, SSL inclus |
| **Domaine** | athenasr.com (existant) | Migration DNS vers Vercel |
| **Email** | Brevo (ex-Sendinblue) | Transactionnel + marketing, francais, RGPD |

### 6.2 Performance cible

| Metrique | Cible |
|----------|-------|
| Lighthouse Performance | > 90 |
| Lighthouse Accessibility | > 95 |
| Lighthouse SEO | > 95 |
| Lighthouse Best Practices | > 90 |
| Time to First Byte | < 200ms |
| Largest Contentful Paint | < 2.5s |
| Cumulative Layout Shift | < 0.1 |

### 6.3 Responsive

- Mobile-first design
- Breakpoints : 640px (sm) / 768px (md) / 1024px (lg) / 1280px (xl)
- Test sur : iPhone SE, iPhone 14, Samsung Galaxy S23, iPad, Desktop 1080p, Desktop 1440p

---

## 7. CHARTE EDITORIALE

### 7.1 Ton et voix

| Dimension | Directive |
|-----------|-----------|
| **Ton general** | Professionnel mais chaleureux. Expert mais accessible. |
| **Registre** | Vouvoiement. Phrases courtes. Pas de jargon non explique. |
| **Posture** | "Nous sommes a vos cotes" (pas "nous sommes au-dessus de vous") |
| **Interdit** | Jargon technique non explique, promesses non tenables, ton anxiogene excessif |
| **Autorise** | Chiffres choc (84%, 70%), temoignages, ton direct et honnete |

### 7.2 Mots-cles de marque

- "Expert independant" (pas "cabinet de conseil")
- "Vos droits" (pas "votre dossier")
- "On s'occupe de tout" (pas "nous vous accompagnons dans vos demarches")
- "Securiser" (pas "optimiser" -- trop financier)
- "Regimes obligatoires" (pas "retraite" seul -- trop generique)

### 7.3 Formules interdites

- "N'hesitez pas a nous contacter" (tiede, passif)
- "Nous vous accompagnons" (generique, tout le monde le dit)
- "Solutions sur mesure" (vide de sens)
- "Votre partenaire de confiance" (trop marketing)

### 7.4 Formules encouragees

- "On s'en occupe." (direct, rassurant)
- "Vos droits, rien que vos droits." (positionne l'independance)
- "Chaque trimestre compte." (concret)
- "Vous n'avez rien a faire." (decharge mentale)

---

*Document genere le 28 mars 2026 - Specs fonctionnelles V1.0*
