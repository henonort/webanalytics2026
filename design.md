# Directives Design & UX - Dashboard Analytics Prêt-à-Porter

## 🎯 Vision globale
Créer un dashboard qui respire le **luxe accessible** et le **professionnalisme**. L'utilisateur (directeur marketing, CEO) doit pouvoir scanner les informations clés en 10 secondes, puis approfondir s'il le souhaite. Pense "rapport annuel d'une maison de mode" plutôt que "tableau Excel amélioré".

---

## 🎨 Direction Artistique

### Palette de couleurs
```css
:root {
  /* Couleurs principales */
  --primary: #1a1a2e;        /* Bleu nuit profond - Headers, textes importants */
  --secondary: #16213e;      /* Bleu marine - Backgrounds sections */
  --accent: #e94560;         /* Rouge corail - CTAs, highlights, alertes positives */
  --accent-secondary: #0f3460; /* Bleu roi - Graphiques, liens */
  
  /* Neutres */
  --bg-light: #f8f9fa;       /* Fond page */
  --bg-card: #ffffff;        /* Fond cartes */
  --text-primary: #1a1a2e;   /* Texte principal */
  --text-secondary: #6c757d; /* Texte secondaire, labels */
  --text-muted: #adb5bd;     /* Texte désactivé */
  
  /* Indicateurs de performance */
  --success: #10b981;        /* Vert émeraude - Hausse, positif */
  --warning: #f59e0b;        /* Ambre - Attention */
  --danger: #ef4444;         /* Rouge - Baisse, négatif */
  
  /* Graphiques - Palette harmonieuse */
  --chart-1: #e94560;        /* Rouge corail */
  --chart-2: #0f3460;        /* Bleu roi */
  --chart-3: #00d9c0;        /* Turquoise */
  --chart-4: #f39c12;        /* Or */
  --chart-5: #9b59b6;        /* Violet */
}
```

### Typographie
```css
/* Import Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Inter:wght@300;400;500;600;700&display=swap');

:root {
  --font-display: 'Playfair Display', Georgia, serif;  /* Titres - Élégance mode */
  --font-body: 'Inter', -apple-system, sans-serif;     /* Corps - Lisibilité data */
}

/* Hiérarchie typographique */
h1 { font: 700 2.5rem/1.2 var(--font-display); }      /* Titre principal */
h2 { font: 600 1.75rem/1.3 var(--font-display); }     /* Sections */
h3 { font: 600 1.25rem/1.4 var(--font-body); }        /* Sous-sections */
.kpi-value { font: 700 2.5rem/1 var(--font-body); }   /* Gros chiffres KPI */
.kpi-label { font: 500 0.75rem/1.4 var(--font-body); text-transform: uppercase; letter-spacing: 0.05em; }
body { font: 400 1rem/1.6 var(--font-body); }
```

### Espacements & Grille
```css
/* Système d'espacement cohérent (base 8px) */
--space-xs: 0.5rem;   /* 8px */
--space-sm: 1rem;     /* 16px */
--space-md: 1.5rem;   /* 24px */
--space-lg: 2rem;     /* 32px */
--space-xl: 3rem;     /* 48px */
--space-2xl: 4rem;    /* 64px */

/* Largeur max contenu */
--container-max: 1400px;

/* Border radius */
--radius-sm: 8px;
--radius-md: 12px;
--radius-lg: 16px;
--radius-full: 9999px;
```

---

## 🏗️ Architecture de la page (ordre logique pour le client)

### 1. **Header Hero** (première impression)
```
┌─────────────────────────────────────────────────────────────┐
│  🏷️ Logo/Nom marque                         Période: Q4 2025 │
│                                                              │
│     AUDIT PERFORMANCE E-COMMERCE                             │
│     Septembre - Décembre 2025                                │
│                                                              │
│  "Une croissance de +47% portée par le Black Friday"         │
│  ← Phrase d'accroche résumant l'insight principal            │
└─────────────────────────────────────────────────────────────┘
```
- Background: dégradé subtil `linear-gradient(135deg, var(--primary), var(--secondary))`
- Texte blanc, titre en Playfair Display
- Hauteur: ~200px, pas plus

### 2. **KPIs Executive Summary** (les 10 secondes du CEO)
```
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│ 💰 CA    │ │ 👥 Users │ │ 🛒 Conv. │ │ 📈 ROAS  │ │ 🛍️ Panier│
│ 847 250€ │ │  45 230  │ │   4.2%   │ │   5.8x   │ │   127€   │
│  ↑ +32%  │ │  ↑ +28%  │ │  ↑ +0.8% │ │  ↑ +1.2x │ │  ↓ -5€   │
└──────────┘ └──────────┘ └──────────┘ └──────────┘ └──────────┘
```
- **5 cartes max** - les métriques les plus importantes
- Grosses valeurs, petits labels
- Indicateur de tendance avec couleur (vert/rouge) et flèche
- Ombre portée douce: `box-shadow: 0 4px 20px rgba(0,0,0,0.08)`
- Icônes émoji ou Lucide icons (CDN)

### 3. **Évolution temporelle** (comprendre la tendance)
```
┌─────────────────────────────────────────────────────────────┐
│  📊 Évolution du chiffre d'affaires & trafic                │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                            📈                          │  │
│  │                    ___/\___/  \                       │  │
│  │        ___/\___/\/            \_                      │  │
│  │   ___/                          \___                  │  │
│  │  Sept      Oct       Nov       Déc                    │  │
│  └───────────────────────────────────────────────────────┘  │
│  [● CA]  [● Sessions]  [● Nouveaux clients]    Légende      │
└─────────────────────────────────────────────────────────────┘
```
- Line chart avec **2-3 métriques max** pour rester lisible
- Tooltip au hover avec détails
- Annotation sur le pic Black Friday
- Zone grisée légère pour weekends optionnelle

### 4. **Funnel de conversion** (où perd-on les clients ?)
```
┌─────────────────────────────────────────────────────────────┐
│  🎯 Parcours d'achat - Funnel de conversion                 │
│                                                              │
│  ████████████████████████████████████████  100% Vues produit│
│  ██████████████████████████               65% Ajout panier  │
│  █████████████████                        42% Livraison     │
│  ████████████                             31% Paiement      │
│  ████████                                 24% Achat ✓       │
│                                                              │
│  💡 Point de friction : -23% entre panier et livraison      │
└─────────────────────────────────────────────────────────────┘
```
- Visualisation en barres horizontales décroissantes
- Couleur dégradée ou accent sur l'étape finale
- Pourcentage de perte entre chaque étape
- Insight automatique sur le plus gros drop-off

### 5. **Performance par canal** (où investir ?)
```
┌─────────────────────────────────┐ ┌─────────────────────────┐
│  📣 Sources de trafic           │ │  💻 Répartition devices │
│  ┌─────────────────────────┐    │ │      ┌─────┐            │
│  │ SEO      ████████  35%  │    │ │     /  📱  \           │
│  │ Ads      ██████    28%  │    │ │    |  62%   |          │
│  │ Meta     █████     22%  │    │ │     \      /           │
│  │ Direct   ███       10%  │    │ │      └─────┘           │
│  │ Email    ██         5%  │    │ │  📱 62%  💻 32%  📟 6% │
│  └─────────────────────────┘    │ └─────────────────────────┘
└─────────────────────────────────┘
```
- Barres horizontales pour les canaux (plus lisible que pie)
- Donut chart pour devices (visuel et compact)
- Couleurs distinctes par canal

### 6. **Répartition Homme/Femme** (segments clés mode)
```
┌─────────────────────────────────────────────────────────────┐
│  👔👗 Performance par segment                                │
│                                                              │
│     HOMME                              FEMME                 │
│    423 500€                           423 750€               │
│      50%                                50%                  │
│   ┌──────┐                           ┌──────┐               │
│   │██████│                           │██████│               │
│   │██████│                           │██████│               │
│   └──────┘                           └──────┘               │
│  Panier: 134€                       Panier: 121€            │
└─────────────────────────────────────────────────────────────┘
```
- Comparaison visuelle côte à côte
- Métriques secondaires sous les barres

### 7. **Tableau de synthèse mensuelle** (pour les détails)
```
┌─────────────────────────────────────────────────────────────┐
│  📅 Récapitulatif mensuel                                   │
│  ┌─────────┬──────────┬──────────┬──────────┬─────────────┐ │
│  │         │   Sept   │   Oct    │   Nov    │    Déc      │ │
│  ├─────────┼──────────┼──────────┼──────────┼─────────────┤ │
│  │Sessions │  15 230  │  10 450  │  16 800  │   18 750    │ │
│  │Revenue  │ 168 500€ │ 125 200€ │ 195 400€ │  358 150€   │ │
│  │Conv.    │   3.8%   │   3.2%   │   4.1%   │    4.8%     │ │
│  └─────────┴──────────┴──────────┴──────────┴─────────────┘ │
└─────────────────────────────────────────────────────────────┘
```
- Tableau sobre, lignes alternées légères
- Mise en évidence de la meilleure/pire valeur par ligne
- Pas de bordures lourdes, juste des séparateurs subtils

### 8. **Insights & Recommandations** (valeur ajoutée consultant)
```
┌─────────────────────────────────────────────────────────────┐
│  💡 Recommandations stratégiques                            │
│                                                              │
│  ┌─ 🎯 PRIORITÉ HAUTE ─────────────────────────────────────┐│
│  │ 1. Optimiser l'étape livraison                          ││
│  │    Le taux de drop entre panier et livraison (-23%)     ││
│  │    suggère des frais de port dissuasifs.                ││
│  │    → Tester la livraison offerte dès 80€                ││
│  └─────────────────────────────────────────────────────────┘│
│                                                              │
│  ┌─ 📈 CROISSANCE ─────────────────────────────────────────┐│
│  │ 2. Capitaliser sur le SEO                               ││
│  │    Premier canal d'acquisition avec le meilleur ROI...  ││
│  └─────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
```
- Cartes avec bordure colorée à gauche (priorité = rouge, croissance = vert)
- Icônes pour scanner rapidement
- Structure : Constat → Donnée → Action

### 9. **Footer méthodologie**
```
┌─────────────────────────────────────────────────────────────┐
│  📋 Méthodologie                                            │
│  • Données : Export GA4 simulé, Sept-Déc 2025              │
│  • Nettoyage : Agrégation journalière → mensuelle          │
│  • Anomalies : Pic du 02/12 identifié (Black Friday)       │
│  • Calculs : Taux conversion = purchases/sessions × 100    │
│                                                    © 2025   │
└─────────────────────────────────────────────────────────────┘
```
- Texte petit, discret mais présent
- Fond légèrement plus sombre que le reste

---

## ✨ Effets & Interactions

### Micro-animations (subtiles)
```css
/* Cartes KPI au hover */
.kpi-card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.kpi-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(0,0,0,0.12);
}

/* Apparition au scroll (optionnel) */
.fade-in {
  animation: fadeIn 0.6s ease-out forwards;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
```

### Tooltips sur graphiques
- Fond sombre semi-transparent
- Texte blanc, padding généreux
- Flèche pointant vers le point de données

---

## 📱 Responsive

### Breakpoints
```css
/* Tablette */
@media (max-width: 1024px) {
  .kpi-grid { grid-template-columns: repeat(3, 1fr); }
  .two-columns { grid-template-columns: 1fr; }
}

/* Mobile */
@media (max-width: 640px) {
  .kpi-grid { grid-template-columns: repeat(2, 1fr); }
  h1 { font-size: 1.75rem; }
  .kpi-value { font-size: 1.75rem; }
}
```

---

## 🚫 Ce qu'il faut éviter

- ❌ Trop de couleurs différentes (max 5 + neutres)
- ❌ Graphiques 3D (illisibles et datés)
- ❌ Texte trop petit (min 14px pour le corps)
- ❌ Trop d'informations par section
- ❌ Bordures épaisses et ombres dures
- ❌ Animations distrayantes
- ❌ Pie charts pour plus de 5 catégories

---

## ✅ Checklist finale design

- [ ] Hiérarchie visuelle claire (on sait où regarder en premier)
- [ ] Contraste suffisant (WCAG AA minimum)
- [ ] Espaces blancs généreux (le contenu respire)
- [ ] Cohérence des couleurs et typos
- [ ] Graphiques lisibles sans zoomer
- [ ] Responsive tablette fonctionnel
- [ ] Temps de chargement < 2s
- [ ] Impression PDF propre si besoin