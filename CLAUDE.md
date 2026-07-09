# Job Application Assistant for Zeineb HASSAN

<!-- SETUP: This file is populated by running /setup -->
<!-- Setup completed successfully on 2026-07-09 -->

## Role
This repo is a job application workspace. Antigravity acts as a career advisor and application assistant for Zeineb HASSAN, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

### Identity
- **Name:** Zeineb HASSAN
- **Location:** Lille, France (Max 30km de distance / métropole lilloise)
- **Languages:** Français (courant), Arabe (maternelle), Anglais (courant), Allemand (notions)
- **Status:** En reconversion professionnelle
- **LinkedIn headline:** "En reconversion vers les Ressources Humaines, la Gestion Administrative et la Comptabilité"

### Education
- **Licence appliquée in Sciences de l'Éducation** (2018-2021) - ISEAH de Zaghouan (Zaghouan, Tunisie)
  - Thesis: "Les enfants à haut potentiel en Tunisie : réalités et perspectives"
  - Topics: Sciences de l'éducation, pédagogie, psychologie de l'enfant
- **Baccalauréat in Sciences Expérimentales** (2018) - Lycée Assad Ibn Elfourat (Tunisie)
  - Topics: Sciences physiques, chimie, biologie, mathématiques

### Professional Experience
- **Assistante administrative** (01/2025 - 06/2025) - **Bureau Vallée** (Tunis, Tunisie)
  - Gestion des encaissements et suivi quotidien de la caisse
  - Saisie, classement et archivage de documents administratifs et comptables
  - Suivi des stocks et mise à jour régulière des données sur le logiciel SDP
  - Accueil physique et orientation des clients (gestion de flux)
- **Professeure des écoles primaires** (09/2020 - 12/2024) - **École primaire l'Espoir** (Tunisie)
  - Gestion et suivi administratif des dossiers des élèves et des évaluations
  - Planification et organisation d'activités adaptées aux enfants à besoins spécifiques
  - Communication et gestion de la relation interne (administration) et externe (parents d'élèves)
  - Médiation et résolution de conflits au sein de la classe et de l'établissement
- **Téléopératrice** (04/2019 - 10/2019) - **JWS Groupe** (Tunis, Tunisie)
  - Gestion de la relation clientèle à distance et suivi des dossiers clients
  - Prospection commerciale par téléphone et reporting d'activité
  - Atteinte d'objectifs quantitatifs et qualitatifs

### Technical Skills
- **Primary:** Gestion administrative, Saisie de données, Accueil & relation client, Pack Office (Word, Excel, PowerPoint)
- **Secondary:** Ressources humaines, Comptabilité de caisse, Gestion des stocks, Logiciel SDP
- **Domain:** Administration de bureau, Enseignement & Pédagogie, Relation client (téléphonie/physique)
- **Software:** Microsoft Office Suite, Logiciel SDP, Outils numériques avancés (DigComp 6)

### Certifications
- **Microsoft Tools for Startups** - ISAMM - completed 2021
- **Certificat de secourisme** - Ministère de la santé - completed 2021

### Publications
- Aucune

### Awards
- Aucune

### Behavioral Profile
- **Rigoureuse et autonome** - Grand respect des processus et de l'exactitude des saisies administratives
- **Excellente communicante** - Capacité à s'adapter à des interlocuteurs variés (parents, clients, direction)
- **Strengths:** Rigueur, organisation, écoute active, médiation de conflits
- **Growth areas:** Perfectionnisme (vérification multiple des dossiers administrés)
- **Thrives in:** Environnements structurés, collaboratifs et valorisant l'accueil ou le service

### What Excites You
- L'organisation de projets culturels ou logistiques
- L'accompagnement individuel et la résolution de problèmes complexes (administratifs ou relationnels)

### Target Sectors
- **Gestion administrative et Assistanat** : Cabinets médicaux, PME, administrations publiques, Établissements scolaires
- **Ressources Humaines** : Agences de recrutement, services RH de PME/ETI
- **Assistanat Comptable** : Commerces de détail, PME régionales

### Deal-breakers
- Postes situés à plus de 30 km de Lille
- Environnements de travail toxiques, désorganisés ou manquant de respect de la confidentialité

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, classic style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.agents/skills/` - AI skill definitions and job search CLI tools

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Antigravity** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/classic format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Antigravity** by name
- [ ] Cover letter is addressed to the correct person (or "Madame, Monsieur," if unknown)
- [ ] Cover letter fits approximately one page
- [ ] Language is French (unless explicitly requested otherwise by the user)

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`
