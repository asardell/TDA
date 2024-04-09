# Dplyr, Ggplot2 et Esquisse

## Objectifs
Voici les objectifs de ce chapitre :
- [ ] Importer un fichier excel
- [ ] Notion de factor
- [ ] Opération d'agrégation sur une dataframe
- [ ] Découvrir des packages utiles (dplyr, ggplot2 et esquisse)

- [Dplyr, Ggplot2 et Esquisse](#dplyr-ggplot2-et-esquisse)
  - [Objectifs](#objectifs)
  - [Exercice 1 - Importer les données](#exercice-1---importer-les-données)
    - [Mémo](#mémo)
    - [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r)
  - [Exercice 2 - Utiliser Dplyr pour trier et filtrer](#exercice-2---utiliser-dplyr-pour-trier-et-filtrer)
    - [Mémo](#mémo-1)
    - [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-1)
  - [Exercice 3 - Utiliser Dplyr et le pipe %\>% pour agréger](#exercice-3---utiliser-dplyr-et-le-pipe--pour-agréger)
    - [Mémo](#mémo-2)
    - [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-2)
  - [Exercice 4 - Comprendre ggplot2 avec esquisse](#exercice-4---comprendre-ggplot2-avec-esquisse)
  - [Liens utiles](#liens-utiles)


## Exercice 1 - Importer les données

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|--------------------|-------------|----------------------|---------|
| `read_excel()` | Lit un fichier Excel dans R. | `path` : le chemin vers le fichier Excel, `sheet` : le nom ou l'index de la feuille à lire (par défaut la première feuille) | `readxl::read_excel(path = "/chemin/vers/votre/fichier.xlsx", sheet = "Nom_de_la_feuille")` |
| `as.factor()` | Convertit un vecteur en facteur. | `x` : le vecteur à convertir | `as.factor(x = c("A", "B", "A", "C"))` |

### Exercice sur les Fonctions en R

1. Importez le jeu de données *pokemon.xlsx* à l’aide du package `readxl`.

<details>
<summary>Correction</summary>

```r
library(readxl)
pokemon <- read_excel(path = "pokemon.xlsx",sheet = "pokemon")
```
</details>

2. Combien de lignes, colonnes sont présentes dans ce dataset (utilisez les fonctions adaptées) ?

<details>
<summary>Correction</summary>

```r
dim(pokemon)
ncol(pokemon)
nrow(pokemon)
```
</details>

3. Affichez un résumé des données avec la fonction adaptée. On remarque peut-être que les variables qualitatives n'ont pas de statistique.

<details>
<summary>Correction</summary>

```r
summary(pokemon)
```
</details>

4. On souhaite analyser les variables `generation`, `is_legendary`, et `type` en tant que variables qualitatives. Modifier le type de ces variables pour les transformer en type `factor`.

<details>
<summary>Correction</summary>

```r
pokemon$is_legendary <-as.factor(pokemon$is_legendary)
pokemon$generation <-as.factor(pokemon$generation)
pokemon$type <-as.factor(pokemon$type)
```
</details>

5. Affichez un nouveau résumé des données avec la fonction adaptée.
<details>
<summary>Correction</summary>

```r
summary(pokemon)
```
</details>

## Exercice 2 - Utiliser Dplyr pour trier et filtrer

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|--------------------|-------------|----------------------|---------|
| `select()` | Sélectionne des colonnes d'un jeu de données. | `data` : le jeu de données, `...` : les colonnes à sélectionner | `dplyr::select(data = dataframe, col1, col2)` |
| `slice()` | Sélectionne des lignes spécifiques d'un jeu de données. | `data` : le jeu de données, `rows` : les rangs à sélectionner | `dplyr::slice(data = dataframe, rows = c(1, 3, 5))` |
| `filter()` | Filtre les lignes d'un jeu de données en fonction de conditions spécifiques. | `data` : le jeu de données, `...` : les conditions de filtrage | `dplyr::filter(data = dataframe, col1 > 10)` |
| `arrange()` | Trie les lignes d'un jeu de données en fonction de variables spécifiques. | `data` : le jeu de données, `...` : les variables de tri | `dplyr::arrange(data = dataframe, col1)` |
| `is.na()` | Vérifie si les valeurs sont manquantes (NA). | `x` : vecteur ou objet à tester | `is.na(x = vecteur)` |
| `!is.na()` | Vérifie si les valeurs ne sont pas manquantes (non-NA). | `x` : vecteur ou objet à tester | `!is.na(x = vecteur)` |

### Exercice sur les Fonctions en R

1. Installer le package `dplyr` s'il n'est pas encore installé.
<details>
<summary>Correction</summary>

```r
install.packages("dplyr")
library(dplyr)
```
</details>

2. Sélectionnez la colonne `nom` et `is_legendary`.
<details>
<summary>Correction</summary>

```r
resultat = select(pokemon, nom, is_legendary)
View(resultat)
```
</details>

3. Sélectionnez les 10 premières lignes et toutes les colonnes.
<details>
<summary>Correction</summary>

```r
resultat = slice(pokemon, 1:10)
View(resultat)
```
</details>

4. Sélectionnez les 50 premières lignes et les deux premières colonnes.
<details>
<summary>Correction</summary>

```r
resultat <- select(pokemon, c(1,2))
resultat <- slice(resultat, 1:50)
View(resultat)
```
</details>

5. Sélectionnez toutes les colonnes sauf la dernière.
<details>
<summary>Correction</summary>

```r
resultat <- select(pokemon, -speed)
View(resultat)
```
</details>

6. Sélectionnez les colonnes 2,9,10,8 dans cet ordre.
<details>
<summary>Correction</summary>

```r
resultat <- select(pokemon, 2,9,10,8)
View(resultat)
```
</details>

7. Sélectionnez les lignes 20 à 30 et 80 à 100
<details>
<summary>Correction</summary>

```r
resultat <- slice(pokemon, 20:30,80:100)
View(resultat)
```
</details>

8. Triez le dataset par ordre alphabétique et afficher la première ligne.
<details>
<summary>Correction</summary>

```r
resultat <- arrange(pokemon, nom)
resultat <- slice(resultat, 1)
View(resultat)
```
</details>

9. Triez le dataset par `weight_kg` en ordre décroissant, et afficher la première ligne
<details>
<summary>Correction</summary>

```r
resultat <- arrange(pokemon, desc(weight_kg))
resultat <- slice(resultat, 1)
View(resultat)
```
</details>

10. Triez le dataset par `attack` en ordre décroissant puis par `speed` en ordre croissant, et afficher les 10 premières lignes.
<details>
<summary>Correction</summary>

```r
resultat <- arrange(pokemon, desc(attack), speed)
resultat <- slice(resultat, 10)
View(resultat)
```
</details>

11. Filtrez sur les pokemons qui ont 150 ou plus d’`attack` puis trier le résultat par ordre décroissant d’`attack`.
<details>
<summary>Correction</summary>

```r
resultat <- arrange(  filter(pokemon, attack > 150)  , desc(attack) )
View(resultat)
```
</details>

12. Filtrez sur les pokemons de `type` dragon,ghost,psychic et dark

<details>
<summary>Correction</summary>

```r
resultat <-filter(pokemon, type %in% c("dragon","psychic","dark","ghost"))
View(resultat)
```
</details>

13. Filtrez sur les pokemons de `type` fire avec plus de 100 d’attack, puis trier le résultat par ordre décroissant d’`attack`.
<details>
<summary>Correction</summary>

```r
resultat <- arrange(  filter(pokemon, attack > 100 & type == "fire"), desc(attack) )
View(resultat)
```
</details>

14. Filtrez sur les pokemons qui ont entre 100 et 150 de `speed`. Les trier par `speed` décroissant.
<details>
<summary>Correction</summary>

```r
resultat <- arrange ( filter(pokemon,  speed >= 100 & speed <= 150)   , desc(speed))
View(resultat)
```
</details>

15. Filtrez sur les pokémons qui ont des valeurs manquantes sur la variable `height_m`.
<details>
<summary>Correction</summary>

```r
resultat <- filter(pokemon, is.na(height_m))
View(resultat)
```
</details>

16. Filtrez sur les pokemons qui ont des valeurs renseignées à la fois pour la variable `weight_kg` et la variable `height`.
<details>
<summary>Correction</summary>

```r
resultat <- filter(pokemon, !is.na(height_m)   & !is.na(weight_kg) )
View(resultat)
```
</details>

## Exercice 3 - Utiliser Dplyr et le pipe %>% pour agréger

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|--------------------|-------------|----------------------|---------|
| `group_by()` | Crée des groupes de données en fonction de variables spécifiques. | `data` : le jeu de données, `...` : les variables de groupe | `dplyr::group_by(data = dataframe, col1)` |
| `summarise()` | Résume les données groupées en effectuant des calculs. | `data` : le jeu de données, `...` : les calculs à effectuer | `dplyr::summarise(data = dataframe, mean_col1 = mean(col1))` |

:warning: voici un raccourci pour écrire le pipe `%>%` : `CTRL` + `SHIFT` + `M`.

### Exercice sur les Fonctions en R

1. Calculez l’attack moyenne en fonction de la variable `type`, puis filtrez sur les 3 `types` avec les moyennes les plus élevées.
<details>
<summary>Correction</summary>

```r
pokemon %>%  
    group_by(type) %>% #il faut que le symbole %>%  soit à la suite de la commande qui le précède
    summarise(moy_attack = mean(attack)) %>% 
    arrange(desc(moy_attack)) %>% 
    slice(1:3) %>%
    View()
```
</details>

2. Calculez le nombre de pokemon par `type` , puis triez par ordre décroissant ces effectifs.
<details>
<summary>Correction</summary>

```r
pokemon %>%  
    group_by(type) %>% #il faut que le symbole %>%  soit à la suite de la commande qui le précède
    summarise(effectif = n()) %>% 
    arrange(desc(effectif))  %>% 
    View()
```
</details>

3. Calculez la médiane de `weight_kg` par `type`.
<details>
<summary>Correction</summary>

```r
pokemon %>%  
    group_by(type) %>% #il faut que le symbole %>%  soit à la suite de la commande qui le précède
    summarise(median_weight = median(weight_kg, na.rm = TRUE)) %>% 
    View()
```
</details>

4. Calculez le nombre de pokemon par `type` et `generation`
<details>
<summary>Correction</summary>

```r
pokemon %>%  
    group_by(type, generation) %>% #il faut que le symbole %>%  soit à la suite de la commande qui le précède
    summarise(effectif = n()) %>% 
    View()
```
</details>

5. Calculez la moyenne de chaque critère (`weight_kg`, `height_m`, `attack`, `defense` et `speed`) en fonction de chaque `type`.

<details>
<summary>Correction</summary>

```r
pokemon %>%  
    group_by(type) %>% #il faut que le symbole %>%  soit à la suite de la commande qui le précède
    summarise(moy_weight_kg = mean(weight_kg, na.rm = TRUE),
                moy_height_m = mean(height_m, na.rm = TRUE),
                moy_attack = mean(attack, na.rm = TRUE),
                moy_defense = mean(defense, na.rm = TRUE),
                moy_speed = mean(speed, na.rm = TRUE)) %>% 
    View()
```
</details>


## Exercice 4 - Comprendre ggplot2 avec esquisse

1. Installer le package `ggplot2` puis `esquisse` s'ils ne sont pas encore installés.
<details>
<summary>Correction</summary>

```r
# Liste des packages à installer
packages <- c("ggplot2", "esquisse")

# Vérifier et installer chaque package
for (pkg in packages) {
  if (!requireNamespace(pkg, quietly = TRUE)) {
    install.packages(pkg)
  }
}
```
</details>

2. Lancer la fonction `esquisser()` puis s'amuser un peu.
<details>
<summary>Correction</summary>

```r
library(ggplot2)
library(esquisse)
esquisser()
```
</details>

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)
- [Dplyr en détail](https://juba.github.io/tidyverse/10-dplyr.html)
- [Ggplot en détail](https://juba.github.io/tidyverse/08-ggplot2.html)
- [Esquisse en détail](https://juba.github.io/tidyverse/08-ggplot2.html#ladd-in-esquisse)



