---
jupytext:
  encoding: '# -*- coding: utf-8 -*-'
  formats: ipynb, md:myst, py
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
La partie donnant les concepts pour faire ces exercices est [accessible ici](https://pcsi3physiquestan.github.io/intro_python/notebook/np_vecteurs.html).

Voici quelques exercices pour vous entraîner à coder. Les conseils donnés pour les premiers exercices sont toujours valables. _Pensez à créer un fichier par exercice._

+++
## Tracé simple.
```{admonition} Tracé simple.
Vous devez tracer le graphique de la fonction $f(x) = 2x + 3 * sin(x)$ sur l'intervalle $[0, 4\pi]$ en prenant $N = 2000$ points pour le tracé.

On suppose qu'il s'agit du mouvement d'une "Masse sur un axe". Le tracé de la courbe devra être rouge (trait plein). Les abscisses seront des temps (en secondes) et les ordonnées des positions (en mètre). Utilisez ces informations pour légender et titrer votre graphique.
```

```{dropdown} Quelques indices pour s'organiser
* Vous avez besoin des deux bibliothèques. N'oubliez pas de les importer.
* Vous n'allez pas créer un vecteur de 2000 points manuellement, pensez aux fonction qui permettent de créer automatiquement des vecteurs.
* Seule la fonction `sin` __de la bibliothèque `numpy`__ est vectorialisable.
* Essayer d'avoir une organisation claire de vos instructions pour créer le graphique. Vous pourrez la réutiliser souvent.
```

Vous devriez obtenir le graphique suivant (cliquez sur la croix).

```{code-cell}
:tags: [hide-input, hide-output]
import matplotlib.pyplot  as plt
import numpy as np

def f(x):
  return 2*x + 3 *np.sin(x)

x = np.linspace(0, 4 * np.pi, 2000)
y = f(x)

f, ax = plt.subplots()
f.suptitle("Masse sur un axe")

ax.set_xlabel("t(s)")
ax.set_ylabel("Position(m)")

ax.plot(x, y, color='red', label='x(t)')

ax.legend()
```

+++

## Tracé et manipulation des vecteurs
````{admonition} Tracé et manipulation des vecteurs
:class: tip
Un point matériel M de masse $m$ se déplaçant sans frottements sur un axe $Ox$ en étant attaché à un ressort de raideur $k$ et de longueur à vide $l_0$ constitue un oscillateur harmonique. L'évolution temporelle de la position du point M (lâché depuis la position $X_0$ sans vitesse initiale) est donnée par :

$$
x_M(t) = (X_0 - l_0) \cos (\omega_0 t) + l_0
$$

avec $\omega_0 = \sqrt{\frac{k}{m}}$

1. Montrer par le calcul que la vitesse du point M est donnée par $v_M(t) = -(X_0 - l_0) \omega_0 \sin (\omega_0 t)$.
2. Vous devez créer quatre graphiques :
    1. Le premier représente la position $x_M$ en fonction du temps.
    2. Le second représente la vitesse $v_M$ en fonction du temps.
    3. Le troisième représente l'énergie potentielle $E_p = \frac{1}{2}k x_M^2$ en fonction du temps.
    4. Le quatrième représente l'énergie cinétique $E_c = \frac{1}{2}m v_M^2$ en fonction du temps.

On prendra : $k=11 \rm{N.m^{-1}}; m=0.3 \rm{kg}; X_0 = 0.1 \rm{m}; l_0=0.06 \rm{m}$ et on réfléchira au vecteur numpy `temps` à créer pour calculer les abcisses. Il faut :
* observer suffisamment de périodes (3)
* suivre les variations du signal (une centaine de points par période)

N'oubliez le caractère vectoriel des opérations sur les vecteurs numpy, vous devez écrire ce script sans utiliser de boucle. Cliquez sur la croix pour voir ce que vous devez obtenir.
````

```{code-cell}
:tags: [hide-input, hide-output]

k = 11
m = 0.3
X0 = 0.1
l0 = 0.06
w0 = np.sqrt(11 / 0.3)

def xM(x):
  return (X0 - l0) * np.cos(w0 * x) + l0

def vM(x):
  return - w0 *(X0 - l0) * np.sin(w0 * x)


temps = np.linspace(0, 6 * np.pi / w0, 100)
xMt = xM(temps)
vMt = vM(temps)
Ep = 1 / 2 * k * xMt ** 2
Ec = 1 / 2 * m * vMt ** 2

f, ax = plt.subplots()
f.suptitle("Oscillateur harmonique")

ax.set_xlabel("t(s)")
ax.set_ylabel("Position(m)")

ax.plot(temps, xMt, color='red', label='xM(t)')

ax.legend()

f, ax = plt.subplots()
f.suptitle("Oscillateur harmonique")

ax.set_xlabel("t(s)")
ax.set_ylabel("Vitesse(m/s)")

ax.plot(temps, vMt, color='red', label='vM(t)')

ax.legend()


f, ax = plt.subplots()
f.suptitle("Oscillateur harmonique")

ax.set_xlabel("t(s)")
ax.set_ylabel("Energie potentielle(J)")

ax.plot(temps, Ep, color='red', label='Ep(t)')

ax.legend()

f, ax = plt.subplots()
f.suptitle("Oscillateur harmonique")

ax.set_xlabel("t(s)")
ax.set_ylabel("Energie cinétique(J)")

ax.plot(temps, Ec, color='red', label='Ec(t)')

ax.legend()

```

