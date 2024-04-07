# Algorithmique

## Objectifs
Voici les objectifs de ce TD :
- [ ] Créer une fonction
- [ ] Créer une structure conditionelle
- [ ] Créer des boucles

- [Algorithmique](#algorithmique)
  - [Objectifs](#objectifs)
  - [Objectifs](#objectifs-1)
  - [Exercice 1 - Création de fonction](#exercice-1---création-de-fonction)
    - [Mémo](#mémo)
    - [La commande `function()`](#la-commande-function)
    - [La commande `if() {}`](#la-commande-if-)
    - [La commande `else() {}`](#la-commande-else-)
    - [La commande `else if() {}`](#la-commande-else-if-)
  - [Exercice 2 - Création des boucles](#exercice-2---création-des-boucles)
    - [Mémo](#mémo-1)
  - [Liens utiles](#liens-utiles)


## Objectifs
Voici les objectifs de ce chapitre :
- [ ] Construire des structures conditionnelles
- [ ] Construire des boucles
- [ ] Créer des fonctions
- [ ] Utilisation des fonctions de test logique


## Exercice 1 - Création de fonction

Dans cet exercice, vous allez devoir programmer plusieurs fonctions pour calculer le salaire net à partir d'un salaire brut pour **le statut de salarié uniquement**. Nous utiliserons cette [page web](https://www.salaire-brut-en-net.fr/) pour comprendre les éléments qui interviennent dans le calcul. Ne pas tenir compte de l'élement *NOMBRE DE MOIS DE PRIME CONVENTIONNELLE* sur présent sur le site.

<img src="./img/salaire.PNG" alt="" style="height: 400px;">

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|-------------------|-------------|----------------------|---------|
| `is.numeric()` | Vérifie si un objet est de type numérique. | `x` : l'objet à vérifier | `is.numeric(x)` |
| `function(toto, tata = valeur_par_defaut) { ... }` | Définit une fonction avec un argument obligatoire et un argument facultatif avec une valeur par défaut. | `toto` : l'argument requis pour la fonction<br> `tata` : l'argument qui peut être omis lors de l'appel de la fonction, avec une valeur par défaut | `my_function <- function(toto, tata = 1) { ... }` |
| `return(objet_a_retourner)` | Termine l'exécution d'une fonction et renvoie une valeur spécifiée. | `objet_a_retourner` : la valeur à renvoyer à partir de la fonction | `return(resultat)` |
| `if(condition) { bloc_de_code }` | Exécute un bloc de code si la condition est vraie. | `condition` : la condition à évaluer | `if(x > 0) { print("x est positif") }` |
| `if(condition) { bloc_de_code } else { autre_bloc_de_code }` | Exécute un bloc de code si la condition est vraie, sinon exécute un autre bloc de code. | `condition` : la condition à évaluer | `if(x > 0) { print("x est positif") } else { print("x est négatif ou nul") }` |
| `if(condition1) { bloc_de_code1 } else if(condition2) { bloc_de_code2 }` | Exécute un bloc de code si la première condition est vraie, sinon vérifie une autre condition et exécute un autre bloc de code si cette condition est vraie. | `condition1`, `condition2` : les conditions à évaluer | `if(x > 0) { print("x est positif") } else if(x == 0) { print("x est nul") }` |
| `readline(prompt = "")` | Lit une ligne depuis l'entrée standard (généralement le clavier). | `prompt` : le message à afficher à l'utilisateur pour le guider lors de la saisie | `valeur <- readline(prompt = "Veuillez saisir une valeur : ")` |
| `cat(..., sep = " ")` | Concatène et imprime les éléments fournis. | `...` : les objets à imprimer <br> `sep` : le séparateur à utiliser entre les éléments (par défaut, un espace) | `cat("Hello", "world!", sep = " ")` |

### La commande `function()`

1. Créer une fonction `salaire_net_cadre()` qui prend en entrée le salaire mensuel brut d'un cadre et qui retourne le salaire net **avant impôt**. Ne pas tenir compte du temps de travail. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
salaire_net_cadre = function(salaire_brut) {
        salaire_net_avant_impot = salaire_brut * 0.75
        return(salaire_net_avant_impot) }
#Test de la fonction
salaire_net_cadre(salaire_brut = 3000)
```
</details>

2. Modifier la fonction pour que ce salaire mensuel brut **avant impôt** soit de 2500€ si l'utilisateur ne renseigne pas ce paramètre.

<details>
<summary>Correction</summary>

```r
salaire_net_cadre = function(salaire_brut = 2500) {
        salaire_net_avant_impot = salaire_brut * 0.75
        return(salaire_net_avant_impot) }
#Test de la fonction
salaire_net_cadre()
```
</details>

3. Modifier la fonction `salaire_net_cadre()` en ajoutant le paramètre temps de travail avec comme valeur par défaut 100%. Ne pas tenir compte du taux de prélèvement à la source. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
salaire_net_cadre = function(salaire_brut = 2500,temps_travail = 1) {
        salaire_net_avant_impot = salaire_brut * 0.75 * temps_travail
        return(salaire_net_avant_impot) 
}
#Test de la fonction
salaire_net_cadre(salaire_brut = 3000,
                  temps_travail = 0.8)
```
</details>


### La commande `if() {}`

4. Modifier la fonction `salaire_net_cadre()` pour que la fonction retourne une erreur si le salaire mensuel brut en entrée n'est pas une valeur numerique. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
salaire_net_cadre = function(salaire_brut = 2500,temps_travail = 1) {
  
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }
  
  salaire_net_avant_impot = salaire_brut * 0.75 * temps_travail
  return(salaire_net_avant_impot) 
}
#Test de la fonction
salaire_net_cadre(salaire_brut = "2000€")
salaire_net_cadre(salaire_brut = 2000)
```
</details>

5. Modifier la fonction `salaire_net_cadre()` pour que la fonction retourne une erreur si le temps de travail n'est pas numérique et n'est pas compris entre 0 et 1. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
salaire_net_cadre = function(salaire_brut = 2500,temps_travail = 1) {
  
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }

  if (!is.numeric(temps_travail)) {
    return("Erreur :  le temps de travail doit doit être une valeur numérique")
  }

  if ( (temps_travail > 1) | (temps_travail < 0)) {
    return("Erreur :  le temps de travail doit être une valeur numérique entre 0 et 1")
  }

  salaire_net_avant_impot = salaire_brut * 0.75 * temps_travail
  return(salaire_net_avant_impot) 
}
#Test de la fonction
salaire_net_cadre(salaire_brut = 2000, temps_travail = "100%")
salaire_net_cadre(salaire_brut = 2000, temps_travail = 0.8)
salaire_net_cadre(salaire_brut = 2000, temps_travail = 100)
```
</details>

### La commande `else() {}`

6. Créer une nouvelle fonction `salaire_net()` identique à la précédente mais avec un paramètre en plus qui est le statut *cadre/non cadre* du salarié. La fonction retourne également une erreur si le statut n'est pas *cadre* ou *non cadre*. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
salaire_net = function(salaire_brut = 2500,temps_travail = 1, statut) {
  
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }
  
  if (!is.numeric(temps_travail)) {
    return("Erreur :  le temps de travail doit doit être une valeur numérique")
  }

  if ( (temps_travail > 1) | (temps_travail < 0)) {
    return("Erreur :  le temps de travail doit être une valeur numérique entre 0 et 1")
  }

  if (!statut %in% c("cadre","non cadre")) {
    return("Erreur :  le statut doit être cadre ou non cadre")
  }

  if (statut == "cadre") {
        salaire_net_avant_impot = salaire_brut * temps_travail * 0.75
  } else {
        salaire_net_avant_impot = salaire_brut * temps_travail * 0.78
  }

  return(salaire_net_avant_impot) 
}
#Test de la fonction
salaire_net(salaire_brut = 2000, statut = "cadre")
salaire_net(salaire_brut = 2000, statut = "non cadre")
salaire_net(salaire_brut = 2000, statut = "technicien")
```
</details>

### La commande `else if() {}`

Voici un tableau **fictif** du taux de prélèvement à la source selon le salaire net mensuel : 

| Revenu mensuel net      | Taux |
|:------------------------:|:----:|
| Jusqu'à 1 591 €         | 0 %  |
| 1 591 € à 2 006 €       | 2,9 %|
| 2 006 € à 3 476 €       | 9,9 %|
| 3 476 € à 8 557 €       | 20 % |
| Supérieur à 8 557 €     | 43 % |

7. Modifier la fonction précédente pour calculer le salaire net mensuel **après prélèvement à la source**. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
salaire_net = function(salaire_brut = 2500,temps_travail = 1, statut) {
  
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }
  
  if (!is.numeric(temps_travail)) {
    return("Erreur :  le temps de travail doit doit être une valeur numérique")
  }

  if ( (temps_travail > 1) | (temps_travail < 0)) {
    return("Erreur :  le temps de travail doit être une valeur numérique entre 0 et 1")
  }

  if (!statut %in% c("cadre","non cadre")) {
    return("Erreur :  le statut doit être cadre ou non cadre")
  }

  if (statut == "cadre") {
        salaire_net_avant_impot = salaire_brut * temps_travail * 0.75
  } else {
        salaire_net_avant_impot = salaire_brut * temps_travail * 0.78
  }

  if (salaire_net_avant_impot <= 1591) {
    salaire_net_apres_impot <- salaire_net_avant_impot
  } else if (salaire_net_avant_impot <= 2006) {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.029)
  } else if (salaire_net_avant_impot <= 3476) {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.099)
  } else if (salaire_net_avant_impot <= 8557) {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.20)
  } else {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.43)
  }

  return(salaire_net_apres_impot) 
}
```
</details>

8. Créer une fonction `shifumi()` qui demande à l'utilsateur de saisir une valeur dans la console entre *pierre* , *papier* ou *ciseaux*. La fonction simule également un de ces trois choix à l'aide de la fonction `sample()` puis retourne le résultat. Tester la fonction pour vérifier.

<details>
<summary>Correction</summary>

```r
shifumi <- function() {
  # Demander à l'utilisateur de saisir une valeur
  choix_utilisateur <- readline(prompt = "Choisissez entre pierre, papier ou ciseaux : ")
  
  # Vérifier si l'utilisateur a saisi une valeur valide
  if (choix_utilisateur %in% c("pierre", "papier", "ciseaux")) {
    # Simuler un choix aléatoire pour l'ordinateur
    choix_ordi <- sample(c("pierre", "papier", "ciseaux"), 1)
    
    # Afficher les choix de l'utilisateur et de l'ordinateur
    cat("Votre choix :", choix_utilisateur, "\n")
    cat("Choix de l'ordinateur :", choix_ordi, "\n")
    
    # Retourner le résultat du jeu
    if (choix_utilisateur == choix_ordi) {
      return("Égalité !")
    } else if ((choix_utilisateur == "pierre" & choix_ordi == "ciseaux") |
               (choix_utilisateur == "papier" & choix_ordi == "pierre") |
               (choix_utilisateur == "ciseaux" & choix_ordi == "papier")) {
      return("Vous avez gagné !")
    } else {
      return("L'ordinateur a gagné !")
    }
  } else {
    return("Valeur invalide. Veuillez choisir entre pierre, papier ou ciseaux.")
  }
}

#Test de la fonction
shifumi()
```
</details>

## Exercice 2 - Création des boucles

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|--------------------|-------------|----------------------|---------|
| `for (variable in sequence) { ... }` | Exécute un bloc de code pour chaque valeur dans une séquence spécifiée. | `variable` : la variable qui prendra les valeurs de la séquence à chaque itération | `for (i in 1:10) { ... }` |
| `while (condition) { ... }` | Exécute un bloc de code tant qu'une condition spécifiée est vraie. | `condition` : l'expression logique qui doit être vraie pour continuer à exécuter le bloc de code | `while (x < 10) { ... }` |

1. Somme cummulée : Créer une boucle `for()` qui parcourt les éléments du vecteur `c(1,2,3,4,5)` un par un. À chaque itération de la boucle, ajouter l'élément en cours au résultat précédent et afficher le résultat.

<details>
<summary>Correction</summary>

```r
resultat = 0
for (element in c(1,2,3,4,5)) {
  resultat = resultat +  element
  print(paste("le resultat est : ",resultat))
}
```
</details>

2. Somme cummulée : Créer une boucle `while()` qui calcule la somme cumulative des nombres entiers à partir de 1 jusqu'à ce que la somme dépasse 50, en affichant le résultat à chaque étape ainsi que la valeur actuelle de l'élément à laquelle la boucle s'est arrêtée. 

<details>
<summary>Correction</summary>

```r
element = 1
resultat = 0
while (resultat <= 50) {
  resultat = resultat +  element
  print(paste("le resultat est : ",resultat))
  print(paste("le programme s'est arrêté à la valeur : ", element))
  element = element + 1
}
```
</details>

3. Parcourir toutes les colonnes du dataframe `iris` à  l'aide d'une boucle `for()`. Pour chaque itération afficher la type de la colonne.

<details>
<summary>Correction</summary>

```r
for (colonne in colnames(iris)) {
        type_colonne = class(iris[ , colonne])
        print(paste("la colonne ", colonne, " est de type : ", type_colonne))
}
```
</details>

4. Même question mais avec une boucle `while()`.

<details>
<summary>Correction</summary>

```r
# Initialisation de l'indice de colonne
indice_colonne <- 1

# Tant qu'il reste des colonnes à parcourir dans iris
while (indice_colonne <= ncol(iris)) {
  # Récupération du nom de la colonne
  nom_colonne <- colnames(iris)[indice_colonne]
  
  # Récupération du type de données de la colonne
  type_colonne <- class(iris[, nom_colonne])
  
  # Affichage du résultat
  print(paste("la colonne ", nom_colonne, " est de type : ", type_colonne))
  
  # Passage à la colonne suivante
  indice_colonne <- indice_colonne + 1
}
```
</details>

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)
- [Algorithmique](https://asardell.github.io/programmation-r/algo.html#construire-une-fonction)



