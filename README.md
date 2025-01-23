# TP06 - Fonctions
**STS 1CIEL** - Ce TP a pour but de mettre en oeuvre les notions apprises en cours sur les fonctions.

Ce repository est un projet CLion dans lequel vous trouverez un certain nombre de fichiers `.cpp` qui vont vous permettre de coder chaque exercice demandé. Une fois terminé il suffira de faire un commit, puis un push vers GitHub afin de rendre votre travail.

## Exo1 - La plus simple des fonctions simples
Écrivez en C++ une fonction appelée `hello()` dont le seul but est d’afficher à l’écran :

```text
Hello World !
```
Votre fonction ne comportera pas d’arguments et ne retournera rien, vous appellerez votre fonction dans la fonction `main()` et testerez son fonctionnement.

## Exo 2 - Message long ou message court
Votre programme demandera à l’utilisateur de saisir une phrase, si la phrase saisie comporte plus de 10 caractères, votre programme affichera :

```text
C'était une long message.
```

À l’inverse si votre phrase en comporte moins de 10 :

```text
C'était un court message.
```

Pour réaliser ce programme vous créerez une fonction `message()` dans le fichier exo2.cpp, cette fonction aura en paramètre une chaîne de caractère et devra retourner un booléen true si la chaîne est supérieure ou égale à 10 caractères et false dans le cas inverse.

<details>
<summary>👍<b>Coup de pouce :</b> Obtenir la longueur d'une chaîne de caractère </summary>

La méthode `length()` retourne la longueur d’une chaîne de caractère, nous donnons ci-dessous un exemple de son utilisation :

```cpp
longueur = maChaine.length();
```
Dans l’exemple ci-dessus la variable `longueur` contiendra le nombre de caractères de la chaîne `maChaine` .
</details>

## Exo 3 - Convertisseur de température
Dans cet exercice vous créerez un programme qui sera utilisé pour convertir des températures en Fahrenheit vers des Celsius ou des Kelvin à l’aide de deux fonctions :
- La premiere fonction que vous devez créer est `fahrenheit_to_celsius()` , cette fonction retournera la température en Celsius. Utilisez la fonction `round()` pour arrondir le résultat. 

Nous rappelons que la formule pour passer des degrés Fahrenheit aux degrés Celsius  est :

$$temp_{celsius}=\frac{5}{9}\times(temp_{fahrenheit}-32)$$

La seconde fonction que vous devez créer est `fahrenheit_to_kelvin()` ,cette fonction retournera la température en Kelvin. Utilisez la fonction `round()` pour arrondir le résultat. Nous rappelons que la formule pour passer des degrés Fahrenheit aux degrés Kelvin est :

$$temp_{kelvin}=\frac{5}{9}\times(temp_{fahrenheit}-32)+273$$

Dans ce programme les température seront **stockées dans des variables de type double** .

À présent, dans votre programme principal faites un menu qui demande à l’utilisateur qu’elle conversion il souhaite réaliser :

```text
Quelle conversion souhaitez vous faire ?
1 - Fahrenheit - Celsius
2 - Fahrenheit - Kelvin
3 - Quitter
```
Une fois le choix effectué, le programme demande de saisir la température :

```text
Saisissez la température en Fahrenheit :
```
Affichez ensuite le résultat et afficher à nouveau au menu principal pour une nouvelle conversion.

**Suppléments** : Si le programme précédent fonctionne ajouter au menu les conversions : Celsius -
Fahrenheit et Celsius - Kelvin.

## Exo 4 - Enclos à brebis

### Chapitre 1 : L'enclos
Nous souhaitons créer une fonction `enclos(int n)` qui affiche à l’écran un carré de `O` formant un enclos. Nous donnons ci-dessous un exemple pour `n=5` :

```text
O O O O O
O       O
O       O
O       O
O O O O O
```
Créez un programme en C++ qui demande à l’utilisateur la taille de l’enclos souhaité, puis appelle la fonction `enclos()` dans la fonction `main()` , afin de tracer celui-ci à l’écran.

<details>
<summary>👍<b>Coup de pouce :</b> Dessiner un carré plein</summary>
Nous donnons ci-dessous le code C++ permettant de réaliser un carré plein :

```cpp
#include <iostream>
using namespace std;

int main() {
    int n=5; // Taille de l'enclos
    for(int i=0;i<n;i++){ // Boucle des LIGNES
        for(int j=0;j<n;j++){ // Boucle des COLONNES
            cout << "O ";
        }
        cout << endl; // Retour à la ligne en fin de ligne de "O "
    }

    return 0;
}    
```
Ce qui donne à l’écran :


```text
O O O O O 
O O O O O 
O O O O O 
O O O O O 
O O O O O 
```
</details>

### Chapitre 2 : La brebis

Nous remarquons que ce bel enclos est bien inutile sans aucune brebis dedans ! Ajoutez à votre fonction `enclos()` 2 arguments supplémentaires et une valeur de retour : `int enclos(int n, int brebis_i, int brebis_j)`.

La brebis sera symbolisée par le caractère `*`

- L’entier `brebis_i` correspond à la coordonnée de la brebis au niveau vertical (lignes)
- L’entier `brebis_j` correspond à la coordonnée de la brebis au niveau horizontal (colonnes)

Votre fonction retournera un entier représentant le code d’erreur :
- `0` si tout s’est bien passé, que l’enclos est traçable et que la brebis peut brouter dedans.
- `1` si l’enclos n’est pas traçable car l’argument $n\le 2$.
- `2` si la brebis ne peut pas brouter dans l'enclos : $brebis_i\le 0$ ou  $brebis_j\le 0$ ou $brebis_i\ge n-1$ ou $brebis_j\ge n-1$

Cette fois-ci, demandez à l’utilisateur la taille de l’enclos désirée, et la position (i,j) de la brebis. Votre programme affichera à l’écran l’enclos avec sa brebis **si le dessin est réalisable**, si la fonction `enclos()` retourne une erreur vous afficherez à l’écran un message d’erreur en expliquant le problème et reproposerez une nouvelle saisie.

Nous donnons ci-dessous un exemple pour `n=6` , `brebis_i=2` et `brebis_j=3` :

```text
O O O O O O 
O         O 
O     *   O 
O         O 
O         O 
O O O O O O 
```

### Chapitre 3 : Brebis inattendue
Nous souhaitons créer une nouvelle fonction void `brebis_aleatoire(int n, int i, int j)` qui retournera les coordonnées d’une brebis **par référence** dans les variables `i` et `j` de manière aléatoire suivant le côté `n` de l’enclos.

À présent votre programme demandera à l’utilisateur de saisir la taille de l’enclos, puis s’il veut placer une brebis de manière aléatoire ou donner les coordonnées de celle-ci, vous devez également donner la possibilité à l’utilisateur de sortir du programme.

Exemple de sortie console :

```text
ENCLOS A BREBIS
Saisissez la taille de l'enclos svp : 4
MENU
1 - Placement de brebis aléatoire
2 - Placement avec saisie de coordonnées
3 - Quitter
1

O O O O
O   * O
O     O
O O O O

MENU
1 - Placement de brebis aléatoire
2 - Placement avec saisie de coordonnées
3 - Quitter
```

<details>
<summary>👍<b>Coup de pouce :</b> Tir aléatoire</summary>
Nous donnons ci-dessous un exemple d'utilisation de la bibliothèque random afin de générer un entier aléatoire compris entre 1 et 9 :

```cpp
#include <iostream>
#include <random>

int main() {
    // Initialisation du générateur de nombres aléatoires
    std::random_device rd;  // Génère une graine aléatoire
    std::mt19937 gen(rd()); // Générateur de nombres aléatoires Mersenne Twister
    std::uniform_int_distribution<> dis(1, 9); // Distribution uniforme entre 1 et 9

    // Génération d'un nombre aléatoire
    int random_number = dis(gen);

    // Affichage du nombre aléatoire
    std::cout << "Nombre aléatoire entre 1 et 9: " << random_number << std::endl;

    return 0;
}
```
</details>

## Exo 5 - Overloaded functions (*Fonctions surchargées*)

Dans cet exercice, vous allez créer un programme qui calcule la surface de deux formes, un carré et un rectangle, en appelant la fonction surchargée `find_area()`.

Créer en C++ 2 fonctions :

- La fonction `find_area()` pour le carré **reçoit une valeur entière** et **retourne une valeur entière**.
- La fonction `find_area()` pour le rectangle reçoit **deux valeurs de type double** et retourne **une valeur de type double**.

⚠️ Rappelez-vous que les deux prototypes de fonction doivent avoir le même nom de fonction : `find_area()`.

Pour finir, appelez vos fonctions dans le `main()`, vous créerez un menu demandant à l'utilisateur quel type de surface il souhaite calculer, de saisir le ou les côtés et afficherez le résultat :

```text
**** Calcul d'Aires ****
1 - Carre
2 - Rectangle
3 - Quitter

2
Saisissez la valeur des 2 cotes en cm :
5.3 6.2
Le rectangle a une surface de 32.86 cm2

**** Calcul d'Aires ****
1 - Carre
2 - Rectangle
3 - Quitter
```

