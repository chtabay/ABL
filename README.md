# ABL — Conseil en retraite obligatoire

Site vitrine du cabinet ABL, expert indépendant en droits de retraite obligatoire.

**URL :** [https://chtabay.github.io/ABL/](https://chtabay.github.io/ABL/)

---

## Stack technique

| Composant | Choix V1 |
|-----------|----------|
| Site | HTML / CSS / JS statique (single page) |
| Hébergement | GitHub Pages (`docs/`) |
| Fonts | Google Fonts (Cormorant Garamond, Plus Jakarta Sans + 4 alternatives DA) |
| Parsing RIS | pdf.js (client-side, aucune donnée transmise) |
| Analytics | Google Analytics 4 (conditionnel au consentement cookies) |

## Structure du projet

```
ABL/
├── docs/              # Fichiers publiés sur GitHub Pages
│   └── index.html
├── wireframes/        # Source de travail (exclu du repo public)
│   └── index.html
├── internal/          # Documentation interne (exclu du repo public)
│   ├── 00_POINT_ETAPE_STRATEGIQUE.md
│   ├── 01_AUDIT_ATHENASR.md
│   ├── 02_ANALYSE_OFFRE_ATHENASR.md
│   ├── 02bis_PRODUCTIVITE_AGENTIQUE_ATHENASR.md
│   ├── 03_SPECS_FONCTIONNELLES_V2.md
│   └── 04_CONFORMITE_LEGALE_DRAFT.md
├── specimen/          # RIS de test (exclu du repo public)
├── .gitignore
└── README.md
```

## Pages du site

| Page | État |
|------|------|
| Accueil (hero, segments, offres, témoignages, équipe, FAQ) | ✅ En ligne |
| Offres (Diagnostic, Bilan, Sérénité, Urgence) | ✅ En ligne |
| Simulateur (estimation rapide + analyse RIS) | ✅ En ligne |
| Entreprise (B2B) | ✅ En ligne |
| Dirigeants (TNS) | ✅ En ligne |
| À propos | ✅ En ligne |
| Contact | ✅ En ligne |
| Mentions légales | ✅ En ligne |
| CGV | ✅ En ligne |
| Politique de confidentialité | ✅ En ligne |
| Bandeau cookies RGPD | ✅ Fonctionnel |

---

## Reste à faire

### Priorité haute — Sprint 1

- [ ] **Direction Artistique (DA)** — Choisir la DA finale parmi les 5 presets (A-E) et retirer le switcher dev
- [ ] **Nom de domaine** — Finaliser le choix et configurer le domaine personnalisé
- [ ] **Visuels IA** — Générer les images pour les placeholders (hero, segments, équipe, entreprise, à propos)
- [ ] **Bios de l'équipe** — Rédiger et intégrer les profils des 3 recrues
- [ ] **Google Analytics** — Remplacer `G-XXXXXXXXXX` par le vrai ID de mesure GA4
- [ ] **Mentions légales** — Compléter SIRET, RCS, TVA, directrice de publication
- [ ] **CGV** — Compléter SIRET, désigner un médiateur de la consommation
- [ ] **Validation juridique** — Faire relire CGV + Politique de confidentialité par un juriste

### Priorité moyenne — Sprint 2

- [ ] **Contenu SEO** — Articles de blog, pages de mots-clés stratégiques
- [ ] **Formulaire de contact** — Connecter à un service d'email (Resend, Brevo)
- [ ] **Prise de RDV en ligne** — Intégrer Cal.com ou Calendly
- [ ] **Ajustement offre** — Itérer les packages/tarifs selon les retours marché
- [ ] **Business plan v1** — Construire avec les premières données réelles
- [ ] **Agent CRM + Relances** — Automatisation via n8n + HubSpot

### Priorité basse — Sprint 3

- [ ] **Dashboard conseillère** — Vue dossiers, pipeline client, KPIs
- [ ] **Parsing RIS avancé** — Calibrage sur davantage de formats réels
- [ ] **Générateur de rapports** — Templates ABL avec injection des données client
- [ ] **Base de connaissances** — Documentation réglementaire interrogeable
- [ ] **Espace client sécurisé** — Upload documents, messagerie, suivi
- [ ] **CRM intégration** — Synchronisation HubSpot/Pipedrive
- [ ] **Migration Next.js / Vercel** — Si les besoins serveur l'exigent

---

## Développement

Le fichier source est `wireframes/index.html`. Après modification :

```bash
# Copier vers le dossier public
Copy-Item -Path "wireframes\index.html" -Destination "docs\index.html" -Force

# Commit et push
git add docs/index.html
git commit -m "Description de la modification"
git push
```

Le site se met à jour automatiquement via GitHub Pages (branche `main`, dossier `/docs`).
