---
name: job-scraper
description: >
  Scrapes French job sites for new positions matching your profile. Deduplicates across runs.
  Triggers on: job scrape, find jobs, search jobs, new jobs, job search, scrape jobs, /scrape
allowed-tools: Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion
---

# Job Scraper

---

## How It Works

This skill searches multiple **French job portals** using targeted queries based on your profile, deduplicates against previously seen jobs and the application tracker, and presents new matches with a quick fit assessment. All searches target the **Lille metropolitan area (≤30 km)**.

## Invocation

The user triggers this skill by saying things like:
- "Find new jobs"
- "Scrape for jobs"
- "Any new positions?"
- "/scrape"

Optional arguments:
- A focus area, e.g. "/scrape rh" or "/scrape admin" or "/scrape compta"
- "broad" to run all search categories, e.g. "/scrape broad"

---

## Execution Steps

### Step 0: Load State

1. Read `job_scraper/seen_jobs.json` (create if missing - start with `{"seen": {}}`)
2. Read `job_search_tracker.csv` to extract already-applied companies+roles
3. Read `search-queries.md` (this directory) for the search strategy

### Step 1: Search

Run **WebSearch** queries from `search-queries.md`. By default, run **Priorité 1 + Priorité 2**. If the user said "broad", run all 5 priority categories.

If the user specified a focus area:
- `/scrape admin` → Priorité 1 uniquement
- `/scrape rh` → Priorité 2 uniquement
- `/scrape compta` → Priorité 3 uniquement
- `/scrape accueil` → Priorité 4 uniquement

For each search:
- Use `WebSearch` with site-specific queries targeting **francetravail.fr**, **indeed.fr**, **hellowork.com**, **linkedin.com/jobs**, **jobijoba.com**
- Target the **Lille +30 km** geographic area (see Filtre Géographique in search-queries.md)
- Look for postings from the **last 14 days**

### Step 2: Fetch & Parse

For each promising result from Step 1:
- Use `WebFetch` to retrieve the job posting page
- Extract: **job title**, **company**, **location**, **posting date** (or "recent"), **URL**, **key requirements** (brief), **application deadline** (if listed)
- Skip if the URL or company+title combo already exists in `seen_jobs.json`
- Skip if the company+role already appears in `job_search_tracker.csv`
- **Skip if location is outside the Lille +30 km zone** (see Filtre Géographique in search-queries.md)

### Step 3: Quick Fit Assessment

For each new job, do a rapid fit check (NOT the full evaluation from `04-job-evaluation.md` - just a quick signal):

- **High match**: Role directly involves core skills (gestion administrative, saisie, accueil, RH)
- **Medium match**: Role is adjacent to experience (comptabilité de caisse, relation client)
- **Low match**: Role requires significant skills currently lacking (SIRH avancé, comptabilité générale)

### Step 4: Deduplicate & Store

1. Add ALL fetched jobs (new and skipped) to `seen_jobs.json` with structure:
```json
{
  "seen": {
    "<url_or_company_title_key>": {
      "title": "...",
      "company": "...",
      "url": "...",
      "first_seen": "YYYY-MM-DD",
      "fit": "high/medium/low",
      "status": "new/skipped/evaluated"
    }
  }
}
```
2. Only present jobs NOT already in the seen list or tracker.

### Step 5: Present Results

Present new jobs in a table sorted by fit (high first):

```
## Nouvelles Offres — YYYY-MM-DD

Trouvé X nouvelles offres (Y haute, Z moyenne, W faible correspondance).

| # | Fit | Poste | Entreprise | Localisation | Deadline | Lien |
|---|-----|-------|------------|--------------|----------|------|
| 1 | 🟢 Haute | ... | ... | Lille (5 km) | ... | [Voir](...) |

### Points forts des offres haute correspondance
Pour chaque offre haute correspondance, ajouter 2-3 points :
- Pourquoi elle correspond au profil
- Compétences clés à vérifier
- Points d'attention ou red flags
```

After presenting, ask:
> "Tu veux que j'évalue une de ces offres en détail ? Donne-moi le numéro."

If the user picks a number, invoke the **job-application-assistant** skill workflow (fit evaluation first, then CV + cover letter if approved).

### Step 6: Update Tracker (Optional)

If the user decides to apply to any job, add a row to `job_search_tracker.csv`.

---

## Important Rules

1. **Never fabricate job postings.** Only present jobs found via actual WebSearch/WebFetch results.
2. **Respect deduplication.** Always check seen_jobs.json AND job_search_tracker.csv before presenting.
3. **Strict geographic filter.** Skip any job outside the Lille +30 km zone — this is a hard deal-breaker. Flag "zone limite" (20-30 km) jobs with a ⚠️ marker.
4. **Only open positions.** Skip postings with expired deadlines or those marked as closed.
5. **Be efficient with WebFetch.** Don't fetch every search result — use titles and snippets to pre-filter before fetching full pages.
6. **Parallel searches.** Use the Agent tool or parallel WebSearch calls to speed up the search phase.
7. **French portals only.** Do NOT use Danish portals (jobindex.dk, jobbank.dk, jobdanmark.dk, jobnet.dk, karriere.dk). The target market is France / Lille.
