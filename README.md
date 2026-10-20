# Teranga — site web

Site vitrine de **Teranga**, services immobiliers à Montréal : peinture, nettoyage, réparations, informatique & web, sécurité & incendie.

Site 100 % statique (HTML, CSS, JavaScript), sans compilation : il se déploie tel quel.

## Structure

```
teranga-site/
├── index.html          # tout le site (styles et scripts inclus)
├── data/
│   └── gallery.json    # vidéo d'accueil + chantiers avant / après
├── media/
│   ├── hero.mp4        # vidéo d'accueil (avec son, activable par le visiteur)
│   └── ...             # photos avant / après
└── .nojekyll           # désactive Jekyll sur GitHub Pages
```

## Ajouter un chantier avant / après

1. Déposez les deux photos dans `media/` (JPEG, idéalement 1600 px de large max, moins de 500 Ko chacune).
   Nommage conseillé : `2026-10-salon-rosemont-avant.jpg` et `2026-10-salon-rosemont-apres.jpg`.
2. Ajoutez une entrée **en haut** de la liste `projects` dans `data/gallery.json` :

```json
{
  "heroVideo": "media/hero.mp4",
  "projects": [
    {
      "id": "salon-rosemont",
      "title": "Salon – 4½ Rosemont",
      "category": "Peinture",
      "before": "media/2026-10-salon-rosemont-avant.jpg",
      "after": "media/2026-10-salon-rosemont-apres.jpg",
      "date": "2026-10-20"
    }
  ]
}
```

- `id` : unique, sans espaces.
- `category` : `Peinture`, `Nettoyage`, `Réparations`, `Sécurité` ou `Informatique` (les filtres se créent automatiquement).
- Tant que `projects` est vide, le site affiche un aperçu de démonstration.

3. Faites un commit et un push : le site se met à jour tout seul.

## Changer la vidéo d'accueil

Remplacez `media/hero.mp4` (MP4, 16:9, 10 à 20 secondes, moins de 15 Mo).
Pour retirer la vidéo, mettez `"heroVideo": null` : l'animation de rubans de peinture s'affiche à la place.

## Déployer

**GitHub Pages** (gratuit) : *Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)`*.
Le site sera en ligne à `https://pds98.github.io/teranga-site/`.

**Netlify ou Vercel** (gratuit) : importez le dépôt, sans commande de build, dossier de publication `/`.
Un nom de domaine (ex. `teranga-immo.ca`) peut ensuite être branché depuis leur tableau de bord.

## Tester en local

Le site lit `data/gallery.json`, il faut donc un petit serveur (ouvrir le fichier directement ne charge pas la galerie) :

```bash
cd teranga-site
python3 -m http.server 8000
# puis ouvrir http://localhost:8000
```

## Contact

- Pape Bouna Semou Niang — 438 989-1469 (sécurité & incendie)
- Demba Sow — 819 701-8681 (informatique & génie logiciel)
