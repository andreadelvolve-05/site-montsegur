# Cours HTML & CSS : comprendre le site de Montségur, ligne par ligne

> **À qui s'adresse ce cours ?**
> À toute personne qui n'a **jamais écrit une ligne de code**. On part de zéro et on s'appuie uniquement sur le vrai code du site de Montségur que nous avons construit ensemble : les fichiers `index.html` et `style.css`.
>
> **Comment le lire ?**
> Dans l'ordre, chapitre par chapitre. Ouvrez les deux fichiers du projet à côté de ce cours : chaque exemple cité ici existe dans le code, et vous pouvez le retrouver.

---

## Sommaire

1. [Introduction : qu'est-ce qu'un site web ?](#1-introduction--quest-ce-quun-site-web-)
2. [La grammaire du HTML](#2-la-grammaire-du-html)
3. [Le squelette de la page : `<head>` et ses réglages](#3-le-squelette-de-la-page--head-et-ses-réglages)
4. [Les grandes zones de la page : le HTML sémantique](#4-les-grandes-zones-de-la-page--le-html-sémantique)
5. [Le contenu : titres, textes, listes, liens et images](#5-le-contenu--titres-textes-listes-liens-et-images)
6. [L'accessibilité dans le HTML](#6-laccessibilité-dans-le-html)
7. [La grammaire du CSS](#7-la-grammaire-du-css)
8. [Les sélecteurs : viser le bon élément](#8-les-sélecteurs--viser-le-bon-élément)
9. [Les variables et les couleurs](#9-les-variables-et-les-couleurs)
10. [Les unités de mesure](#10-les-unités-de-mesure)
11. [La typographie](#11-la-typographie)
12. [Le modèle de boîte](#12-le-modèle-de-boîte)
13. [Les fonds et les images](#13-les-fonds-et-les-images)
14. [Flexbox : aligner sur une ligne](#14-flexbox--aligner-sur-une-ligne)
15. [CSS Grid : ranger dans un tableau](#15-css-grid--ranger-dans-un-tableau)
16. [Le positionnement et les calques](#16-le-positionnement-et-les-calques)
17. [Les pseudo-classes et pseudo-éléments](#17-les-pseudo-classes-et-pseudo-éléments)
18. [Transitions et animations : le carrousel](#18-transitions-et-animations--le-carrousel)
19. [Le responsive : s'adapter à tous les écrans](#19-le-responsive--sadapter-à-tous-les-écrans)
20. [Organiser son code : la méthode BEM](#20-organiser-son-code--la-méthode-bem)
21. [Bonnes pratiques et points à améliorer dans notre site](#21-bonnes-pratiques-et-points-à-améliorer-dans-notre-site)
22. [Exercices pour pratiquer](#22-exercices-pour-pratiquer)
23. [Aide-mémoire](#23-aide-mémoire)

---

## 1. Introduction : qu'est-ce qu'un site web ?

### 1.1 Une page web, c'est une maison

Imaginez que vous construisez une maison :

- **Le HTML**, c'est le **gros œuvre** : les murs, les pièces, les portes, les fenêtres. Il dit *ce qu'il y a* dans la page : un titre, un paragraphe, une image, un menu.
- **Le CSS**, c'est la **décoration** : la peinture, le papier peint, la disposition des meubles. Il dit *à quoi ça ressemble* : couleurs, tailles, espacements, position.

Une maison sans décoration reste habitable, mais elle est austère. De la même façon, une page HTML sans CSS s'affiche, mais en noir sur blanc, avec la police par défaut, tout empilé de haut en bas.

> 💡 **À retenir** : **HTML = le contenu et sa structure. CSS = l'apparence.** On les écrit dans deux fichiers séparés.

### 1.2 Les fichiers de notre projet

```
montsegur-accueil/
├── index.html          ← la page (le HTML)
├── style.css           ← la décoration (le CSS)
└── images/             ← les photos et le logo
    ├── affiche-unesco.jpg
    ├── catharisme.jpg
    ├── fondation-patrimoine.jpg
    ├── hero-montsegur.jpg
    ├── logo-grand-site.png
    ├── nature.jpg
    ├── village.jpg
    └── carrousel/      ← les 3 images du diaporama d'accueil
        ├── pog2-montsegur (2).jpg
        ├── village.jpg
        └── village_2.jpg
```

- **`index.html`** : par convention, `index` est le nom de la page d'accueil d'un site. Quand on ouvre un dossier sur un serveur web, c'est ce fichier qui s'affiche en premier.
- **`style.css`** : le nom est libre, mais `style.css` est très courant.
- **`images/`** : ranger les images dans un dossier à part, c'est comme ranger ses outils dans une boîte : on s'y retrouve plus vite.

### 1.3 Comment voir le résultat ?

Double-cliquez sur `index.html` : il s'ouvre dans votre navigateur (Chrome, Firefox, Edge…). Le **navigateur** est le programme qui **lit** le code et le **transforme** en page visible, comme un lecteur qui lit une partition et joue la musique.

Après chaque modification, enregistrez le fichier puis rechargez la page (**F5**, ou **Ctrl + F5** pour forcer le rechargement complet, images et CSS compris).

> 🛠️ **Astuce** : faites un clic droit sur n'importe quel élément de la page puis **« Inspecter »**. Les **outils de développement** s'ouvrent : vous voyez le HTML à gauche et le CSS appliqué à droite. C'est le meilleur outil pour apprendre.

### 1.4 La page de Montségur, vue d'ensemble

De haut en bas, notre page contient :

| Zone | Ce qu'on y voit |
|---|---|
| **En-tête** | Le logo « Montségur », le menu, le bouton « Billetterie » |
| **Hero** | La grande bannière avec le diaporama de photos et « Bienvenue à Montségur » |
| **Infos pratiques** | Le bandeau beige avec 4 liens en pastilles |
| **UNESCO** | Un texte à gauche, une affiche à droite |
| **Découvrir** | 3 cartes : catharisme, village, nature |
| **Bandeau** | « Le vaisseau de pierre » sur une photo du pog |
| **Actualités** | 2 articles |
| **Contact** | Les coordonnées de la mairie |
| **Pied de page** | Liens utiles, partenaires, copyright |

Nous allons décortiquer chacune de ces zones.

---

## 2. La grammaire du HTML

### 2.1 Les balises

HTML signifie **HyperText Markup Language**, « langage de balisage ». Une **balise** est une étiquette entre chevrons `< >` qui indique la nature d'un contenu.

Exemple tiré de notre page :

```html
<h1 class="hero__title">Bienvenue à Montségur</h1>
```

Décomposition :

- `<h1 ...>` → la **balise ouvrante** : « ici commence un titre de niveau 1 ».
- `Bienvenue à Montségur` → le **contenu**, ce que l'on voit à l'écran.
- `</h1>` → la **balise fermante** (avec une barre oblique `/`) : « ici s'arrête le titre ».

L'ensemble (ouvrante + contenu + fermante) s'appelle un **élément**.

> 🎁 **Analogie** : une balise ouvrante et une balise fermante, c'est comme le couvercle et le fond d'une boîte. Ce qui est entre les deux est *dans* la boîte.

### 2.2 Les balises orphelines

Certaines balises n'ont **pas de contenu**, donc pas de balise fermante. On les appelle **balises orphelines** (ou éléments vides) :

```html
<meta charset="UTF-8">
<img src="images/catharisme.jpg" alt="Les ruines du château de Montségur" loading="lazy">
<br>
```

- `<meta>` donne une information technique.
- `<img>` affiche une image : l'image *est* le contenu, il n'y a rien à mettre « dedans ».
- `<br>` force un retour à la ligne.

### 2.3 Les attributs

Un **attribut** apporte une précision sur une balise. Il s'écrit dans la balise ouvrante, sous la forme `nom="valeur"`.

```html
<a href="#decouvrir" class="btn btn--outline">Découvrir Montségur</a>
```

- `href="#decouvrir"` → **où mène** le lien.
- `class="btn btn--outline"` → deux **classes** (des étiquettes) que le CSS utilisera pour le décorer. Plusieurs classes se séparent par un **espace**.

> 🏷️ **Analogie** : si la balise est un objet (« un lien »), les attributs sont ses caractéristiques, comme sur une fiche produit : « destination : la section Découvrir », « style : bouton contour ».

Attributs que vous croiserez dans notre code : `class`, `id`, `href`, `src`, `alt`, `lang`, `charset`, `name`, `content`, `rel`, `target`, `loading`, `datetime`, `aria-label`, `aria-hidden`, `crossorigin`. Chacun est expliqué quand il apparaît.

### 2.4 `class` et `id` : les étiquettes

```html
<section class="section section--alt" id="decouvrir">
```

- **`class`** : une étiquette **réutilisable**. Plusieurs éléments peuvent avoir la même classe (toutes nos sections ont `class="section"`). Le CSS s'en sert pour appliquer le même style à tous.
- **`id`** : un identifiant **unique** dans la page, comme un numéro de sécurité sociale. Ici, `id="decouvrir"` permet au bouton « Découvrir Montségur » de faire défiler la page jusqu'à cette section.

### 2.5 L'imbrication

Les éléments se rangent **les uns dans les autres**, comme des poupées russes :

```html
<ul class="hero__labels">
  <li class="tag">Patrimoine mondial UNESCO</li>
  <li class="tag">Grand Site de France</li>
  <li class="tag">Grand site d'Occitanie</li>
</ul>
```

- `<ul>` est le **parent** : la liste.
- Les trois `<li>` sont ses **enfants** : les éléments de la liste. Entre eux, ils sont **frères**.

⚠️ **Règle d'or** : on ferme toujours les balises **dans l'ordre inverse** de leur ouverture. Le dernier ouvert est le premier fermé.

```html
<!-- ✅ Correct -->
<p><a href="#">lien</a></p>

<!-- ❌ Incorrect : les boîtes se chevauchent -->
<p><a href="#">lien</p></a>
```

L'**indentation** (les espaces en début de ligne) ne change rien pour le navigateur, mais elle rend visible cette imbrication pour l'humain. Dans notre fichier, chaque niveau est décalé de 2 espaces.

### 2.6 Les commentaires

```html
<!-- Les labels du site, sous forme de petites étiquettes -->
```

Tout ce qui est entre `<!--` et `-->` est **ignoré** par le navigateur. Ce sont des **notes pour les humains**. Notre fichier en contient beaucoup, comme ces grands cadres qui séparent les zones :

```html
<!-- ===================================================
     HERO : grande image d'accueil
     (l'image de fond est définie dans style.css)
     =================================================== -->
```

> 📒 **Analogie** : ce sont les post-it collés sur un plan d'architecte.

### 2.7 Les entités : les caractères spéciaux

```html
<h2 class="section__title">L'Unesco pour notre château&nbsp;! C'est fait&nbsp;!</h2>
```

`&nbsp;` est une **entité HTML** : un code qui représente un caractère spécial. Ici, c'est une **espace insécable** (*non-breaking space*). Elle empêche le navigateur de couper la ligne à cet endroit.

Pourquoi ? En français, on met une espace avant `!`. Sans `&nbsp;`, le point d'exclamation pourrait se retrouver seul au début de la ligne suivante, ce qui est laid. On l'utilise aussi dans `500&nbsp;ha` et `2&nbsp;368&nbsp;m` pour ne jamais séparer un nombre de son unité.

---

## 3. Le squelette de la page : `<head>` et ses réglages

Toute page HTML suit le même squelette. Voici le début de notre `index.html` :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <!-- Encodage des caractères (pour afficher correctement les accents) -->
  <meta charset="UTF-8">

  <!-- Indispensable pour le responsive : adapte la page à la largeur de l'écran -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Titre affiché dans l'onglet du navigateur -->
  <title>Montségur – Site officiel</title>

  <!-- Résumé de la page pour les moteurs de recherche -->
  <meta name="description" content="Site officiel de Montségur (Ariège) : château inscrit à l'UNESCO, Grand Site de France, village classé et nature préservée.">

  <!-- Polices Google Fonts ... -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Zilla+Slab:wght@600;700&family=Montserrat:wght@400;500;600&display=swap" rel="stylesheet">

  <!-- Notre feuille de style -->
  <link rel="stylesheet" href="style.css">
</head>

<body>
  ...
</body>
</html>
```

> 🧍 **Analogie** : une page HTML, c'est un corps humain. La **tête** (`<head>`) contient le cerveau : des informations invisibles mais essentielles. Le **corps** (`<body>`) est ce que tout le monde voit.

### 3.1 `<!DOCTYPE html>`

- **Ligne 1** : ce n'est pas une balise mais une **déclaration**. Elle dit au navigateur : « ce document est écrit en HTML moderne (HTML5) ».
- Sans elle, le navigateur passe en « mode de compatibilité » et peut afficher la page de façon bizarre. **Toujours la mettre en première ligne.**

### 3.2 `<html lang="fr">`

- C'est la **racine** : tout le reste de la page est rangé dedans. Elle se ferme à la toute dernière ligne avec `</html>`.
- `lang="fr"` indique que la page est **en français**. C'est important pour :
  - les **lecteurs d'écran** (logiciels qui lisent la page à voix haute pour les personnes aveugles), qui choisissent alors la bonne prononciation ;
  - les **moteurs de recherche** ;
  - la **traduction automatique** et la **césure** des mots.

### 3.3 `<head>` : les coulisses

Rien de ce qui est dans `<head>` ne s'affiche dans la page elle-même. On y met des **réglages**.

#### `<meta charset="UTF-8">`

- `meta` = « métadonnée », une information *sur* la page.
- `charset="UTF-8"` choisit l'**encodage des caractères** : la table de correspondance entre les lettres et les codes informatiques. **UTF-8** contient tous les caractères du monde, dont nos accents : « Montségur », « château », « Pyrénées ».
- Sans lui, vous risquez de voir « MontsÃ©gur » à la place de « Montségur ».

#### `<meta name="viewport" ...>`

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- Le **viewport** est la zone visible de la page à l'écran.
- `width=device-width` : « la largeur de la page = la largeur réelle de l'écran ».
- `initial-scale=1.0` : « pas de zoom au chargement ».
- Sans cette ligne, un téléphone afficherait la page comme sur un écran d'ordinateur, en tout petit, et il faudrait zoomer. **C'est la ligne indispensable du responsive** (voir chapitre 19).

#### `<title>`

```html
<title>Montségur – Site officiel</title>
```

- Le texte affiché dans l'**onglet** du navigateur, dans les **favoris** et comme titre bleu dans les **résultats Google**.
- Une seule balise `<title>` par page.

#### `<meta name="description" ...>`

- `name="description"` : on donne un **résumé** de la page.
- `content="..."` : le texte du résumé. Google l'affiche souvent sous le titre dans ses résultats. Il n'est pas visible dans la page.

#### `<link>` : relier un fichier externe

La balise `<link>` **relie** la page à une autre ressource. L'attribut `rel` (*relation*) précise la nature du lien.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

- `rel="preconnect"` : « prépare dès maintenant la connexion avec ce serveur, on va en avoir besoin ». C'est comme **réserver une table** au restaurant avant d'arriver : on gagne du temps.
- `href="..."` : l'adresse du serveur. `fonts.googleapis.com` fournit les instructions de police, `fonts.gstatic.com` les fichiers de police eux-mêmes.
- `crossorigin` : les fichiers de police sont téléchargés avec un mode de sécurité particulier (CORS). Cet attribut prépare la connexion dans ce même mode, sinon la préparation ne servirait à rien.

```html
<link href="https://fonts.googleapis.com/css2?family=Zilla+Slab:wght@600;700&family=Montserrat:wght@400;500;600&display=swap" rel="stylesheet">
```

- `rel="stylesheet"` : « ce fichier est une **feuille de style** ».
- L'adresse demande à Google Fonts deux polices :
  - `family=Zilla+Slab:wght@600;700` → la police **Zilla Slab** en épaisseurs 600 (semi-gras) et 700 (gras), pour les **titres** ;
  - `family=Montserrat:wght@400;500;600` → la police **Montserrat** en épaisseurs 400 (normal), 500 et 600, pour le **texte**.
  - `display=swap` → pendant le téléchargement, le texte s'affiche avec une police de secours, puis est **échangé** (*swap*) avec la bonne. Le visiteur n'attend jamais devant une page vide.
- On ne charge que les épaisseurs utilisées : chaque épaisseur est un fichier à télécharger.

```html
<link rel="stylesheet" href="style.css">
```

- **La ligne la plus importante pour nous** : elle relie la page à **notre** CSS.
- `href="style.css"` est un **chemin relatif** : « le fichier `style.css` qui est dans le même dossier que moi ».
- Cette ligne est placée **après** Google Fonts : ainsi notre CSS peut utiliser ces polices.

### 3.4 `<body>` : la partie visible

Tout ce qui est entre `<body>` et `</body>` s'affiche dans la fenêtre. C'est l'objet des chapitres 4 à 6.

---

## 4. Les grandes zones de la page : le HTML sémantique

### 4.1 Qu'est-ce que la sémantique ?

**Sémantique** veut dire « qui a du sens ». Une balise sémantique dit **ce qu'est** son contenu, et pas seulement comment il s'affiche.

> 🗺️ **Analogie** : dans un supermarché, les panneaux « Fruits et légumes », « Boulangerie », « Caisse » aident à s'orienter. Les balises sémantiques sont ces panneaux. Les personnes aveugles (via leur lecteur d'écran) et Google s'en servent pour comprendre et parcourir la page.

Voici le plan sémantique de notre page :

```
<body>
├── <header>   en-tête du site
│   └── <nav>  menu principal
├── <main>     contenu principal
│   ├── <section>  hero
│   ├── <section>  infos pratiques
│   ├── <section>  UNESCO          → contient une <figure>
│   ├── <section>  découvrir       → contient un <header> et 3 <article>
│   ├── <section>  bandeau
│   ├── <section>  actualités      → contient un <header> et 2 <article>
│   └── <section>  contact         → contient une <address>
└── <footer>   pied de page
```

### 4.2 `<header>` : l'en-tête

```html
<header class="site-header">
  <div class="container header__inner">

    <!-- Logo en texte -->
    <a href="index.html" class="logo"> <!-- TODO -->
      Montségur
      <span class="logo__subtitle">Site officiel</span>
    </a>

    <!-- Menu principal -->
    <nav class="main-nav" aria-label="Menu principal">
      ...
    </nav>

    <!-- Bouton mis en avant -->
    <a href="#" class="btn btn--primary btn--small">Billetterie</a>

  </div>
</header>
```

- `<header>` = **l'en-tête**. Placé directement dans `<body>`, il représente l'en-tête **du site** : logo, menu, bouton important.
- `class="site-header"` : une classe pour le décorer (fond anthracite).
- `<div class="container header__inner">` : une boîte de rangement (voir 4.8) avec deux classes : `container` centre le contenu, `header__inner` aligne logo, menu et bouton.
- Le logo est un **lien** vers `index.html`, la page d'accueil. C'est une convention universelle : cliquer sur le logo ramène à l'accueil.
- `<span class="logo__subtitle">Site officiel</span>` : un morceau de texte qu'on veut styler à part (plus petit, en majuscules).

Un `<header>` peut aussi être l'**en-tête d'une section**. On le retrouve dans les sections « Découvrir » et « Actualités » :

```html
<header class="section__header">
  <p class="section__label">Découvrir</p>
  <h2 class="section__title">Montségur, entre histoire et montagne</h2>
</header>
```

Il regroupe le sur-titre et le titre de la section.

### 4.3 `<nav>` : la navigation

```html
<nav class="main-nav" aria-label="Menu principal">
  <ul class="main-nav__list">
    <li><a href="#">Château et musée</a></li>
    <li><a href="#">Village</a></li>
    <li><a href="#">Sentiers</a></li>
    <li><a href="#">Animations</a></li>
    <li><a href="#">Vie communale</a></li>
  </ul>
</nav>
```

- `<nav>` signale un **bloc de navigation principal**.
- `aria-label="Menu principal"` donne un **nom** à ce bloc pour les lecteurs d'écran (voir chapitre 6).
- À l'intérieur, une **liste** `<ul>` de liens. Un menu est une liste de destinations, d'où l'utilisation d'une liste.
- `href="#"` est un **lien temporaire** qui ne mène nulle part : les vraies pages n'existent pas encore.

### 4.4 `<main>` : le contenu principal

```html
<!-- Contenu principal (id="contenu" = cible du lien d'évitement) -->
<main id="contenu">
  ...
</main>
```

- `<main>` contient le **contenu unique** de la page, tout ce qui n'est ni l'en-tête ni le pied de page. **Un seul** `<main>` par page.
- `id="contenu"` en fait une cible de lien, prévue pour un « lien d'évitement » (voir chapitre 21, ce lien n'est pas encore dans le HTML).

### 4.5 `<section>` : un chapitre de la page

```html
<section class="section section--alt" id="decouvrir">
```

- `<section>` regroupe un **bloc thématique** qui a en général son propre titre. C'est l'équivalent d'un **chapitre** dans un livre.
- Notre `<main>` contient 7 sections : hero, infos pratiques, UNESCO, découvrir, bandeau, actualités, contact.

Quand une section n'a pas de titre visible, on peut lui donner un nom avec `aria-label` :

```html
<section class="quick-links" aria-label="Infos pratiques">
```

### 4.6 `<article>` : un contenu autonome

```html
<article class="card">
  <img class="card__image" src="images/catharisme.jpg" alt="Les ruines du château de Montségur" loading="lazy">
  <div class="card__body">
    <h3 class="card__title">Montségur et le Catharisme</h3>
    <p class="card__text">
      L'histoire de Montségur et de son château a été établie à partir
      de documents historiques, notamment les archives de
      l'Inquisition, et des fouilles archéologiques menées sur le site.
    </p>
    <a href="#" class="link-arrow">En savoir plus</a>
  </div>
</article>
```

- `<article>` désigne un contenu **qui a du sens tout seul**, qu'on pourrait découper et publier ailleurs : un article de presse, une fiche, une carte.
- **Test simple** : « Si je colle ce bloc seul sur une autre page, est-il compréhensible ? » Oui pour chaque carte et chaque actualité, donc ce sont des `<article>`.

### 4.7 `<footer>` : le pied de page

```html
<footer class="site-footer">
  <div class="container footer__inner">
    <div class="footer__col"> ... </div>
    <div class="footer__col"> ... </div>
    <div class="footer__col"> ... </div>
  </div>

  <p class="footer__copy">© 2026 Commune de Montségur</p>
</footer>
```

- `<footer>` = le **pied de page** : informations secondaires, liens utiles, partenaires, droits d'auteur.
- Il contient 3 colonnes (`footer__col`) et une ligne de copyright.

### 4.8 `<div>` et `<span>` : les boîtes neutres

Ces deux balises **n'ont aucun sens** particulier. Ce sont des **boîtes de rangement** qu'on utilise quand aucune balise sémantique ne convient, surtout pour la mise en page.

```html
<div class="hero__buttons">
  <a href="#" class="btn btn--primary">Réserver ma visite</a>
  <a href="#decouvrir" class="btn btn--outline">Découvrir Montségur</a>
</div>
```

- `<div>` (*division*) est une boîte de type **bloc** : elle occupe toute la largeur et passe à la ligne. Ici, elle regroupe les deux boutons pour que le CSS puisse les aligner.

```html
<span class="contact__label">Téléphone</span>
```

- `<span>` est une boîte **en ligne** : elle reste dans le flux du texte, comme un surligneur. Ici, elle permet de styler le mot « Téléphone » différemment.

> 📦 **Analogie** : `<div>` est un carton de déménagement (on y range des blocs entiers), `<span>` est un surligneur (on marque quelques mots dans une phrase).

**Bloc ou en ligne ?** C'est une notion clé :

| Type | Comportement | Exemples dans notre code |
|---|---|---|
| **Bloc** (*block*) | Prend toute la largeur, commence sur une nouvelle ligne | `div`, `p`, `h1`–`h3`, `ul`, `li`, `section`, `header`, `footer`, `article`, `figure`, `address` |
| **En ligne** (*inline*) | Prend juste la place de son contenu, reste dans la ligne | `a`, `span`, `time`, `img` (par défaut) |

### 4.9 `<figure>` : une illustration

```html
<figure class="split__image">
  <img src="images/affiche-unesco.jpg" alt="Affiche de la campagne : les forteresses royales du Languedoc inscrites à l'UNESCO" loading="lazy">
</figure>
```

- `<figure>` encadre une **illustration** liée au texte : image, schéma, graphique. On peut y ajouter une légende avec `<figcaption>` (non utilisé ici).
- Par défaut, `<figure>` a des marges ; notre CSS les retire (voir chapitre 12).

### 4.10 `<address>` : des coordonnées

```html
<!-- <address> est la balise sémantique pour les coordonnées -->
<address class="contact__card">
  <p class="contact__name">Mairie de Montségur</p>
  <p>32 rue du village<br>09300 Montségur</p>
  ...
</address>
```

- `<address>` contient les **coordonnées de contact** : adresse postale, téléphone, e-mail.
- Par défaut, les navigateurs l'affichent **en italique** ; notre CSS le remet droit avec `font-style: normal`.

### 4.11 `<time>` : une date compréhensible par les machines

```html
<!-- <time> indique une date lisible par les machines -->
<time class="news__date" datetime="2026-07-03">3 juillet 2026</time>
```

- Le contenu « 3 juillet 2026 » est pour les **humains**.
- L'attribut `datetime="2026-07-03"` donne la même date au format standard **année-mois-jour**, compréhensible par les **machines** : moteurs de recherche, agendas, assistants vocaux.

> 🌍 **Analogie** : c'est comme écrire une date à la fois en toutes lettres pour un lecteur, et en code-barres pour une caisse automatique.

---

## 5. Le contenu : titres, textes, listes, liens et images

### 5.1 Les titres `<h1>` à `<h3>`

HTML propose 6 niveaux de titres, de `<h1>` (le plus important) à `<h6>`. Notre page utilise les trois premiers :

```html
<h1 class="hero__title">Bienvenue à Montségur</h1>
<h2 class="section__title">Montségur, entre histoire et montagne</h2>
<h3 class="card__title">Montségur et le Catharisme</h3>
```

- **`<h1>`** : le titre principal de la page. **Un seul** par page : « Bienvenue à Montségur ».
- **`<h2>`** : les titres de section : « L'Unesco pour notre château ! », « Le vaisseau de pierre », « La vie du village », « Venir à Montségur »… et les titres de colonnes du pied de page.
- **`<h3>`** : les sous-titres à l'intérieur d'une section : le titre de chaque carte et de chaque actualité.

> 📖 **Analogie** : c'est le sommaire d'un livre. `h1` = titre du livre, `h2` = chapitres, `h3` = sous-parties. **On ne saute pas de niveau** : pas de `h3` sans `h2` au-dessus.

⚠️ On choisit le niveau d'un titre selon sa **place dans le plan**, jamais pour sa taille. La taille se règle en CSS. Exemple : dans le pied de page, « Informations » est un `<h2>` (titre d'une zone), mais le CSS l'affiche tout petit, en majuscules.

### 5.2 Les paragraphes `<p>`

```html
<p class="hero__text">
  La cité majeure du catharisme, inscrite au patrimoine mondial de l'UNESCO.
</p>
```

- `<p>` = un **paragraphe** de texte.
- Les **retours à la ligne et espaces multiples** dans le code sont **ignorés** : le navigateur les remplace par une seule espace. Le texte de l'exemple s'affiche donc sur une seule ligne si la place le permet.

On utilise aussi `<p>` pour de petits textes isolés, comme les sur-titres :

```html
<p class="section__label">Patrimoine mondial</p>
```

### 5.3 Le retour à la ligne `<br>`

```html
<p>32 rue du village<br>09300 Montségur</p>
```

- `<br>` (*break*) force un **retour à la ligne** à l'intérieur d'un paragraphe.
- On le réserve aux cas où le retour à la ligne **fait partie du contenu**, comme une adresse postale ou un poème. Pour espacer des blocs, on utilise le CSS.

### 5.4 Les listes `<ul>` et `<li>`

```html
<ul class="footer__list">
  <li><a href="#">Château et musée</a></li>
  <li><a href="#">Hébergements et commerces</a></li>
  <li><a href="#">Conseils municipaux</a></li>
  <li><a href="#">Mentions légales et crédits</a></li>
</ul>
```

- `<ul>` (*unordered list*) = une **liste à puces**, sans ordre particulier.
- `<li>` (*list item*) = **un élément** de la liste. Un `<li>` est toujours l'enfant direct d'un `<ul>` (ou d'un `<ol>`, liste numérotée).

Notre page utilise des listes partout où il y a **plusieurs éléments de même nature** :

| Liste | Classe |
|---|---|
| Menu principal | `main-nav__list` |
| Étiquettes du hero | `hero__labels` |
| Infos pratiques | `quick-links__list` |
| Liens d'une actualité | `news__links` |
| Réseaux sociaux, liens et partenaires du pied de page | `footer__list` |

Les puces, elles, sont retirées en CSS avec `list-style: none` : la **structure** reste une liste (utile aux lecteurs d'écran, qui annoncent « liste de 4 éléments »), mais l'**apparence** change.

### 5.5 Les liens `<a>`

`<a>` (*anchor*, « ancre ») crée un **lien hypertexte**. Son attribut essentiel est `href` (*hypertext reference*), la destination. Notre page utilise **six sortes** de liens.

#### 1. Lien vers une autre page du site

```html
<a href="index.html" class="logo">
```

Chemin relatif vers un fichier du projet.

#### 2. Lien temporaire

```html
<a href="#">Village</a>
```

`#` seul ne mène nulle part (il remonte en haut de la page). C'est un **emplacement réservé**, en attendant que la vraie page existe.

#### 3. Lien vers une section de la même page (ancre)

```html
<a href="#decouvrir" class="btn btn--outline">Découvrir Montségur</a>
...
<section class="section section--alt" id="decouvrir">
```

- `#decouvrir` = « va à l'élément dont l'`id` est `decouvrir` ».
- Au clic, la page défile jusqu'à la section « Découvrir ». Grâce au CSS `scroll-behavior: smooth`, ce défilement est **doux** (voir chapitre 7).

#### 4. Lien vers un autre site, dans un nouvel onglet

```html
<a href="https://www.fondation-patrimoine.org/les-projets/chateau-et-pog-de-montsegur/105349" class="link-arrow" target="_blank" rel="noopener">Faire un don pour le château</a>
```

- `href="https://..."` : une **adresse complète** (URL absolue), avec le protocole `https://`.
- `target="_blank"` : ouvre le lien dans un **nouvel onglet**. Le visiteur garde notre site ouvert.
- `rel="noopener"` : une **sécurité**. Sans lui, la page ouverte pourrait prendre le contrôle de l'onglet d'origine (par exemple le rediriger vers une fausse page). **Toujours l'associer à `target="_blank"`.**

#### 5. Lien vers un fichier PDF

```html
<a href="https://www.montsegur.fr/wp-content/uploads/2026/07/DISCOURS-SIGNATURE-FONDATION-PATRIMOINE_MAIRE.pdf" class="link-arrow" target="_blank" rel="noopener">Lire le discours du maire (PDF)</a>
```

Un lien peut pointer vers n'importe quel fichier. Bonne pratique : **annoncer le format** dans le texte du lien, « (PDF) », pour que le visiteur sache à quoi s'attendre.

#### 6. Liens « téléphone » et « e-mail »

```html
<a href="tel:+33561011027">05 61 01 10 27</a>
<a href="mailto:mairie.montsegur@orange.fr">mairie.montsegur@orange.fr</a>
```

- `tel:` : sur un téléphone, le clic **lance l'appel**. On écrit le numéro au format international (`+33` puis le numéro sans le premier `0`), sans espaces.
- `mailto:` : le clic **ouvre la messagerie** avec l'adresse déjà remplie.

> ✍️ **Bonne pratique** : un texte de lien doit être **compréhensible seul**. « Faire un don pour le château » est clair. Dans notre code, « En savoir plus » est répété plusieurs fois : un lecteur d'écran qui liste les liens entendra trois fois la même chose (voir chapitre 21).

### 5.6 Les images `<img>`

```html
<img class="card__image" src="images/catharisme.jpg" alt="Les ruines du château de Montségur" loading="lazy">
```

Décomposition attribut par attribut :

- `class="card__image"` : pour le style (recadrage au même format pour les 3 cartes).
- `src="images/catharisme.jpg"` (*source*) : le **chemin** du fichier image. `images/` = « dans le dossier images ».
- `alt="Les ruines du château de Montségur"` (*alternative*) : un **texte de remplacement** qui décrit l'image. Il est :
  - **lu à voix haute** par les lecteurs d'écran ;
  - **affiché** si l'image ne se charge pas ;
  - **lu par Google** pour comprendre l'image.
- `loading="lazy"` : **chargement paresseux**. L'image n'est téléchargée que lorsque le visiteur s'en approche en faisant défiler la page. La page s'affiche plus vite, et on économise les données mobiles.

> 🛋️ **Analogie** pour `lazy` : un restaurant qui ne cuisine un plat que lorsque vous le commandez, au lieu de tout préparer à l'avance.

Un bon `alt` décrit ce que l'image **apporte**. Comparez :

```html
<!-- Précis et utile -->
alt="Les élus et partenaires réunis au pied du pog pour la signature de la convention"

<!-- Pour un logo : on donne son nom -->
alt="Logo Grand Site de France Montségur"
```

### 5.7 Les images de fond : un cas à part

Les images du **carrousel** et du **bandeau** ne sont pas des `<img>` : elles sont définies dans le CSS avec `background-image`. Pourquoi ? Ce sont des images **décoratives**, posées *derrière* du texte. Elles n'apportent pas d'information indispensable. Règle générale :

- **Image qui est du contenu** (une photo d'actualité, une affiche) → `<img>` avec un `alt`.
- **Image de décor** (un fond) → CSS.

Le carrousel utilise trois `<span>` vides comme supports :

```html
<!-- Diaporama de fond : 3 images qui défilent en fondu (CSS seul) -->
<div class="hero__slides" aria-hidden="true">
  <span class="hero__slide hero__slide--1"></span>
  <span class="hero__slide hero__slide--2"></span>
  <span class="hero__slide hero__slide--3"></span>
</div>
```

- Chaque `<span>` est une **toile vide** sur laquelle le CSS pose une photo.
- `aria-hidden="true"` dit aux lecteurs d'écran : « ignore ce bloc, il est purement décoratif ».

Tout le fonctionnement est expliqué au chapitre 18.

---

## 6. L'accessibilité dans le HTML

L'**accessibilité** (souvent abrégée **a11y**) consiste à rendre un site utilisable par **tout le monde** : personnes aveugles ou malvoyantes, personnes qui naviguent au clavier, personnes âgées, connexions lentes…

> ♿ **Analogie** : une rampe d'accès à côté d'un escalier. Elle sert aux fauteuils roulants, mais aussi aux poussettes et aux valises. L'accessibilité web profite à tout le monde.

Ce que fait notre HTML pour l'accessibilité :

| Technique | Exemple dans notre code | Rôle |
|---|---|---|
| Langue de la page | `<html lang="fr">` | Bonne prononciation par les lecteurs d'écran |
| Balises sémantiques | `<header>`, `<nav>`, `<main>`, `<footer>` | Permettent de sauter directement à une zone |
| Hiérarchie de titres | un `h1`, puis des `h2`, puis des `h3` | Permet de survoler la page par titres |
| Textes alternatifs | `alt="Les ruines du château..."` | Décrire les images |
| Nom des zones | `aria-label="Menu principal"` | Nommer un bloc qui n'a pas de titre visible |
| Masquer le décor | `aria-hidden="true"` sur le diaporama | Ne pas encombrer la lecture |
| Vraies listes | `<ul>` / `<li>` pour les menus | Annonce « liste de 5 éléments » |
| Dates lisibles | `<time datetime="...">` | Comprises par les machines |

### 6.1 Les attributs `aria-*`

**ARIA** (*Accessible Rich Internet Applications*) est une famille d'attributs qui donnent des **informations supplémentaires** aux technologies d'assistance. Ils ne changent **rien à l'affichage**.

```html
<nav class="main-nav" aria-label="Menu principal">
<section class="quick-links" aria-label="Infos pratiques">
```

- `aria-label` donne un **nom** à la zone. Le lecteur d'écran annonce : « Navigation, Menu principal ».

```html
<div class="hero__slides" aria-hidden="true">
```

- `aria-hidden="true"` **cache** le bloc aux lecteurs d'écran (mais pas aux yeux).

Le CSS prévoit aussi un style pour `aria-current="page"`, l'attribut qui signale « ce lien correspond à la page où l'on se trouve » (voir chapitre 17).

> ⚖️ **Règle des pros** : « Pas d'ARIA vaut mieux que du mauvais ARIA. » On utilise d'abord la bonne balise HTML, et ARIA seulement en complément.

---

## 7. La grammaire du CSS

CSS signifie **Cascading Style Sheets**, « feuilles de style en cascade ».

### 7.1 Une règle CSS

Prenons une règle de notre `style.css` :

```css
.section__title {
  font-size: 2.2rem;
}
```

Décomposition :

- `.section__title` → le **sélecteur** : **à qui** s'applique la règle. Ici, à tous les éléments qui ont la classe `section__title`. Le point `.` signifie « classe ».
- `{ ... }` → les **accolades** délimitent le **bloc de déclarations**.
- `font-size` → la **propriété** : **quoi** modifier (la taille du texte).
- `:` → les deux-points séparent la propriété de sa valeur.
- `2.2rem` → la **valeur** : **comment** (2,2 fois la taille de base).
- `;` → le point-virgule **termine** la déclaration. Ne l'oubliez jamais.

> 🎨 **Analogie** : une règle CSS est une consigne au peintre. « *Tous les volets* (sélecteur) : *couleur* (propriété) → *vert* (valeur). »

Une règle peut contenir plusieurs déclarations :

```css
.section__label {
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--color-accent);
  margin-bottom: 0.5rem;
}
```

Ce sont les petits sur-titres rouge bordeaux en majuscules, comme « PATRIMOINE MONDIAL » ou « DÉCOUVRIR ».

### 7.2 Les commentaires CSS

```css
/* Centre le contenu et limite sa largeur */
```

En CSS, les commentaires s'écrivent entre `/*` et `*/`. Notre fichier commence par un grand commentaire qui sert de **sommaire** :

```css
/* =========================================================
   FEUILLE DE STYLE – Page d'accueil de Montségur

   Sommaire :
   1.  Variables (couleurs, polices, arrondis)
   2.  Base (réinitialisation, typographie)
   3.  Éléments réutilisables (container, boutons, sections...)
   ...
   13. Responsive (tablette et ordinateur)
   ========================================================= */
```

Un commentaire sert aussi à **désactiver** du code temporairement. C'est le cas ici (nous y reviendrons au chapitre 12) :

```css
/* *,
*::before,
*::after {
  box-sizing: border-box;
} */
```

### 7.3 La cascade

« En cascade » signifie que **plusieurs règles peuvent viser le même élément**, et que le navigateur doit décider laquelle gagne. Trois critères, dans l'ordre :

1. **L'importance** (on ne l'utilise pas ici).
2. **La spécificité** : la règle la plus **précise** gagne.
3. **L'ordre** : à précision égale, la règle écrite **en dernier** gagne.

Exemple d'**ordre** dans notre code :

```css
/* Plus haut dans le fichier */
.btn {
  padding: 0.85rem 1.6rem;
  ...
}

/* Plus bas */
.btn--small {
  padding: 0.5rem 1.1rem;
  font-size: 0.9rem;
}
```

Le bouton « Billetterie » a les deux classes : `class="btn btn--primary btn--small"`. Les deux règles ont la même précision (une classe chacune), donc **la dernière écrite gagne** : le bouton prend le petit padding. C'est pour cela que les **variantes** (`--small`) sont écrites **après** la règle de base.

### 7.4 La spécificité

La spécificité est un **score de précision**. Simplement :

| Sélecteur | Points (approximatifs) |
|---|---|
| Une balise (`p`, `a`) | 1 |
| Une classe (`.btn`), une pseudo-classe (`:hover`), un attribut (`[aria-current]`) | 10 |
| Un id (`#decouvrir`) | 100 |

Exemple dans notre code :

```css
a {
  color: var(--color-accent);          /* score 1 : bordeaux */
}

.site-footer a {
  color: #e7ddcc;                      /* score 10 + 1 = 11 : beige */
}
```

Les liens du pied de page sont visés par les deux règles. `.site-footer a` est plus précis (11 contre 1) : il gagne, les liens du pied de page sont beiges.

> 🏆 **Analogie** : une consigne générale (« tous les employés portent un badge ») est remplacée par une consigne plus précise (« les employés de l'accueil portent un badge doré »).

### 7.5 L'héritage

Certaines propriétés **se transmettent** du parent aux enfants : couleur du texte, police, taille, interligne… Ce n'est pas le cas des marges, bordures ou fonds.

```css
body {
  margin: 0;
  font-family: var(--font-text);
  font-size: 1rem;           /* 1rem = 16px */
  line-height: 1.7;          /* interligne aéré */
  color: var(--color-text);
  background-color: var(--color-stone-light);
}
```

Comme tout est dans `<body>`, **toute la page hérite** de la police Montserrat, de la taille 16 px, de l'interligne 1,7 et de la couleur anthracite. On n'a pas besoin de le répéter. Les éléments qui veulent autre chose le redéfinissent, comme `.hero` qui passe le texte en blanc :

```css
.hero {
  color: var(--color-white);
  ...
}
```

Tous les textes du hero (titre, paragraphe) héritent alors du blanc.

> 👪 **Analogie** : comme des enfants qui héritent de la couleur des yeux de leurs parents, mais pas de leur manteau.

### 7.6 Les premières règles de base

Le chapitre « 2. BASE » de notre CSS règle l'apparence générale :

```css
html {
  scroll-behavior: smooth;   /* défilement doux vers les ancres (#decouvrir) */
}
```

- `scroll-behavior: smooth` : quand on clique sur un lien vers une ancre (`#decouvrir`), la page **glisse** jusqu'à la cible au lieu d'y sauter d'un coup.

```css
h1,
h2,
h3 {
  font-family: var(--font-title);
  font-weight: 700;
  line-height: 1.15;
  margin: 0 0 0.5em;
}
```

- Une règle pour **trois sélecteurs** à la fois (séparés par des virgules) : tous les titres utilisent la police de titre, en gras, avec un interligne serré et une marge sous le titre.

```css
p {
  margin: 0 0 1em;
}
```

- Les paragraphes ont seulement une marge **en dessous**, égale à la taille du texte.

```css
img {
  display: block;
  max-width: 100%;           /* une image ne dépasse jamais son conteneur */
}
```

- `display: block` : l'image devient un bloc. Cela supprime un petit espace parasite sous les images en ligne.
- `max-width: 100%` : une image n'est **jamais plus large que sa boîte**. Une photo de 2000 px de large rétrécit pour tenir dans un téléphone. **Règle essentielle du responsive.**

```css
a {
  color: var(--color-accent);
}
```

- Tous les liens sont **bordeaux** par défaut (au lieu du bleu des navigateurs).

---

## 8. Les sélecteurs : viser le bon élément

Le sélecteur répond à la question : **à qui** s'applique cette règle ? Voici tous ceux de notre fichier.

### 8.1 Le sélecteur de balise

```css
body { ... }
p { ... }
img { ... }
a { ... }
```

Vise **toutes** les balises de ce nom.

### 8.2 Le sélecteur de classe `.`

```css
.container { ... }
.card { ... }
```

Vise tous les éléments qui ont cette classe. **C'est le sélecteur le plus utilisé de notre fichier**, car il est réutilisable et précis.

### 8.3 Le regroupement `,`

```css
h1,
h2,
h3 { ... }
```

« À h1 **et** à h2 **et** à h3 ». Évite de répéter trois fois la même règle.

### 8.4 Le sélecteur descendant (espace)

```css
.split__text p {
  color: var(--color-text-light);
  font-size: 1.05rem;
}
```

L'**espace** signifie « **à l'intérieur de** ». Ici : « les `<p>` qui se trouvent dans un élément `.split__text` ». Seuls les paragraphes du bloc UNESCO deviennent gris et un peu plus grands, pas les autres paragraphes de la page.

Autres exemples : `.split__image img`, `.news__body p`, `.contact__intro p`, `.contact__card a`, `.site-footer a`, `.main-nav__list a`.

### 8.5 Le sélecteur de frère adjacent `+`

```css
.news__links li + li {
  margin-top: 0.4rem;            /* espace entre deux liens */
}
```

`li + li` = « un `<li>` qui suit **immédiatement** un autre `<li>` ». Donc tous les éléments de la liste **sauf le premier**. Résultat : un espace **entre** les éléments, mais pas au-dessus du premier.

> 🚃 **Analogie** : dans un train, on ajoute un attelage devant chaque wagon **qui suit un autre wagon**. La locomotive, elle, n'en a pas besoin.

Même technique dans le pied de page : `.footer__list li + li`.

### 8.6 La pseudo-classe `:last-child`

```css
.contact__card p:last-child {
  margin-bottom: 0;
}
```

« Le paragraphe qui est le **dernier enfant** de la carte contact ». On retire sa marge du bas pour que l'espace intérieur de la carte soit le même en haut et en bas.

### 8.7 Le sélecteur d'attribut `[...]`

```css
.quick-links__item[aria-current="page"] { ... }
```

Les crochets visent un élément selon un **attribut** : « les liens `.quick-links__item` qui ont `aria-current="page"` ».

### 8.8 La pseudo-classe `:root`

```css
:root {
  --color-stone-light: #f4efe6;
  ...
}
```

`:root` vise la **racine** du document, c'est-à-dire `<html>`. C'est l'endroit conventionnel pour déclarer les **variables** globales (chapitre 9).

### 8.9 Le sélecteur universel `*`

```css
/* *,
*::before,
*::after {
  box-sizing: border-box;
} */
```

`*` vise **absolument tous les éléments**. (Cette règle est actuellement commentée, voir chapitre 12.)

### 8.10 Les pseudo-classes d'état et les pseudo-éléments

`:hover`, `:focus-visible`, `:active`, `::before`, `::after` réagissent à l'interaction ou créent du contenu. Ils ont leur propre chapitre (chapitre 17).

---

## 9. Les variables et les couleurs

### 9.1 Les variables CSS (propriétés personnalisées)

```css
/* --- 1. VARIABLES ---
   Modifiez une valeur ici : elle change sur toute la page.

   Charte reprise du site d'origine (montsegur.fr) :
   beige pierre #c0b297, anthracite #231f20, bordeaux #840b0d. */
:root {
  /* Tons pierre / roche / beige chaud (fonds et cartes) */
  --color-stone-light: #f4efe6;  /* beige très clair : fond de page */
  --color-stone: #e7ddcc;        /* beige roche : sections alternées */
  --color-stone-deep: #c0b297;   /* beige pierre du site d'origine */
  --color-white: #fffdf9;        /* blanc cassé chaud : cartes */

  /* Gris foncé / anthracite (textes et structure) */
  --color-text: #231f20;         /* anthracite : texte principal */
  --color-text-light: #59524d;   /* gris chaud : texte secondaire */
  --color-dark: #2b2728;         /* anthracite : en-tête et pied de page */

  /* Couleur d'accent (boutons, liens, sur-titres) */
  --color-accent: #840b0d;       /* bordeaux du site d'origine */
  --color-accent-dark: #620809;  /* bordeaux foncé : survol */

  /* Polices proches de celles du site d'origine :
     Zilla Slab remplace Clarendon, Montserrat remplace Gotham */
  --font-title: "Zilla Slab", Georgia, serif;
  --font-text: "Montserrat", system-ui, -apple-system, "Segoe UI", sans-serif;

  /* Formes */
  --radius: 14px;
}
```

**Déclarer** une variable :

- Son nom commence **toujours par deux tirets** : `--color-accent`.
- On lui donne une valeur : `#840b0d`.

**Utiliser** une variable : avec la fonction `var()` :

```css
a {
  color: var(--color-accent);
}
```

`var(--color-accent)` est remplacé par `#840b0d`.

> 🎨 **Analogie** : c'est le **nuancier** d'un peintre. Au lieu d'écrire le code de la couleur à 15 endroits, on écrit « bordeaux Montségur ». Si la mairie change de bordeaux, on modifie **une seule ligne** et toute la page suit.

Nos variables forment la **charte graphique** du site :

| Variable | Valeur | Usage |
|---|---|---|
| `--color-stone-light` | `#f4efe6` | Fond général de la page |
| `--color-stone` | `#e7ddcc` | Fond des sections alternées |
| `--color-stone-deep` | `#c0b297` | Bandeau infos pratiques, sous-titre du logo |
| `--color-white` | `#fffdf9` | Cartes, texte sur fond sombre |
| `--color-text` | `#231f20` | Texte principal |
| `--color-text-light` | `#59524d` | Texte secondaire |
| `--color-dark` | `#2b2728` | En-tête, pied de page, pastille active |
| `--color-accent` | `#840b0d` | Liens, boutons, sur-titres |
| `--color-accent-dark` | `#620809` | Survol des boutons |
| `--font-title` | Zilla Slab… | Titres |
| `--font-text` | Montserrat… | Texte courant |
| `--radius` | `14px` | Arrondi des cartes et images |

### 9.2 Les couleurs hexadécimales

`#840b0d` est une couleur en **notation hexadécimale** :

- Le `#` annonce la couleur.
- Les 6 caractères sont 3 paires : **rouge** (`84`), **vert** (`0b`), **bleu** (`0d`).
- Chaque paire va de `00` (rien) à `ff` (maximum), en base 16 (chiffres 0 à 9 puis lettres a à f).

Ici beaucoup de rouge (`84`), presque pas de vert ni de bleu : c'est un **rouge foncé**, le bordeaux.

> 💡 Pas besoin de calculer : les éditeurs de code et les outils de développement affichent un petit carré coloré et un sélecteur de couleur.

### 9.3 Les couleurs `rgba()` avec transparence

```css
.btn--outline:hover {
  background-color: rgba(255, 255, 255, 0.15);
}
```

`rgba(rouge, vert, bleu, opacité)` :

- Les trois premiers nombres vont de **0 à 255**. `255, 255, 255` = blanc.
- Le quatrième, l'**alpha**, va de **0** (totalement transparent) à **1** (opaque). `0.15` = 15 % d'opacité.

Résultat : un **voile blanc très léger** qui laisse voir la photo derrière le bouton.

On utilise beaucoup cette technique dans notre site :

```css
/* Pastilles des infos pratiques au survol : anthracite à 8 % */
background-color: rgba(35, 31, 32, 0.08);

/* Étiquettes du hero : noir à 20 % */
background-color: rgba(0, 0, 0, 0.2);

/* Bordure des étiquettes : blanc à 50 % */
border: 1px solid rgba(255, 255, 255, 0.5);
```

`35, 31, 32` est notre anthracite `#231f20` exprimé en décimal.

### 9.4 Le mot-clé `transparent`

```css
.btn {
  border: 2px solid transparent;
}
```

Une bordure **invisible** mais qui **occupe sa place**. Pourquoi ? Le bouton contour (`.btn--outline`) a une bordure blanche de 2 px. En donnant une bordure transparente de même épaisseur à **tous** les boutons, les deux boutons du hero ont exactement la **même taille**.

---

## 10. Les unités de mesure

| Unité | Signification | Exemple dans notre code |
|---|---|---|
| `px` | Pixel, une taille fixe | `--radius: 14px;`, `max-width: 1140px;` |
| `rem` | Multiple de la taille de texte **de la racine** (16 px par défaut) | `padding: 4rem 0;` → 64 px |
| `em` | Multiple de la taille de texte **de l'élément lui-même** | `margin: 0 0 1em;`, `letter-spacing: 0.12em;` |
| `%` | Pourcentage de la taille du parent | `width: 100%;`, `max-width: 100%;` |
| `ch` | Largeur du caractère « 0 » de la police | `max-width: 14ch;` |
| `fr` | Fraction de l'espace disponible (Grid) | `grid-template-columns: 1fr 1fr;` |
| `s` | Seconde (durées) | `transition: transform 0.2s;` |
| sans unité | Un multiplicateur | `line-height: 1.7;` |

### 10.1 `rem` : l'unité de référence

```css
body {
  font-size: 1rem;           /* 1rem = 16px */
}
```

- **1rem = 16 px** si l'utilisateur n'a pas changé la taille de texte de son navigateur.
- Avantage majeur : si une personne malvoyante règle son navigateur sur « texte très grand », **tout ce qui est en `rem` grandit** proportionnellement. Avec des `px`, rien ne bougerait.

Quelques conversions de notre code :

| Valeur | En pixels (base 16) |
|---|---|
| `0.5rem` | 8 px |
| `1rem` | 16 px |
| `1.5rem` | 24 px |
| `2.8rem` | 44,8 px |
| `5rem` | 80 px |

### 10.2 `em` : relatif à soi-même

```css
h1, h2, h3 {
  margin: 0 0 0.5em;
}
```

La marge sous un titre vaut **la moitié de la taille de ce titre**. Un grand titre a donc une grande marge, un petit titre une petite marge : les proportions restent harmonieuses automatiquement.

```css
.section__label {
  letter-spacing: 0.12em;
}
```

L'espace entre les lettres vaut 12 % de la taille du texte : il s'adapte si on change la taille.

### 10.3 `ch` : en nombre de caractères

```css
.hero__title {
  font-size: 2.8rem;
  max-width: 14ch;               /* limite la largeur à ~14 caractères */
}
```

Le titre « Bienvenue à Montségur » ne dépasse pas environ 14 caractères de large, ce qui le force à passer sur **deux lignes** : « Bienvenue à / Montségur ». C'est plus élégant qu'une très longue ligne.

### 10.4 Sans unité : `line-height`

```css
line-height: 1.7;
```

L'interligne vaut **1,7 fois la taille du texte**. Sans unité, il se recalcule pour chaque taille de texte. C'est la méthode recommandée.

---

## 11. La typographie

### 11.1 `font-family` : la police

```css
--font-title: "Zilla Slab", Georgia, serif;
--font-text: "Montserrat", system-ui, -apple-system, "Segoe UI", sans-serif;
```

On donne une **liste de polices par ordre de préférence**, séparées par des virgules. Le navigateur prend la première disponible :

1. `"Zilla Slab"` : notre police Google Fonts. Les guillemets sont nécessaires car le nom contient une espace.
2. `Georgia` : une police installée sur presque tous les ordinateurs, au cas où Google Fonts ne répond pas.
3. `serif` : un **mot-clé générique** : « n'importe quelle police à empattements ». C'est le filet de sécurité final.

> 🧵 **Analogie** : une liste de courses avec des remplacements : « des fraises Gariguette ; sinon des fraises ; sinon n'importe quel fruit rouge ».

- **serif** = police à **empattements** (les petits pieds au bout des lettres), qui évoque le classique, la pierre gravée : idéale pour les titres d'un site patrimonial.
- **sans-serif** = police **sans empattements**, plus moderne et très lisible à l'écran : idéale pour le texte.

Pour la police de texte, `system-ui`, `-apple-system` et `"Segoe UI"` sont les polices système de Windows, macOS, iOS et Android.

### 11.2 `font-size` : la taille

```css
.hero__title {
  font-size: 2.8rem;
}
```

44,8 px sur mobile. Le chapitre 19 montre comment elle grandit sur les grands écrans (4rem, puis 5rem).

### 11.3 `font-weight` : l'épaisseur

```css
.btn {
  font-weight: 600;
}
```

De 100 (très fin) à 900 (très épais). `400` = normal, `700` = gras. Rappel : on a téléchargé Montserrat en 400, 500 et 600, et Zilla Slab en 600 et 700. On n'utilise que ces valeurs.

### 11.4 `font-style` : l'italique

```css
/* <address> est en italique par défaut : on le remet droit */
.contact__card {
  font-style: normal;
}
```

`normal` ou `italic`. Ici on **annule** l'italique que le navigateur applique d'office à `<address>`.

### 11.5 `line-height` : l'interligne

```css
body { line-height: 1.7; }          /* texte aéré, agréable à lire */
h1, h2, h3 { line-height: 1.15; }   /* titres compacts */
.logo { line-height: 1; }           /* logo très serré */
```

Un texte long a besoin d'air pour que l'œil retrouve facilement la ligne suivante. Un titre en gros caractères, lui, paraît décousu si on l'aère trop.

### 11.6 `text-transform` : la casse

```css
.section__label {
  text-transform: uppercase;
}
```

Affiche le texte en **MAJUSCULES**, sans modifier le HTML. Dans le code, on a écrit « Découvrir » ; à l'écran, on lit « DÉCOUVRIR ». Avantage : le lecteur d'écran lit le mot normalement, au lieu d'épeler des majuscules.

### 11.7 `letter-spacing` : l'espacement des lettres

```css
.logo__subtitle {
  font-size: 0.65rem;
  text-transform: uppercase;
  letter-spacing: 0.18em;
}
```

Espace **ajouté entre chaque lettre**. Les petits textes en majuscules gagnent beaucoup en lisibilité et en élégance quand on les espace. C'est le style « S I T E   O F F I C I E L » sous le logo.

### 11.8 `text-align` : l'alignement

```css
.section__header {
  text-align: center;
}
```

`left` (gauche, par défaut), `center`, `right`, `justify`. Les en-têtes de sections, le bandeau et la ligne de copyright sont centrés.

### 11.9 `text-decoration` : le soulignement

```css
.link-arrow {
  text-decoration: none;
}

.link-arrow:hover {
  text-decoration: underline;
}
```

Les liens sont soulignés par défaut. On retire le soulignement (`none`), et on le **remet au survol** (`underline`) pour confirmer que l'élément est cliquable.

### 11.10 `white-space` et `overflow-wrap` : gérer les retours à la ligne

```css
.main-nav__list {
  white-space: nowrap;     /* empêche les liens de se couper sur 2 lignes */
}
```

`nowrap` interdit au texte de passer à la ligne : « Château et musée » reste sur une seule ligne.

```css
/* Les longues adresses e-mail peuvent passer à la ligne sur petit écran */
.contact__card a {
  overflow-wrap: anywhere;
}
```

L'inverse : une adresse comme `mairie.montsegur@orange.fr` ne contient pas d'espace, donc le navigateur ne sait pas où la couper. Sur un petit téléphone, elle déborderait de la carte. `overflow-wrap: anywhere` autorise une coupure **n'importe où** si nécessaire.

---

## 12. Le modèle de boîte

### 12.1 Tout est une boîte

En CSS, **chaque élément est une boîte rectangulaire**, composée de 4 couches, de l'intérieur vers l'extérieur :

```
┌──────────────────────────────────────┐
│               MARGIN                 │  ← espace extérieur (transparent)
│   ┌──────────────────────────────┐   │
│   │           BORDER             │   │  ← la bordure
│   │   ┌──────────────────────┐   │   │
│   │   │       PADDING        │   │   │  ← espace intérieur (prend le fond)
│   │   │   ┌──────────────┐   │   │   │
│   │   │   │   CONTENT    │   │   │   │  ← le contenu (texte, image)
│   │   │   └──────────────┘   │   │   │
│   │   └──────────────────────┘   │   │
│   └──────────────────────────────┘   │
└──────────────────────────────────────┘
```

> 🖼️ **Analogie** : un tableau accroché au mur.
> - **content** = la toile peinte ;
> - **padding** = le passe-partout, le carton blanc autour de la toile ;
> - **border** = le cadre doré ;
> - **margin** = l'espace vide sur le mur entre ce tableau et le suivant.

### 12.2 `padding` : l'espace intérieur

```css
.card__body {
  padding: 1.5rem;
}
```

24 px d'espace entre le bord de la carte et son texte, **sur les 4 côtés**. Le padding prend la couleur de fond de l'élément.

La propriété `padding` accepte de 1 à 4 valeurs :

| Écriture | Signification | Exemple dans notre code |
|---|---|---|
| `padding: A;` | A sur les 4 côtés | `.card__body { padding: 1.5rem; }` |
| `padding: A B;` | A en haut et en bas, B à gauche et à droite | `.btn { padding: 0.85rem 1.6rem; }` |
| `padding: A B C D;` | haut, droite, bas, gauche (sens des aiguilles d'une montre) | — |

> 🕐 **Astuce mnémotechnique** pour 4 valeurs : on part de **midi** et on tourne comme une aiguille : **haut → droite → bas → gauche**.

Exemple pas à pas :

```css
.section {
  padding: 4rem 0;
}
```

→ 64 px **en haut et en bas** (l'espace qui sépare les sections), **0 à gauche et à droite**.

On peut aussi viser un seul côté :

```css
.site-footer {
  padding-top: 3rem;
}
```

### 12.3 `margin` : l'espace extérieur

```css
p {
  margin: 0 0 1em;
}
```

Avec **3 valeurs** : haut = `0`, gauche et droite = `0`, bas = `1em`. Les paragraphes n'ont donc d'espace **qu'en dessous**.

```css
body {
  margin: 0;
}
```

Les navigateurs ajoutent par défaut 8 px de marge autour de la page. On les retire pour que l'en-tête et les bandeaux touchent les bords de l'écran.

```css
.split__image {
  margin: 0;
}
```

Même chose pour `<figure>`, qui a des marges par défaut (le commentaire du code le précise).

**Centrer une boîte avec `margin: auto`** :

```css
.container {
  width: 100%;
  max-width: 1140px;
  margin: 0 auto;
  padding: 0 1rem;
}
```

Ligne par ligne :

- `width: 100%` → la boîte prend toute la largeur disponible…
- `max-width: 1140px` → … mais **jamais plus de 1140 px**. Sur un grand écran, le texte ne s'étale pas sur toute la largeur (illisible).
- `margin: 0 auto` → 0 en haut et en bas ; `auto` à gauche et à droite. Le navigateur **partage l'espace restant à parts égales** des deux côtés : la boîte est **centrée**.
- `padding: 0 1rem` → 16 px d'espace intérieur à gauche et à droite, pour que le texte ne colle jamais au bord de l'écran sur mobile.

> 📏 **Analogie** : `.container` est comme une **colonne de journal**. Quelle que soit la taille de la table, le journal garde une largeur lisible et on le pose au milieu.

Presque toutes nos sections ont une `<div class="container">` à l'intérieur : le **fond** de la section s'étend sur tout l'écran, mais le **contenu** reste centré.

Autres centrages par `auto` :

```css
.section__header {
  max-width: 640px;
  margin: 0 auto 2.5rem;    /* haut 0, côtés auto (centré), bas 2.5rem */
}

.split__image img {
  max-width: 360px;
  width: 100%;
  margin: 0 auto;
}
```

### 12.4 `border` : la bordure

```css
.contact__card {
  border-top: 4px solid var(--color-accent);
}
```

La syntaxe raccourcie : **épaisseur, style, couleur**.

- `4px` → épaisseur ;
- `solid` → trait plein (il existe aussi `dashed` pour des tirets, `dotted` pour des points) ;
- `var(--color-accent)` → bordeaux.

`border-top` ne trace que le **haut** : c'est le liseré bordeaux en haut de la carte contact.

Autres bordures de notre code :

```css
.tag {
  border: 1px solid rgba(255, 255, 255, 0.5);   /* contour blanc à moitié transparent */
}

.footer__copy {
  border-top: 1px solid rgba(255, 255, 255, 0.1); /* fine ligne de séparation */
}

.main-nav__list a {
  border-bottom: 2px solid transparent;          /* soulignement invisible… */
}

.main-nav__list a:hover {
  border-bottom-color: var(--color-stone-deep);  /* … qui devient beige au survol */
}
```

L'astuce du menu : la bordure basse **existe toujours** mais est transparente. Au survol, on change **seulement sa couleur** avec `border-bottom-color`. Comme la bordure était déjà là, rien ne bouge : le texte ne « saute » pas.

### 12.5 `border-radius` : les coins arrondis

```css
.card {
  border-radius: var(--radius);    /* 14px */
}

.btn {
  border-radius: 50px;
}

.quick-links__item {
  border-radius: 999px;
}
```

- `14px` → coins légèrement arrondis pour les cartes.
- `50px` ou `999px` → une valeur **plus grande que la moitié de la hauteur** donne des extrémités parfaitement rondes : c'est la forme **pilule** (*pill*) des boutons, des étiquettes et des pastilles.

### 12.6 `box-shadow` : l'ombre portée

```css
.quick-links__item[aria-current="page"],
.quick-links__item:active {
  box-shadow: 0 6px 16px -8px rgba(35, 31, 32, 0.6);
}
```

Les valeurs, dans l'ordre :

1. `0` → décalage horizontal (aucun) ;
2. `6px` → décalage vertical (l'ombre descend de 6 px, comme sous une lumière venant d'en haut) ;
3. `16px` → flou (plus c'est grand, plus l'ombre est douce) ;
4. `-8px` → étalement négatif : l'ombre est **plus petite** que la pastille, ce qui la rend discrète ;
5. `rgba(35, 31, 32, 0.6)` → couleur anthracite à 60 %.

Résultat : la pastille active semble **légèrement soulevée** du bandeau.

Les cartes utilisent `box-shadow: var(--shadow)`, mais cette variable n'est pas déclarée : voir chapitre 21.

### 12.7 `width`, `max-width`, `height`, `min-height`

```css
.hero {
  min-height: 560px;              /* hauteur minimale de la bannière */
}
```

- `width` / `height` → largeur / hauteur **fixes**.
- `max-width` → largeur **maximale** : la boîte peut être plus petite, jamais plus grande.
- `min-height` → hauteur **minimale** : la boîte peut grandir si son contenu l'exige, mais ne sera jamais plus petite.

Pour le hero, `min-height` est idéal : la bannière fait au moins 560 px, mais si le texte est plus long (sur un petit écran par exemple), elle s'agrandit au lieu de couper le texte.

```css
.quick-links__item {
  height: 100%;
}
```

Chaque pastille prend toute la hauteur de sa case : si un libellé tient sur deux lignes, toutes les pastilles de la rangée ont la même hauteur.

### 12.8 `box-sizing` : comment on mesure la boîte

Par défaut (`content-box`), la `width` ne concerne **que le contenu**. Le padding et la bordure s'**ajoutent** par-dessus :

```
width: 100%  +  padding 1rem à gauche  +  padding 1rem à droite
= 100% + 32px  → la boîte dépasse de son parent !
```

Avec `box-sizing: border-box`, la `width` **inclut** le padding et la bordure. C'est beaucoup plus intuitif : « 100 % » veut vraiment dire 100 %.

Dans notre code :

```css
.quick-links__item {
  height: 100%;
  box-sizing: border-box;
  padding: 0.7rem 1.1rem;
}
```

Grâce à `border-box`, la pastille fait **exactement** 100 % de la hauteur de sa case, padding compris.

La règle globale qui applique `border-box` à **tous** les éléments existe en haut du fichier, mais elle est **commentée** (donc inactive). Nous verrons au chapitre 21 pourquoi il faut la réactiver.

```css
/* La largeur d'un élément inclut son padding et sa bordure */
/* *,
*::before,
*::after {
  box-sizing: border-box;
} */
```

### 12.9 `display` : le type de boîte

`display` décide **comment une boîte se comporte** par rapport aux autres. Valeurs utilisées dans notre code :

| Valeur | Effet | Exemple |
|---|---|---|
| `block` | Bloc : toute la largeur, passe à la ligne | `img`, `.logo__subtitle`, `.contact__label` |
| `inline-block` | Reste dans la ligne, mais accepte largeur, hauteur et padding vertical | `.tag`, `.news__date` |
| `flex` | Range ses enfants en ligne ou en colonne (chapitre 14) | `.header__inner`, `.card` |
| `grid` | Range ses enfants dans un quadrillage (chapitre 15) | `.card-grid`, `.footer__inner` |

Exemple :

```css
.logo__subtitle {
  display: block;
  margin-top: 0.3rem;
}
```

Le `<span>` « Site officiel » est en ligne par défaut : il se placerait à côté de « Montségur ». En le passant en `block`, il descend **sous** le nom.

```css
.tag {
  display: inline-block;
  padding: 0.3rem 0.85rem;
}
```

Les étiquettes du hero restent côte à côte (comportement en ligne), mais acceptent un padding vertical qui pousse correctement les éléments autour (comportement bloc). Le meilleur des deux mondes.

### 12.10 `overflow` : ce qui dépasse

```css
.card {
  border-radius: var(--radius);
  overflow: hidden;              /* l'image suit les coins arrondis */
}
```

`overflow: hidden` **coupe** tout ce qui dépasse de la boîte. Sans lui, l'image carrée de la carte déborderait des coins arrondis. Avec, elle est découpée proprement en suivant l'arrondi.

> ✂️ **Analogie** : un emporte-pièce. Tout ce qui sort de la forme est coupé.

```css
.main-nav__list {
  overflow-x: auto;        /* si le menu est trop long : défilement horizontal */
}
```

`overflow-x` ne concerne que l'axe horizontal. `auto` = « ajoute une barre de défilement **seulement si nécessaire** ». Sur un téléphone, le menu trop long peut **glisser du doigt** horizontalement.

---

## 13. Les fonds et les images

### 13.1 `background-color`

```css
.section--alt {
  background-color: var(--color-stone);
}
```

Une couleur de fond. On alterne les sections claires (`--color-stone-light`, hérité du `body`) et un peu plus foncées (`--color-stone`), comme les **rayures d'un pull** : l'œil distingue facilement où commence chaque partie.

### 13.2 `background-image` avec un dégradé

Le bandeau « Le vaisseau de pierre » :

```css
.banner {
  background-image:
    linear-gradient(rgba(35, 31, 32, 0.55), rgba(35, 31, 32, 0.55)),
    url("images/hero-montsegur.jpg");
  background-size: cover;
  background-position: center 40%;   /* cadre le château sur son pog */
  color: var(--color-white);
  padding: 6rem 0;
  text-align: center;
}
```

Ligne par ligne :

- `background-image:` → on empile **deux couches** de fond, séparées par une virgule. **La première écrite est au-dessus.**
  - `linear-gradient(rgba(35, 31, 32, 0.55), rgba(35, 31, 32, 0.55))` → un **dégradé** d'une couleur vers… la même couleur : c'est en fait un **voile uni** anthracite à 55 %. Il assombrit la photo pour que le texte blanc soit lisible.
  - `url("images/hero-montsegur.jpg")` → la **photo** du château, en dessous. Le chemin est relatif au fichier CSS.
- `background-size: cover` → la photo est agrandie ou réduite pour **couvrir toute la surface**, sans déformation. Ce qui dépasse est coupé.
- `background-position: center 40%` → horizontalement centrée ; verticalement, on garde la partie située à 40 % depuis le haut, là où se trouve le château.
- `color: var(--color-white)` → texte blanc.
- `padding: 6rem 0` → 96 px en haut et en bas : c'est ce qui donne sa **hauteur** au bandeau.
- `text-align: center` → texte centré.

> 🕶️ **Analogie** : le voile sombre est comme des lunettes de soleil posées sur la photo. Elle reste visible, mais le texte blanc ressort beaucoup mieux.

### 13.3 `background` et le dégradé du hero

```css
/* Dégradé sombre au-dessus des images pour rendre le texte lisible */
.hero::before {
  ...
  background: linear-gradient(to top, rgba(35, 31, 32, 0.85), rgba(35, 31, 32, 0.25));
}
```

- `background` est la propriété **raccourcie** qui regroupe toutes les propriétés `background-*`.
- `linear-gradient(to top, A, B)` → un dégradé **du bas vers le haut** : de A (anthracite à 85 %, très sombre) en bas, vers B (anthracite à 25 %, léger) en haut.

Pourquoi ? Le texte du hero est placé **en bas** de la bannière : c'est là qu'il faut le plus assombrir. En haut, on laisse la photo respirer.

### 13.4 `object-fit` et `aspect-ratio` : recadrer les `<img>`

Pour les vraies balises `<img>`, l'équivalent de `background-size: cover` est `object-fit` :

```css
.card__image {
  width: 100%;
  aspect-ratio: 3 / 2;           /* même proportion pour toutes les images */
  object-fit: cover;             /* recadre sans déformer */
}
```

Ligne par ligne :

- `width: 100%` → l'image prend toute la largeur de la carte.
- `aspect-ratio: 3 / 2` → sa hauteur est calculée pour respecter un **rapport 3:2** (3 de large pour 2 de haut), le format classique d'une photo. Les trois cartes ont donc des images **de même hauteur**, même si les fichiers d'origine ont des formats différents.
- `object-fit: cover` → l'image **remplit** ce cadre sans être déformée : ce qui dépasse est rogné.

> 🖼️ **Analogie** : vous mettez une photo dans un cadre plus petit. `cover` coupe les bords pour la faire tenir sans l'écraser. Sans `object-fit`, la photo serait **étirée**, avec des visages aplatis.

Les actualités utilisent un format plus allongé :

```css
.news__image {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}
```

`16 / 9` est le format des écrans de télévision.

Pour le logo, il **ne faut surtout pas** le rogner :

```css
/* Le logo ne doit pas être recadré : on le centre sur le vert
   officiel du logo Grand Site de France (seule couleur hors charte) */
.news__image--logo {
  object-fit: contain;
  background-color: #275f38;
  padding: 2rem;
}
```

- `object-fit: contain` → l'image entière est visible, réduite pour **tenir dans le cadre**. Il reste des espaces vides…
- `background-color: #275f38` → … qu'on remplit avec le **vert officiel** du logo, pour que l'ensemble paraisse voulu.
- `padding: 2rem` → de l'air autour du logo.

| `object-fit` | Comportement | Usage |
|---|---|---|
| `cover` | Remplit tout le cadre, rogne ce qui dépasse | Photos |
| `contain` | Montre tout, laisse des bandes vides | Logos, schémas |

### 13.5 `backdrop-filter` : le verre dépoli

```css
.tag {
  backdrop-filter: blur(4px);    /* léger flou derrière l'étiquette */
  background-color: rgba(0, 0, 0, 0.2);
}
```

- `backdrop-filter` applique un filtre à **ce qui se trouve derrière** l'élément.
- `blur(4px)` → un flou de 4 px.
- Combiné à un fond semi-transparent, cela crée un effet de **verre dépoli** : les étiquettes « Patrimoine mondial UNESCO », etc. restent lisibles quelle que soit la photo derrière.

> 🚿 **Analogie** : la vitre dépolie d'une douche. On devine les formes derrière, mais elles ne gênent pas.

### 13.6 `opacity` : la transparence d'un élément entier

```css
.hero__slide {
  opacity: 0;
}
```

`opacity` va de **0** (invisible) à **1** (totalement visible). Contrairement à `rgba()` qui rend une seule **couleur** transparente, `opacity` rend **tout l'élément** transparent, contenu compris. C'est la base du fondu du carrousel (chapitre 18).

---

## 14. Flexbox : aligner sur une ligne

### 14.1 Le principe

**Flexbox** est un mode de mise en page pour ranger des éléments **sur un axe** : en ligne (par défaut) ou en colonne. On l'active **sur le parent** avec `display: flex`, et ce sont **ses enfants directs** qui se rangent.

> 📚 **Analogie** : une étagère. Le parent est l'étagère, les enfants sont les livres. On décide comment ranger les livres : serrés à gauche, répartis, centrés, sur plusieurs étagères s'il n'y a pas la place…

### 14.2 L'en-tête : logo, menu et bouton

```css
/* Flexbox : logo, menu et bouton côte à côte.
   flex-wrap permet de passer à la ligne si la place manque. */
.header__inner {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  gap: 0.75rem 1.5rem;
}
```

Les enfants de `.header__inner` sont : le logo, le `<nav>`, le bouton Billetterie.

Ligne par ligne :

- `display: flex` → les trois enfants se rangent **côte à côte**.
- `flex-wrap: wrap` → s'il n'y a pas assez de place, ils **passent à la ligne** au lieu de s'écraser. (Valeur par défaut : `nowrap`, tout sur une ligne.)
- `align-items: center` → alignement sur l'axe **vertical** : les trois éléments sont **centrés en hauteur** les uns par rapport aux autres. Le petit bouton est aligné avec le milieu du logo.
- `justify-content: space-between` → répartition sur l'axe **horizontal** : le premier élément est collé à gauche, le dernier à droite, et l'espace restant est réparti **entre** eux.
- `gap: 0.75rem 1.5rem` → l'**écart** entre les éléments : 12 px entre les lignes, 24 px entre les colonnes.

Les deux axes de flexbox :

```
justify-content →  (axe principal : horizontal par défaut)
┌──────────────────────────────────────────────┐
│ [Logo]          [Menu .........]  [Billet.]  │  ↕ align-items
└──────────────────────────────────────────────┘    (axe secondaire)
```

Valeurs utiles de `justify-content` :

| Valeur | Résultat |
|---|---|
| `flex-start` | Tout à gauche (par défaut) |
| `center` | Tout au centre |
| `flex-end` | Tout à droite |
| `space-between` | Premier à gauche, dernier à droite, espace entre |

### 14.3 `order` : changer l'ordre d'affichage

```css
/* Sur mobile, le menu occupe toute la largeur sous le logo
   (order: 3 le place après le bouton) */
.main-nav {
  order: 3;
  width: 100%;
}
```

- `order` change l'ordre **visuel** d'un enfant flex, sans toucher au HTML. Par défaut, tous les éléments ont `order: 0`. Avec `order: 3`, le menu passe **après** les autres, donc après le bouton.
- `width: 100%` → le menu prend toute la largeur. Comme `flex-wrap: wrap` est actif, il est **obligé de passer à la ligne**.

Résultat sur mobile :

```
┌─────────────────────────────────┐
│ Montségur           [Billetterie]│
│ Château · Village · Sentiers  → │  ← le menu, sur sa propre ligne
└─────────────────────────────────┘
```

Sur ordinateur, le chapitre 19 remet `order: 0` et `width: auto` : le menu revient entre le logo et le bouton.

### 14.4 Le menu lui-même

```css
.main-nav__list {
  display: flex;
  gap: 1.25rem;
  list-style: none;
  margin: 0;
  padding: 0.25rem 0;
  overflow-x: auto;        /* si le menu est trop long : défilement horizontal */
  white-space: nowrap;     /* empêche les liens de se couper sur 2 lignes */
}
```

- `display: flex` → les `<li>` (normalement empilés) se mettent **en ligne**.
- `gap: 1.25rem` → 20 px entre chaque lien.
- `list-style: none` → supprime les **puces**.
- `margin: 0` et `padding: 0.25rem 0` → retire les marges par défaut des listes (les navigateurs ajoutent un retrait à gauche pour les puces).
- `overflow-x: auto` + `white-space: nowrap` → sur un petit écran, le menu reste sur une ligne et **défile horizontalement**.

### 14.5 Les étiquettes et les boutons du hero

```css
.hero__labels {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  list-style: none;
  margin: 0 0 1.5rem;
  padding: 0;
}

.hero__buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}
```

Même recette : en ligne, avec un écart régulier, et passage à la ligne si l'écran est trop étroit. C'est le **motif flexbox le plus courant** : `display: flex` + `flex-wrap: wrap` + `gap`.

> 💡 **`gap`** est la manière moderne d'espacer des éléments : l'espace est mis **uniquement entre** eux, jamais avant le premier ni après le dernier.

### 14.6 Le hero : coller le texte en bas

```css
.hero {
  min-height: 560px;              /* hauteur minimale de la bannière */
  display: flex;
  align-items: flex-end;          /* le texte se place en bas */
  padding: 4rem 0;
}
```

Le hero est un conteneur flex ; son enfant est `.hero__content`. `align-items: flex-end` aligne cet enfant **à la fin de l'axe vertical**, c'est-à-dire **en bas** de la bannière. Le texte se pose en bas, sur la partie la plus sombre du dégradé, et la photo occupe le haut.

### 14.7 Les cartes : flexbox en colonne

```css
.card {
  display: flex;
  flex-direction: column;
  ...
}

.card__body {
  display: flex;
  flex-direction: column;
  flex-grow: 1;                  /* toutes les cartes ont la même hauteur */
  padding: 1.5rem;
}

.card__text {
  color: var(--color-text-light);
  flex-grow: 1;                  /* pousse le lien en bas de la carte */
}
```

C'est une technique très utile. Décomposons :

- `flex-direction: column` → l'axe principal devient **vertical** : les enfants s'empilent de haut en bas (image, puis corps de la carte).
- Dans la grille (chapitre 15), les trois cartes d'une rangée ont la même hauteur. Mais leurs textes ont des longueurs différentes.
- `flex-grow: 1` sur `.card__body` → le corps de la carte **prend toute la place restante** sous l'image.
- `flex-grow: 1` sur `.card__text` → à l'intérieur du corps, le paragraphe **s'étire** pour occuper l'espace vide…
- … ce qui **pousse le lien « En savoir plus » tout en bas**.

Résultat : les trois liens « En savoir plus » sont **parfaitement alignés**, quelle que soit la longueur des textes.

```
┌─────────┐ ┌─────────┐ ┌─────────┐
│  image  │ │  image  │ │  image  │
│ Titre   │ │ Titre   │ │ Titre   │
│ texte   │ │ texte   │ │ texte   │
│ court   │ │ texte   │ │ texte   │
│         │ │ long    │ │ moyen   │
│         │ │ long    │ │         │
│ Lien →  │ │ Lien →  │ │ Lien →  │  ← alignés grâce à flex-grow
└─────────┘ └─────────┘ └─────────┘
```

> 🎈 **Analogie** : `flex-grow: 1` est un ballon qu'on gonfle dans un carton : il prend tout l'espace libre et pousse le reste contre la paroi.

### 14.8 Les pastilles : centrer dans les deux sens

```css
.quick-links__item {
  display: flex;
  align-items: center;
  justify-content: center;
  ...
}
```

`align-items: center` + `justify-content: center` = **centrage parfait**, horizontal et vertical. Le texte de chaque pastille est au milieu, même si une pastille voisine est plus haute.

### 14.9 Les réseaux sociaux du pied de page

```css
/* Variante : liens côte à côte (réseaux sociaux) */
.footer__list--inline {
  display: flex;
  gap: 1.25rem;
}
```

Facebook et Instagram côte à côte, au lieu d'être empilés.

---

## 15. CSS Grid : ranger dans un tableau

### 15.1 Le principe

Si flexbox range sur **une ligne**, **Grid** range dans un **quadrillage à deux dimensions** : lignes **et** colonnes.

> 🍫 **Analogie** : une tablette de chocolat, ou une boîte à œufs. On définit le nombre de cases, et chaque enfant se place dans une case.

On l'active sur le parent avec `display: grid`, puis on définit les colonnes avec `grid-template-columns`.

### 15.2 L'unité `fr`

`fr` (*fraction*) représente **une part de l'espace disponible**.

- `1fr 1fr` → 2 colonnes **égales**.
- `3fr 2fr` → 2 colonnes : la première prend 3 parts, la seconde 2 parts (sur 5 au total), soit 60 % / 40 %.

### 15.3 Les infos pratiques : 2 puis 4 colonnes

```css
/* Grille de 2 colonnes sur mobile, liens en forme de pastille (pill) */
.quick-links__list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.5rem;
  list-style: none;
  margin: 0;
  padding: 0.85rem 0;
}
```

- `display: grid` → active la grille.
- `grid-template-columns: repeat(2, 1fr)` → `repeat(2, 1fr)` est un raccourci pour `1fr 1fr` : **2 colonnes égales**. Les 4 liens forment donc un carré de 2 × 2.
- `gap: 0.5rem` → 8 px entre les cases.
- `list-style: none; margin: 0;` → on retire puces et marges de la liste.
- `padding: 0.85rem 0` → de l'air au-dessus et en dessous des pastilles.

Sur tablette et ordinateur, une media query passe à `repeat(4, 1fr)` : **4 colonnes** sur une seule ligne (chapitre 19).

### 15.4 Les cartes « Découvrir » : une grille automatique

```css
/* CSS Grid : autant de colonnes que possible, de 280px minimum */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}
```

C'est la ligne la plus « magique » du fichier. Décomposons-la de l'intérieur vers l'extérieur :

- `minmax(280px, 1fr)` → chaque colonne fait **au minimum 280 px**, et **au maximum une part égale** de l'espace.
- `auto-fit` → « crée **autant de colonnes qu'il en tient** ».
- `repeat(auto-fit, ...)` → répète ce modèle autant que possible.

Résultat, **sans aucune media query** :

| Largeur disponible | Colonnes |
|---|---|
| Téléphone (≈ 350 px) | 1 colonne (une seule tient avec 280 px minimum) |
| Tablette (≈ 650 px) | 2 colonnes |
| Ordinateur (≈ 1100 px) | 3 colonnes |

> 🪑 **Analogie** : un restaurant qui installe des tables de 280 cm minimum. Petite salle : une table. Grande salle : autant de tables qu'il en tient, élargies pour remplir l'espace.

### 15.5 Le bloc UNESCO : texte + image

```css
/* Sur mobile : texte puis image, l'un sous l'autre */
.split {
  display: grid;
  gap: 2.5rem;
  align-items: center;
}
```

- Sans `grid-template-columns`, la grille a **une seule colonne** : le texte et l'image sont **empilés**.
- `gap: 2.5rem` → 40 px entre les deux.
- `align-items: center` → centre verticalement les éléments dans leur case (utile quand ils seront côte à côte).

Sur ordinateur :

```css
.split {
  grid-template-columns: 3fr 2fr;
  gap: 4rem;
}
```

→ texte à gauche (60 %), affiche à droite (40 %).

### 15.6 Les actualités, le contact, le pied de page

Même principe partout :

```css
.news-grid {
  display: grid;
  gap: 2rem;
}                    /* mobile : 1 colonne → tablette : repeat(2, 1fr) */

.contact {
  display: grid;
  gap: 2.5rem;
  align-items: center;
}                    /* mobile : 1 colonne → ordinateur : 1fr 1fr */

.footer__inner {
  display: grid;
  gap: 2rem;
}                    /* mobile : 1 colonne → tablette : repeat(3, 1fr) */
```

On écrit d'abord une grille à **une colonne** pour le téléphone, et on ajoute des colonnes pour les grands écrans dans les media queries. C'est la méthode **mobile first** (chapitre 19).

### 15.7 Flexbox ou Grid ?

| Besoin | Outil | Exemple dans notre code |
|---|---|---|
| Aligner des éléments sur **une ligne**, tailles libres | **Flexbox** | Menu, boutons, étiquettes |
| Empiler et pousser des éléments dans une colonne | **Flexbox** | Intérieur des cartes |
| Ranger dans des **colonnes régulières** | **Grid** | Cartes, actualités, pied de page |
| Deux zones de proportions précises | **Grid** | Bloc UNESCO (3fr 2fr) |

> 💡 **Règle simple** : flexbox pour **une dimension**, Grid pour **deux dimensions** ou des colonnes bien alignées.

---

## 16. Le positionnement et les calques

### 16.1 Le flux normal

Par défaut, les éléments suivent le **flux normal** : ils s'empilent de haut en bas comme les lignes d'un texte, sans se chevaucher. La propriété `position` permet d'en sortir.

### 16.2 `position: relative` et `position: absolute`

Le hero superpose **4 couches** :

```
  (le visiteur regarde d'ici)
            👁
  ┌──────────────────────────┐  z-index: 2  → le texte et les boutons (.hero__content)
  ├──────────────────────────┤  z-index: 1  → le dégradé sombre (.hero::before)
  ├──────────────────────────┤  z-index: 0  → les 3 photos du diaporama (.hero__slides)
  └──────────────────────────┘  fond         → couleur anthracite (.hero)
```

Le code :

```css
.hero {
  position: relative;
  overflow: hidden;               /* masque le zoom des images */
  isolation: isolate;             /* garde les calques dans la bannière */
  background-color: var(--color-dark);
  color: var(--color-white);
  ...
}
```

- `position: relative` → le hero devient le **repère** de ses enfants positionnés. Sans cela, les calques `absolute` se positionneraient par rapport à la page entière.
- `overflow: hidden` → rien ne dépasse de la bannière.
- `isolation: isolate` → crée un **contexte d'empilement** isolé : les `z-index` des enfants ne s'appliquent qu'**à l'intérieur** du hero et ne peuvent pas passer au-dessus d'autres parties de la page.
- `background-color: var(--color-dark)` → un fond anthracite, visible seulement pendant le chargement des images.

```css
.hero__slides {
  position: absolute;
  inset: 0;
  z-index: 0;
}
```

- `position: absolute` → l'élément **sort du flux** : il ne pousse plus les autres éléments, il « flotte ». Il se place par rapport à son repère, le hero.
- `inset: 0` → raccourci pour `top: 0; right: 0; bottom: 0; left: 0;`. L'élément est collé aux **4 bords** du repère : il **couvre tout le hero**.
- `z-index: 0` → sa place dans la pile : tout en dessous.

> 🗂️ **Analogie** : des **calques transparents** sur un rétroprojecteur. `position: absolute` pose une feuille par-dessus les autres. `z-index` est le numéro de la feuille dans la pile : plus il est grand, plus la feuille est au-dessus.

```css
.hero__content {
  position: relative;
  z-index: 2;                     /* le texte passe devant les images */
}
```

Le contenu reste dans le flux (`relative` ne le déplace pas), mais `z-index` ne fonctionne que sur un élément positionné : on lui met donc `position: relative` pour pouvoir le placer **au-dessus** (`z-index: 2`).

### 16.3 Le lien d'évitement : `absolute` pour cacher

```css
/* Lien d'évitement : caché hors de l'écran, il apparaît au clavier (Tab) */
.skip-link {
  position: absolute;
  left: 1rem;
  top: -100px;
  background: var(--color-white);
  padding: 0.5rem 1rem;
  z-index: 10;
}

.skip-link:focus {
  top: 1rem;
}
```

- `top: -100px` → le lien est placé **100 px au-dessus du haut de la page**, donc invisible.
- `:focus` → quand on le sélectionne avec la touche **Tab**, `top: 1rem` le fait **apparaître** en haut à gauche.
- `z-index: 10` → il passe devant tout.

Ce lien permet aux personnes qui naviguent au clavier de **sauter le menu** pour aller directement au contenu. Le style est prêt, mais le lien n'est pas encore dans le HTML (voir chapitre 21).

---

## 17. Les pseudo-classes et pseudo-éléments

### 17.1 Les pseudo-classes : réagir à un état

Une **pseudo-classe** (avec **un** deux-points `:`) vise un élément **dans un certain état**.

#### `:hover` : le survol de la souris

```css
.btn--primary {
  background-color: var(--color-accent);
  color: var(--color-white);
}

.btn--primary:hover {
  background-color: var(--color-accent-dark);
}
```

Le bouton bordeaux devient **bordeaux foncé** quand la souris passe dessus. C'est un **retour visuel** : « oui, c'est cliquable ».

Tous les survols de notre site :

| Élément | Effet au survol |
|---|---|
| Bouton bordeaux (`.btn--primary`) | Fond plus foncé |
| Bouton contour (`.btn--outline`) | Voile blanc à 15 % |
| Liens « En savoir plus » (`.link-arrow`) | Soulignés |
| Menu principal | Texte blanc + trait beige en dessous |
| Pastilles infos pratiques | Fond anthracite à 8 % |
| Cartes (`.card`) | Montent de 4 px |
| Liens du pied de page | Blancs et soulignés |

#### `:focus` et `:focus-visible` : la navigation au clavier

```css
/* Contour bien visible pour la navigation au clavier */
a:focus-visible {
  outline: 3px solid var(--color-accent);
  outline-offset: 3px;
}
```

- Quand on navigue avec la touche **Tab**, l'élément sélectionné a le **focus**.
- `:focus-visible` ne s'active **que pour le clavier**, pas au clic de la souris. On évite ainsi un contour disgracieux après chaque clic, tout en gardant une indication claire pour qui en a besoin.
- `outline` → un **contour** de 3 px bordeaux. Contrairement à `border`, il **ne prend pas de place** : il ne décale rien.
- `outline-offset: 3px` → le contour est décollé de 3 px de l'élément, pour être plus lisible.

> 🔦 **Analogie** : `:focus-visible`, c'est le faisceau d'une lampe torche qui montre où l'on se trouve quand on avance dans le noir (sans souris).

Les pastilles ont leur propre contour, anthracite, mieux visible sur le fond beige :

```css
/* Navigation au clavier : contour net et visible */
.quick-links__item:focus-visible {
  outline: 2px solid var(--color-dark);
  outline-offset: 2px;
}
```

#### `:active` : le moment du clic

```css
/* État actif (page en cours ou clic) : pastille anthracite pleine */
.quick-links__item[aria-current="page"],
.quick-links__item:active {
  background-color: var(--color-dark);
  color: var(--color-white);
  box-shadow: 0 6px 16px -8px rgba(35, 31, 32, 0.6);
}
```

- `:active` s'applique **pendant que le bouton de la souris est enfoncé**. La pastille devient anthracite pleine au moment du clic.
- `[aria-current="page"]` vise un lien qui porterait l'attribut `aria-current="page"` : il resterait **affiché en anthracite en permanence**, pour indiquer « vous êtes sur cette page ». Sur la page d'accueil, aucun lien ne porte cet attribut.

Pour l'utiliser sur une future page « Accès » :

```html
<a href="#" class="quick-links__item" aria-current="page">Accès</a>
```

### 17.2 Les pseudo-éléments : créer du contenu en CSS

Un **pseudo-élément** (avec **deux** deux-points `::`) crée une **boîte supplémentaire** qui n'existe pas dans le HTML.

- `::before` → une boîte **au début** de l'élément.
- `::after` → une boîte **à la fin** de l'élément.

Ils exigent la propriété `content`, même vide.

#### La flèche des liens

```css
/* ::after ajoute une flèche après le texte, sans toucher au HTML */
.link-arrow::after {
  content: " →";
}
```

Dans le HTML, on a écrit `En savoir plus`. À l'écran, on lit **« En savoir plus → »**. La flèche est **décorative** : on la met en CSS pour ne pas la répéter dans chaque lien, et on peut la changer en une seule ligne.

#### Le dégradé du hero

```css
.hero::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 1;
  background: linear-gradient(to top, rgba(35, 31, 32, 0.85), rgba(35, 31, 32, 0.25));
}
```

- `content: ""` → une boîte **vide** (sans texte), mais qui existe.
- `position: absolute; inset: 0;` → elle couvre tout le hero.
- `z-index: 1` → entre les photos (0) et le texte (2).
- `background: linear-gradient(...)` → le voile sombre.

On évite ainsi d'ajouter une `<div>` vide dans le HTML uniquement pour la décoration.

> ✨ **Analogie** : les pseudo-éléments sont des **autocollants** que le CSS colle sur un élément. Ils ne font pas partie de la structure, ils décorent.

---

## 18. Transitions et animations : le carrousel

### 18.1 `transition` : passer en douceur d'un état à l'autre

Sans transition, un changement au survol est **instantané**, brutal. Une transition le rend **progressif**.

```css
.card {
  ...
  transition: transform 0.2s;
}

.card:hover {
  transform: translateY(-4px);
}
```

- `transition: transform 0.2s` → « quand la propriété `transform` change, fais le changement **en 0,2 seconde** ».
- `transform: translateY(-4px)` → **déplace** la carte de 4 px **vers le haut** (axe Y vertical ; négatif = vers le haut).

Résultat : au survol, la carte **se soulève doucement**, comme si on la prenait en main.

> 🎚️ **Analogie** : un variateur de lumière. Sans transition, c'est un interrupteur (allumé/éteint d'un coup). Avec, la lumière monte progressivement.

`transform` est idéal pour les animations : il déplace l'élément **visuellement**, sans recalculer la mise en page autour. C'est fluide, même sur un téléphone peu puissant.

Plusieurs transitions à la fois :

```css
.quick-links__item {
  transition:
    background-color 0.3s ease,
    color 0.3s ease,
    box-shadow 0.3s ease;
}
```

- Trois propriétés, séparées par des virgules, chacune en 0,3 s.
- `ease` → la **courbe de vitesse** : démarrage doux, accélération, arrivée douce. C'est plus naturel qu'une vitesse constante.

Au survol, le fond des pastilles apparaît en **fondu**, au lieu de clignoter d'un coup.

### 18.2 `@keyframes` et `animation` : le diaporama

Une **transition** a besoin d'un déclencheur (le survol). Une **animation** se lance **toute seule** et peut se **répéter** à l'infini. C'est ce qu'il faut pour un carrousel automatique.

#### Étape 1 : le HTML, trois toiles empilées

```html
<div class="hero__slides" aria-hidden="true">
  <span class="hero__slide hero__slide--1"></span>
  <span class="hero__slide hero__slide--2"></span>
  <span class="hero__slide hero__slide--3"></span>
</div>
```

#### Étape 2 : chaque toile couvre tout le hero, invisible

```css
.hero__slide {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  opacity: 0;
  animation: hero-fade 18s ease-in-out infinite;   /* 6s par image */
}
```

- `position: absolute; inset: 0;` → les trois `<span>` sont **empilés exactement au même endroit**, et couvrent tout le hero.
- `background-size: cover; background-position: center;` → chaque photo remplit la surface, centrée.
- `opacity: 0` → par défaut, toutes sont **invisibles**.
- `animation: hero-fade 18s ease-in-out infinite;` → la propriété raccourcie :
  - `hero-fade` → le **nom** de l'animation à jouer (définie plus bas) ;
  - `18s` → la **durée** d'un cycle complet : 18 secondes ;
  - `ease-in-out` → la courbe de vitesse : départ et arrivée en douceur ;
  - `infinite` → **répète à l'infini**.

#### Étape 3 : une photo différente pour chaque toile

```css
/* Délais décalés de 6s ; -1.44s = la 1re image est déjà visible au chargement */
.hero__slide--1 {
  background-image: url("images/carrousel/pog2-montsegur%20(2).jpg");
  animation-delay: -1.44s;
}

.hero__slide--2 {
  background-image: url("images/carrousel/village.jpg");
  animation-delay: 4.56s;
}

.hero__slide--3 {
  background-image: url("images/carrousel/village_2.jpg");
  animation-delay: 10.56s;
}
```

- `background-image: url(...)` → la photo de chaque toile.
- `%20` dans le nom du premier fichier : le nom réel contient une **espace** (`pog2-montsegur (2).jpg`). Dans une adresse web, une espace s'écrit `%20`. **Bonne pratique** : nommer ses fichiers sans espaces ni parenthèses, par exemple `pog2-montsegur.jpg`.
- `animation-delay` → le **décalage** de départ de chaque animation. Les trois toiles jouent la **même** animation, mais **décalées de 6 secondes** l'une par rapport à l'autre (4,56 − (−1,44) = 6 ; 10,56 − 4,56 = 6).

#### Étape 4 : le scénario de l'animation

```css
/* Fondu enchaîné */
@keyframes hero-fade {
  0%   { opacity: 0; }
  8%   { opacity: 1; }
  33%  { opacity: 1; }
  41%  { opacity: 0; }
  100% { opacity: 0; }
}
```

`@keyframes` définit les **images clés** de l'animation, comme les étapes d'un scénario. Les pourcentages représentent l'avancement dans le cycle de 18 s. Le navigateur calcule tout seul les étapes intermédiaires.

| Étape | Temps (sur 18 s) | Opacité | Ce qui se passe |
|---|---|---|---|
| `0%` | 0 s | 0 | Invisible |
| `0%` → `8%` | 0 → 1,44 s | 0 → 1 | **Apparition** en fondu |
| `8%` → `33%` | 1,44 → 6 s | 1 | **Pleinement visible** |
| `33%` → `41%` | 6 → 7,44 s | 1 → 0 | **Disparition** en fondu |
| `41%` → `100%` | 7,44 → 18 s | 0 | Invisible, attend son tour |

Chaque photo est donc visible environ un tiers du temps, et les fondus se chevauchent : pendant qu'une photo disparaît, la suivante apparaît. C'est un **fondu enchaîné**.

#### Pourquoi `-1.44s` pour la première ?

Si la première image commençait à 0 %, la page afficherait **un fond vide** pendant 1,44 s (le temps du fondu d'apparition). Un délai **négatif** fait démarrer l'animation **comme si elle avait déjà commencé** depuis 1,44 s : au chargement, la première photo est **déjà entièrement visible**. 1,44 s = 8 % de 18 s.

> 🎞️ **Analogie** : trois projecteurs de diapositives pointés sur le même écran. Chacun allume sa lampe progressivement, la garde allumée, puis l'éteint. On a décalé leurs minuteries de 6 secondes pour qu'ils prennent le relais l'un après l'autre.

**Modifier le carrousel** :

- Pour **changer une photo** : remplacer le nom du fichier dans `.hero__slide--1`, `--2` ou `--3`.
- Pour **ralentir** : passer `18s` à `24s` (8 s par image). Il faut alors recalculer les délais : un décalage de durée ÷ 3 entre les images (8 s), et décaler le tout de 8 % de la durée (1,92 s), soit `-1.92s`, `6.08s` et `14.08s`.

### 18.3 Respecter les préférences de mouvement

```css
/* Pas d'animation si l'utilisateur la désactive dans son système */
@media (prefers-reduced-motion: reduce) {
  .quick-links__item {
    transition: none;
  }
}
```

Certaines personnes (sujettes au mal des transports, aux migraines, à certains troubles vestibulaires) activent dans leur système l'option « réduire les animations ». `prefers-reduced-motion: reduce` détecte ce réglage, et on **désactive** alors les transitions des pastilles.

Le carrousel n'a pas encore cette protection : voir chapitre 21.

---

## 19. Le responsive : s'adapter à tous les écrans

### 19.1 Qu'est-ce que le responsive ?

Un site **responsive** (« adaptatif ») s'adapte à la taille de l'écran : téléphone, tablette, ordinateur.

> 💧 **Analogie** : l'eau prend la forme du verre dans lequel on la verse. Une page responsive prend la forme de l'écran qui l'affiche.

Les outils déjà vus qui rendent notre page responsive **sans effort** :

- la balise `<meta name="viewport">` (chapitre 3) ;
- `max-width: 100%` sur les images (chapitre 7) ;
- les unités relatives `rem`, `%`, `fr` (chapitre 10) ;
- `flex-wrap: wrap` (chapitre 14) ;
- `repeat(auto-fit, minmax(280px, 1fr))` (chapitre 15).

### 19.2 Mobile first

```css
/*
   Méthode « mobile first » : le style de base vise les téléphones,
   puis on l'adapte aux grands écrans dans la partie 13.
*/
```

**Mobile first** (« le mobile d'abord ») : on écrit d'abord le CSS pour le **plus petit écran**, puis on **ajoute** des règles pour les écrans plus grands.

Pourquoi ? La version mobile est la plus simple (souvent une seule colonne). Il est plus facile d'**ajouter** des colonnes que d'en **retirer**. Et les téléphones ne chargent pas de règles inutiles.

> 🏠 **Analogie** : on construit d'abord un studio fonctionnel, puis on ajoute des pièces quand on a plus de terrain.

### 19.3 Les media queries

Une **media query** applique des règles **seulement si une condition est vraie**.

```css
/* TABLETTE : à partir de 700px */
@media (min-width: 700px) {
  ...
}
```

- `@media` → « règles conditionnelles ».
- `(min-width: 700px)` → « si la fenêtre fait **au moins** 700 px de large ».
- Tout ce qui est entre les accolades ne s'applique qu'à cette condition.

Notre site a **deux paliers** (on les appelle des **points de rupture**, *breakpoints*) :

```
0 px ──────────── 700 px ──────────── 1000 px ────────────▶
   TÉLÉPHONE      │     TABLETTE      │     ORDINATEUR
   (style de base)│ (@media 700px)    │ (@media 1000px)
```

Les règles **s'additionnent** : sur un ordinateur, les styles de base, **puis** ceux de 700 px, **puis** ceux de 1000 px s'appliquent, chacun remplaçant le précédent si besoin.

### 19.4 Le palier tablette (≥ 700 px)

```css
/* TABLETTE : à partir de 700px */
@media (min-width: 700px) {
  .container {
    padding: 0 2rem;
  }

  .hero__title {
    font-size: 4rem;
  }

  /* Infos pratiques : 4 colonnes */
  .quick-links__list {
    grid-template-columns: repeat(4, 1fr);
    gap: 0.75rem;
    padding: 1rem 0;
  }

  .quick-links__item {
    font-size: 0.9rem;
  }

  /* Actualités : 2 colonnes */
  .news-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  /* Pied de page : 3 colonnes */
  .footer__inner {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

Ce qui change, règle par règle :

| Règle | Téléphone | Tablette |
|---|---|---|
| Marges latérales du `.container` | 16 px | 32 px |
| Taille du titre du hero | 2,8rem (45 px) | 4rem (64 px) |
| Infos pratiques | 2 × 2 | 4 sur une ligne |
| Actualités | 1 colonne | 2 colonnes |
| Pied de page | 1 colonne | 3 colonnes |

### 19.5 Le palier ordinateur (≥ 1000 px)

```css
/* ORDINATEUR : à partir de 1000px */
@media (min-width: 1000px) {
  .section {
    padding: 6rem 0;
  }

  /* Le menu repasse sur la même ligne que le logo */
  .main-nav {
    order: 0;
    width: auto;
  }

  .main-nav__list {
    gap: 2rem;
    overflow: visible;
  }

  .hero__title {
    font-size: 5rem;
  }

  .hero {
    min-height: 680px;
    padding: 6rem 0;
  }

  .section__title {
    font-size: 2.8rem;
  }

  .banner {
    padding: 9rem 0;
  }

  .banner__title {
    font-size: 3.6rem;
  }

  /* Blocs texte + image : 2 colonnes côte à côte */
  .split {
    grid-template-columns: 3fr 2fr;
    gap: 4rem;
  }

  .contact {
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
}
```

Ce qui change :

- **Plus d'espace** : sections (96 px en haut et en bas), hero (680 px minimum), bandeau (144 px en haut et en bas).
- **Titres plus grands** : hero 5rem (80 px), sections 2,8rem, bandeau 3,6rem.
- **Menu** : `order: 0` et `width: auto` le remettent **entre le logo et le bouton**, sur la même ligne. `overflow: visible` retire le défilement horizontal, devenu inutile.
- **Deux colonnes** : bloc UNESCO (60/40) et contact (50/50).

> 🛠️ **Pour tester** : dans le navigateur, ouvrez les outils de développement (**F12**), puis cliquez sur l'icône **téléphone/tablette** (ou **Ctrl + Maj + M**). Vous pouvez choisir un modèle de téléphone ou faire varier la largeur, et voir la page se réorganiser en direct.

### 19.6 Une media query de préférence

On a vu au chapitre 18 une autre sorte de media query, qui ne teste pas la taille de l'écran mais une **préférence de l'utilisateur** :

```css
@media (prefers-reduced-motion: reduce) { ... }
```

---

## 20. Organiser son code : la méthode BEM

### 20.1 Le problème

Sur un gros site, on finit par avoir des centaines de classes. Si on les appelle `.title`, `.text`, `.image`, on ne sait plus à quoi elles servent, et un changement à un endroit casse un autre endroit.

### 20.2 La solution BEM

**BEM** = **Bloc, Élément, Modificateur**. C'est une **convention de nommage** expliquée en haut de notre CSS :

```css
/*
   Nommage des classes (méthode BEM simplifiée) :
   - .bloc            → un composant (ex : .card)
   - .bloc__element   → une partie du composant (ex : .card__title)
   - .bloc--variante  → une variante (ex : .btn--primary)
*/
```

- **Bloc** : un composant **autonome** et réutilisable. → `.card`, `.btn`, `.hero`, `.news`
- **Élément** (deux tirets bas `__`) : une **partie** d'un bloc, qui n'a pas de sens en dehors de lui. → `.card__image`, `.card__title`, `.card__body`, `.card__text`
- **Modificateur** (deux tirets `--`) : une **variante** du bloc ou de l'élément. → `.btn--primary`, `.btn--outline`, `.btn--small`, `.section--alt`, `.news__image--logo`

> 🚗 **Analogie** : une voiture.
> - **Bloc** : `.voiture`
> - **Éléments** : `.voiture__roue`, `.voiture__portiere`, `.voiture__volant`
> - **Modificateurs** : `.voiture--rouge`, `.voiture--cabriolet`
>
> On sait tout de suite qu'une `.voiture__roue` appartient à une voiture, et qu'une `.voiture--rouge` est une voiture comme les autres, mais rouge.

### 20.3 BEM dans notre code

Exemple complet avec la carte :

```html
<article class="card">                          <!-- Bloc -->
  <img class="card__image" ...>                 <!-- Élément -->
  <div class="card__body">                      <!-- Élément -->
    <h3 class="card__title">...</h3>            <!-- Élément -->
    <p class="card__text">...</p>               <!-- Élément -->
    <a href="#" class="link-arrow">...</a>      <!-- Autre bloc réutilisable -->
  </div>
</article>
```

Et les modificateurs, qui **s'ajoutent** à la classe de base :

```html
<a href="#" class="btn btn--primary btn--small">Billetterie</a>
```

- `btn` → le style commun à tous les boutons (forme pilule, padding, gras) ;
- `btn--primary` → la variante bordeaux ;
- `btn--small` → la variante plus petite.

Les variantes **se combinent** comme des briques de Lego.

Avantages :

- **Lisibilité** : en lisant `.news__date`, on sait que c'est la date d'une actualité.
- **Pas de conflit** : `.card__title` et `.news__title` sont deux classes distinctes, on peut les modifier indépendamment.
- **Spécificité faible et régulière** : presque tous nos sélecteurs font 10 points (une classe), donc la cascade est prévisible.

### 20.4 L'organisation du fichier CSS

Notre `style.css` est rangé **du général au particulier**, avec un sommaire numéroté :

1. **Variables** → les réglages globaux.
2. **Base** → les balises HTML brutes (`body`, `h1`, `p`, `img`, `a`).
3. **Éléments réutilisables** → `.container`, `.section`, `.btn`, `.tag`, `.link-arrow`.
4. à 12. **Les zones de la page**, dans l'ordre où elles apparaissent à l'écran.
13. **Responsive** → les media queries, à la fin pour qu'elles remplacent les règles précédentes.

> 🗄️ **Analogie** : une cuisine bien rangée. Les ingrédients de base dans le placard (variables), les ustensiles communs dans le tiroir (éléments réutilisables), puis une étagère par recette (une section par zone).

---

## 21. Bonnes pratiques et points à améliorer dans notre site

### 21.1 Les bonnes pratiques déjà appliquées

| ✅ Bonne pratique | Où dans notre code |
|---|---|
| HTML et CSS séparés | `index.html` + `style.css` |
| Langue et encodage déclarés | `<html lang="fr">`, `<meta charset="UTF-8">` |
| Balise viewport | `<head>` |
| Balises sémantiques | `header`, `nav`, `main`, `section`, `article`, `footer`, `address`, `time`, `figure` |
| Un seul `<h1>`, hiérarchie de titres respectée | `h1` → `h2` → `h3` |
| Textes alternatifs descriptifs | Tous les `<img>` |
| Chargement différé des images | `loading="lazy"` |
| Liens externes sécurisés | `target="_blank" rel="noopener"` |
| Liens `tel:` et `mailto:` | Bloc contact |
| Variables CSS pour la charte | `:root` |
| Unités relatives | `rem`, `em`, `%`, `fr` |
| Mobile first + media queries | Partie 13 du CSS |
| Nommage BEM | Toutes les classes |
| Code commenté et rangé avec un sommaire | Les deux fichiers |
| Contours visibles au clavier | `:focus-visible` |
| Respect de `prefers-reduced-motion` | Pastilles des infos pratiques |
| Espaces insécables en typographie française | `&nbsp;` avant `!` et dans les nombres |

### 21.2 Points à améliorer

En relisant le code pour ce cours, j'ai relevé plusieurs points. Ce sont d'excellents cas d'étude : les comprendre, c'est progresser.

#### 1. La variable `--shadow` n'est pas déclarée

```css
.card {
  box-shadow: var(--shadow);
}
```

`var(--shadow)` est utilisée 4 fois (`.split__image img`, `.card`, `.news`, `.contact__card`), mais `--shadow` n'existe pas dans `:root`. Le navigateur ne peut pas la remplacer : la déclaration est **ignorée**, et **les cartes n'ont pas d'ombre**.

**Correction** : ajouter la variable dans `:root`, par exemple :

```css
:root {
  ...
  --shadow: 0 10px 30px -12px rgba(35, 31, 32, 0.25);
}
```

> 🔍 **Leçon** : une variable mal orthographiée ou oubliée ne provoque **aucune erreur visible**. Le style ne s'applique simplement pas. Les outils de développement l'affichent barré ou grisé.

#### 2. La règle `box-sizing: border-box` est commentée

```css
/* *,
*::before,
*::after {
  box-sizing: border-box;
} */
```

Sans elle, `.container` a `width: 100%` **plus** `padding: 0 1rem`. Sa largeur totale vaut donc 100 % + 32 px : elle est **plus large que l'écran**. Sur téléphone, cela peut faire apparaître un **défilement horizontal** indésirable.

**Correction** : retirer le `/*` et le `*/` pour réactiver la règle. C'est la règle que presque tous les sites modernes placent en tête de leur CSS.

#### 3. Les boutons ont perdu `display: inline-block`

```css
.btn {
  padding: 0.85rem 1.6rem;
  border: 2px solid transparent;
  ...
}
```

Un `<a>` est **en ligne** par défaut. Or un élément en ligne **ignore son padding vertical** pour la mise en page : le fond s'étend bien, mais il peut **chevaucher** le texte au-dessus ou en dessous. Dans le hero et l'en-tête, le parent est en `flex`, ce qui corrige le problème. Mais le bouton « Préparer ma venue » de la section Contact est dans un bloc normal.

**Correction** : ajouter `display: inline-block;` à `.btn`.

#### 4. Le lien d'évitement est stylé mais absent du HTML

Le CSS contient `.skip-link`, et le commentaire de `<main id="contenu">` en parle, mais le lien lui-même n'est pas dans la page.

**Correction** : l'ajouter juste après `<body>` :

```html
<a href="#contenu" class="skip-link">Aller au contenu</a>
```

#### 5. Le carrousel ne respecte pas `prefers-reduced-motion`

Le diaporama tourne même chez les personnes qui ont demandé à réduire les animations.

**Correction** :

```css
@media (prefers-reduced-motion: reduce) {
  .hero__slide {
    animation: none;
  }

  .hero__slide--1 {
    opacity: 1;
  }
}
```

→ seule la première photo s'affiche, fixe.

#### 6. Des commentaires périmés

```css
.hero {
  overflow: hidden;               /* masque le zoom des images */
```

Le zoom animé a été supprimé, mais le commentaire est resté. `overflow: hidden` reste utile, mais le commentaire induit en erreur.

```html
<a href="index.html" class="logo"> <!-- TODO -->
```

Un `TODO` (« à faire ») sans explication : on ne sait plus ce qu'il reste à faire.

> 📝 **Leçon** : **un commentaire faux est pire que pas de commentaire.** Quand on modifie le code, on met à jour les commentaires.

#### 7. Des couleurs écrites en dur

```css
.main-nav__list a {
  color: #e7ddcc;
}
.hero__text {
  color: #f4efe6;
}
```

Ces valeurs sont exactement `--color-stone` et `--color-stone-light`. Mieux vaut écrire `var(--color-stone)` : si la charte change, tout suit.

#### 8. Des liens « En savoir plus » répétés

Un lecteur d'écran qui liste les liens de la page entend « En savoir plus » quatre fois, sans savoir sur quoi. On peut préciser le texte (« En savoir plus sur le catharisme ») ou ajouter un texte invisible réservé aux lecteurs d'écran.

#### 9. Les liens `href="#"`

Ce sont des emplacements réservés. Avant la mise en ligne, chacun doit mener à une vraie page, sinon le visiteur clique… et rien ne se passe.

#### 10. Les noms de fichiers et le poids des images

- `pog2-montsegur (2).jpg` contient une espace et des parenthèses, ce qui oblige à écrire `%20` dans le CSS. **Règle** : des noms en minuscules, sans accents, sans espaces, avec des tirets : `pog2-montsegur.jpg`.
- Les images du carrousel sont trop petites pour la bannière (1252 à 2016 px de large), et sont donc agrandies et pixélisées. Une image de fond plein écran devrait faire au moins **2560 px de large**. On peut aussi les convertir au format **WebP**, plus léger que le JPEG à qualité égale.

### 21.3 Les réflexes à garder

1. **Indenter** son code pour voir l'imbrication.
2. **Commenter** l'intention, pas l'évidence, et tenir les commentaires à jour.
3. **Valider** son code : le validateur officiel du W3C (validator.w3.org) signale les erreurs HTML.
4. **Tester** sur plusieurs tailles d'écran (mode responsive du navigateur) et au **clavier seul** (touche Tab).
5. **Utiliser les variables** plutôt que des valeurs en dur.
6. **Choisir la balise selon le sens**, régler l'apparence en CSS.
7. **Ne jamais oublier** `alt` sur les images et `rel="noopener"` avec `target="_blank"`.

---

## 22. Exercices pour pratiquer

Faites une copie du dossier du projet avant de commencer, pour pouvoir revenir en arrière.

### Niveau 1 : modifier des valeurs

1. **Changez la couleur d'accent** : dans `:root`, remplacez `--color-accent: #840b0d;` par `#1f5f8b` (un bleu). Observez tout ce qui change : liens, boutons, sur-titres, liseré du contact. Remettez le bordeaux ensuite.
2. **Agrandissez les coins arrondis** : passez `--radius` à `24px`.
3. **Changez la flèche** des liens : remplacez `" →"` par `" ›"` dans `.link-arrow::after`.

### Niveau 2 : corriger les points du chapitre 21

4. Déclarez la variable `--shadow` et vérifiez que les cartes ont maintenant une ombre.
5. Réactivez la règle `box-sizing: border-box`.
6. Ajoutez le lien d'évitement dans le HTML, puis testez-le : rechargez la page et appuyez **une fois** sur **Tab**.
7. Ajoutez la protection `prefers-reduced-motion` au carrousel.

### Niveau 3 : ajouter du contenu

8. **Ajoutez une quatrième carte** dans « Découvrir » (copiez un `<article class="card">` complet et changez le texte). Observez comment la grille `auto-fit` la place selon la largeur de l'écran.
9. **Ajoutez une quatrième photo au carrousel** : un `<span class="hero__slide hero__slide--4">`, une règle `.hero__slide--4` avec son image, puis recalculez la durée (24 s pour 6 s par image) et les délais de chaque toile.
10. **Créez une variante de bouton** `.btn--light` : fond blanc cassé, texte anthracite, et au survol fond beige pierre. Utilisez-la pour le bouton « Préparer ma venue ».

---

## 23. Aide-mémoire

### 23.1 Balises HTML utilisées

| Balise | Rôle |
|---|---|
| `<!DOCTYPE html>` | Déclare un document HTML5 |
| `<html>` | Racine de la page |
| `<head>` | Réglages invisibles |
| `<meta>` | Métadonnée (encodage, viewport, description) |
| `<title>` | Titre de l'onglet |
| `<link>` | Relie un fichier externe (CSS, polices) |
| `<body>` | Contenu visible |
| `<header>` | En-tête (du site ou d'une section) |
| `<nav>` | Bloc de navigation |
| `<main>` | Contenu principal (un seul par page) |
| `<section>` | Partie thématique |
| `<article>` | Contenu autonome |
| `<footer>` | Pied de page |
| `<figure>` | Illustration |
| `<address>` | Coordonnées |
| `<time>` | Date ou heure |
| `<div>` | Boîte bloc neutre |
| `<span>` | Boîte en ligne neutre |
| `<h1>` à `<h3>` | Titres hiérarchisés |
| `<p>` | Paragraphe |
| `<br>` | Retour à la ligne |
| `<ul>` / `<li>` | Liste à puces / élément de liste |
| `<a>` | Lien |
| `<img>` | Image |
| `<!-- -->` | Commentaire |

### 23.2 Propriétés CSS utilisées

| Catégorie | Propriétés |
|---|---|
| **Texte** | `font-family`, `font-size`, `font-weight`, `font-style`, `line-height`, `color`, `text-align`, `text-transform`, `text-decoration`, `letter-spacing`, `white-space`, `overflow-wrap` |
| **Boîte** | `display`, `width`, `max-width`, `height`, `min-height`, `margin`, `padding`, `border`, `border-radius`, `box-sizing`, `box-shadow`, `outline`, `outline-offset`, `overflow` |
| **Fonds** | `background`, `background-color`, `background-image`, `background-size`, `background-position`, `backdrop-filter`, `opacity` |
| **Images** | `object-fit`, `aspect-ratio` |
| **Listes** | `list-style` |
| **Flexbox** | `display: flex`, `flex-direction`, `flex-wrap`, `justify-content`, `align-items`, `gap`, `flex-grow`, `order` |
| **Grid** | `display: grid`, `grid-template-columns`, `repeat()`, `minmax()`, `auto-fit`, `fr`, `gap` |
| **Position** | `position`, `inset`, `top`, `left`, `z-index`, `isolation` |
| **Mouvement** | `transition`, `transform`, `animation`, `animation-delay`, `@keyframes`, `scroll-behavior` |
| **Contenu généré** | `content` |
| **Conditions** | `@media (min-width: …)`, `@media (prefers-reduced-motion: reduce)` |
| **Variables** | `--nom: valeur;`, `var(--nom)` |

### 23.3 Sélecteurs

| Sélecteur | Vise | Exemple |
|---|---|---|
| `p` | Toutes les balises `<p>` | `p { margin: 0 0 1em; }` |
| `.classe` | Les éléments de cette classe | `.card` |
| `A, B` | A et B | `h1, h2, h3` |
| `A B` | Les B à l'intérieur de A | `.site-footer a` |
| `A + B` | Le B juste après un A | `li + li` |
| `[attr="val"]` | Les éléments avec cet attribut | `[aria-current="page"]` |
| `:root` | La racine `<html>` | `:root { --… }` |
| `*` | Tous les éléments | `* { box-sizing: … }` |
| `:hover` | Survolé | `.card:hover` |
| `:focus` / `:focus-visible` | Sélectionné (au clavier) | `a:focus-visible` |
| `:active` | En train d'être cliqué | `.quick-links__item:active` |
| `:last-child` | Dernier enfant | `p:last-child` |
| `::before` / `::after` | Boîte créée au début / à la fin | `.link-arrow::after` |

### 23.4 Glossaire

- **Attribut** : précision ajoutée dans une balise ouvrante (`href`, `class`, `alt`…).
- **Balise** : étiquette `<…>` qui délimite un élément HTML.
- **BEM** : convention de nommage Bloc__Élément--Modificateur.
- **Breakpoint** (point de rupture) : largeur d'écran à partir de laquelle la mise en page change.
- **Cascade** : mécanisme qui décide quelle règle CSS gagne en cas de conflit.
- **Héritage** : transmission de certaines propriétés du parent aux enfants.
- **Media query** : bloc de règles CSS conditionnelles.
- **Mobile first** : écrire d'abord le style pour mobile, puis l'enrichir pour les grands écrans.
- **Pseudo-classe** : état d'un élément (`:hover`, `:focus`…).
- **Pseudo-élément** : boîte générée par le CSS (`::before`, `::after`).
- **Responsive** : qui s'adapte à la taille de l'écran.
- **Sémantique** : qui décrit le sens du contenu.
- **Sélecteur** : la partie d'une règle CSS qui désigne les éléments visés.
- **Spécificité** : score de précision d'un sélecteur.
- **Variable CSS** : valeur nommée réutilisable, déclarée avec `--`.
- **Viewport** : zone visible de la page à l'écran.

---

> 🎓 **Le mot de la fin**
>
> Vous savez maintenant lire **chaque ligne** du site de Montségur. Le secret pour progresser n'est pas de tout retenir par cœur, mais de **pratiquer** : modifiez une valeur, rechargez, observez, et recommencez. Les outils de développement (clic droit → Inspecter) seront vos meilleurs alliés.
>
> Bonne construction !
