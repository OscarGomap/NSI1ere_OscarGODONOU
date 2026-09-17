# Site de cours - Première NSI (O. Godonou)

Ce site est construit avec [MkDocs](https://www.mkdocs.org/) et le thème
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/). Il est
100 % gratuit à héberger sur **GitHub Pages**.

## Tester le site en local (facultatif)

```bash
pip install -r requirements.txt
mkdocs serve
```

Puis ouvrir http://127.0.0.1:8000 dans un navigateur.

## Mettre le site en ligne sur GitHub Pages

1. **Créer un dépôt GitHub** (public, gratuit) — par exemple nommé `1NSI`.
2. **Pousser ce dossier** dans le dépôt :
   ```bash
   git init
   git add .
   git commit -m "Premier import du site"
   git branch -M main
   git remote add origin https://github.com/VOTRE-PSEUDO/1NSI.git
   git push -u origin main
   ```
3. Dans les **paramètres du dépôt** sur GitHub (Settings → Pages), régler
   "Build and deployment" → **Source : Deploy from a branch**, puis choisir
   la branche `gh-pages` (elle sera créée automatiquement par le workflow
   au premier push, dossier `/ (root)`).
4. À chaque `git push` sur `main`, le site est reconstruit et republié
   automatiquement grâce au workflow `.github/workflows/deploy.yml`.
5. Le site sera accessible à l'adresse :
   `https://VOTRE-PSEUDO.github.io/1NSI/`

## Ajouter du contenu

- Chaque page est un simple fichier **Markdown** (`.md`) dans le dossier `docs/`.
- Pour ajouter une nouvelle page, créer le fichier `.md` puis l'ajouter dans
  la liste `nav:` du fichier `mkdocs.yml`.
- Les blocs `!!! note`, `!!! example`, `!!! tip`, `!!! warning` créent les
  encadrés colorés (admonitions). Les blocs `??? abstract` créent des
  corrections repliables/dépliables.
