
![image](https://www.espritsante.com/images/0248103001340357281.jpg)

https://are00dynamic-2018.github.io/PROJET-ABEILLE/

# Table des matières 
- [Membre du groupe](#membres)  
- [Description du projet ](#sujet)
- [Modélisations mathématiques de la reproduction des abeilles](#doc_ref)  
  - [Suite Fibonacci ](#Fibonacci)
  
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

  -On a pris en compte le fait qu'après la ponte , les oeufs éclosent au bout de 3 semaines à peu près.
  
  -On a pris en compte la mort des abeilles qui vient ,après éclosion, environ 7 semaines (en y appliquant un facteur aléatoire) et on a pris en compte la mort d'abeilles par des prédateurs avec aussi un facteur aléatoire qui sera plus élevé pour les ouvrières car ce sont elles qui sortent de la ruche et donc qui ont le plus de risques de mourrir.

(Notes:la durée de vie est varie aussi en fonction de la période en réalité pour les ouvrières 13 à 38 jours en été , 30 à 60 jours au printemps , environ 140 jours en hiver et pour les mâles de 21 à 32 jours au printemps et le début de l’été et jusqu’à 90 jours à la fin de l’été et en automne ) 



-On sait que la ponte des oeufs dépend aussi de la période de l'année , on s'est donc basé sur une courbe empirique de celle-ci pour trouver une fonction l'approchant en choisissant d'observer l'évolution d'une population d'abeilles de Provence On a donc approximé la courbe des pontes en fonction de la période de l'année par un polynôme de degré 4.

![image](http://nicolas.blogs.com/.a/6a00d83455b58069e20115721bba3b970b-pi)
  
<a name="Bibliographie"/>
# Bibliographie

http://www.lenombredor.free.fr/nature.htm
https://fr.wikipedia.org/wiki/Abeille
https://fr.wikipedia.org/wiki/Suite_de_Fibonacci
https://www.futura-sciences.com/planete/dossiers/zoologie-abeilles-accueillir-ruche-chez-soi-976/page/10/
https://catoire-fantasque.be/cycle-de-developpement-abeilles/
http://www.apivet.eu/2009/07/le-cycle-dune-colonie-dabeille-et-les-influences-externes.html

