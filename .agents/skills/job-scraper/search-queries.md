# Search Queries for Job Scraper (France / Lille)

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

Primary (French job market):
- **linkedin.com/jobs** - LinkedIn job listings (filter: France / Lille)
- **indeed.fr** - Indeed France
- **apec.fr** - Apec (cadres et rôles techniques/ingénieurs)
- **francetravail.fr** - France Travail (ex-Pôle Emploi)
- **welcometothejungle.com** - Welcome to the Jungle (startups et entreprises tech)

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies in the Lille region (e.g. Decathlon, Leroy Merlin, OVHcloud)

## Query Categories

Queries are grouped by priority. Each query should be combined with your location terms ("Lille", "Nord", "Hauts-de-France") where the site supports it.

### Priority 1: [YOUR_PRIMARY_ROLE_TYPE]

These match your strongest and most desired career direction.

```
site:indeed.fr "[YOUR_PRIMARY_JOB_TITLE]" "Lille"
site:apec.fr "[YOUR_PRIMARY_JOB_TITLE]" "Lille"
site:linkedin.com/jobs "[YOUR_PRIMARY_JOB_TITLE]" France
```

### Priority 2: [YOUR_DOMAIN_EXPERTISE]

These match your domain expertise.

```
site:indeed.fr [YOUR_DOMAIN_KEYWORD_1] Lille
site:welcometothejungle.com [YOUR_DOMAIN_KEYWORD_1] Lille
site:linkedin.com/jobs [YOUR_DOMAIN_KEYWORD_1] "Lille" France
```

### Priority 3: [YOUR_ADJACENT_ROLE_TYPE]

Adjacent roles you could pivot into.

```
site:indeed.fr "[YOUR_ADJACENT_TITLE_1]" [YOUR_KEY_SKILL] Lille
site:apec.fr "[YOUR_ADJACENT_TITLE_2]" [YOUR_KEY_SKILL] Lille
```

### Priority 4: Broader Technical / Consulting

Wider net for general technical roles.

```
site:indeed.fr [YOUR_KEY_SKILL] "Lille"
site:linkedin.com/jobs "[YOUR_KEY_SKILL]" Lille
site:apec.fr [YOUR_DOMAIN] Lille
```

## Location Filter (Lille +30km)

When evaluating results, verify the job location is within reasonable commute distance from Lille (maximum 30km).

Ideal areas:
- Lille (centre), Villeneuve-d'Ascq, Marcq-en-Barœul, Lambersart, La Madeleine

Acceptable areas (within 15-20km):
- Roubaix, Tourcoing, Seclin, Armentières, Lesquin

Borderline areas (within 30km / ~30-45 min commute):
- Lens, Douai, Orchies

Too far (requires relocation or full remote):
- Paris, Bruxelles, Amiens

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
