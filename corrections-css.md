## A) Corriger le HTML : `<!DOCTYPE html>` en trop à la fin

Votre fichier se termine par :
```

</html><!DOCTYPE html>
```

À corriger :

* supprimer le `<!DOCTYPE html>` en trop (il doit apparaître **une seule fois**, tout au début)

---

## B) Normalize.css : le mettre en local (consigne)

Actuellement :
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css"/>
```

À corriger :

* télécharger normalize en `./css/normalize.css`
* puis :
```

<link rel="stylesheet" href="./css/normalize.css">
```

💡 *En local, votre site marche même si Internet bloque des ressources externes.*

---

## C) Taille de texte : ajouter une utilisation de `em`

Vous avez :

* `px` ✅ (ex: `p { font-size: 28px; }`)
* `rem` ✅ (ex: `h2 { font-size: 2rem; }`)
* mais pas de `em` clairement

À ajouter (exemple) :
```
footer {
font-size: 1.1em;
}
```

💡 *L’exercice demande les 3 unités pour comparer leur comportement.*

> *`em` dépend de la taille du parent, donc c’est utile pour des zones spécifiques.*

---

## D) Centrage + largeur max : votre `.page` est bien écrite mais pas utilisée

Vous avez ce CSS :
```
.page {
max-width: 800px;
margin: 0 auto;
padding: 20px;
}
```

Mais dans le HTML, aucun élément n’a `class="page"`.

À corriger :

* envelopper le contenu (ou au minimum `<main>`) dans une div `.page` :
```

<div class="page">
  <header>...</header>
  <main>...</main>
  <footer>...</footer>
</div>
```

💡 *Le CSS ne s’applique que si le sélecteur correspond à un élément existant.*

> *Si une classe n’est pas utilisée, son style ne sert à rien.*

---

## E) Image trop grande : `.pelien { width: 800px; }` n’est pas responsive

Actuellement :
```
.pelien {
width: 800px;
}
```

Problème :

* sur mobile, 800px peut dépasser l’écran

À corriger (responsive) :
```
.pelien {
max-width: 800px;
width: 100%;
height: auto;
display: block;
margin: 0 auto;
}
```

💡 *On veut une image qui s’adapte à l’écran.*

> *`max-width` limite, `width: 100%` rend fluide.*

---

## F) Police : `@font-face` OK, mais le chemin semble faux

Dans `main.css` (qui est dans `css/`), vous avez :
```
src: url('fonts/bangers-regular.woff2')
```

Si votre police est dans `fonts/` à la racine du projet, depuis `css/main.css` il faut remonter :
```
src: url('../fonts/bangers-regular.woff2')
```

> *Quand on est dans `css/`, on doit souvent utiliser `../` pour remonter.*

---

## G) HTML : structure des titres (plus propre)

Vous avez 2 fois un `h1` :

* `Bienvenue sur mon CV` (dans le header)
* `Je me présente :` (dans le main)

À corriger :

* garder un seul `h1` pour le titre principal
* transformer l’autre en `h2`

💡 *Un seul `h1` améliore la structure et l’accessibilité.*

> *Les titres doivent être hiérarchisés (`h1` → `h2` → `h3`).*

---

## H) Liens externes : ouvrir dans un nouvel onglet (optionnel mais conseillé)

Pour les liens vers YouTube/Instagram/X :
```
<a href="..." target="_blank" rel="noopener noreferrer">...</a>
```

> *`noopener` protège contre certaines manipulations entre onglets.*
