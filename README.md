# ABL — Conseil en retraite obligatoire

Site vitrine du cabinet ABL, expert indépendant en droits de retraite obligatoire.

**URL :** [https://chtabay.github.io/ABL/](https://chtabay.github.io/ABL/)

---

## Stack technique

| Composant | Choix V1 |
|-----------|----------|
| Site | HTML / CSS / JS statique (single page) |
| Hébergement | GitHub Pages (`docs/`) |
| Fonts | Google Fonts — Cormorant Garamond + Plus Jakarta Sans |
| Parsing RIS | pdf.js (client-side, aucune donnée transmise) |
| Analytics | Google Analytics 4 (conditionnel au consentement cookies) |

## Structure du projet

```
ABL/
├── docs/              # Fichiers publiés sur GitHub Pages
│   ├── index.html
│   ├── presentation.html / presentation-v2.html / comparaison-presentations.html
│   └── assets/        # Images, logos caisses, cartes, visuels Sora
├── wireframes/        # Source de travail (copier vers docs/ après modification)
│   └── index.html
├── assets/            # Fichiers sources images (hors docs si besoin)
├── internal/          # Documentation interne (exclu du repo public)
├── specimen/          # RIS de test (exclu du repo public)
├── presentation/      # Présentations source (PPTX, PDF)
├── .gitignore
└── README.md
```

## Pages du site

| Page | État |
|------|------|
| Accueil (hero, segments, offres, témoignages, équipe, caisses, international) | ✅ En ligne |
| Offres (Diagnostic, Bilan, Sérénité, Urgence) | ✅ En ligne |
| Simulateur (estimation rapide + analyse RIS) | ✅ En ligne |
| Entreprise (B2B) | ✅ En ligne |
| Dirigeants (TNS) | ✅ En ligne |
| À propos | ✅ En ligne |
| Contact | ✅ En ligne |
| Mentions légales | ✅ En ligne (à compléter — données société) |
| CGV | ✅ En ligne (à compléter — données société + médiateur) |
| Politique de confidentialité | ✅ En ligne |
| Bandeau cookies RGPD | ✅ Fonctionnel |
| Présentations HTML (V1 premium / V2 administrative) | ✅ Sous-pages (liens discrets) |

---

## Reste à faire

### Priorité haute — Données & conformité (site statique)

- [ ] **Informations personnelles et d’entreprise** — Renseigner sur le site et dans les pages légales : dénomination sociale, forme juridique, capital, siège social, adresses des agences (Toulouse, Bordeaux, etc.), téléphone, e-mail professionnel, SIRET, RCS, TVA intracommunautaire, directrice de publication, hébergeur (déjà mentionné : GitHub Pages).
- [ ] **Bios de l’équipe** — Remplacer les placeholders `[A. — Prénom Nom]` etc. par les noms et textes définitifs des trois expertes.
- [ ] **Google Analytics** — Remplacer `G-XXXXXXXXXX` par le vrai ID de mesure GA4 (ou retirer le script tant que l’ID n’est pas disponible).
- [ ] **CGV** — Compléter les champs légaux restants et désigner un médiateur de la consommation conformément à l’obligation applicable.
- [ ] **Validation juridique** — Faire relire CGV + Politique de confidentialité par un juriste.
- [ ] **Nom de domaine** — Finaliser le choix et configurer le domaine personnalisé sur GitHub Pages.

### Priorité haute — Parcours client (outillage / intégrations)

Ces sujets dépassent le site statique seul ; ils impliquent choix d’outils, comptes et éventuellement un backend ou des services tiers.

- [ ] **Prise de rendez-vous** — Choisir et intégrer une solution (Cal.com, Calendly, Microsoft Bookings, etc.) : créneaux, types de RDV, lien depuis la page Contact et les CTA, cohérence avec les disponibilités réelles du cabinet.
- [ ] **Paiement et facturation** — Définir le flux métier : devis, acompte, solde, moyens de paiement (virement, lien de paiement type Stripe / PayPal / solution française), numérotation et conservation des factures, conformité facturation électronique / obligations comptables selon votre statut.
- [ ] **Signature électronique** — Définir les documents à signer (mandats, CGV, devis) et l’outil (DocuSign, Yousign, Universign, etc.) ; intégration au parcours (lien après devis, envoi par e-mail, archivage).

### Priorité moyenne — Sprint produit / communication

- [ ] **Contenu SEO** — Articles de blog, pages de mots-clés stratégiques.
- [ ] **Formulaire de contact** — Connecter à un service d’e-mail transactionnel (Resend, Brevo, etc.) si le simple affichage du mail ne suffit pas.
- [ ] **Ajustement offre** — Itérer packages / tarifs selon les retours marché.
- [ ] **Business plan v1** — Construire avec les premières données réelles.
- [ ] **Agent CRM + relances** — Automatisation via n8n + HubSpot / Pipedrive.

### Priorité basse — Sprint back-office / V2

- [ ] **Dashboard conseillère** — Vue dossiers, pipeline client, KPIs.
- [ ] **Parsing RIS avancé** — Calibrage sur davantage de formats réels.
- [ ] **Générateur de rapports** — Templates ABL avec injection des données client.
- [ ] **Base de connaissances** — Documentation réglementaire interrogeable.
- [ ] **Espace client sécurisé** — Upload documents, messagerie, suivi.
- [ ] **CRM intégration** — Synchronisation HubSpot / Pipedrive.
- [ ] **Migration Next.js / Vercel** — Si les besoins serveur l’exigent.

---

## Déjà réalisé (référence)

- Alignement du site sur les présentations (méthode Reconstitution / Stratégie / Liquidation, chiffres Cour des Comptes, bloc international, barre de logos caisses).
- Retrait du switcher DA et réduction des polices Google à deux familles.
- Intégration des visuels Sora (hero, pictos segments, portraits équipe, ambiance cabinet, formation B2B).
- Présentations HTML V1 / V2 et document de comparaison.

---

## Développement

Le fichier source principal est `wireframes/index.html`. Après modification :

```powershell
Copy-Item -Path "wireframes\index.html" -Destination "docs\index.html" -Force
git add docs/index.html
git commit -m "Description de la modification"
git push
```

Le site se met à jour automatiquement via GitHub Pages (branche `main`, dossier `/docs`).
