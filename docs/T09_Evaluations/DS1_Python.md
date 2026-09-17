# DS n°1 - Python : variables, boucles, fonctions

!!! warning "Modalités"
    Devoir surveillé individuel, sans document ni ordinateur. Durée : 1 heure.
    Le code sera rédigé au stylo sur la copie ; la syntaxe exacte de Python
    est exigée.

## Exercice 1 — Questions de cours (5 points)

1. Quelle est la différence entre les instructions `for` et `while` ?
   Donner un exemple de situation où l'on préfère chacune des deux.
2. Qu'affiche le code suivant ?
   ```python
   x = 5
   x += 3
   x = x * 2
   print(x)
   ```
3. Pourquoi l'indentation est-elle importante en Python ?

## Exercice 2 — Boucles (7 points)

1. Écrire un programme qui affiche tous les multiples de 7 compris entre 0
   et 100.
2. Écrire un programme qui calcule la somme des entiers pairs de 1 à `n`
   (`n` donné).
3. Écrire un programme utilisant une boucle `while` qui demande un mot de
   passe à l'utilisateur jusqu'à ce qu'il saisisse `"nsi2026"`.

## Exercice 3 — Fonctions (8 points)

1. Écrire une fonction `est_premier(n)` qui renvoie `True` si l'entier `n`
   (supposé $\geqslant 2$) est un nombre premier, `False` sinon.
2. Écrire une fonction `nb_premiers(n)` qui renvoie le nombre de nombres
   premiers inférieurs ou égaux à `n`, en réutilisant la fonction
   précédente.
3. Donner la spécification (rôle, paramètre, valeur renvoyée) de la
   fonction `est_premier`.

??? abstract "Corrigé"
    **Exercice 1**

    1. `for` est utilisée quand on connaît à l'avance le nombre
       d'itérations ou la séquence à parcourir (ex : parcourir une liste).
       `while` est utilisée quand la fin de la boucle dépend d'une
       condition dont on ne connaît pas à l'avance le nombre d'itérations
       (ex : attendre une saisie valide).
    2. `x` vaut `5`, puis `8` (5+3), puis `16` (8×2). Le programme affiche
       `16`.
    3. L'indentation délimite les blocs d'instructions (corps d'un `if`,
       d'une boucle, d'une fonction...). Sans elle, Python ne peut pas
       savoir quelles lignes appartiennent à quel bloc.

    **Exercice 2**

    ```python
    for i in range(0, 101, 7):
        print(i)

    def somme_pairs(n):
        somme = 0
        for i in range(2, n + 1, 2):
            somme += i
        return somme

    mot_de_passe = ""
    while mot_de_passe != "nsi2026":
        mot_de_passe = input("Mot de passe : ")
    ```

    **Exercice 3**

    ```python
    def est_premier(n):
        if n < 2:
            return False
        for diviseur in range(2, n):
            if n % diviseur == 0:
                return False
        return True

    def nb_premiers(n):
        compteur = 0
        for i in range(2, n + 1):
            if est_premier(i):
                compteur += 1
        return compteur
    ```

    Spécification : `est_premier(n)` prend en paramètre un entier `n`
    supérieur ou égal à 2, et renvoie `True` si `n` est un nombre premier
    (aucun diviseur autre que 1 et lui-même), `False` sinon.
