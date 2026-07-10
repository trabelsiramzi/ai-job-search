---
name: francetravail-search
version: 1.0.0
description: >
  Utiliser ce skill pour rechercher des offres d'emploi sur France Travail (francetravail.fr,
  ex-Pôle Emploi), le principal portail public d'emploi en France. Déclencher pour toute
  recherche d'offres dans la région lilloise, les Hauts-de-France, ou le marché français en général.
  Phrases déclencheurs : France Travail, Pôle Emploi, francetravail.fr, offres d'emploi France,
  chercher un emploi en France, emploi Lille, offres Hauts-de-France, assistante administrative Lille,
  secrétaire Lille, emploi administration Lille, RH Lille, comptabilité Lille.
context: fork
allowed-tools: Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion
---

# France Travail Search Skill

Recherche d'offres d'emploi sur **francetravail.fr** (ex-Pôle Emploi), le plus grand portail
public d'emploi en France. Couvre tous les secteurs, mis à jour en temps réel, gratuit et sans
authentification pour la consultation des offres.

## ⚠️ Zone géographique : Lille +30 km uniquement

Toutes les recherches sont filtrées sur la métropole lilloise. Ne pas présenter d'offres hors zone.

## Quand utiliser ce skill

- Rechercher des offres d'assistante administrative, secrétaire, assistante RH à Lille
- Rechercher des offres d'aide comptable, employé administratif dans les Hauts-de-France
- Consulter une offre spécifique sur France Travail (URL ou numéro d'offre)
- Trouver des offres récentes dans un périmètre de 30 km autour de Lille

## Méthode de recherche (via WebSearch + WebFetch)

Ce skill utilise WebSearch et WebFetch pour accéder à France Travail — pas de CLI disponible.

### Étape 1 : Construire les requêtes

Utiliser les requêtes de `search-queries.md` (catégories Priorité 1 à 5) qui sont déjà formatées pour francetravail.fr :

```
site:francetravail.fr "assistante administrative" Lille
site:francetravail.fr "secrétaire administrative" Lille
site:francetravail.fr "assistant administratif" "59"
```

### Étape 2 : Recherche directe sur France Travail (optionnel)

L'URL de recherche directe France Travail :
```
https://www.francetravail.fr/offres/recherche.aspx?motsCles=TERMES&lieux=75999&rayon=30&tri=1
```

Remplacer `TERMES` par les mots-clés du poste. Le code `75999` correspond à Lille.

### Étape 3 : Extraire les offres

Pour chaque résultat :
- **Titre du poste** (ex. "Assistante administrative H/F")
- **Entreprise** (ou "Non communiqué" si masquée)
- **Lieu** (ville + département)
- **Type de contrat** (CDI, CDD, Intérim, etc.)
- **Date de publication** / **Date limite**
- **URL** (lien direct vers l'offre)
- **Référence France Travail** (ex. `166MRHJ`)

### Étape 4 : Quick fit assessment

| Correspondance | Critère |
|---|---|
| 🟢 Haute | Poste d'assistante administrative, secrétaire, assistante de direction |
| 🟡 Moyenne | Assistante RH, aide comptable, chargée de clientèle |
| 🔴 Faible | Poste nécessitant SIRH avancé, comptabilité générale |

## Codes ROME pertinents pour le profil

Lors d'une recherche avancée sur France Travail, utiliser ces codes ROME pour filtrer :

| Code ROME | Métier |
|-----------|--------|
| M1607 | Secrétariat |
| M1501 | Assistanat en ressources humaines |
| M1203 | Comptabilité |
| M1601 | Accueil et renseignements |
| M1604 | Assistanat de direction |

## Filtres géographiques France Travail

- **Département** : 59 (Nord) — toujours prioritaire
- **Rayon** : 30 km autour de Lille
- **Villes incluses** : Lille, Villeneuve-d'Ascq, Roubaix, Tourcoing, Marcq-en-Barœul, Seclin, Armentières, Lens (⚠️ 30 km limite)

## Exemple de requêtes efficaces

```
site:francetravail.fr "assistante administrative" "59" CDI
site:francetravail.fr "secrétaire" Lille "offre d'emploi"
site:francetravail.fr "assistante RH" "Hauts-de-France"
francetravail.fr assistante administrative Lille -Dunkerque -Calais
```

## Règles

1. **Zone géographique stricte** : Exclure toutes offres hors Lille +30 km.
2. **Offres actives uniquement** : Vérifier que la date limite n'est pas dépassée.
3. **Ne pas fabriquer d'offres** : Uniquement les résultats réels de WebSearch/WebFetch.
4. **Déduplication** : Croiser avec `seen_jobs.json` et `job_search_tracker.csv`.
