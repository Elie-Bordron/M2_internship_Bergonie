# oncoscanR
- Arm-level Alteration  
    Dans cet ordre: 
    - lit les segments d'altération du fichier segments.txt
    - fusionne les segments de même CN distants de moins de 300Kbp.
    - supprime les segments de moins de 300Kbp 
    - si 80% d'un bras présente la même altération, ce bras est indiqué comme altéré (GAIN/LOSS/AMP/LOH).
- Score LST
    - voir cahier

# CGHcall
- fichiers qui parlent de ce package:
    article: CGHcall_article.pdf
    description des fonctions du package: CGHcall_functions.pdf
    reference manual: CGHcall_Reference_Manual__usemewiththescript.pdf
    R script à utiliser avec le manuel: CGHcall.R
- les auteurs de la comparaison de 6 outils disent avoir créé cghcall*, mais ne le rendent disponible nulle part. Un fichier Tex constitue leur "additional material", par contre. CGHcall est concu pour du aCGH. Il utilise les informations de breakpoint (par l'algo CBS, typiquement), ainsi que "plusieurs concepts biologiques ignorés par les autres algorithmes" et classifie le LRR entre ref et tumeur en 5 états.
- *voir notes_on_articles.md pour les infos sur l'article.*\
L'article ne décrit pas très bien comment le package fonctionne. il parle surtout du mixture model utilisé, il faudrait que je prenne un peu de temps pour comprendre mieux ce qu'est et comment fonctionne un mm. En attendant, je peux avoir une meilleure vue d'ensemble du package en regardant les fonctions utilisées dans le workflow (normalisation...).

-> je lis CGHcall_Reference_Manual__usemewiththescript.pdf en parallèle de CGHcall.R .
Le pipeline est le suivant: 
## Input
un tableau / fichier texte:
- les lignes sont des sondes
- les colonnes sont [voir https://www.rdocumentation.org/packages/CGHbase/versions/1.32.0/topics/make_cghRaw]
passe forcément par la fonction make_cghRaw.

## Output
voir fin du pipeline pour les résultats bruts. 
Différents plots peuvent également être produits:
- Les plots par échantillon présentent des barres vertes et rouges aux endroits où des aberrations sont détectées. Ces dernières correspondent à la probabilité d'avoir un réel gain/perte à cet endroit: si la barre dépasse les 50%, l'altération est considérée réelle.
- Les Frequency plots montrent la fréquence de gains / loss sur tous les échantillons.
- Les Summary plots sont des frequency plots un peu plus sophistiqués: ils pondèrent 


## Pipeline
``Wilting <- make_cghRaw(Wilting)``
Convertit un dataframe/fichier texte en objet cghRaw.

``cghdata <- preprocess(Wilting, maxmiss=30, nchrom=22)``
Applique différents procédés de préprocess nécessaires pour la suite. maxmiss supprime les lignes ayant des NA dans 30% de leurs échantillons. nchrom indique les chromosomes à garder, les autres sont supprimés.

``norm.cghdata <- normalize(cghdata, method="median", smoothOutliers=TRUE)``
Normalisation très basique selon la médiane ou le mode; smoothing des outliers ; possible correction si la proportion de cellules tumorales n'est pas 100%.


`norm.cghdata <- norm.cghdata[,1:2] # To save time we will limit our analysis to the first two samples from here on.`
``seg.cghdata <- segmentData(norm.cghdata, method="DNAcopy",undo.splits="sdundo",undo.SD=3, clen=10, relSDlong=5)``

Apply DNAcopy algorithm that performs segmentation. Cette fonction est un wrapper autour de DNAcopy et permet de défaire les "splits" différemment selon si le segment est long ou court, en tre autres. voir cahier pour plus de précisions.

`postseg.cghdata <- postsegnormalize(seg.cghdata)`
faire une normalisation après la segmentation permet de mieux définir le zéro.


``tumor.prop <- c(0.75, 0.9) # one value per sample. proportion of contamination by healthy cells``
``result <- CGHcall(postseg.cghdata,nclass=5,cellularity=tumor.prop)``
L'étape de calling. Le mixture model est créé et utilisé ici. On indique la cellularité dans le vecteur tumor.prop pour qu'elle soit prise en compte (car oui, ça se fait dans cete étape). Le nombre de classes qu'on veut en sortie doit également être précisé.

`result <- ExpandCGHcall(result,postseg.cghdata)`
Pour convertir le résultat en un objet CGHcall. pour voir l'output, lancer le script CGHcall.R: on récupère des tableaux de la forme suivante:
```
            sample1 sample2
probe1      1       1
probe2      1       1
probe3      1       1
probe4      1       1
probe5      1       1
probe6      1       1
```
Ici, la variable est le nombre de copies qui a été called. On a 2 échantillons parce qu'on peut lancer CGHcall sur plusieurs échantillons. On peut récupérer de la même façon le CN brut, ou un tableau de segmentation.

## après la réunion
puis-je voir la distribution gaussienne de toutes les données? oui, voir logratios_for_hist dans CGHcall.R . ça plot une unique courbe de gauss; peut-être qu'avec de vraies données ce serait plus parlant.