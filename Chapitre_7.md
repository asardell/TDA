# Algorithmique

## Objectifs
Voici les objectifs de ce TD :
- [ ] Créer une fonction
- [ ] Créer une structure conditionelle
- [ ] Créer des boucles

1. [Algorithmique](#algorithmique)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Créer des fonctions et structures conditionnelles](#exercice-1---créer-des-fonctions-et-structures-conditionnelles)
   3. [Exercice 2 - Créer des boucles](#exercice-2---créer-des-boucles)
   4. [Liens utiles](#liens-utiles)


## Exercice 1 - Créer des fonctions et structures conditionnelles

1. Créer une fonction qui calcule l'IMC d'une personne selon sa taille et son poids
<details>
<summary>Correction</summary>

```r
imc <- function(taille,poids) {
   calcul <- poids / (taille^2)
   return (calcul) }
```
</details>

2. Créer une fonction qui prend en entrée en vecteur, s'il est numeric la fonction retourne un boxplot, sinon un barplot. La fonction exporte également le graphique au format png avec la fonction `dev.print()`
<details>
<summary>Correction</summary>

```r
create_plot <- function(x, titre) {
  if (is.numeric(x) ) {
    boxplot(x, main = titre)
    dev.print(device = png,
              file = paste0(titre,".png"),
              width = 600)
  } else {
    barplot(table(x), main = titre)
    dev.print(device = png,
              file = paste0(titre,".png"),
              width = 600)
    } 
}
```
</details>

## Exercice 2 - Créer des boucles

1. Construire une boucle `for` qui execute la fonction précédente sur chaque colonne d'un dataset
<details>
<summary>Correction</summary>

```r
for (colonne in colnames(iris)) {
   create_plot(x = iris[, colonne],
               titre = colonne)
}
```
</details>

2. Même question mais avec une boucle `while`.
<details>
<summary>Correction</summary>

```r
indice_colonne = 1
while (indice_colonne <= ncol(iris)) {
   iris_colonne_name = colnames(iris)[indice_colonne]
   create_plot(x = iris[, iris_colonne_name],
               titre = iris_colonne_name)
   indice_colonne = indice_colonne + 1
}
```
</details>

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)
- [Algorithmique](https://asardell.github.io/programmation-r/algo.html#construire-une-fonction)



