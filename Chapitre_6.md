# Analyses multidimensionnelles (ACP, Clustering, Régression)

## Objectifs
Voici les objectifs de ce TD :
- [ ] Construire et analyser une ACP
- [ ] Construire et analyser un clustering
- [ ] Modéliser une régression linéaire pour prédire

1. [Analyses multidimensionnelles (ACP, Clustering, Régression)](#analyses-multidimensionnelles-acp-clustering-régression)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Importer les données](#exercice-1---importer-les-données)
   3. [Exercice 2 - L'ACP](#exercice-2---lacp)
   4. [Exercice 3 - Le Clustering](#exercice-3---le-clustering)
   5. [Exercice 4 - Régression linénaire](#exercice-4---régression-linénaire)
   6. [Liens utiles](#liens-utiles)


## Exercice 1 - Importer les données

1. Importez le jeu de données *fromage.txt* à l’aide de l'assistant RStudio.
<details>
<summary>Correction</summary>

```r
fromage <- read.delim("fromage.txt")
View(fromage)
```
</details>


2. Faire une résumé des données.
<details>
<summary>Correction</summary>

```r
summary(fromage)
```
</details>

3. Calculer la matrice de corrélation sur les variables quantitatives.
<details>
<summary>Correction</summary>

```r
ls_quantiColonne <- colnames(fromage)[-1]
cor(fromage[    , ls_quantiColonne   ])
```
</details>

## Exercice 2 - L'ACP

:warning: Plus d'infos dans les liens utiles !

1. Installer le package `factoextra` puis `FactoMineR` s'ils ne sont pas encore installés.
<details>
<summary>Correction</summary>

```r
# Liste des packages à installer
packages <- c("factoextra", "FactoMineR")

# Vérifier et installer chaque package
for (pkg in packages) {
  if (!requireNamespace(pkg, quietly = TRUE)) {
    install.packages(pkg)
  }
}

library(factoextra)
library(FactoMineR)
```
</details>

2. Calculer l'ACP avec la fonction `PCA()`.
<details>
<summary>Correction</summary>

```r
res.pca <- PCA(fromage[  , ls_quantiColonne  ], scale.unit = TRUE, ncp = 9, graph = TRUE)
```
</details>

3. Afficher les différents éléments calculés disponibles dans l'objet `res.pca`.
<details>
<summary>Correction</summary>

```r
attributes(res.pca)
```
</details>

4. Reproduire les tutoriels en lien utiles mais avec les données sur les fromages.

<details>
<summary>Correction</summary>

```r
fromage = read.csv("fromage.txt", sep = "", row.names = 1)

res.pca <- PCA(fromage, 
               scale.unit = TRUE, ncp = 9, graph = TRUE)

View(res.pca$ind$coord)
fviz_eig(res.pca, addlabels = TRUE, ylim = c(0, 100))

fviz_pca_ind(res.pca, col.ind = "cos2", 
             gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"),
             repel = TRUE )

fviz_pca_var(res.pca, col.var = "contrib",
             gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07") )

cor(fromage$magnesium, res.pca$ind$coord[ , 1])
```
</details>



## Exercice 3 - Le Clustering

:warning: utiliser le tutoriel en lien utile uniquement sur la méthode des `kmeans` et `cah` pour analyser si les deux méthodes donnent les mêmes résultats

<details>
<summary>Correction</summary>

```r
#centrage réduction des données
fromage.cr <- scale(fromage,center=T,scale=T)

#matrice des distances entre individus
d.fromage <- dist(fromage.cr)

#utilisant le carré de la distance
cah.ward <- hclust(d.fromage,method="ward.D2")

#affichage dendrogramme
plot(cah.ward) 

#dendrogramme avec matérialisation des groupes
rect.hclust(cah.ward,k=4)

#découpage en 4 groupes
groupes.cah <- cutree(cah.ward,k=4)

#j'ajoute une colonne dans le dataframe
fromage$cah = groupes.cah
```
</details>


## Exercice 4 - Régression linénaire

1. Construire un modèle avec la fonction `lm()` pour prédire les `calories` en fonction des `lipides`.
<details>
<summary>Correction</summary>

```r
model_simple <- lm(calories ~ lipides, data = fromage)
```
</details>

2. Analyser les coefficients de la régression
<details>
<summary>Correction</summary>

```r
attributes(model_simple)
model_simple$coefficients
```
</details>

3. Prédire sur les mêmes données pour tester les performances du modèle en utilisant la fonction `predict()`
<details>
<summary>Correction</summary>

```r
pred <- predict(object = model_simple, newdata = fromage)
```
</details>

4. Afficher un nuage de point entre les valeurs observées et prédites.
<details>
<summary>Correction</summary>

```r
plot(x = fromage$calories, y = pred)
```
</details>

5. Calculer deux métriques de performance, le `RMSE` et la coefficient de corrélation entre les valeurs observées et prédites.
<details>
<summary>Correction</summary>

```r
SE <- (fromage$calories - pred)^2
MSE <- mean(SE)
RMSE <- sqrt(MSE)
RMSE
cor(x = fromage$calories, y = pred)
```
</details>

6. Même questions que les précédentes mais avec une régression linéaire multiple pour prédire les calories en fonction de toutes les autres variables quantitatives.
<details>
<summary>Correction</summary>

```r
model_simple <- lm(calories ~ ., data = fromage)
attributes(model_simple)
model_simple$coefficients
pred <- predict(object = model_simple, newdata = fromage)

plot(x = fromage$calories, y = pred)
SE <- (fromage$calories - pred)^2
MSE <- mean(SE)
RMSE <- sqrt(MSE)
cor(x = fromage$calories, y = pred)
```
</details>


## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)
- [ACP en détail](http://www.sthda.com/english/articles/31-principal-component-methods-in-r-practical-guide/112-pca-principal-component-analysis-essentials/)
- [Méthodes des réductions de dimensions avec R](https://www.r-bloggers.com/2017/02/factoextra-r-package-easy-multivariate-data-analyses-and-elegant-visualization/)
- [CAH express avec Ricco](https://eric.univ-lyon2.fr/ricco/cours/didacticiels/R/cah_kmeans_avec_r.pdf)




