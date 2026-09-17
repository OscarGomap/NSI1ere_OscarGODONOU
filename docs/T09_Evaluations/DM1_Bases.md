# DM n°1 - Bases numériques et booléens

!!! warning "Modalités"
    Travail individuel, à rendre en TP ou sur l'espace de rendu. Durée
    indicative : 45 minutes.

## Exercice 1 — Conversions (8 points)

1. Convertir $42_{10}$ en binaire (montrer les étapes par divisions
   successives).
2. Convertir $101101_2$ en décimal.
3. Convertir $2A_{16}$ (hexadécimal) en décimal.
4. Combien de valeurs distinctes peut-on représenter sur 6 bits ?

## Exercice 2 — Booléens (6 points)

1. Construire la table de vérité de l'expression `(a or b) and (not c)`.
2. Simplifier l'expression `not (not a)`.
3. Écrire en Python une expression booléenne qui vaut `True` si un entier
   `n` est un multiple de 3 **ou** de 5.

## Exercice 3 — Programmation (6 points)

Écrire une fonction Python `en_binaire(n)` qui renvoie la représentation
binaire (sous forme de chaîne de caractères) d'un entier positif `n`, sans
utiliser la fonction native `bin`.

??? abstract "Corrigé"
    **Exercice 1**

    1. $42 = 101010_2$ (42÷2=21 r.0, 21÷2=10 r.1, 10÷2=5 r.0, 5÷2=2 r.1,
       2÷2=1 r.0, 1÷2=0 r.1 → lu de bas en haut : 101010)
    2. $101101_2 = 32+0+8+4+0+1 = 45_{10}$
    3. $2A_{16} = 2\times16 + 10 = 42_{10}$
    4. $2^6 = 64$ valeurs distinctes.

    **Exercice 2**

    | a | b | c | (a or b) and (not c) |
    |---|---|---|------------------------|
    | V | V | V | F |
    | V | V | F | V |
    | V | F | V | F |
    | V | F | F | V |
    | F | V | V | F |
    | F | V | F | V |
    | F | F | V | F |
    | F | F | F | F |

    `not (not a)` se simplifie en `a`.

    ```python
    n % 3 == 0 or n % 5 == 0
    ```

    **Exercice 3**

    ```python
    def en_binaire(n):
        if n == 0:
            return "0"
        resultat = ""
        while n > 0:
            resultat = str(n % 2) + resultat
            n = n // 2
        return resultat
    ```
