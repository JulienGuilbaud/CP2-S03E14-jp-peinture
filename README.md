# Atelier : Jean Pierre Peinture

Voici le site vitrine de Jean-Pierre, peintre de son métier.

Nous allons travailler dessus pour mieux comprendre l'intérêt des mixins. Nous en profiterons pour revoir les media-queries, flexbox et découvrir la fonction css `calc()`.

## :zero: Observations

En premier lieu, vous allez devoir explorer le code qu'on vous a laissé.

---

### :microscope: Le HTML

Il n'y a qu'un seul fichier html : `index.html`.

---

### :microscope: Le SCSS

Prenez le temps de comprendre l'architecture du dossier `scss`. Regardez bien le code de chaque fichier et donnez un role à chacun.

| fichier | rôle |
|:----------|:-------------|
| index.scss | Appelle tous les autres fichiers SCSS, c'est ce fichier central qui sera lié dans le html |
| _var.scss | Liste les variables, des valeurs qu'on pourra réutiliser |
| _reset.scss | Remise à 0 des styles pour une base uniforme |
| _global.scss | Les styles génériques, on y trouvera surtout des sélecteur d'élements (body, a, p) |
| _mixin.scss | Liste des mixins, des paquets de propriétés réutilisables |
| commponents/_button.scss | Les styles spécifiques aux boutons |
| commponents/_header.scss | Les styles spécifiques aux header |
| commponents/_card.scss | Les styles spécifiques aux cartes |
| commponents/_footer.scss | Les styles spécifiques aux footer |

---

### :construction: Installation des dépendances

Vous commencez à être habitués.
Quand un fichier package.json se trouve à la racine du projet, il faut utiliser la commande suivante :

```bash
npm install
```
---

### :microscope: Le rendu du site

Vous avez dans le dossier docs/snapshots, trois images du rendu du site : une pour différentes largeurs.

Pour connaitre les breakpoints, explorez les fichiers scss.

| snapshot | breakpoint |
|:----------|:-------------|
| jpp-big.png | à partir de 90 rem (par défaut 1440px) |
| jpp-medium.png | à partir de 50 rem (par défaut 800px) |
| jpp-small.png | tout le reste : en dessous de 50 rem |

---

### :traffic_light: Lancement du serveur de développement

```bash
npm start
```
---

## :one: Nos missions

Le site a été intégré en __mobile first__ ! Donc vous disposez de tout le SCSS et le HTML pour mobile. Il manque encore certains détails pour la largeur `medium` et la largeur `big`.

---

### :mans_shoe: Le Footer

Sur les maquettes (snapshot), on voit qu'en largeur d'écran médium les liens doivent être affichés en ligne.
Regardez comment sont implantées les media-queries dans `components/_header.scss` et essayez de faire de même dans `components/_footer.scss` pour modifier l'apparence du site.


<details><summary>Indice</summary>

Trouvez le bon endroit pour placer ce morceau de code qui permet de changer les directives CSS la largeur d'affichage est médium.

```scss
    @include mixin.medium {
        display: flex;
    }
```
</details>

---

### :balloon: L'intro et son titre

Dans un premier temps, trouvez dans quel fichier se trouve le CSS de l'introduction du site.

Ensuite, sur la maquette *big*, on peut voir que le titre et le texte prennent plus de place. En effet, leur largeur doit passer à 80%.

Trouvez un moyen de mettre cet affichage en place.

<details><summary>Indice</summary>

Ajoutez au bon endroit et dans le bon fichier ce morceau de code :

```scss
    @include mixin.big {
        width: 80%;
    }
```
</details>

---

### :nut_and_bolt: Le corps du site

On voit que la largeur totale du `<main>` change en fonction de la largeur d'affichage.

Il y a même deux variables prévues pour ces largeurs dans le fichier SCSS dédié.

Mettez en place ces deux largeurs pour l'affichage *medium* et l'affichage *big*.

<details><summary>Indice</summary>

Ces variables sont définies dans le fichier `_var.scss`.

```scss
    $container-width-medium: 40rem;
    $container-width-big: 80rem;
```
</details>

---

### :dango: Les vignettes de réalisation

#### a. La disposition des vignettes entre elles

Les vignettes prennent actuellement toute la largeur de leur conteneur.

Il faut qu'en affichage *medium* elles ne prennent que la moitié de la largeur du conteneur.

Il faut qu'en affichage *big* elles ne prennent que le quart de la largeur du conteneur.

Si on place la directive `width:50%`, il n'y aura pas la place pour les espacer entre elles. Pour tenir compte de cet espacement, on peut effectuer un calcul avec la fonction `calc()`.

Par exemple : `width: calc(50% - 1rem)`.

Ici, `1rem` correspond à la largeur de l'espacement entre les vignettes à prendre en compte.

La largeur de l'espacement est sauvegardé dans la variable `$gutter`.

Essayez de mettre en place la modification de la largeur des vignettes en fonction de la largeur de l'affichage.

<details><summary>Indice</summary>
Vous pouvez le faire directement sur la classe `.card` dans `_global.scss`.
</details>

#### b. La disposition des éléments à l'intérieur des vignettes

La disposition des éléments à l'intérieur de la vignette n'est pas en colonne.
A vous de trouvez comment les positionner comme sur les maquettes quand on passe à l'affichage *medium*.

<details><summary>Indice</summary>
Vous pouvez le faire directement sur la classe dans `components/_card.scss`.
</details>

---

### :straight_ruler: Un mixin pour les souligner tous

Cela n'apparait pas sur les maquettes, mais les liens du footer et "en savoir plus" doivent faire apparaitre un soulignement quand on est les survole.

Le soulignement doit être éloigné des caractères de 0.4em.

- Mettez en place ce soulignement pour ces deux types de liens

On s'aperçoit que c'est toujours le même code. Pourquoi ne pas mettre ce code CSS dans une mixin ? Allez-y et appelez la quand nécessaire !

---

## :two: Bravo à vous ! :confetti_ball:
