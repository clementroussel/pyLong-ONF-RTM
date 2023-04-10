Flow-R
******

Flow-R (Flow path assessment of gravitational hazads at a Regional scale) est un modèle empirique 2D développé par l’université de Lausanne 
(Horton. Et al., 2013) et permettant la modélisation à large échelle de la propagation de laves torrentielles.

Flow-R couple un algorithme d'étalement avec un algorithme de propagation. On décrit ici le modèle de propagation qui fait 
l'hypothèse, comme pour les mouvements de masse (écroulements, chutes de blocs), que la distance peut être approchée par une modélisation de la ligne d'énergie.
L'originalité réside ici dans le fait que l'angle de la ligne est modulé en faisant l'hypothèse d'une vitesse maximale possible des laves torrentielles.

La conservation de l'énergie s'écrit entre deux points 1 et 2 le long du profil en long:

.. math::

   \Delta E_{TOT} = \left( E_{cin,1} + E_{pot,1} \right) - \left( E_{cin,2} + E_{pot,2} \right) = j

où:

- :math:`\Delta E_{TOT}` représente la variation d'énergie totale;
- :math:`E_{cin}` la composante d'énergie cinétique;
- :math:`E_{pot}` la composante d'énergie potentielle;
- :math:`j` les pertes de charges liées aux frottements.

La distance maximale de propagation est déterminée par intersection de la ligne d’énergie avec le terrain naturel. 

La vitesse peut être déterminée en chaque point du profil en long avec l’équation suivante:

.. math::

   V_{i} = min \left\{ \sqrt{ V_{i-1}^2 + 2.g.\Delta z - 2.g.\Delta x.tan{\varphi}}, V_{max} \right\}

avec:

- :math:`V_i` la vitesse au nœud de calcul;
- :math:`i`, :math:`V_{i-1}` la vitesse au nœud de calcul :math:`i-1`;
- :math:`\Delta x` la distance séparant les nœuds calcul :math:`i` et :math:`i-1`
- :math:`\Delta z` la différence d’altitude  entre les nœuds :math:`i-1` et :math:`i`;
- :math:`\tan \varphi` la pente de la ligne d’énergie;
- :math:`V_{max}` la vitesse maximale des laves.

On donne ci-après les valeurs d’angles de lignes d’énergie donnés dans la littérature sans limitation de vitesse en dehors du contexte de laves issues de débâcles d’OGP.
Pour des laves torrentielles, en s’appuyant sur des travaux Rickenmann et Zimmermann (1993), Bathurst (1997) et Huggel (2002), les auteurs indiquent un angle de 
ligne d’énergie :math:`\varphi` minimum de 11°. Cette valeur semble adaptée pour des laves à forte proportion de matériaux grossiers 
(coarse and medium-grained debris flows). D’après Zimmermann, cet angle est susceptible de chuter à 7° pour des matériaux plus fins (matrice argileuse prépondérante) 
et où les matériaux grossiers dans le front sont moins nombreux. La valeur de 11° correspond à la valeur typique d’angle de ligne d’énergie 
identifiée dans la littérature scientifique dans les laves issues de débâcles d’OGP. La valeur de 7° est inférieure à la valeur minimale de 9° identifiée pour des GLOF.

La limitation de la vitesse maximale des laves a pour effet de réduire la distance de parcours. 
Il n’est donc pas recommandé d’utiliser ce modèle avec des valeurs de ligne d’énergie issues de la littérature sur les laves d’origine GLOF (9 à 11°), qui elles, 
sont issues d’une analyse ne prenant pas en compte de limitation sur la vitesse. L’application du modèle montre que lorsqu’une limitation de la vitesse est utilisée, 
la valeur d’angle change de signification : elle ne correspond plus à une ligne d’énergie mais à la valeur de l’angle du profil en long en dessous duquel l’écoulement 
commence à décélérer (dynamique de dépôt). Une valeur de l’ordre de 3 à 4° devrait être pertinente.

Compte tenu du manque de recul sur l’approche de calcul avec limitation de la vitesse, des tests doivent être réalisés sur des cas documentés pour vérifier sa cohérence.