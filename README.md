# Assistant de Recherche d'Emploi IA (Lille +30km)

<p align="center">
  <img src="claude_animation.gif" alt="Assistant IA Recherche d'Emploi" width="200">
</p>

Bienvenue dans votre espace personnalisé de recherche d'emploi ! Cet outil utilise l'intelligence artificielle (**Google Antigravity** ou **Claude Code**) pour vous aider à trouver des offres d'emploi autour de **Lille (dans un rayon de 30 km)**, évaluer si elles vous correspondent, et rédiger automatiquement votre **CV** et votre **lettre de motivation** sur-mesure en format PDF professionnel.

> [!NOTE]  
> Ce guide est spécialement rédigé pour les personnes n'ayant pas de compétences techniques particulières en informatique. Suivez simplement les étapes ci-dessous pas à pas.

---

## 💡 Comment ça marche ?

Au lieu d'envoyer le même CV générique à toutes les entreprises, l'assistant IA va analyser chaque offre d'emploi et adapter vos documents pour vous donner le maximum de chances d'obtenir un entretien.

```
 /setup             /scrape              /apply <lien>
   |                   |                       |
   v                   v                       v
Créer votre        Rechercher des         Analyser l'offre,
profil de base     offres sur Lille       adapter le CV et rédiger
   |               (+30 km)               la lettre de motivation
   v                   |                       |
Fichiers de            v                       v
profil prêts       Afficher les offres     Vérifier la mise en page
                   triées par pertinence   et générer les PDF finaux
```

---

## 🛠️ Prérequis (À installer une seule fois)

Pour utiliser cet outil, vous devez installer trois éléments gratuits sur votre ordinateur :

### 1. L'assistant IA (Google Antigravity ou Claude Code)
C'est le programme avec lequel vous allez discuter.
*   **Si vous utilisez Google Antigravity (Recommandé) :** Installez l'outil `agy`.
*   **Si vous utilisez Claude Code :** Ouvrez l'application *Terminal* (ou *Invite de commandes* sur Windows) et tapez la commande suivante :
    ```bash
    npm install -g @anthropic-ai/claude-code
    ```

### 2. Le moteur de recherche d'emploi (Bun)
Cet outil permet à l'IA d'aller chercher les offres d'emploi sur internet (LinkedIn, etc.).
*   Ouvrez votre terminal et copiez-collez cette commande :
    ```bash
    curl -fsSL https://bun.sh/install | bash
    ```

### 3. Le générateur de PDF professionnels (LaTeX)
Pour que vos CV et lettres de motivation soient magnifiques et parfaitement mis en page, nous utilisons un système professionnel appelé LaTeX.
*   **Sur Windows :** Téléchargez et installez le logiciel gratuit [MiKTeX](https://miktex.org/download) en cochant toutes os options par défaut.
*   **Sur Mac :** Téléchargez et installez [MacTeX](https://tug.org/mactex/).
*   **Sur Linux (Ubuntu/Debian) :** Tapez cette commande dans votre terminal :
    ```bash
    sudo apt install texlive-full
    ```

---

## 🚀 Guide étape par étape (Pour commencer)

### Étape 1 : Préparer vos documents existants
1. Dans le dossier du projet, vous trouverez un sous-dossier nommé `documents/`.
2. Glissez-y votre CV actuel (au format PDF ou Word) et éventuellement une version PDF de votre profil LinkedIn ou vos diplômes.

### Étape 2 : Lancer l'assistant
Ouvrez votre terminal dans le dossier du projet et tapez la commande de l'assistant de votre choix :
```bash
# Si vous utilisez Google Antigravity :
agy

# Si vous utilisez Claude Code :
claude
```

### Étape 3 : Configurer votre profil pour Lille
Une fois connecté à l'assistant (vous verrez un écran de discussion), tapez la commande suivante :
```text
/setup
```
L'assistant va vous poser des questions simples en français. **Indiquez-lui que vous recherchez des postes à Lille et ses alentours (rayon de 30 km)**. L'IA va lire les documents de l'Étape 1 pour remplir automatiquement votre profil (diplômes, expériences, compétences) et configurer votre zone géographique.

### Étape 4 : Rechercher des offres d'emploi
Pour voir les offres disponibles en ce moment, tapez :
```text
/scrape
```
L'IA va scanner LinkedIn pour la région de **Lille (+30 km)** et vous présenter un tableau des postes disponibles, triés par niveau de compatibilité avec votre profil (Compatibilité Haute, Moyenne ou Basse).

### Étape 5 : Postuler à une offre
Dès que vous repérez une offre intéressante, donnez le lien à l'IA ou copiez-collez le texte de l'offre :
```text
/apply [collez le lien ou le texte de l'offre d'emploi ici]
```
L'IA va alors :
1. Analyser en détail l'offre d'emploi.
2. Adapter votre CV (mettre en avant les expériences les plus pertinentes pour ce poste).
3. Rédiger une lettre de motivation ciblée (par exemple, expliquant pourquoi travailler à Lille dans cette entreprise vous motive).
4. Relire et ajuster automatiquement les documents pour qu'ils soient parfaits.

### Étape 6 : Télécharger vos PDF prêts à l'envoi
Une fois que l'IA a terminé d'adapter vos fichiers, quittez l'assistant en tapant `/exit`. Dans votre terminal normal, tapez ces deux commandes simples pour générer vos fichiers PDF finaux :

```bash
# Pour générer votre CV (dans le dossier cv/)
cd cv && lualatex main_<nom_de_l_entreprise>.tex && cd ..

# Pour générer votre lettre de motivation (dans le dossier cover_letters/)
cd cover_letters && xelatex cover_<nom_de_l_entreprise>_<poste>.tex && cd ..
```
Vos documents PDF prêts à être envoyés se trouveront dans les dossiers `cv/` et `cover_letters/` !

---

## 📂 Organisation de vos fichiers

Voici où sont rangées les informations importantes si vous souhaitez les consulter ou les modifier à la main :

| Dossier ou Fichier | À quoi sert-il ? |
| :--- | :--- |
| `documents/` | C'est ici que vous déposez votre CV de départ pour que l'IA le lise. |
| `cv/` | Contient les CV générés pour chaque entreprise au format LaTeX (`.tex`) et PDF. |
| `cover_letters/` | Contient les lettres de motivation rédigées pour chaque poste. |
| `job_search_tracker.csv` | Un tableau Excel/CSV simple qui enregistre toutes les entreprises où vous avez postulé pour suivre vos candidatures. |
| `.agents/rules/job-application-rules.md` | Les consignes que l'IA doit suivre (comme "rédiger dans un ton professionnel en français"). |

---

## 💡 Conseils pour obtenir les meilleurs résultats

*   **Soyez précis lors de l'entretien de départ (`/setup`) :** Plus vous donnez de détails à l'IA sur ce que vous savez faire (outils maîtrisés, projets réalisés), plus vos CV et lettres de motivation seront convaincants et uniques.
*   **Vérifiez toujours les dates et contacts :** Même si l'IA fait tout le travail de mise en page et de rédaction, relisez les PDF générés pour vérifier que vos coordonnées de contact et les dates sont correctes avant d'envoyer votre candidature !

Bonne chance dans vos recherches d'emploi sur la métropole lilloise ! 🚀
