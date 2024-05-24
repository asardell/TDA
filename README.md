# IUT_SD1

Ce document `README.md` est présent dans tous les repositories GitHub. Il permet de présenter le contenu du référentiel Git.
Ce documet est écrit dans le cadre du module de programmation statistique sous R.

## Objectifs globaux

Voici les objectifs de ce module :
- [x] Comprendre les bases du langage
- [x] Manipuler des vecteurs
- [x] Manipuler des dataframes
- [x] Calculer des statistiques
- [x] Construire des graphiques
- [x] Utiliser des structures algorithmiques
- [x] Tester des méthodes d'analyses multidimensionnelles

## Planning

1. Chapitre 1 : Les bases de R et les vecteurs
2. Chapitre 2 : Les bases des dataframes
3. Chapitre 3 : Importer et manipulation de dataframe
4. Chapitre 4 : Rappel et cas pratique (FACULTATIF)
5. Chapitre 5 : Création et personnalisation de graphiques élémentaires
5. Chapitre 6 : Dplyr, Ggplot2 et Esquisse
6. Chapitre 7 : Analyses multidimensionnelles (ACP, Clustering, Régression)
7. Chapitre 8 : Algorithmique
8. Chapitre 9 : Gestion des dates et chaîne de caractères

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)

## Tableau Récap

| Nom de la commande | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `$` | Accéder à une colonne d'un dataframe | | `df$colonneA` |
| `[ , ]` | Accéder à certaines lignes et/ou colonnes d'un datarame. | | `dfExtraction <- df[ c(5,6), c("colonneB", "colonneD")]` |
| `[ ]` | Accéder aux éléments d'un vecteur. | | `vecteur1[4]` |
| `:` | Génère un séquence avec un pas de 1. | | `sequence <- 8:15` |
| `[-1]` | Accèder à tous les éléments sauf ceux précisés. | | `vecteur1[-4]` |
| `[ , ]` | Indexe un dataframe au niveau des lignes et des colonnes. | `row_index` : index ou condition pour sélectionner les lignes, `col_index` : index ou noms de colonnes pour sélectionner les colonnes. | `donnees_subset <- donnees[1:10, c("colonne1", "colonne2")]` |
| `[ - , ]` | Indexation inverse, exclut les lignes ou colonnes spécifiées. | `row_index` : index ou condition pour exclure les lignes, `col_index` : index ou noms de colonnes pour exclure les colonnes. | `donnees_sans_colonne3 <- donnees[, -3]` |


| Nom de la fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `c()` | Concatène des vecteurs ou des valeurs pour créer un nouveau vecteur. |  | `nouveaux_vecteur <- c(vecteur1, vecteur2)` |
| `rm()` | Supprime des objets (variables ou fonctions) de l'environnement. | `list = ls()` supprime tous les objets | `rm(objet1, objet2)` |
| `print()` | Affiche dans la console. | | `print(objet1)` |
| `seq()` | Génère une séquence de nombres. | `from`, `to`, `by` spécifiant le début, la fin et l'incrément. | `sequence <- seq(1, 10, by = 2)` |
| `rep()` | Répète les éléments d'un vecteur plusieurs fois. | `times` spécifiant le nombre de répétitions. | `replication <- rep(5, times = 5)` |
| `length()` | Retourne la longueur d'un vecteur. |  | `longueur <- length(vecteur)` |
| `class()` | Retourne le type de classe d'un objet. |  | `type_classe <- class(objet)` |
| `sum()` | Calcule la somme des éléments d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `somme <- sum(vecteur)` |
| `mean()` | Calcule la moyenne des éléments d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `moyenne <- mean(vecteur)` |
| `median()` | Calcule la médiane d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `mediane <- median(vecteur)` |
| `min()` | Retourne la valeur minimale d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `minimum <- min(vecteur)` |
| `max()` | Retourne la valeur maximale d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `maximum <- max(vecteur)` |
| `sd()` | Calcule l'écart type d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `ecart_type <- sd(vecteur)` |
| `var()` | Calcule la variance d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `variance <- var(vecteur)` |
| `quantile()` | Calcule les quantiles d'un vecteur. | `x` : le vecteur pour lequel calculer les quantiles. `probs` : les quantiles à calculer (par exemple, c(0.25, 0.5, 0.75)). `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `quantiles <- quantile(vecteur, probs = c(0.25, 0.5, 0.75))` |
| `sort()` | Trie les éléments d'un vecteur. | `x` : le vecteur à trier. `decreasing` : un booléen indiquant si le tri doit être effectué par ordre décroissant (par défaut, `FALSE`). | `vecteur_tri <- sort(vecteur)` |
| `unique()` | Retourne les valeurs uniques d'un vecteur. |  | `valeurs_uniques <- unique(vecteur)` |
| `round()` | Arrondit les nombres d'un vecteur à un nombre spécifié de décimales. | `x` : le vecteur à arrondir. `digits` : nombre de décimales (par défaut 0). | `arrondi <- round(3.14159, digits = 2)` |
| `abs()` | Calcule la valeur absolue des éléments d'un vecteur. | | `valeurs_absolues <- abs(vecteur)` |
| `table()` | Construit une table de fréquences pour un vecteur ou une combinaison de vecteurs. | `x` : vecteur ou combinaison de vecteurs pour lesquels construire la table. | `table_frequences <- table(vecteur)` |
| `prop.table()` | Convertit les fréquences d'une table en proportions. | `x` : la table de fréquences à convertir. `margin` : indique les marges à utiliser lors du calcul des proportions (par défaut, `NULL` signifie utiliser toutes les marges). | `proportions <- prop.table(table_frequences)` |
| `rnorm()` | Génère des échantillons aléatoires suivant une distribution normale. | `n` : nombre d'échantillons à générer. `mean` : moyenne de la distribution. `sd` : écart-type de la distribution. | `echantillon_norm <- rnorm(100, mean = 10, sd = 2)` |
| `runif()` | Génère des échantillons aléatoires suivant une distribution uniforme. | `n` : nombre d'échantillons à générer. `min` : valeur minimale de la distribution. `max` : valeur maximale de la distribution. | `echantillon_unif <- runif(50, min = 0, max = 1)` |
| `sample()` | Sélectionne un échantillon aléatoire à partir d'un vecteur. | `x` : vecteur à partir duquel échantillonner. `size` : taille de l'échantillon. `replace` : avec ou sans remise.| `echantillon_aleatoire <- sample(vecteur, size = 3, replace = TRUE)` |
| `hist()` | Crée un histogramme à partir d'un vecteur de données. | `x` : le vecteur de données à utiliser. `breaks` : le nombre de bâtons (barres) dans l'histogramme. | `histogramme <- hist(data_vector, breaks = 10)` |
| `boxplot()` | Crée une boîte à moustaches à partir d'un ou plusieurs vecteurs de données. | `x` : un ou plusieurs vecteurs de données à utiliser. | `boite_moustaches <- boxplot(data_vector1, data_vector2)` |
| `data()` | Retourne la liste des noms des jeux de données chargés par défaut. |  | `data()` |
| `ncol()` | Retourne le nombre de colonnes dans un objet (par exemple, un dataframe ou une matrice). |  | `nombre_colonnes <- ncol(objet)` |
| `nrow()` | Retourne le nombre de lignes dans un objet (par exemple, un dataframe ou une matrice). |  | `nombre_lignes <- nrow(objet)` |
| `dim()` | Retourne les dimensions (nombre de lignes et de colonnes) d'un objet (par exemple, un dataframe ou une matrice). |  | `dimensions <- dim(objet)` |
| `colnames()` | Retourne ou définie les noms des colonnes dans un dataframe ou une matrice. | Aucun ou nouveaux noms de colonnes | `noms_colonnes <- colnames(dataframe)` ou `colnames(dataframe) <- c("Nom1", "Nom2", ...)` |
| `summary()` | Produit un résumé statistique des données dans un objet (par exemple, un vecteur, un dataframe, etc.). |  | `res <- summary(objet)` |
| `View()` | Ouvre une visionneuse de données pour explorer un dataframe ou une matrice dans une fenêtre séparée. | Aucun | `View(dataframe)` |
| `head()` | Affiche les premières lignes d'un dataframe ou d'une matrice. | `n` : nombre de lignes à afficher (par défaut 6) | `premieres_lignes <- head(dataframe, n = 10)` |
| `read.csv()` | Lit un fichier CSV et retourne un dataframe. | `file` : le chemin ou l'URL du fichier CSV à lire, `header` : spécifie si la première ligne contient les noms des variables (par défaut TRUE), `dec` : le caractère utilisé pour indiquer le point décimal (par défaut "."), `sep` : le séparateur de champ (par défaut ","). | `donnees <- read.csv("fichier.csv", header = TRUE, dec = ",", sep = ";")` |
| `subset()` | Retourne un sous-ensemble d'un objet (par exemple, un dataframe) en fonction de certaines conditions. | `x` : l'objet à sous-ensemble, `subset` : la condition de sous-ensemble. | `sous_ensemble <- subset(dataframe, condition)` |
| `write.table()` | Écrit un objet (par exemple, un dataframe) dans un fichier texte ou CSV. | `x` : l'objet à écrire, `file` : le nom du fichier de sortie, `sep` : le séparateur de champ (par défaut " "), `row.names` : spécifie si les noms de lignes doivent être inclus (par défaut TRUE). | `write.table(dataframe, file = "output.csv", sep = ",", row.names = FALSE)` |
| `rbind()` | Ajoute des lignes à un dataframe existant en les liant par les colonnes. | `nouveau_dataframe <- rbind(dataframe1, dataframe2)` |
| `getwd()` | Retourne le répertoire de travail actuel. | | `current_dir <- getwd()` |
| `setwd()` | Change le répertoire de travail actuel. | `dir` : le chemin du nouveau répertoire de travail | `setwd("/chemin/vers/le/nouveau/repertoire")` |
| `cor()` | Calcule la corrélation entre deux vecteurs. | `x` : le premier vecteur, `y` : le deuxième vecteur, `method` : la méthode de calcul de la corrélation (par défaut "pearson"). | `correlation <- cor(x = vecteur1, y = vecteur2, method = "spearman")` |
| `plot()` | Trace un nuage de points entre deux vecteurs. | `x` : le premier vecteur, `y` : le deuxième vecteur, `xlab` : étiquette de l'axe des abscisses, `ylab` : étiquette de l'axe des ordonnées, `main` : titre du graphique. | `plot(vecteur1, vecteur2, xlab = "Variable X", ylab = "Variable Y", main = "Nuage de points")` |
| `cov()` | Calcule la covariance entre deux vecteurs. | `x` : le premier vecteur, `y` : le deuxième vecteur. | `covariance <- cov(x = vecteur1, y = vecteur2)` |
| `install.packages()` | Installe un package R depuis un dépôt CRAN ou local. | `pkgs` : le nom du package à installer, `repos` : l'URL du dépôt, `dependencies` : spécifie si les dépendances doivent également être installées (par défaut TRUE). | `install.packages("nom_du_package")` |
| `library()` | Charge un package R déjà installé en mémoire pour être utilisé dans la session R courante. | `package` : le nom du package à charger. | `library(nom_du_package)` |
| `order()` | Trie les éléments d'un vecteur ou un dataframe et retourne les rangs dans l'ordre croissant ou décroissant. | `x` : le ou les vecteurs à trier, `decreasing` : spécifie si le tri doit être effectué dans l'ordre décroissant (par défaut FALSE). | `indices_tri <- order(vecteur, decreasing = FALSE)` |
| `read_excel()` | Lit un fichier Excel dans R. | `path` : le chemin vers le fichier Excel, `sheet` : le nom ou l'index de la feuille à lire (par défaut la première feuille) | `readxl::read_excel(path = "/chemin/vers/votre/fichier.xlsx", sheet = "Nom_de_la_feuille")` |
| `as.factor()` | Convertit un vecteur en facteur. | `x` : le vecteur à convertir | `as.factor(x = c("A", "B", "A", "C"))` |
| `select()` | Sélectionne des colonnes d'un jeu de données. | `data` : le jeu de données, `...` : les colonnes à sélectionner | `dplyr::select(data = dataframe, col1, col2)` |
| `slice()` | Sélectionne des lignes spécifiques d'un jeu de données. | `data` : le jeu de données, `rows` : les rangs à sélectionner | `dplyr::slice(data = dataframe, rows = c(1, 3, 5))` |
| `filter()` | Filtre les lignes d'un jeu de données en fonction de conditions spécifiques. | `data` : le jeu de données, `...` : les conditions de filtrage | `dplyr::filter(data = dataframe, col1 > 10)` |
| `arrange()` | Trie les lignes d'un jeu de données en fonction de variables spécifiques. | `data` : le jeu de données, `...` : les variables de tri | `dplyr::arrange(data = dataframe, col1)` |
| `is.na()` | Vérifie si les valeurs sont manquantes (NA). | `x` : vecteur ou objet à tester | `is.na(x = vecteur)` |
| `!is.na()` | Vérifie si les valeurs ne sont pas manquantes (non-NA). | `x` : vecteur ou objet à tester | `!is.na(x = vecteur)` |
| `group_by()` | Crée des groupes de données en fonction de variables spécifiques. | `data` : le jeu de données, `...` : les variables de groupe | `dplyr::group_by(data = dataframe, col1)` |
| `summarise()` | Résume les données groupées en effectuant des calculs. | `data` : le jeu de données, `...` : les calculs à effectuer | `dplyr::summarise(data = dataframe, mean_col1 = mean(col1))` |
