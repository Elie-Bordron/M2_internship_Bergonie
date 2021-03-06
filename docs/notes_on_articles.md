
# <span style="color:#ff9999">Automated Detection of Arm-Level Alterations for Individual Cancer Patients in the Clinical Setting
2021_Christinat_HRD_Oncoscan.pdf
Article d'oncoscanR


Copy number alterations, a genetic event, promotes tumor development. these events are used as predictive biomarkers in clinical care. they are roughly classified as arm-level or focal. genome-wide techniques exist to classify arm-level ones, but challenges exist:
- How to define an arm-level alteration? there is no consensus on it.
- there is a lack of tools to compute them for individual patients.
To answer this, using OncoScan, clinical samples were analyzed. The results indicate respectively that:
- sum of altered segments was a better indicator than longest segment to define an arm-level alteration, BUT Some of the discordances ultimately were attributed to human error.
- a new software has been made publicly available in routine analyses (https://doi.org/10.1016/j.jmoldx.2021.08.003)

Les altérations arm-level sont plus longues que les focales: elles contiennent des centaines de gènes. Leur effet sur les phénotypes de cancer est connu, mais il est compliqué, quand ce n'est pas impossible, de lier cet effet à des gènes individuels.
Cependant, les avancées technologiques récentes en génomique offrent des indications sur la valeur prédictive des arm-level alterations: on associe par exemple la perte de tels bras de tels chromosomes à un critère principal de diagnostic pour les oligodendrogliomes. Il y a plusieurs autres exemples de ça, également pour le pronostic. D'autre part,  l'aneuploidie (le fait pour une cellule d'avoir un nombre anormal de chromosomes, donc de ne pas être euploide) a un intérêt dans le pronostic mais n'est pas toujours utilisé dans la prise de décision thérapeutique.
Certaines méthodes utilisent du FFPE mais ces manips sont sujettes à dégrader l'ADN. la technique Oncoscan est conçue et optimisée pour le FFPE. D'autre part, GISTIC est une méthode largement utilisée pour estimer les Copy Number Alterations (CNA).
Enfin, la définition d'arm-level varie dans les exemples présents dans la littérature. Le seuil d'altération d'un bras chromosomique à partir duquel on ne considère plus l'altération comme focale mais comme arm-level varie au cas par cas.
Cette étude vise à définir précisément les arm-level alterations qui peuvent être appliquées dans un contexte clinique.

En utilisant la technique Oncoscan sur des échantillons FFPE, des .CEL ont été produits, puis convertis en .OSCHP (OncoScan array data) qui ont été analysés à l'aide du logiciel Chromosome Analysis Suite (ChAS) avec le génome de référence: hg19. Les résultats ont été évalués manuellement. Précision: les segments de moins de 50 marqueurs ou moins de 50 Kbp ont été ignorés.

## 2eme lecture
Deux techniques ont été suivies pour définir une ALA: SoS (sum of altered segments) et LS (Longest Segment). -> diviser la longueur par la longueur du bras , si la PAA (proportion of Arm Altered) est de + de 90%, le bras chromosomique est caractérisé comme altéré.
Le seuil de 90% a été évalué par rapport à 80, 85 et 95; les auteurs ont conclu qu'il offrait le meilleur compromis.

Un filtrage (seuls les segments de longueur supérieure à X sont gardés) et un smoothing (les segments de même CN distants de moins de X bp sont fusionnés) sont appliqués (X=300Kbp) aux données avant le calcul de la PAA.
300kbp a été choisi car:
1. c'est la résolution d'OncoScan
2. c'est la valeur qui donne le plus de robustesse comparé à 0bp, 1Mbp et 3Mbp.



## Estimation of Percentage Arm Alteration
les données de nombre de copies ont été utilisées pour  détecter des arm-level alterations (ALA), puis ont été processées par un script R


# <span style="color:#ff9999">Uterine smooth muscle tumor analysis by comparative genomic hybridization: a useful diagnostic tool in challenging lesions
these_S.CROCE.pdf    (Thèse de Sabrina)

## résumé rapide: 
the diagnosis of STUMP tumors is often challenging. The authors proposed to test the hypothesis that GI could split those tumors in two groups: benign and malignant. A study was conducted, using a threshold of 10 to classify the STUMP.
In conclusion, genomic index is a useful technique to classify these tumors. more specifically, genomic index divides problematic uterine smooth muscle lesions into leiomyomas and leiomyosarcomas.

## discussion 
La classification histologique basée sur les "three features" permet généralement de caractériser les TMLU (tumeurs du muscle lisse utérin) en bénignes ou malignes.  
Cependant, dans certains cas, l'interprétation de ces critères est trop subjective , et le rôle de facteurs externes (traitement endocrinien...) peut compliquer le diagnostic.  
Le terme STUMP désigne les TMLU dont le potentiel malignant est incertain. Il s'agit donc d'un terme fourre-tout qui ne désigne pas une entité biologique mais une catégorie arbitraire, c'est pourquoi l'utilisation de ce terme est à limiter quand c'est possible.
Les auteurs font l'hypothèse suivante: Le comportement clinique de tumeurs du muscle lisse utérin est *fortement* lié avec des profils génomiques spécifiques (pouvant être caractérisés par le GI).
Dans cete étude, une trentaine de tumeurs du muscle lisse utérin pour lesquelles la caractérisation ne fut pas concluante ont été analysées.  

Pour tester la pertinence de l'analyse du profil génomique, les auteurs ont d'abord analysé des lésions bénignes (leiomyomes) et malignantes (leiomyosarcomes) qui ont été caractérisées de manière très concluante.
La correspondance entre l'index génomique et le comportement clinique était parfaite; L'analyse du profil génomique pour caractériser ces tumeurs est donc pertinente.

Le GI a ainsi été utilisé pour séparer les Smooth muscle uterine tumors *problématiques* en 2 groupes autour de 10.
Le premier groupe, GI<10 , n'avait pas de métastase et se comportait comme un leiomyome (bénin, donc). Le second groupe, GI>10, consistait en tumeurs ayant une récurrence qui s'approche de celle des Leiomyosarcomes.
Le GI est donc utile pour pronostiquer la survie sans métastases. Le GI n'est pas concluant pour pronostiquer la survie globale, peut-être parce que dans l'étude, plus d'évènements de récurrence métastatique que de décès sont survenus.
[S'ensuit un paragraphe qui relativise ce qu'on vient de dire, et parle successivement des façons d'améliorer le pouvoir pronostic du GI, des biais de l'étude, des paramètres morpho utilisés pour caractériser les LeioMyoSarcomes et pourquoi certains sont à utiliser avec précaution (le mitotic count, effectué sur des cellules Ischémiques (donc ayant des noyaux tachetés pouvant passer pour des mitoses), peut être très différent selon l'observateur) et comment les auteurs ont coutourné ces problèmes (seules des régions avec des cellules en fuseau ont été utilisées)]
Les auteurs indiquent ce qui a été fait auparavant: utiliser l'analyse du profil génomique comme outil de diagnostic n'a jamais été fait.

Ils définissent donc ici le seuil de 10 du GI permettant de classifier les STUMPs en bénins et malins, respectivement proches de leiomyomes et leiomyosarcomes.

Le terme de STUMP se mélange, dans la littérature, à d'autres termes pour définir des tumeurs parfois différentes. En ce sens, il peut être complexe de comparer plusieurs études sur l'évolution clinique des STUMPs. Une méta-analyse qui a pris en compte ces biais a conclu que le taux de récurrence pour ces tumeurs allait de 10.4 à 26.7%.

Malgré le fait que le terme STUMP ne désigne pas un type de tumeurs en particulier, l'analyse du profil génomique (donc l'utilisation du GI) est un outil pertinent et puissant pour assister le diagnostic des lésions du muscle lisse utérin difficiles à caractériser.

Contrairement aux LMS ("high-grade"), les STUMP sont généralement des tumeurs plus "low-grade", car la récurrence est souvent retardée et l'évolution clinique prolongée (selon la biblio). Cela corrobore ce que les auteurs ont trouvé.

Le GI permet de classer les STUMPs en LM et LMS, mais cela ajoute des cas indolents au spectre des LMS, qui sont conventionnellement plus agressifs.

***En conclusion, L'analyse de profils génomiques par array-CGH est un outil de diagnostic innovant (en 2015) complémentaire à l'approche morphologique, et est pertinent pour classifier les tumeurs du muscle lisse utérin difficiles à caractériser.***





# <span style="color:#ff9999">The Nanocind Signature Is an Independent Prognosticator of Recurrence and Death in Uterine Leiomyosarcomas
Nanocind_signature_S._CROCE.pdf

Uterine leiomyosarcoma is an aggressive tumor responsible for a signiﬁcant proportion of uterine cancer–related deaths. Plus, using the FIGO staging system, it is currently impossible to predict the clinical outcome of stage I leiomyosarcomas. However, the authors published in 2010 a transcriptomic signature (67 genes related to chromosome biogenesis, mitosis control, and chromosome segregation), which has proven since its predicting efficiency over different cancer types. Plus, it has been successfully used with NanoCind (Nanostring) technology, which makes it usable routinely.
Uterine leiomyosarcoma were analyzed with the Nanocind signature. The process split the group in two groups. This result was validated.
In conclusion, the NanoCind signature is a powerful prognostic indicator that outperforms FIGO staging and the genomic index. Plus, GI is platform-dependent. 

Il est plusieurs fois fait mention de l'article [17] (`Croce S, Ducoulombier A, Ribeiro A, Lesluyes T, Noel JC, Amant F, et al. Genome profiling is an efficient tool to avoid the STUMP classification of uterine smooth muscle lesions: a comprehensive array-genomic hybridization analysis of 77 tumors. Mod Pathol 2018;31:816–28.`)de la biblio en parlant du GI. lire cet article.

# <span style="color:#ff9999"> A faster circular binary segmentation algorithm for the analysis of array CGH data
DNAcopy__segmentation_algo_for_CGH_data.pdf

## abstract
la technologie array-CGH recense le nombre de copies de milliers de sites d'un génome. l'algorithme CBS développé dans cet article permet de segmenter le génome en régions de même nombre de copies. Le nombre d'opérations est O(N²) avec N = nombre de sondes. L'approche 100% permutation atteint donc ses limites sur les arrays récents qui peuvent contenir des dizaines de milliers de sondes=marqueurs. Les auteurs ont développé une approche hybride pour passer à un temps linéaire. Mais comment procède-t-il?

## Methods
l'algo prend un chromosome, et trouve récursivement des breakpoint dans chaque segment. il arrete quand aucun break point ne peut être trouvé. De manière générale, un test de permutation est utilisé.


Il peut être utilisé dans R à l'aide du package DNAcopy.

# <span style="color:#ff9999"> Copy number aberrations from Affymetrix SNP 6.0 genotyping data—how accurate are commonly used prediction approaches ?

Copy_number_aberrations_from_Affymetrix_SNP.pdf

Les aberrations du nombre de copies (CNA) jouent un rôle important dans la recherche sur le cancer. Un défi dans la quantification des CNA est l'effet de variables confondantes. pour traiter de ce problème, Les auteurs ont comparé les différents algorithmes d'identification de CNA sur les données d'Affymetrix SNP 6.0 genotyping.
Conclusion:


# <span style="color:#ff9999"> A statistical approach for detecting genomic aberrations in heterogeneous tumor samples from single nucleotide polymorphism genotyping data
oncoSNP.pdf

-> je pensais qu'oncoSNP était dédié spécifiquement à oncoscan / Affymetrix SNP, mais il n'en est rien :/
OncoSNP semble être écrit en matlab. à `https://sites.google.com/site/oncosnp/user-guide/downloads`, j'apprends que l'outil est disponible exclusivement sous linux en 64 bit.

# <span style="color:#ff9999"> CGHcall: calling aberrations for array CGH tumor profiles

CGHcall_article.pdf

## Intro
 définition de l'array-CGH; définition du calling (transformer les logs ratio en copy number, donc caractériser en gain/loss/amp(/loh)); les algos de segmentation classiques détectent les breakpoints et les levels mais ne font pas directement de calling: c'est problématique quand on a beaucoup de bp et de levels différents. 
 De nouveaux algos sont basés sur des mesures de confidence (P-val, False Discovery Rate). Comme ils sont basés sur des statistiques, le niveau de CN "normal" a un statut différent des loss et gain, ce qui limite le nombre d'aberrations lors du calling.  Cependant, de l'expérience des auteurs, les biologistes préfèrent les approches plus "state-neutral" pour obtenir la meilleure classification entre 3 ou 4 états. _Utiliser un mixture model permet cela_ !  
 CGHcall combine les points forts des méthodes développées dans le passé:
 1. la segmentation de DNAcopy (CBS, donc) est utilisée. C'est l'un des meilleurs algos dans son domaine.
 2. les loss, gain et normal states ne peuvent être anticipés donc CGHcall utilise des effets aléatoires (VOIR L'ARTICLE CGHcall_random_effects.pdf)
 3. les résultats de segmentation sont combinés avec un Mixture model (VOIR CGHcall_mixturemodel_picard.pdf) afin d'obtenir la classification par segment la plus réaliste possible (plutôt que par individu(?)).
De plus:
- six états (double deletion, single deletion, normal, gain, double gain and amplification) au lieu des trois conventionels (loss, normal, gain (and amp)) sont utilisés; ce qui a une plus grande correspondance avec la réalité biologique.
- Ils utilisent un mixture model combiné aux résultats de segmentation basé sur le travail de  `CGHcall_mixturemodel_picard.pdf`

## Methods
Je ne comprends pas le lien entre ces phrases:
```
Pb récurrent des données array-CGH: Les sondes d'un chromosome sont souvent très corrélées avec leurs voisines.
CGHcall reconnait que les algos de segmentation sont efficaces pour cette tâche (trouver des breakpoints). 
Les clones d'un même segment appartiennent tous forcément au même état.
```
Passons, voici la suite:
Ils ont fitté un modèle (de mixture, donc) en utilisant les données LR normalisées. une courbe de gauss représente les données de chaque segment. Les sondes sont classées dans 

## Results
- "CGHcall outperformed the other methods for this setting (SEE SUPPLEMENTARY INFORMATION)." `<---voir ce que ça veut dire`
- "Nous illustrons l'utilisation de notre modèle à 6 états à la place du modèle plus courant à 3 états." -> ils ont fait tourner les 2 modèles sur les mêmes données, et le modèle 6-states trouve des résultats corroborés par le travail visuel d'un expert et par une analyse FISH, résultats qui ne sont pas trouvés par le modèle à 3 copies. 
- ils travaillent sur un mixture model dit (1), et un mixture model dit alternatif. 
    - les mixture proportions de mm1 sont estimées à partir de toutes les données, ce qui peut entraîner un problème. Lequel? comme des chromosomes(ou bras) peuvent être non altérés de manière récurrente, ils tirent vers le bas la probabilité (calculée sur tous les chromosomes) d'un chromosome altéré d'être caractérisé comme tel. Pour résoudre cela, le modèle alternatif est construit en considérant le bras chromosomique comme niveau de résolution. Pourquoi? Parce que :
        1. "Cela limite le nombre de paramètres à estimer"
        2. On ne peut pas considérer les segments comme une entité commune, car leur longueur diffère entre plusieurs échantillons.
        3. Beaucoup d'événements d'aberration surviennent au niveau des bras.
    - mm1 fait du calling par segment, et mmalt fait du calling par bras. Au niveau du modèle de mixture, ça veut dire qu'il cherche à classifier les données en bras plutôt qu'en segments.

## discussion
- Le modèle de mélange hiérarchique permet la variabilité au sein des niveaux de gain ou de perte, ce qui permet de tenir compte des effets (inconnus) qui font que les aberrations se traduisent par des niveaux de log-ratio non constants.
- CGHcall a une option permettant de corriger les données brutes pour différentes contaminations par des cellules saines



Supplementary information: `CGHcallSupplement_vdWiel.pdf`
"Summary Plot is a function which produced overview helps to determine the aberrated chromosomal regions that are recurrent."

Supplementary information's article 7: ``CGHcall__rare_ampliconsxxx.pdf`` 


# <span style="color:#ff9999"> A Segmentation-Clustering problem for the analysis of array CGH data
CGHcall_mixturemodel_picard.pdf      

## Intro
Les techniques d' array-CGH produisent des résultats pouvant être représentés par une succession de segments. Les techniques de segmentation sont tout naturellement utilisées pour les traiter, mais elles ne permettent pas de donner un statut biologique aux segments détectés.  
Les auteurs proposent un nouveau model pour répondre à ça, qui combine un modèle de seg avec un mixture model. Ils présentent (aussi!) un algorithme hybride qui permet d'estimer les paramètres par maximum likelihood. Cet algo est basé sur le dynamic programming (voir wkp) et l'algorithme expectation–maximization.

## 1 - A new model for the segmentation-clustering problem
Les données de log ratio peuvent être séparées en segments. On considère qu'au sein d'un segment (donc entre deux break-points), la moyenne et l'écart-type sont constants.
En plus de cette organisation spatiale, les données peuvent être réparties dans des clusters, et l'approche du modèle de mélange est choisie pour résoudre ce problème.
On considère ainsi que les données sont réparties en un nombre P de clusters ayant chacun un poids, leur somme vaut 1. Tous ces poids constituent les "mixing proportions", qui représentent la probabilité *a priori* qu'un segment appartienne au cluster P. À l'inverse, la probabilité *a posteriori* du même événement sachant que yk (la valeur de log ratio) a été observée est [voir article, je ne peux pas l'expliquer. Ce qu'il faut retenir est qu'elle dépend de yk.]
Contrairement aux modèles de mélange conventionnels, où on obtient des informations sur les données individuelles (les sondes dans notre cas), ce modèle se concentre sur l'appartenance des segments à un cluster.


## 2 - An hybrid algorithm combining the EM algorithm and Dynamic Programming
voir notes.

voir aussi cahier à 17/03. ou https://medium.com/@chloebee/the-em-algorithm-explained-52182dbb19d9 pour compléter


## Discussion
Cette partie n'est pas claire. voir plutôt les méthodes pour comprendre pk ils utilisent un mm pour faire de la segmentation.




# <span style="color:#ff9999"> DNAcopy: A Package for Analyzing DNA Copy Data
DNAcopy_documentation.pdf

Cet outil sert à identifier les régions où un gain / une perte de nombre de copies survient, et met à disposition une fonction pour faire différents plots.

smoothing outliers: si une donnée individuelle est trop éloignée des autres, l'aplatir pour qu'elle rejoigne les autres sondes proches d'elle.
puis, segmenter et plotter.

# <span style="color:#ff9999"> Mitotic Checkpoints and Chromosome Instability Are Strong Predictors of Clinical Outcome in Gastrointestinal Stromal Tumors
Definition_GI.pdf

L'article où le GI est défini.

## abstract
L'importance des mutations impliquées dans l'oncogenèse des GISTs (GastroIntestinal Stromal Tumors) est connue, à l'inverse de l'origine des métastases des GISTs. Les auteurs ont établi préalablement la signature CINSARC (gene expression) liée à la complexité génomique et se sont demandés si elle pouvait prédire l'évolution des GISTs.  
Les résultats valident que CINSARC prédit l'évolution en métastases. La perte de certains gènes a été identifiée comme causale de la forte valeur de CINSARC, de réarrangement chromosomique, et ultimement de métastases. à partir de ces conclusions, les auteurs ont établi un index génomique prenant en compte le nombre et le type d'altérations de nombre de copies d'ADN. Cet index a un fort pouvoir pronostic pour les GISTs.  
En conclusion, les auteurs proposent qu'un GI élevé obtenu par CGH à partir d'échantillons FFPE pourrait identifier les patients classés en "risque intermédiaire" par la classification AFIP qui pourraient bénéficier d'une thérapie à l'imatinib.
```
La signature CINSARC = on regarde quels gènes parmi les 67 choisis sont inactivés, et on en déduit l'agressivité du cancer. Mais quel est le mécanisme qui se cache derrière ça? -> le GI permet d'évaluer ce mécanisme, à savoir l'altération du nombre de copies.
au final, le GI, CINSARC, et AURKA (l'expression du gène AURKA pour être précis) sont plus performants qu' AFIP.
```

## Introduction
Qu'est-ce qu'un GIST
Quelles altérations un GIST présente généralement 
Cetains patients rechutent après traitement, et cette rechute pourrait être prévenue avec une thérapie à base d'imatinib. L'évaluation précise du risque métastatique serait donc très utile, et est désirable.  
Plusieurs critères *pathologiques* ont été proposés pour prédire le devenir des patients avec GIST: [...].
Ces critères définissent des groupes, mais avec une large zone grise, où le risque de métastase est mal défini. Il y a donc un besoin de mieux comprendre les GIST pour mieux identifier les biomarqueurs liés aux évolutions aggressives.  
Pour répondre à cela, des études d'expression de gènes et de nombre de copies d'ADN ont été menées, mais sans que les résultats ne soient concluants. Il a été montré que le nombre et la complexité des réarrangements génomiques  augmente avec le stage tumoral, mais aucun seuil n'a été défini.  
La signature CINSARC a été utilisée pour caractériser 67 GISTs. Afin d'identifier les mécanismes qui conduisent à un score CINSARC élevé, des analyses de nombre de copies d'ADN et d'expression génomique ont été menées sur le génome entier.  
## resultats
Le profil CGH des tumeurs n'évoluant pas en métastases présente peu de pertes ou de gains (surtout des chr entiers). à l'inverse, les tumeurs évoluant en métastases présentent plus d'altérations segmentaires.
"We therefore decided to test whether genome complexity could predict metastatic outcome" ->

## discussion
AURKA, CINSARC et le GI sont de meilleurs prédicteurs du devenir d'un GIST que le gold sandard, la classification AFIP. Utiliser largement AURKA serait un pas en avant dans la gestion des GISTs, mais son application clinique est limitée par la qualité de l'ARNm extrait d'échantillons FFPE. La CGH est déjà largement utilisée en routine, et est applicable au FFPE. Le GI, déterminé à partir de la CGH, a un pouvoir prédictif proche d'AURKA. Ainsi, le GI est potentiellement le meilleur outil de gestion de la thérapie Imatinib pour les patients GISTs à risque intermédiaire selon la classification AFIP.


# <span style="color:#ff9999"> Allele-specific copy number analysis of tumors (ASCAT)
ASCAT_article.pdf  
## abstract
Allele-specific Copy number pour tumeurs solides.; estimation de la`` ploidie et de la cellularité`` $voir fig 1 article, plus bas.$.
![fig 1 article ASCAT](docs_I_made/images/ASCAT_fig1.png "figure 1 article ASCAT")
L'agrégation des profils ASCAT obtenus rend compte de la ``distribution des fréquences génomiques de gains et pertes`` $voir fig S6 supplementary plus bas$, et permet de visualiser sur le génome entier les événements de`` nombre de copies neutre`` et de ``LOH``, $voir fig 4 article plus bas$, bien que l'API d'ASCAT ne semble pas présenter de fonction qui le permette (pour les CNNE).
![fig 6 suppl ASCAT](docs_I_made/images/ASCAT_suppl_fig6.png "fig 6 suppl ASCAT")
![fig 4 article ASCAT](docs_I_made/images/ASCAT_article_fig4.png "fig 4 article ASCAT")
Les profils ASCAT ($voir fig 1 article plus haut$)permettent également de construire une ``carte d'asymétrie allélique`` $voir fig 5 article$ (genome-wide map of allelic skewness), qui indique les loci où un allèle est perdu plus que l'autre.

## Intro
Les altérations génomiques sont facteurs clés de nombreux cancers. Les génomes tumoraux sont largement traités par CGH pour caractériser ces altérations, mais l'interprétation de telles données peut être difficile, majoritairement pour deux raisons:
- beaucoup de tumeurs dérivent d'un état diploide
- beaucoup de données contiennent des cellules de populations tumorales différentes et de cellules saines.
Ainsi, bien des travaux ont été limités à l'étude des gains et pertes et ne peuvent pas attribuer un nombre de copies correct à chaque locus du génome de référence.
Les auteurs présentent ainsi une analyse au niveau allélique du nombre de copies, qui prend en compte l'aneuploidie ainsi que l'infiltration de cellules saines.
Des profils ASCAT (allele specific CN analysis of Tumor) sur le génome entier sont ainsi obtenus. L'analyse de ces profils a révélé des différences (de gain, loss, LOH...)entre les sous-types de cancer du sein que les auteurs ont identifié.

## Discussion
La CGH est un standard pour traiter les aberrations chromosomales dans les tumeurs. Cependant, il reste difficile de déterminer des profils précis de nombre de copies.  
Certains facteurs compliquent également les choses: __les cellules tumorales sont souvent aneuploides (=nombre de copies altéré), et les échantillons contiennent souvent plusieurs populations de tumeurs + des cellules saines__ [^1]. De plus, la CGH n'indique pas quel allèle a été perdu/gagné, et elle ignore les aberrations de nombre de copies neutre. Soit dit en passant, les événements de nombre de copies neutre (copy number-neutral event (CNNE)) sont définis par un changement allélique (pour un SNP nativement hétérozygote) pour lequel le nombre de copies total ne diffère pas de la ploidie tumorale. Par exemple, imaginons une tumeur globalement quadriploide. à une position donnée, on a donc 2 copies de chaque allèle. un allèle perd une de ses copies tandis que le deuxième en gagne une de plus. on est alors à 1 et 3 copies pour les 2 allèles. Au total, on est bien en 4n, donc CN-neutral.
Bref, les technologies SNP promettent de résoudre ce problème. Cependant, pour que l'ASCN soit calculé à partir de données SNP, ces deux effets doivent être modélisés simultanément.
Les auteurs ont développé ASCAT, un outil pour inférer des profils ASCAT **à partir de données SNP** (mais les données OncoScan permettent aussi d'obtenir cette information).
![fig 3 article](docs_I_made/images/ASCAT_article_fig3.png "figure 1")
La distribution de la ploidie et de la proportion de cellules montre que la variabilité de ces paramètres peut être grande (voir figure 1) . Cela indique que les analyses qui ne les prennent pas en compte interprètent incorrectement 50% des cas.
Les profils ASCAT permettent de visualiser les événements LOH et copy number-neutral, événements non perceptibles par l'aCGH. Les auteurs ont observé que la distribution de LOH correspondait fortement avec la distribution des pertes, ce qui s'explique par le fait que de nombreuses pertes résultent également en LOH. D'autre part, des correspondances entre les pertes et les copy number-neutral events (CNNE) ont été observées. Cela indique que les fréquences de perte par allèle sont plus grandes qu'on ne l'imagine en travaillant avec des outils ne prenant pas en compte les CNNE. 
Voici pourquoi:
- ASCAT observe que loss & CNNE sont corrélés
- Or ASCAT prend en compte les CNNE.
- si il ne les prenait pas en compte, le nombre de CNNE trouvés passerait à 0. La corrélation indique que dès lors, le nombre de loss diminuerait.
- les outils ne prenant pas en compte les CNNE sont dans ce cas. On peut donc dire que ces outils sous-estiment largement le nombre réel de loss.
La correction pour la cellularité révèle que les tumeurs qui en ont le plus eu besoin ne présentent pas moins d'aberrations que les autres, seulement que ces aberrations étaient manquées par les approches qui ne tiennent pas compte de ce paramètre.
Une carte d'asymétrie allélique est également construite. Cette dernière indique les positions où un allèle est gagné préférentiellement à l'autre. on peut avoir cette carte avec les résultats d'oncoscanR. (oncoscan plutot ?)

## Matériel et Methodes
Affymetrix Oncoscan donne les valeurs de log ratio et de BAF pour chaque sonde. ASCAT estime le nombre de copies réel à partir de ces valeurs (et à partir d'autres paramètres comme la ``ploidie ψ (psi)`` et la ``cellularité ρ (rho)``). Psi et Rho compliquent l'analyse et sont souvent importants, donc exprimer logR et BAF en fonction de l'ASCN permet de prendre en compte ces deux paramètres. Cependant, ils doivent être estimés à partir des données pour chaque échantillon tumoral.  
*Ouvrons une parenthèse*  
Pour rendre la méthode plus robuste au bruit des données en input, les données logR et BAF sont pré-processées par `Allele-Specific Piecewise Constant Fitting (ASPCF)`, un algorithme de segmentation et de filtrage.  
*Fermons la parenthèse*
D'abord, les sondes homozygotes en germline $donc avec un BAF de 0 et 1 $ sont supprimées des données BAF, car elles n'apportent aucune information sur le CN total.
Ensuite, ASPCF fitte des fonctions constantes (y=k, donc des traits horizontaux) pour log Ratio et BAF simultanément, et force les change points des deux paramètres à arriver aux même emplacements sur le génome. Cela produit une segmentation du génome. Pour logR, une valeur est obtenue par segment. pour BAF, deux valeurs par segment , symétriques autour de 0.5, sont retournées (si les valeurs sont de 0.5, une seule valeur est retournée.)  

Ces valeurs sont ensuite envoyées à l'algorithme ASCAT, qui va estimer les paramètres de ploidie et cellularité, ainsi que les calls d'ASCN à partir de ces deux derniers. Mais comment ψ et ρ sont-ils estimés?  
Le vrai nombre de copies est un nombre entier non négatif. Sachant cela, ASCAT teste plusieurs valeurs de ψ et ρ en calculant pour chaque combinaison de ces paramètres l'ASCN, dans le but de trouver le plus proche d'un nombre entier non négatif. Voici comment les auteurs procèdent:
1. on fait varier ρ de (0.10, 0.11, . . ., 1.05) et ψ de (1.00, 1.05, . . ., 5.40).
2. Pour chaque combinaison possible de ψ et ρ, on fait:
    - Pour chaque SNP hétérozygote en germline (~~les SNP de copy number 2, donc~~ non, juste les SNP AB et pas AA ni BB nativement), on calcule la distance entre sa valeur de log ratio et un entier non négatif. la somme de ces valeurs est appelée d pour cette combinaison.
    - On calcule un score g correspondant à la probabilité que cette interprétation soit la bonne. g=100% si d=0, et g=0% si d diffère de 0.25 de nombres entiers non négatifs (0.25 est arbitraire). C'est-à-dire si d est trop grand.
3. chaque valeur de d est un minimum local. Pour filtrer les interprétations improbables, ASCAT exclut les minimums selon ces règles:
    - la ploidie moyenne sort du cadre défini par l'utilisateur par défaut, 1.2-4.8
    - le % de cellules tumorales est <20%
    - les solutions qui ne présentent aucun SNP avec 0 de copy number, pour quelque allele que ce soit (ce qui implique que cette solution n'a pas subi de perte d'allèle, ou bien que cette dernière a été contrebalancée par un gain sur le même allèle). Cela évite d'utiliser des tumeurs tétraploides pour définir le niveau diploide.
    - le score g moyen est inférieur à 80%.
4. Si une seule solution est restante, elle est retenue. Si plusieurs restent, celle qui a le meilleur score g est retenue. Pour la solution choisie, ASCAT retourne  la ``cellularité ρ`` et la ``ploidie ψ`` (cette dernière étant calculée (ne l'a-t-on pas estimée, déjà?) comme le nombre de copies moyen), le score g, le profil ASCAT, et un score de confiance pour chaque aberration trouvée.

On peut également parler du paramètre ``gamma (γ)``, qui dépend de la technologie utilisée. il correspond à la diminution de log Ratio pour une déletion d'un échantillon à 100% de cellules tumorales. `ASCN.ff() teste les valeurs de gamma de  0.35 à 0.95, avec un pas de 0.05` et produit des résultats pour chacune.

## mon récap de l'outil
Les techniques conventionnelles de CGH sont censées analyser les aberrations chromosomales, mais ne prennent pas en compte deux choses importantes:
- Les cellules tumorales sont rarement diploides
- les échantillons sont souvent constitués de différentes populations tumorales + de cellules saines
Ces deux facteurs rendent l'évaluation des aberrations chromosomales compliquée. ASCAT a été développé pour les prend en compte; les profils ASCAT que cet outil génère permettent de visualiser les événements de LOH et de nombre de copies neutre.




[^1]: déjà dit dans l'intro

<!-- # Comment insérer des figures
![alternatetext here](docs_I_made/images/CGHcall_voirslackpourlegende.png "title here")
[plotim]: docs_I_made\images\input_CGHcall.png
![input of CGHcall: a table with 8 columns][plotim]
 -->

# <span style="color:#ff9999"> rCGH: a comprehensive array-based genomic profile platform for precision medicine
rCGH_article.pdf

## Methods and implementation
Une analyse aCGH se décompose en 4 étapes distinctes:
- calcul des log ratios (sample VS reference; fait par ChAS entre autres)
- centralisation
- segmentation
- calling

La _centralisation_ implémentée par rCGH a été décrite dans `Commo,F. et al. (2015) Impact of centralization on aCGH-based genomic profiles for precision medicine in oncology. Ann. Oncol., 26, 582–588`.
Concrètement, le vecteur de log2 relative ratios est considéré comme un mélange de populations gaussiennes. Leurs proportions respectives et leurs paramètres sont estimés en utilisant l'algo EM. Par défaut, si une sous-population se révèle avoir un pic de densité supérieur à la moitié de la plus grande densité, elle est considérée comme représentant un nombre neutre de 2 copies. Sa moyenne est ensuite utilisée pour centraliser le profil. $voir figure S1 $

La _segmentation_ se base sur l'algorithme CBS de DNAcopy. ce que rCGH apporte de nouveau est qu'au lieu d'utiliser les paramètres arbitraires de DNAcopy, la valeur optimale de "undo.SD" est estimée à partir du bruit des données au travers de la médiane de la déviation absolue (MAD), un estimateur de bruit très utilisé [cf suppl. methods rCGH].

_En médecine de précision_, la prise de décision concernant l'orientation thérapeutique passe par l'analyse de gènes exploitables. Leur statut est déterminé par la longueur des altérations et les altérations de nombre de copies.


# <span style="color:#ff9999"> Common exon duplication in animals and its role in alternative splicing
Tandem_duplication_definition.pdf
*Ou la définition des duplications en tandem*
Une duplication en tandem concerne la présence en 2 exemplaires d'un exon au sein d'un gène. c'est-à-dire, l'allongement du chromosome. cf cahier 29/04
Le phénotype TDplus d'un échantillon consiste en des centaines de TDs de 1 à 10 Mb, qui causent au total la duplication de plus de 10% du génome.


# <span style="color:#ff9999"> Ovarian cancers harboring inactivating mutations in CDK12 display a distinct genomic instability pattern characterized by large tandem duplications
TDplus_popova.pdf

définition du score TDplus (td+)
Les (nombreuses) duplications en tandem (détectées en WGS) recouvrent souvent les gains de copies (détectés en SNP-array). christinat et al. se seraient-ils basés là-dessus pour utiliser seulement les gains de copie et déduire qu'il s'agit de TD ?
