**Coudière Yves**
# Rapport TP1
## Séance 1, partie 1
 1. Je choisis d'utiliser emacs et ipython.
 2. On saute la qestion 2.
 3. Les fichiers .md contiennent du code Markdown: l'énoncé du TP pour
    README.md et le compte-rendu à produire pour CR.md. Le fichier
    img/ecran-01.png contient l'image qui est mise en référence dans
    README.md. Les fichiers .py du répertoire src/ contiennent du code
    python. Ce sont des programmes ou des éléments de programme.
## Séance 1, partie 2
 1.
 #! /usr/bin/env python
# -*- coding: utf-8 -*-

import numpy as np
import matplotlib.pyplot as plt

import methodes
import equations

# Résolution approchée de y' = 1-y avec y(0) = 5 pour t dans [0,5]
equations.a = -1.
equations.b = 1.
t0,y0 = 0.,5.
T = 1.
# Avec un pas de 0.1, il faut donc 50 iterations

N,h1,h2,h3,h4,h5,h6,i = 50,0.2,0.1,0.05,0.025,0.0125,0.00625,1
  



[t,y1] = methodes.euler_explicite(t0,h1,N,y0,equations.f_affine)
[t,y2] = methodes.euler_explicite(t0,h2,N,y0,equations.f_affine)
[t,y3] = methodes.euler_explicite(t0,h3,N,y0,equations.f_affine)
[t,y4] = methodes.euler_explicite(t0,h4,N,y0,equations.f_affine)
[t,y5] = methodes.euler_explicite(t0,h5,N,y0,equations.f_affine)
[t,y6] = methodes.euler_explicite(t0,h6,N,y0,equations.f_affine)
# Solution exacte aux mêmes instants
z1 = equations.sol_affine(t,y0)
# Calcul de l'erreur maximum relative
e1 = np.max(np.abs((z1-y1)/z1))
e2 = np.max(np.abs((z1-y2)/z1))
e3 = np.max(np.abs((z1-y3)/z1))
e4 = np.max(np.abs((z1-y4)/z1))
e5 = np.max(np.abs((z1-y5)/z1))
e6= np.max(np.abs((z1-y6)/z1))
# Graphe des solutions exactes et approchées
plt.loglog(t,y1,'b-+',label='solution approchée h=0.1')
plt.loglog(t,z1,'r-',label='solution exacte')
plt.xlabel('t')
plt.ylabel('y')
plt.title("Méthode d'Euler explicite")
plt.legend()
plt.show()

# Écriture de l'erreur en fonction de h


print("{0} | {1}".format(h1,e1))

print("{0} | {1}".format(h2,e2))

print("{0} | {1}".format(h3,e3))

print("{0} | {1}".format(h4,e4))

print("{0} | {1}".format(h5,e5))

print("{0} | {1}".format(h6,e6))

## Séance 2
