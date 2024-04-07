# Gestion des dates et chaîne de caractères

## Objectifs
Voici les objectifs de ce TD :
- [ ] Comprendre les formats date et time
- [ ] Comprendre comment manipuler les chaînes de caractères

1. [Gestion des dates et chaîne de caractères](#gestion-des-dates-et-chaîne-de-caractères)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Les formats date](#exercice-1---les-formats-date)
   3. [Exercice 2 - Parcourir le lien utile sur les chaînes de caratctères](#exercice-2---parcourir-le-lien-utile-sur-les-chaînes-de-caratctères)
   4. [Liens utiles](#liens-utiles)


## Exercice 1 - Les formats date

1. Importer le jeu de donnnées *timestampGame.txt*
<details>
<summary>Correction</summary>

```r
df = read.csv("timestampGame.txt",sep=";", header = TRUE)
```
</details>

2. A partir des liens utiles, convertisser les colonnes au format Date ou Timestamp.

<details>
<summary>Correction</summary>

```r
# Convertir les colonnes au format date
data$V1 <- as.Date(data$V1, format = "%Y-%m-%d")
data$V2 <- as.Date(data$V2, format = "%d-%m-%Y")
data$V3 <- as.Date(data$V3, format = "%m/%d/%Y")
data$V4 <- as.Date(paste("01", data$V4), format = "%d %B %Y")

# Convertir les colonnes au format POSIXct
data$V5 <- as.POSIXct(as.numeric(data$V5), origin = "1970-01-01", tz = "UTC")
data$V6 <- as.POSIXct(data$V6, format = "%Y-%m-%d %H:%M:%S", tz = "UTC")
data$V7 <- as.POSIXct(as.numeric(data$V7), origin = "1970-01-01", tz = "UTC")
data$V8 <- as.POSIXct(data$V8, format = "%A, %B %d, %Y %H:%M:%S", tz = "UTC")
```
</details>

## Exercice 2 - Parcourir le lien utile sur les chaînes de caratctères

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)
- [Focus sur les dates](https://asardell.github.io/programmation-r/chaines.html#manipulation-des-dates)
- [Les chaînes de caratctères](https://asardell.github.io/programmation-r/chaines.html#manipulation-des-cha%C3%AEnes-de-caract%C3%A8res)



