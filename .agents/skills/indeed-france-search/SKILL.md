---
name: indeed-france-search
version: 1.0.0
description: >
  Utiliser ce skill pour rechercher des offres d'emploi sur Indeed France (indeed.fr),
  le plus grand agrégateur d'offres privé en France. Déclencher pour toute recherche
  d'emploi sur Indeed, emploi en France, offres sur Indeed Lille, indeed.fr,
  ou quand l'utilisateur mentionne Indeed dans le contexte français.
  Phrases déclencheurs : Indeed France, indeed.fr, chercher sur Indeed, offres Indeed Lille,
  emploi Indeed Hauts-de-France.
context: fork
allowed-tools: Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion
---

# Indeed France Search Skill

Recherche d'offres d'emploi sur **indeed.fr** — le plus grand agrégateur d'offres d'emploi
en France (agrège France Travail, offres directes d'entreprises, cabinets de recrutement,
intérim). Volume très élevé, mis à jour en temps réel.

## ⚠️ Zone géographique : Lille +30 km uniquement

## Quand utiliser ce skill

- Rechercher des offres d'assistante administrative, secrétaire, RH à Lille sur Indeed
- Compléter une recherche France Travail avec les offres exclusives aux entreprises
- Trouver des offres d'intérim ou de CDD dans les Hauts-de-France

## Méthode de recherche (via WebSearch + WebFetch)

### Requêtes WebSearch directes

```
site:indeed.fr "assistante administrative" Lille
site:indeed.fr "secrétaire administrative" Lille
site:indeed.fr "assistant administratif" "Hauts-de-France"
site:indeed.fr "assistante RH" Lille
site:indeed.fr "aide comptable" Lille
site:indeed.fr "hôtesse d'accueil" Lille
```

### URL de recherche directe Indeed France

```
https://fr.indeed.com/emplois?q=TERMES&l=Lille%2C+Nord&radius=30
```

Remplacer `TERMES` par le titre du poste (ex. `assistante+administrative`).

### Extraction par offre

Pour chaque résultat WebFetch :
- **Titre** et **type de contrat** (CDI/CDD/Intérim)
- **Entreprise** (parfois masquée "Employeur confidentiel")
- **Lieu** (ville + distance approximative de Lille)
- **Salaire** (si affiché)
- **Date de publication**
- **URL** Indeed + **lien "Postuler"**

## Avantages d'Indeed France vs France Travail

| Critère | France Travail | Indeed.fr |
|---------|---------------|-----------|
| Offres publiques | ✅ Toutes | ✅ Agrège |
| Offres directes entreprises | ❌ Partiel | ✅ Volume élevé |
| Offres intérim | ❌ Partiel | ✅ |
| PME/TPE locales | ✅ | ✅ |
| Multinationales Lille | ❌ Partiel | ✅ |

## Requêtes complémentaires efficaces

```
indeed.fr "assistante de direction" Lille -Paris
site:indeed.fr "secrétariat" "Villeneuve-d'Ascq" OR "Roubaix" OR "Tourcoing"
site:indeed.fr "gestionnaire administratif" "59" CDI
```

## Règles

1. **Zone géographique stricte** : Lille +30 km uniquement.
2. **Offres actives** : Vérifier la date de publication (< 14 jours idéalement).
3. **Déduplication** : Croiser avec `seen_jobs.json` et `job_search_tracker.csv`.
4. **Ne pas fabriquer d'offres** : Uniquement résultats réels WebSearch/WebFetch.
