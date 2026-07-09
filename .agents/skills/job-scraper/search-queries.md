# Search Queries for Job Scraper (France / Lille +30km)

<!-- Mis à jour le 2026-07-09 — Configuration complète marché français/lillois -->

## Search Sites

Primary (marché français) :
- **francetravail.fr** — Plus grand portail public français (ex-Pôle Emploi)
- **indeed.fr** — Indeed France, volume élevé, tous secteurs
- **linkedin.com/jobs** — Profils professionnels, RH, admin, cadres
- **hellowork.com** — Généraliste, très présent en région Nord
- **jobijoba.com** — Agrégateur (France Travail + partenaires)
- **welcometothejungle.com** — Entreprises modernes, startups
- **apec.fr** — Cadres, bac+3/5
- **monster.fr** — Généraliste, bonne couverture PME/ETI

Secondary (pages carrières via Google) :
- Recherches `site:` sur les grandes entreprises lilloise : Decathlon, Leroy Merlin, Auchan, Kiabi, La Redoute, OVHcloud, Bonduelle, Worldline, Fnac Darty, CCI Hauts-de-France

---

## Query Categories

Par défaut : exécuter **Priorité 1 + 2**. Avec "broad" : toutes les priorités.

---

### Priorité 1 — Gestion Administrative & Secrétariat ⭐

Correspondance maximale avec les compétences et aspirations de Zeineb.

```
site:francetravail.fr "assistante administrative" Lille
site:francetravail.fr "secrétaire administrative" Lille
site:francetravail.fr "assistant administratif" "59"
site:francetravail.fr "secrétaire" Lille "Nord"
site:indeed.fr "assistante administrative" Lille
site:indeed.fr "secrétaire administrative" Lille
site:indeed.fr "assistant administratif" "Hauts-de-France"
site:hellowork.com "assistante administrative" Lille
site:jobijoba.com "assistante administrative" Lille
site:linkedin.com/jobs "assistante administrative" Lille France
site:linkedin.com/jobs "secrétaire de direction" Lille France
"assistante administrative" Lille -site:linkedin.com
```

---

### Priorité 2 — Ressources Humaines (Administration du Personnel) ⭐

Forte correspondance : communication, gestion de dossiers, médiation.

```
site:francetravail.fr "assistante RH" Lille
site:francetravail.fr "chargée de recrutement" Lille
site:francetravail.fr "gestionnaire RH" "59"
site:indeed.fr "assistante ressources humaines" Lille
site:indeed.fr "chargée de recrutement" Lille
site:welcometothejungle.com "assistante RH" Lille
site:linkedin.com/jobs "administration RH" Lille France
site:linkedin.com/jobs "chargé de recrutement" Lille France
site:hellowork.com "assistante RH" Lille
"assistante RH" OR "chargée RH" Lille "Nord" site:francetravail.fr
```

---

### Priorité 3 — Assistanat Comptable & Gestion

Correspondance adjacente : caisse, stocks, saisie comptable.

```
site:francetravail.fr "assistant comptable" Lille
site:francetravail.fr "aide comptable" "59"
site:francetravail.fr "employé administratif et comptable" Lille
site:indeed.fr "assistant comptable" Lille
site:indeed.fr "aide comptable" "Hauts-de-France"
site:hellowork.com "assistant comptable" Lille
site:jobijoba.com "aide comptable" Lille
```

---

### Priorité 4 — Relation Client & Accueil

Rôles pivot exploitant l'expérience téléopératrice et accueil client.

```
site:francetravail.fr "chargée de clientèle" Lille
site:francetravail.fr "hôtesse d'accueil" Lille
site:francetravail.fr "téléconseillère" "59"
site:indeed.fr "chargée de clientèle" Lille
site:indeed.fr "téléconseillère" Lille
site:indeed.fr "hôtesse d'accueil" Lille
site:hellowork.com "conseillère clientèle" Lille
```

---

### Priorité 5 — Support Administratif Large (filet large)

```
site:francetravail.fr "gestion administrative" Lille
site:francetravail.fr "agent administratif" "59"
site:francetravail.fr "employé de bureau" Lille
site:indeed.fr "gestion administrative" "Lille"
site:linkedin.com/jobs "secrétariat" Lille
site:monster.fr "assistante administrative" Lille
"agent administratif" OR "employé administratif" Lille site:francetravail.fr
```

---

## Filtre Géographique — Lille +30km

**RÈGLE : n'inclure que les offres dont le lieu de travail est ≤ 30km de Lille (centre).**

### Zone Idéale (0–10 km) ✅
Lille, Villeneuve-d'Ascq, Marcq-en-Barœul, Lambersart, La Madeleine, Lomme, Loos, Hellemmes, Faches-Thumesnil, Mons-en-Barœul

### Zone Acceptable (10–20 km) ✅
Roubaix, Tourcoing, Armentières, Seclin, Lesquin, Lezennes, Wasquehal, Mouvaux, Croix, Hem, Wattrelos, Halluin, Comines

### Zone Limite (20–30 km) ⚠️ inclure mais signaler
Lens, Douai, Béthune, Orchies, Don, Carvin, La Bassée, Bailleul

### Trop Loin ❌ — exclure systématiquement
Paris, Bruxelles, Amiens, Valenciennes (50 km), Maubeuge, Dunkerque, Calais, Boulogne-sur-Mer, Hazebrouck (43 km)

### Télétravail complet ✅
Inclure si le poste est 100% remote — signaler "remote" dans la colonne localisation.

---

## Filtre Date

- **Inclure** : offres publiées dans les **14 derniers jours** OU date limite non expirée.
- **Signaler** : offres sans date visible → inclure mais marquer `"date": "unknown"`.
- **Exclure** : offres clôturées ou publiées il y a plus de 30 jours.

---

## Commandes Rapides

- `/scrape` → Priorités 1 + 2 (défaut)
- `/scrape broad` → Toutes les 5 priorités
- `/scrape rh` → Priorité 2 + requêtes LinkedIn RH
- `/scrape admin` → Priorité 1 uniquement
- `/scrape compta` → Priorité 3 uniquement
- `/scrape [ville]` → Filtrer sur une ville spécifique dans la zone +30km
