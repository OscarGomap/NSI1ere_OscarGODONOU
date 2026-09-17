# DM n°2 - Listes et dictionnaires

!!! warning "Modalités"
    Travail individuel, à rendre sous forme de fichier `.py`.

## Exercice 1 — Listes (7 points)

On donne la liste suivante :

```python
temperatures = [21, 19, 25, 30, 18, 22, 27]
```

1. Afficher la deuxième température de la liste.
2. Écrire une fonction `moyenne(liste)` qui renvoie la moyenne des valeurs.
3. Écrire une fonction `nb_superieur(liste, seuil)` qui renvoie le nombre
   d'éléments de `liste` strictement supérieurs à `seuil`.
4. En utilisant une liste en compréhension, créer la liste des températures
   supérieures à 20°C.

## Exercice 2 — Dictionnaires (7 points)

On représente un élève par un dictionnaire :

```python
eleve = {"nom": "Djossou", "notes": [12, 15, 9, 18]}
```

1. Ajouter une clé `"moyenne"` contenant la moyenne des notes de l'élève.
2. Écrire une fonction `meilleure_note(eleve)` qui renvoie la meilleure note
   de l'élève.
3. On donne une liste de plusieurs élèves (même structure que ci-dessus).
   Écrire une fonction `classement(eleves)` qui renvoie la liste des élèves
   triée par moyenne décroissante.

## Exercice 3 — Réflexion (6 points)

Expliquer, en quelques lignes, la différence entre une liste et un
dictionnaire, et donner un exemple de situation où chacune de ces
structures est la plus adaptée.

??? abstract "Corrigé"
    **Exercice 1**

    ```python
    temperatures = [21, 19, 25, 30, 18, 22, 27]

    print(temperatures[1])  # 19

    def moyenne(liste):
        return sum(liste) / len(liste)

    def nb_superieur(liste, seuil):
        compteur = 0
        for valeur in liste:
            if valeur > seuil:
                compteur += 1
        return compteur

    chaudes = [t for t in temperatures if t > 20]
    ```

    **Exercice 2**

    ```python
    eleve = {"nom": "Djossou", "notes": [12, 15, 9, 18]}
    eleve["moyenne"] = sum(eleve["notes"]) / len(eleve["notes"])

    def meilleure_note(eleve):
        return max(eleve["notes"])

    def classement(eleves):
        return sorted(eleves, key=lambda e: sum(e["notes"]) / len(e["notes"]), reverse=True)
    ```

    **Exercice 3**

    Une liste stocke des valeurs **ordonnées**, accessibles par leur
    position (indice) : elle convient pour une séquence où l'ordre compte
    (ex : une liste de notes dans l'ordre de saisie). Un dictionnaire
    associe des **clés à des valeurs** et convient pour représenter des
    données identifiées par un nom plutôt que par une position (ex : les
    informations d'un élève, où l'on veut accéder directement à `"nom"` ou
    `"notes"` sans connaître leur position).
