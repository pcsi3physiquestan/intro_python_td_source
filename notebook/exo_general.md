---
jupytext:
  encoding: '# -*- coding: utf-8 -*-'
  formats: ipynb,md:myst
  split_at_heading: true
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.10.3
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# S'entraîner.

## Analyser un code

````{admonition} Exercice : Fonction et boucle
:class: tip

Observez le code suivant puis répondre aux questions

```{code-block}
def somme_carre(n):
  S = 0
  for i in range(n):
    S = S + i**2
  return S

print(somme_carre(5))
```

1. Vrai/Faux : `n` doit être un entier ou l'appel de cette fonction renverra une erreur.
2. Combien de fois la boucle `for` va-t-elle être parcourue ?
3. Qu'affiche la dernière instruction ?


```{toggle} Cliquer pour afficher les réponses __après réflexion.__
1. __Vrai__ car la fonction `range` demande comme argument un entier.
2. `range(n)` crée une suite de nombres entiers de 0 à n-1. La boucle sera donc parcourue __n fois__.
3. On somme les carré de 0 à 4 soit $0 + 1 + 4 + 9 + 16 = 30$

```

````

````{admonition} Exercice :  Utiliser des listes
:class: tip
Observez le code suivant puis répondre aux questions
```{code-block}
L1 = [1, 2, 3]
L2 = [4, 5, 6]
L = []
for i in range(len(L1)):
  L = L.append(L1[i] + L2[i])

print(len(L1))
print(L1 + L2)
print(L)
```

1. Préciser pour chaque instruction `print` ce qui sera affiché.

```{toggle} Cliquer pour afficher les réponses __après réflexion.__
1. `print(len(L1))` affiche la longueur de la liste `L1`, soit `3`
2. `print(L1 + L2)` : l'opérateur `+` entre deux listes concatène les deux listes. On affiche donc `[1, 2, 3, 4, 5, 6]`
3. `print(L)` : La boucle somme deux à deux les éléments de `L1` et `L2` et stocke le résultat comme élément de la liste `L` on affiche donc : `[5, 7, 9]`
```
````

## Coder soi-même

Vous allez devoir écrire votre propre code. Commencez par :
1. Ouvrir pyzo et créer un nouveau fichier _pour chaque exercice_. Enregistrez le dans un répertoire clair pour le retrouver ensuite (extension `.py` à la fin du fichier).
2. Réfléchir à l'algorithme qu'on vous demande de créer.
3. Ecrire la fonction demandée dans le fichier que vous avez créé.
4. Dans le même fichier, écrire une série d'instructions pour vérifier que votre fonction fonctionne bien (cf. exercices).
5. Exécuter le fichier (`Exécuter > Exécuter le contenu de l'onglet courant` ou `Ctrl + E`) et vérifier que vous obtenez ce qu'il faut. Comprendre les erreurs et les corriger si nécessaire. Vous trouverez [ici quelques conseils pour gérer les erreurs de codage.](erreurs)


### Boucle simple

````{admonition} Boucle simple
:class: tip
Vous devez créer deux fonctions qui prennent chacune comme argument un entier `n` et renvoient la somme des entiers compris entre 0 et `n` __inclus__.

1. La première utilisera une boucle `for`
2. La seconde utilisera une boucle `while`

Tester ensuite votre fonction en affichant son retour pour $n = 0, 1, 2, 5$ et $100$. Les résultats pour ces valeurs sont donnés ci-dessous (cliquez sur la croix).
````

```{code-cell}
:tags: [remove-input, hide-output]
def somme_carre(n):
  s = 0
  for i in range(1, n+1):
    s += i
  return s

print("n=0 : ", somme_carre(0))
print("n=1 : ", somme_carre(1))
print("n=2 : ", somme_carre(2))
print("n=5 : ", somme_carre(5))
print("n=100 : ", somme_carre(100))
```

+++

### Choix d'une boucle

````{admonition} Choix d'une boucle
:class: tip
Vous devez créer une fonction `somme_ks` qui prend chacune comme argument un entier `n` et renvoie la somme des entiers $k$ tels que $k + k^2 + k^3 \leq n$.

1. Pourquoi ne peut-on utiliser qu'un seul type de boucle ? Laquelle ?
2. Proposer une fonction.

Tester ensuite votre fonction en affichant son retour pour $n = 0, 2, 5, 100$ et $2000$. Les résultats pour ces valeurs sont donnés ci-dessous (cliquez sur la croix).
````

```{code-cell}
:tags: [remove-input, hide-output]
def somme_ks(n):
  s = 0
  i = 0
  while i + i**2 + i**3 <= n:
    s += i
    i += 1
  return s

print("n=0 : ", somme_ks(0))
print("n=2 : ", somme_ks(2))
print("n=5 : ", somme_ks(5))
print("n=100 : ", somme_ks(100))
print("n=2000 : ", somme_ks(2000))
```

### Diviseurs
````{admonition} Diviseurs
:class: tip
Ecrire une fonction `getDiv` qui prend un nombre entier `n` non nul et qui renvoie tous les diviseurs (même non premiers) de ce nombre sous forme de liste.

Tester ensuite votre fonction en affichant son retour pour $n = 1, 4, 24, 47$ et $254$. Les résultats pour ces valeurs sont donnés ci-dessous (cliquez sur la croix).

````

```{code-cell}
:tags: [remove-input, hide-output]
def getDiv(n):
    # Fonction qui renvoir tout les diviseurs d'un nombre n.
    L = []
    for i in range(1, n +1):
        if n % i == 0:
            L += [i]
    return L

print("n=1 : ", getDiv(1))
print("n=4 : ", getDiv(4))
print("n=24 : ", getDiv(24))
print("n=47: ", getDiv(47))
print("n=254 : ", getDiv(254))
```