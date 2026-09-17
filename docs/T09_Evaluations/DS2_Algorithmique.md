# DS n°2 - Algorithmique et tri

!!! warning "Modalités"
    Devoir surveillé individuel. Durée : 1 heure. Calculatrice et documents
    interdits.

## Exercice 1 — Recherche dichotomique (6 points)

On donne la liste triée `[2, 5, 8, 12, 16, 23, 38, 45, 56, 72]`.

1. Dérouler à la main la recherche dichotomique de la valeur `23` : indiquer
   à chaque étape les bornes `debut`, `fin` et l'indice `milieu` testé.
2. Combien d'étapes maximum sont nécessaires pour chercher un élément dans
   cette liste de 10 éléments par dichotomie ?
3. Pourquoi la recherche dichotomique nécessite-t-elle que la liste soit
   triée ?

## Exercice 2 — Tri (9 points)

On donne la liste `[7, 2, 9, 4, 1]` à trier par ordre croissant.

1. Dérouler à la main le **tri par sélection** sur cette liste, en indiquant
   l'état de la liste après chaque échange.
2. Dérouler à la main le **tri par insertion** sur la même liste, en
   indiquant l'état de la liste après chaque insertion.
3. Écrire le code Python de la fonction `tri_selection(liste)`.

## Exercice 3 — Complexité (5 points)

1. Quelle est la complexité, en fonction du nombre d'éléments $n$, du tri
   par sélection dans le pire des cas ?
2. Quelle est la complexité de la recherche dichotomique dans le pire des
   cas ?
3. Entre une recherche séquentielle et une recherche dichotomique dans une
   liste triée de 1000 éléments, laquelle est la plus rapide dans le pire
   des cas ? Justifier.

??? abstract "Corrigé"
    **Exercice 1**

    | Étape | debut | fin | milieu | liste[milieu] |
    |-------|-------|-----|--------|----------------|
    | 1 | 0 | 9 | 4 | 16 (< 23, on cherche à droite) |
    | 2 | 5 | 9 | 7 | 45 (> 23, on cherche à gauche) |
    | 3 | 5 | 6 | 5 | 23 → trouvé, indice 5 |

    Avec 10 éléments, il faut au maximum $\lceil \log_2(10) \rceil = 4$
    étapes.

    La dichotomie repose sur la comparaison de l'élément du milieu pour
    éliminer une moitié de la liste : cela ne fonctionne que si la liste
    est triée, sinon on ne peut pas savoir de quel côté chercher.

    **Exercice 2**

    Tri par sélection sur `[7, 2, 9, 4, 1]` :

    - Min = 1 (indice 4) → échange avec indice 0 : `[1, 2, 9, 4, 7]`
    - Min des restants (2,9,4,7) = 2, déjà bien placé : `[1, 2, 9, 4, 7]`
    - Min des restants (9,4,7) = 4 → échange avec indice 2 : `[1, 2, 4, 9, 7]`
    - Min des restants (9,7) = 7 → échange avec indice 3 : `[1, 2, 4, 7, 9]`

    Tri par insertion sur `[7, 2, 9, 4, 1]` :

    - `[7]` puis insertion de 2 → `[2, 7, 9, 4, 1]`
    - insertion de 9 (déjà bien placé) → `[2, 7, 9, 4, 1]`
    - insertion de 4 → `[2, 4, 7, 9, 1]`
    - insertion de 1 → `[1, 2, 4, 7, 9]`

    ```python
    def tri_selection(liste):
        n = len(liste)
        for i in range(n):
            indice_min = i
            for j in range(i + 1, n):
                if liste[j] < liste[indice_min]:
                    indice_min = j
            liste[i], liste[indice_min] = liste[indice_min], liste[i]
        return liste
    ```

    **Exercice 3**

    1. Le tri par sélection est en $O(n^2)$ dans le pire des cas (comme
       dans le meilleur des cas d'ailleurs).
    2. La recherche dichotomique est en $O(\log_2 n)$ dans le pire des cas.
    3. Pour 1000 éléments, une recherche séquentielle nécessite au pire
       1000 comparaisons, contre environ $\log_2(1000) \approx 10$
       comparaisons pour la dichotomie : la recherche dichotomique est donc
       bien plus rapide.
