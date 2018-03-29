
![image](https://www.espritsante.com/images/0248103001340357281.jpg)

https://are00dynamic-2018.github.io/PROJET-ABEILLE/

# Table des matières 
- [Membre du groupe  :honeybee: ](#membres)  
- [Description du projet  :honeybee: ](#sujet)
- [Modélisations mathématiques de la reproduction des abeilles  :honeybee: ](#doc_ref)  
  - [Suite Fibonacci   :sunflower: ](#Fibonacci)

- [Nouvelle Modélisations mathématiques de la reproduction des abeilles appliquée à l'aaparition des pesticides  :honeybee: ](#ParamètresReproductionPesticide)
  - [Paramètres Pesticides  :honeybee: ](#ParamètresPest) 
  - [Paramètres Abeilles  :honeybee: ](#ParamètresAbeilles) 
  - [Modélisation  :honeybee: ](#Modelisation) 

- [Bibliographie  :honeybee: ](#Bibliographie)

<a name="membres"/>
# Membres du groupe :honeybee:  

**LANOUNI sofia**  

**COHEN-SOLAL Roy**

**MALASIGNE Clément**

**LUBEK Lazare** 

<a name="sujet" />
# Description du projet :honeybee: 

  Notre projet consiste à modéliser les effets de pesticides sur une colonie d'abeilles durant plusieurs années. Lors de notre étude, nous allons voir comment modéliser la reproduction des abeilles et notamment l'évolution de la ponte d'oeufs. Ainsi lorsque l'on va simuler l'action du pesticide sur plusieurs colonies, nous allons pouvoir changer certain paramètres de reproduction et suivre l'évolution de la population d'abeilles

<a name="doc_ref"/>
# Modélisations mathématiques de la reproduction des abeilles :honeybee: 

  Dans une colonie d'abeilles, il y a entre 20 000 et 90 000 abeilles. 
  
  Chez les abeilles, la reine décide de féconder ou non les oeufs à partir du sperme emmagasiné des mois, voire des années auparavant.Sachant que les règles de reproduction chez les abeilles sont telles que  l'abeille femelle a un père et une mère(la reine) tandis que l'abeille male n'a qu'une mere(la rien). on peut en déduire une loi mathématique.


![image](http://www.lenombredor.free.fr/nature_fichiers/image021.jpg)

  <a name="Fibonacci"/>
### Fibonacci  :sunflower:
    
  En effet , on remarque que la population d'une ruche peut être modelisée par la suite de _**Fibonacci**._ étant donné qu'à chaque génération , les nombres de femelles et de mâles sont deux nombres consécutifs de cette suite. On peut démontrer mathématiquement que la limite du rapport entre F_(n+1) et F_n est le nombre d'or (~1,618).On comprend donc que le rapport entre les mâle et femelles est environ égale au nombre d'or. Et étant donné qu'on parle d'une ruche qui possède au minimum 10 000 abeilles (soit 4000 mâles et 6000 femelles environ) , c'est à dire environ F_19 et F_20 le rapport entre les deux est assez proche pour approximer dans notre modèle, l'évolution de la population en se servant du coefficient du nombre d'or plutôt que de definir la suite en elle-même qui demanderait beaucoup plus de puissance à notre ordinateur.

  - Nous avons en compte le fait qu'après la ponte , les oeufs éclosent au bout de 3 semaines à peu près.
  - Nous avons en compte la mort des abeilles qui vient ,après éclosion, environ 7 semaines (en y appliquant un facteur aléatoire) et on a pris en compte la mort d'abeilles par des prédateurs avec aussi un facteur aléatoire qui sera plus élevé pour les ouvrières car ce sont elles qui sortent de la ruche et donc qui ont le plus de risques de mourrir.

     (Notes:la durée de vie varie aussi en fonction de la période en réalité pour les ouvrières 13 à 38 jours en été , 30 à 60 jours au printemps , environ 140 jours en hiver et pour les mâles de 21 à 32 jours au printemps et le début de l’été et jusqu’à 90 jours à la fin de l’été et en automne ) 
- On sait que la ponte des oeufs dépend aussi de la période de l'année , on s'est donc basé sur une courbe empirique de celle-ci pour trouver une fonction l'approchant en choisissant d'observer l'évolution d'une population d'abeilles de Provence On a donc approximé la courbe des pontes en fonction de la période de l'année par un polynôme de degré 4.

![Image](http://nicolas.blogs.com/.a/6a00d83455b58069e20115721bba3b970b-pi)

Voilà la ligne de code modélisant le nombre d'oeufs par semaines avant et après 14 semaines. :

    '''
    def nb_oeuf_par_semaine1(k):
      #Avant 14 semaines
      if k<=14:
        nb_oeufs=int((-2.6064*k**3)+(33.363*k**2)+(22.356*k)+1000)
      else:
        #Apres 14 semaines
        nb_oeufs=int((0.3906*k**4)+(-31.539*k**3)+(929*k**2)+(-11826*k)+55718  
    return(7*nb_oeufs)
    '''
        
  Si le nombre de semaines k est inférieur à 14, le nombre d'oeufs par semaine est de (-2.6064 x k³)+(33.363 x k²)+(22.356 x k)+1000).
  En revanche, si le nombre de semaine est supréieur à 14, alors les abeilles pondront un nombre d'oeufs égal à (0.3906 x k⁴)+(-31.539 x k³)+(929 x k²)+(-11826 x k)+55718.
On arrondit à une valeur entière pour simplifier les résultats.

  En réalité, ce n'est pas cette fonction-là que nous utilisons, mais plutôt celle-ci qui utilise des intégrales :


    '''
    def nb_oeuf_par_semaine1(k):
      #Avant 14 semaines
      if k<=14:
        nb_oeufs=int((-(2.6064/4)*(k+1)**4)+((33.363/3)*(k+1)**3)+((22.356/2)*(k+1)**2)+1000*(k+1))-int((-(2.6064/4)*k**4)+((33.363/3)*k**3)+((22.356/2)*k**2)+1000*k)
      else:
        #Apres 14 semaine
        nb_oeufs=int(((0.3906/5)*(k+1)**5)+((-31.539/4)*(k+1)**4)+((929/3)*(k+1)**3)+((-11826/2)*(k+1)**2)+55718*(k+1)) int(((0.3906/5)*(k**5)+((-31.539/4)*k**4)+((929/3)*k**3)+((-11826/2)*k**2)+55718*k))
    return(7*nb_oeufs)
    '''


- Nous avons crée des fonctions qui permettent d'observer le comportement des abeilles sur plusieurs années :
Notre fonction reproduction fonctionne de la façon suivante :
  - Nous appelons population le tuple (nb_males, nb_ouvriere, reine) constitué du nombre de males, d'ouvrières et de la présence ou non de la reine. On crée une liste R, qui représente le nombre de males et de femelles au cours du temps. Le nombre de males et d'ouvrières morts correspond alors au premier tuple de la liste d'oeufs pondus, car chaque semaine, l'on décale d'un rang le nombres d'oeufs pondu jusqu'à 7 semaines (espérance de vie d'une abeille). On soustrait alors le nombre dde males morts et d'ouvrières mortes au nombre de males et d'ouvrières.
  
- Nous avons, par ailleurs, rajouté des causes de morts autres que la vieillesse, qui illustrent les aléas naturels (prédateurs, accidents,...)

<a name="ParamètresReproductionPesticide"/>
# Nouvelle Modélisations mathématiques de la reproduction des abeilles appliquée à l'aaparition des pesticides :honeybee: 

  Après avoir fini de modéliser la population il est temps de s'intéresser aux effets des pesticides sur celle-ci:
On définit 3 paramètres pour le pesticide et 3 paramètre pour les abeilles que l'on compte faire varier dans nos modèles,  à savoir :

  <a name="ParamètresPest"/>
### Paramètres pesticides :sunflower: 



| Paramètres     | Utilité                                                                          |   Variation        |
| ---------------|:--------------------------------------------------------------------------------:|-------------------:|
| `létalité`     |la capacité du pesticide à tuer l'abeille i.e la facilité du pesticide à tuer   | réelle entre 0 et 1|
| `adaptation`   |la capacité des abeilles à resister au pesticide                                | réelle entre 0 et 1|
| `portée`       |la capacité à atteindre une abeille avec le pesticide                           | réelle entre 0 et 1|
   
   Le pesticide depend de ses trois paramètres. Dans notres programme, le pesticide est un tuple caractérisée par ses trois paramètres :
    

    '''
    pesticide=(letalite,adaptation,porte)
    '''

  <a name="ParamètresAbeilles"/>
### Paramètres Abeilles :sunflower:


| Paramètres   | Utilité                                                                                |   Variation        |
| -------------|:--------------------------------------------------------------------------------------:|-------------------:|
| `alpha`      |proportion de la population resistante, qui resite                                      | réelle entre 0 et 1|
| `taux_res`   |taux de resistance sur la population resistante                                         | réelle entre 0 et 1|
| `taux_nres`  |taux de resistance sur la population non resistante ( :exclamation: taux_res>taux_nres )| réelle entre 0 et 1|
  
  Il s'agira de définir une fonction qui renverra le nombre d'abeilles touchées qui prendra en compte la portée ainsi qu'un paramètre aléatoire , on distinguinguera les abeilles touchées resistantes et celles qui ne sont pas reistantes.
A partir de ces abeilles touchées , on prélèvera un certain nombre d'abeilles qui seront effectivement mortes ,chez les resistantes qui depend de leur taux de resistance et idem pour les non resistantes en y faisant intervenir la létalité ainsi qu'un paramètre aléatoire. 
  Nous testerons ensuite la proportion des abeilles mortes par rapport aux abeilles touchées et celui-ci nous indiquera si les abeilles ont resistées ou pas ,en distinguant toujours les abeilles resistantes des non resistantes. En effet , si cette proportion est inférieure au seuil d'adaptation on en déduit que les abeilles ont dévellopés une resistance et donc le taux de resistance des abeilles.

 <a name="Modelisation"/>
### Modelisation

  Dans notre modélisation, on considère que les "abeilles_touchees" représentent la populations femelles étant donné qu'elles sont les seules à sortir de la ruche, elles sont les seules à être touchées par le pesticides. 
  POur la suite des explications, on parlera des abeilles ouvrières butineuses.
  
  D'après les paramètres sités ci-dessus, on peut calculer le nombre d'abeilles touchées. En effet on a **le nombre d'abeilles resistantes touchées** qui est alpha du nombre de population totale d'ouvrière.On affinera à *+/- 1%*. **Le nombre d'abeilles non resistantse** est simplement lenombre total d'ouvrière moins le nombre  d'abeilles resistantes touchées, tours affiner à *+/- 1%*.
  **Ici on a utilisé le paramètre alpha qui correspond à la proportion de la population qui résiste.**
   
 '''
 def abeilles_touchees(nb_ouvriere,alpha):
    res=nb_ouvriere*alpha
    res_touchees=(int(res*(porte*(randrange(9000,11000)/10000))))
    
    nres=nb_ouvriere-res
    nres_touchees=(int(nres*(porte*(randrange(9000,11000)/10000))))
    
    if (res_touchees+nres_touchees)>nb_ouvriere:
        return (res,nres)
    return (res_touchees,nres_touchees)
            
  '''
  A partir du nombre d'abeilles touchées, on peut déterminer le nombre d'abeilles mortes.
 **On utilisera le paramètre letalite qui correspond à la capacité du pesticide à tuer une abeille, le taux_res et le taux_nres qui correspondent aux taux de resitance ou non au pesticides.**
  D'après notre definition la létalité est la proportion d'abeilles tuées sur la population d'abeilles non résistantes. En effet, la poûlation résistantes ne peut pas être tuées car elle resiste face au pesticide. En revanche la proportion de population non resistante va elle être sensible aux pesticides et mourir ou resister. 
  C'est ce que l'on definit dans notres algorithme: 
  
 ''' 
 def abeilles_mortes(touchees,taux_res,taux_nres):
    res_mortes,nres_mortes=touchees
    res_mortes=res_mortes*letalite*(1-taux_res)*(randrange(9000,11000)/10000)
    nres_mortes=nres_mortes*letalite*(1-taux_nres)*(randrange(9000,11000)/10000)
    return(int(res_mortes),int(nres_mortes))
    
 '''
 
 
 
 
 
 
 
 
  '''
  res_t,nres_t=abeilles_touchees(nb_ouvrieres,alpha)
  res_m,nres_m=abeilles_mortes((res_t,nres_t),taux_res,taux_nres)
  taux_res,taux_nres=evolution_res(res_t+nres_t,res_m+nres_m,taux_res,taux_nres)
  alpha=MaJ_alpha(alpha,res_m,nres_m,nb_ouvrieres)
  '''

<a name="Bibliographie"/>
# Bibliographie :honeybee: 

- http://www.lenombredor.free.fr/nature.htm
- https://fr.wikipedia.org/wiki/Abeille
- https://fr.wikipedia.org/wiki/Suite_de_Fibonacci
- https://www.futura-sciences.com/planete/dossiers/zoologie-abeilles-accueillir-ruche-chez-soi-976/page/10/
- https://catoire-fantasque.be/cycle-de-developpement-abeilles/
- http://www.apivet.eu/2009/07/le-cycle-dune-colonie-dabeille-et-les-influences-externes.html

