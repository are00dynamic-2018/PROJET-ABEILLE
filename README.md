
![image](https://www.espritsante.com/images/0248103001340357281.jpg)

https://are00dynamic-2018.github.io/PROJET-ABEILLE/

# Table des matières 
- [Membre du groupe](#membres)  
- [Description du projet ](#sujet)
- [Modélisations mathématiques de la reproduction des abeilles](#doc_ref)  
  - [Suite Fibonacci ](#Fibonacci)

- [Paramètres Pesticides](#ParamètresPest) 
- [Paramètres Abeilles](#ParamètresAbeilles) 

- [Bibliographie](#Bibliographie)

<a name="membres"/>
# Membres du groupe :

**LANOUNI sofia**  

**COHEN-SOLAL Roy**

**MALASIGNE Clément**

**LUBEK Lazare** 

<a name="sujet" />
# Description du projet:

  Notre projet consiste à modéliser les effets de pesticides sur une colonie d'abeilles durant plusieurs années. Lors de notre étude, nous allons voir comment modéliser la reproduction des abeilles et notamment l'évolution de la ponte d'oeufs. Ainsi lorsque l'on va simuler l'action du pesticide sur plusieurs colonies, nous allons pouvoir changer certain paramètres de reproduction et suivre l'évolution de la population d'abeilles

<a name="doc_ref"/>
# Modélisations mathématiques de la reproduction des abeilles:

  Dans une colonie d'abeilles, il y a entre 20 000 et 90 000 abeilles. 
  
  Chez les abeilles, la reine décide de féconder ou non les oeufs à partir du sperme emmagasiné des mois, voire des années auparavant.Sachant que les règles de reproduction chez les abeilles sont telles que  l'abeille femelle a un père et une mère(la reine) tandis que l'abeille male n'a qu'une mere(la rien). on peut en déduire une loi mathématique.


![image](http://www.lenombredor.free.fr/nature_fichiers/image021.jpg)

  <a name="Fibonacci"/>
### Fibonacci
    
  En effet , on remarque que la population d'une ruche peut être modelisée par la suite de _**Fibonacci**._ étant donné qu'à chaque génération , les nombres de femelles et de mâles sont deux nombres consécutifs de cette suite. On peut démontrer mathématiquement que la limite du rapport entre F_(n+1) et F_n est le nombre d'or (~1,618).On comprend donc que le rapport entre les mâle et femelles est environ égale au nombre d'or. Et étant donné qu'on parle d'une ruche qui possède au minimum 10 000 abeilles (soit 4000 mâles et 6000 femelles environ) , c'est à dire environ F_19 et F_20 le rapport entre les deux est assez proche pour approximer dans notre modèle, l'évolution de la population en se servant du coefficient du nombre d'or plutôt que de definir la suite en elle-même qui demanderait beaucoup plus de puissance à notre ordinateur.

  - Nous avons en compte le fait qu'après la ponte , les oeufs éclosent au bout de 3 semaines à peu près.
  - Nous avons en compte la mort des abeilles qui vient ,après éclosion, environ 7 semaines (en y appliquant un facteur aléatoire) et on a pris en compte la mort d'abeilles par des prédateurs avec aussi un facteur aléatoire qui sera plus élevé pour les ouvrières car ce sont elles qui sortent de la ruche et donc qui ont le plus de risques de mourrir.

     (Notes:la durée de vie varie aussi en fonction de la période en réalité pour les ouvrières 13 à 38 jours en été , 30 à 60 jours au printemps , environ 140 jours en hiver et pour les mâles de 21 à 32 jours au printemps et le début de l’été et jusqu’à 90 jours à la fin de l’été et en automne ) 
- On sait que la ponte des oeufs dépend aussi de la période de l'année , on s'est donc basé sur une courbe empirique de celle-ci pour trouver une fonction l'approchant en choisissant d'observer l'évolution d'une population d'abeilles de Provence On a donc approximé la courbe des pontes en fonction de la période de l'année par un polynôme de degré 4.

![image](http://nicolas.blogs.com/.a/6a00d83455b58069e20115721bba3b970b-pi)
 '''
 
 #NOMBRE D OEUFS PAR SEMAINE

def nb_oeuf_par_semaine1(k):
    #Avant 14 semaines
    if k<=14:
        nb_oeufs=int((-2.6064*k**3)+(33.363*k**2)+(22.356*k)+1000)
    else:
    #Apres 14 semaines
        nb_oeufs=int((0.3906*k**4)+(-31.539*k**3)+(929*k**2)+(-11826*k)+55718)
        
    return(7*nb_oeufs)
    
    '''
        
        
- Nous avons crée des fonctions qui permettent d'observer le comportement des abeilles sur plusieurs années.

Après avoir fini de modéliser la population il est temps de s'intéresser aux effets des pesticides sur celle-ci:
On définit 3 paramètres pour le pesticide et 3 paramètre pour les abeilles que l'on compte faire varier dans nos modèles,  à savoir :

<a name="ParamètresPest"/>
## Paramètres pesticides

1) la létalité = la capacité du pesticide à tuer l'abeille

2) l'adaptation = la capacité des abeilles à resister au pesticide

3) la portée = la capacité à atteindre une abeille avec le pesticide

<a name="ParamètresAbeilles"/>
## Paramètres Abeilles

1) Proportion d'abeilles resistantes
2) Taux de restistance d'abeilles resistantes
3) Taux de resistance d'abeilles non resistantes


Il s'agira de définir une fonction qui renverra le nombre d'abeilles touchées qui prendra en compte la portée ainsi qu'un paramètre aléatoire , on distinguinguera les abeilles touchées resistantes et celles qui ne sont pas reistantes.
A partir de ces abeilles touchées , on prélèvera un certain nombre d'abeilles qui seront effectivement mortes ,chez les resistantes qui depend de leur taux de resistance et idem pour les non resistantes en y faisant intervenir la létalité ainsi qu'un paramètre aléatoire. 
Nous testerons ensuite la proportion des abeilles mortes par rapport aux abeilles touchées et celui-ci nous indiquera si les abeilles ont resistées ou pas ,en distinguant toujours les abeilles resistantes des non resistantes. En effet , si cette proportion est est  inférieur au seuil d'adaptation on en déduit que les abeilles ont dévellopés une resistance et donc le taux de resistance des abeilles.


<a name="Bibliographie"/>
# Bibliographie

- http://www.lenombredor.free.fr/nature.htm
- https://fr.wikipedia.org/wiki/Abeille
- https://fr.wikipedia.org/wiki/Suite_de_Fibonacci
- https://www.futura-sciences.com/planete/dossiers/zoologie-abeilles-accueillir-ruche-chez-soi-976/page/10/
- https://catoire-fantasque.be/cycle-de-developpement-abeilles/
- http://www.apivet.eu/2009/07/le-cycle-dune-colonie-dabeille-et-les-influences-externes.html

