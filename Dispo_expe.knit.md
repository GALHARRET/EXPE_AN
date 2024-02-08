::: {.cell}

:::


# Règle des 3R en expérimentation animale

- Elaborée en 1959, née de la réflexion éthique de Russel W. et Burch R., appliquée à l'expérimentation animale en Europe et Amérique du Nord.

- 3 R : Réduire, Remplacer, Raffiner.

## Réduire

Objectif : diminuer le nombre d'animaux utilisés en recherche :

- aux expériences absolument indispensables

- Ne pas répéter des expériences antérieures

Moyen : Rédiger un protocole expérimental avant l'expérience.

## Remplacer 

- Travailler sur des cellules ou des tissus (IN VITRO)

- Simuler numériquement (IN SILICO) les maladies et leur développement $\leadsto$ approche encore imparfaite vue la compléxité du fonctionnement biologique.

## Raffiner 

Optimiser l’expérimentation pour  réduire, supprimer ou soulager la douleur ou la détresse, et ainsi d’améliorer le bien-être des animaux utilisés. 

D'un point de vue statistique, le recours aux plans d'expérience va permettre de contribuer aux 3R.

# Dispositifs expérimentaux

Pour tester l'effet d'un traitement, on utilise des plans expérimentaux. Il s'agit d'un ensemble de méthodes pour

-   planifier des expériences,

-   analyser les résultats expérimentaux.

Ils peuvent s'appliquer dans de nombreux domaines (optimisation de produits, effet d'un traitement, changement de process, ...).

Un dispositif expérimental est un système dans lequel

-   On a une ou plusieurs réponses,

-   qui dépendent d'un certain nombre de facteurs (contrôlés ou non contrôlés).

L'objectif est d'intégrer (contrôler) le maximum de facteurs simultanément dans l'analyse et de réduire le "poids" des facteurs non contrôlés (résidu).

La précision des résultats obtenus dépendra du nombre d'expérience mais aussi de l'organisation de ces plans.

- Dans les précédents cours, les plans à mesures indépendantes ont été présentés, ici on va présenter deux autres types de plans qui serviront d'exemples dans la suite du cours.

- Les nouveaux modèles statistiques qui seront présentés par la suite seront adaptés pour traiter ce type de données.

De façon générique le traitement ou l'exposition désignera le (ou les) facteur(s) d'intérêt.


# Plans à mesures répétées

## Généralités

Dans un plan d'expérience à mesures répétées, un même sujet est mesuré sous chacun des niveaux d'un traitement.

Objectifs :

-   Meilleur contrôle des différences individuelles entre les sujets.

-   Réduire l'erreur expérimentale, la variabilité due aux différences individuelles.

Dans ce type de dispositif on considère souvent un facteur BETWEEN (inter-individuel) qui permet d'étudier si l'effet du traitement (ou de l'exposition) est différent selon le niveau de ce facteur BETWEEN.

# Etude longitudinale

- Suivi d'une population (ou d'un phénomène) dans le temps.

- Au moins deux périodes distinctes avec des sujets identiques.


## Exemple 

Une étude de l'école avait pour objectif de contrôler l'effet au cours du temps de 4 régimes alimentaires sur les paramètres biochimiques liés au contrôle de l'obésité.

On constitue 4 groupes de 6 rats : 

- un groupe contrôle (CC), 

- un groupe recevant un régime enrichi en lipide (LL), 

- un régime enrichi en fructose (FF) 

- un enrichi en lipide et fructose (LF).

Les variables réponses sont les suivantes :

-   Body Weigth ( poids corporel),

-   Masse grasse corporelle,

-   Glycémie,

-   Insulinémie,

-   Taux de cholestérol,

-   Taux de triglycérides,

-   Non Esterified Fatty Acid.

Toutes les données sont mesurées au bout d'une semaine (Week1) puis de 11 (Week11). 

Les données sont disponibles ici : [data1](data1.xlsx)

Le plan d'expérience peut être résumé par la figure suivante :

![figure 1](images/plan1.png)

Un extrait des données recueillies :

On étudie


::: {.cell}

```{.r .cell-code}
rats <- read_excel("data1.xlsx")
rats$Groups<-factor(rats$Groups,levels=c("CC","LL","FF","LF"),labels=c("CC","LL","FF","LF"))
rats$Time<-factor(rats$Time,levels=c("Week 1","Week 11"))
kable(head(rats),digits=2)
```

::: {.cell-output-display}
`````{=html}
<table>
 <thead>
  <tr>
   <th style="text-align:right;"> Rats </th>
   <th style="text-align:left;"> Groups </th>
   <th style="text-align:left;"> Time </th>
   <th style="text-align:right;"> BW </th>
   <th style="text-align:right;"> body fat </th>
   <th style="text-align:right;"> Glycemia </th>
   <th style="text-align:right;"> Insulinemia </th>
   <th style="text-align:right;"> Cholesterol </th>
   <th style="text-align:right;"> TG </th>
   <th style="text-align:right;"> NEFA </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 385.4 </td>
   <td style="text-align:right;"> 44.58 </td>
   <td style="text-align:right;"> 5.13 </td>
   <td style="text-align:right;"> 2.41 </td>
   <td style="text-align:right;"> 1.31 </td>
   <td style="text-align:right;"> 1.83 </td>
   <td style="text-align:right;"> 0.54 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 392.4 </td>
   <td style="text-align:right;"> 23.70 </td>
   <td style="text-align:right;"> 5.45 </td>
   <td style="text-align:right;"> 2.23 </td>
   <td style="text-align:right;"> 2.02 </td>
   <td style="text-align:right;"> 1.34 </td>
   <td style="text-align:right;"> 0.51 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 406.1 </td>
   <td style="text-align:right;"> 36.19 </td>
   <td style="text-align:right;"> 5.52 </td>
   <td style="text-align:right;"> 2.36 </td>
   <td style="text-align:right;"> 1.82 </td>
   <td style="text-align:right;"> 1.82 </td>
   <td style="text-align:right;"> 0.28 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 421.6 </td>
   <td style="text-align:right;"> 36.30 </td>
   <td style="text-align:right;"> 5.46 </td>
   <td style="text-align:right;"> 2.17 </td>
   <td style="text-align:right;"> 1.69 </td>
   <td style="text-align:right;"> 2.41 </td>
   <td style="text-align:right;"> 0.65 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 385.9 </td>
   <td style="text-align:right;"> 43.24 </td>
   <td style="text-align:right;"> 5.52 </td>
   <td style="text-align:right;"> 2.34 </td>
   <td style="text-align:right;"> 2.03 </td>
   <td style="text-align:right;"> 2.15 </td>
   <td style="text-align:right;"> 0.23 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 412.9 </td>
   <td style="text-align:right;"> 29.37 </td>
   <td style="text-align:right;"> 5.95 </td>
   <td style="text-align:right;"> 2.50 </td>
   <td style="text-align:right;"> 1.95 </td>
   <td style="text-align:right;"> 1.77 </td>
   <td style="text-align:right;"> 0.51 </td>
  </tr>
</tbody>
</table>

`````
:::
:::




# Etude de type crossover

Une étude croisée ou un essai croisé est une étude longitudinale dans laquelle les sujets reçoivent une séquence de traitements (ou d'expositions) différents.

### Exemple :

Les effets comportementaux d'un programme de socialisation des chiots ont été évalués chez 58 chiots de race pure et 10 chiots croisés. Chaque sujet a été réparti au hasard dans l'un des cinq groupes : Socialisation plus formation (S & T, n=12), Socialisation (n=10), Formation (n=13), Alimentation (n=12) et Contrôle (n=11). Pour chaque chiot on mesure la réponse à un ensemble de stimuli (commandes, manipulations,...). On s'intéresse à l'intéraction entre le type de stimuli (mesures répétées, effet WITHIN) et le type de programme (effet BETWEEN).

Bibliographie : Kersti Seksel, Evalynn J Mazurski, Alan Taylor, Puppy socialisation programs: short and long term behavioural effects, Applied Animal Behaviour Science, Volume 62, Issue 4, 1999, Pages 335-349, ISSN 0168-1591,[doi](https://doi.org/10.1016/S0168-1591(98)00232-9).


# Etudes à effets imbriqués


### Introduction

-   Ces modèles sont aussi appelés modèles hierarchisés (***nested***).

-   Les niveaux du facteur $B$ sont similaires mais ne sont pas identiques selon les niveaux de l'autre facteur $A.$



## Exemple :

Données de la thèse d'exercice de Sarah Degand (2021) :
EVALUATION DE L’IMPACT DU DILUEUR SUR LA CONCENTRATION EN PROAKAP4 DANS LE SPERME CONGELE DE BOUC : CORRELATION AVEC LA MOBILITE

étude la concentration de ProAKAP4 dans le sperme en fonction de la race et du bouc. Ici les boucs sont considérés par Race, donc l'effet bouc est imbriqué dans l'effet race.


::: {.cell}

```{.r .cell-code}
df<-read_excel("ProAKAP4_BOUC.xlsx")
df$Bouc<-as.factor(df$Bouc)
df$Race<-as.factor(df$Race)
df$Milieu<-as.factor(df$Milieu)
table(df$Bouc,df$Race)
```

::: {.cell-output .cell-output-stdout}
```
   
    11 13
  1  9  9
  2  9  9
  3  9  9
  4  9  9
  5  0  9
```
:::
:::


![exemple de facteurs imbriqués](images/plan2.png)


# Etudes de type SPLIT-PLOT

Split-plot : parcelle fractionnée 
Pour éviter des répétitions, souvent onéreuses, on peut utiliser la technique dite de SPLIT-PLOT.

Par exemple on veut tester l'effet de 3 préparations de pâtes et quatre températures de four sur la qualité visuelle d'une pâte à tarte. On veut répliquer 3 fois l'expérience.

***Question*** : si on veut faire une expérimentation totalement randomisée combien de préparations sont nécessaires ?

***Dispositif Split-Plot*** On réplique 3 fois chaque recette (plot) et on partage en 4 chaque préparation 
(split) et on les assigne aléatoirement à chaque température.

## Mise en oeuvre

On considère deux facteurs $A,B$ ayant respectivement $I,J$ niveaux. On choisit le facteur $A$ sur lequel portera la contrainte.

1. Répéter $K$ fois chaque niveau $a_i$ de $A$. On note $R_{k,i}$ ces blocs

2. Partager chaque blocc $R_{k,i}$ (plot) en $J$ sous-blocs (split) qui seront assignés aléatoirement à chaque niveau de $B.$

On a donc $N=I\times J \times K$ essais.


## Exemple :

Données de la thèse d'exercice de Sarah Degand (2021) :
On veut regarder l'effet du dilueur sur la concentration en ProAKAP4. 
Les données sont disponibles ici : [ProAKAP4](ProAKAP4_BOUC.xlsx)


::: {.cell}

```{.r .cell-code}
df<-read_excel("ProAKAP4_BOUC.xlsx")
df$Bouc<-as.factor(df$Bouc)
df$Race<-as.factor(df$Race)
df$Milieu<-as.factor(df$Milieu)
table(df$Bouc,df$Race)
```

::: {.cell-output .cell-output-stdout}
```
   
    11 13
  1  9  9
  2  9  9
  3  9  9
  4  9  9
  5  0  9
```
:::
:::



![exemple des boucs](images/plan3.png)


# Rappel ANOVA sur données indépendantes

On reprend la base de données sur le régime des rats.

## Modélisation 1 : ANOVA sur mesures indépendantes (aggrégation des données sur Time)

On calcule les moyennes entre la semaine 1 et la semaine 11 de toutes les variables considérées sur les rats.


Du côté de R : on utilise la librarie dplyr très pratique pour manipuler les données. Le site <https://juba.github.io/tidyverse/10-dplyr.html> constitue une très bonne introduction à ce package.

### Le modèle mathématique et les hypothèses des tests

On considère un facteur $A$ à $J$ niveaux, le modèle est

$$
Y_{ij}=\mu+\alpha_{j}+\varepsilon_{ij},
$$ 

où $Y_{ij}$ est la réponse pour l'individu $i$ affecté dans le groupe $j=1,...,J$. Les paramètres $\alpha_j$ sont appelés effets principaux du facteur $A$ on suppose que $\sum_{j=1}^J\alpha_j=0.$ 

On suppose que $\varepsilon_{ij}\sim \mathcal N(0,\sigma^2)$ (hypothèse d'homoscédasticité).

Il a deux questions principalement associées à ce modèle : 

- l'estimation des coefficients $\mu,\alpha_1,...,\alpha_{J-1}$

- la significativité de ces coefficients 

Pour l'estimation on utilise la méthode MCO (moindres carrés ordinaires) et on obtient 

$\hat \mu=\frac 1{J}\sum_{j=1}^J\bar Y_j$ et $\hat \alpha_j=\bar Y_j-\hat \mu.$

Remarque : si tous les groupes sont équilibrés on a $\hat \mu=\overline{\overline Y}.$

On teste deux hypothèses :

- Le facteur $A$ a un effet sur la réponse $Y.$ D'un point de vue mathématique on va tester $H_0:\alpha_1=...=\alpha_J=0$. Le test utilisé s'appelle le test de Fisher (test Omnibus)

- On peut être intéressé uniquement par tester l'effet d'un des niveaux de $A$ c'est à dire $H_0:\alpha_j=0$ pour l'un des niveaux $j$ de $A$. Ce test est un test de Student.

On va étudier par exemple les variables BW et Insulinemia.


::: {.cell}

```{.r .cell-code}
colnames(rats)
```

::: {.cell-output .cell-output-stdout}
```
 [1] "Rats"        "Groups"      "Time"        "BW"          "body fat"   
 [6] "Glycemia"    "Insulinemia" "Cholesterol" "TG"          "NEFA"       
```
:::

```{.r .cell-code}
df1 = rats %>% 
  group_by(Rats,Groups) %>%
  summarise(NEFA=mean(NEFA),TG=mean(TG),C=mean(Cholesterol),
            BW=mean(BW),I=mean(Insulinemia)) 
kable(head(df1))
```

::: {.cell-output-display}
`````{=html}
<table>
 <thead>
  <tr>
   <th style="text-align:right;"> Rats </th>
   <th style="text-align:left;"> Groups </th>
   <th style="text-align:right;"> NEFA </th>
   <th style="text-align:right;"> TG </th>
   <th style="text-align:right;"> C </th>
   <th style="text-align:right;"> BW </th>
   <th style="text-align:right;"> I </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:right;"> 0.3579423 </td>
   <td style="text-align:right;"> 1.676122 </td>
   <td style="text-align:right;"> 1.521581 </td>
   <td style="text-align:right;"> 435.20 </td>
   <td style="text-align:right;"> 2.357126 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:right;"> 0.4165651 </td>
   <td style="text-align:right;"> 1.492578 </td>
   <td style="text-align:right;"> 2.196187 </td>
   <td style="text-align:right;"> 440.60 </td>
   <td style="text-align:right;"> 2.518081 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:right;"> 0.3132758 </td>
   <td style="text-align:right;"> 1.837344 </td>
   <td style="text-align:right;"> 2.117650 </td>
   <td style="text-align:right;"> 483.05 </td>
   <td style="text-align:right;"> 2.292124 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:right;"> 0.4525670 </td>
   <td style="text-align:right;"> 2.172607 </td>
   <td style="text-align:right;"> 1.689075 </td>
   <td style="text-align:right;"> 495.00 </td>
   <td style="text-align:right;"> 2.175999 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:right;"> 0.2543409 </td>
   <td style="text-align:right;"> 1.912967 </td>
   <td style="text-align:right;"> 2.138862 </td>
   <td style="text-align:right;"> 453.15 </td>
   <td style="text-align:right;"> 2.243141 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:left;"> CC </td>
   <td style="text-align:right;"> 0.4821821 </td>
   <td style="text-align:right;"> 1.498147 </td>
   <td style="text-align:right;"> 1.858858 </td>
   <td style="text-align:right;"> 473.80 </td>
   <td style="text-align:right;"> 2.379702 </td>
  </tr>
</tbody>
</table>

`````
:::
:::


### Etude de l'effet régime sur BW

On commence par faire une représentation graphique de NEFA en fonction du groupe


::: {.cell}

```{.r .cell-code}
ggplot(df1,aes(x=Groups,y=BW))+
  geom_boxplot()+
  theme_minimal()+
  labs(title = "BW en fonction du régime")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-6-1.png){width=672}
:::
:::


***Question*** Le regime semble t'il avoir un effet sur BW ? Quel groupe a la plus grande dispersion ? A combien d'observations correspondent les boxplots ?


::: {.cell}

```{.r .cell-code}
relevel(df1$Groups,ref="CC")
```

::: {.cell-output .cell-output-stdout}
```
 [1] CC CC CC CC CC CC LL LL LL LL LL LL FF FF FF FF FF FF LF LF LF LF LF LF
Levels: CC LL FF LF
```
:::

```{.r .cell-code}
modLin<-lm(BW~Groups,data=df1)
library(car)
Anova(modLin,type = "III") %>% kable(digits=3)
```

::: {.cell-output-display}
`````{=html}
<table>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:right;"> Sum Sq </th>
   <th style="text-align:right;"> Df </th>
   <th style="text-align:right;"> F value </th>
   <th style="text-align:right;"> Pr(&gt;F) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:right;"> 5083737.402 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 3258.547 </td>
   <td style="text-align:right;"> 0.000 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Groups </td>
   <td style="text-align:right;"> 309.531 </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> 0.066 </td>
   <td style="text-align:right;"> 0.977 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Residuals </td>
   <td style="text-align:right;"> 31202.482 </td>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:right;">  </td>
   <td style="text-align:right;">  </td>
  </tr>
</tbody>
</table>

`````
:::

```{.r .cell-code}
summary(modLin)
```

::: {.cell-output .cell-output-stdout}
```

Call:
lm(formula = BW ~ Groups, data = df1)

Residuals:
    Min      1Q  Median      3Q     Max 
-66.658 -28.969   0.433  24.258  73.892 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  460.242      8.063  57.084   <2e-16 ***
Groups1        3.225     13.965   0.231    0.820    
Groups2       -2.083     13.965  -0.149    0.883    
Groups3        3.683     13.965   0.264    0.795    
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 39.5 on 20 degrees of freedom
Multiple R-squared:  0.009823,	Adjusted R-squared:  -0.1387 
F-statistic: 0.06613 on 3 and 20 DF,  p-value: 0.9772
```
:::
:::


### Etude de l'effet régime sur la variable Insulinemia


::: {.cell}

```{.r .cell-code}
ggplot(df1,aes(x=Groups,y=I))+
  geom_boxplot()+
  theme_minimal()+
  labs(title = "Insulinemia en fonction du régime")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-8-1.png){width=672}
:::
:::


Les résultats du modèle d'ANOVA :


::: {.cell}

```{.r .cell-code}
modLin<-lm(I~Groups,data=df1)
library(car)
Anova(modLin,type = "III") %>% kable(digits=3)
```

::: {.cell-output-display}
`````{=html}
<table>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:right;"> Sum Sq </th>
   <th style="text-align:right;"> Df </th>
   <th style="text-align:right;"> F value </th>
   <th style="text-align:right;"> Pr(&gt;F) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:right;"> 163.156 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1276.855 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Groups </td>
   <td style="text-align:right;"> 6.061 </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> 15.811 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Residuals </td>
   <td style="text-align:right;"> 2.556 </td>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:right;">  </td>
   <td style="text-align:right;">  </td>
  </tr>
</tbody>
</table>

`````
:::

```{.r .cell-code}
summary(modLin)
```

::: {.cell-output .cell-output-stdout}
```

Call:
lm(formula = I ~ Groups, data = df1)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.67229 -0.14827 -0.05179  0.06656  1.07946 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  2.60733    0.07297  35.733   <2e-16 ***
Groups1     -0.27964    0.12638  -2.213   0.0387 *  
Groups2     -0.27377    0.12638  -2.166   0.0426 *  
Groups3     -0.31656    0.12638  -2.505   0.0210 *  
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 0.3575 on 20 degrees of freedom
Multiple R-squared:  0.7034,	Adjusted R-squared:  0.6589 
F-statistic: 15.81 on 3 and 20 DF,  p-value: 1.665e-05
```
:::
:::

On peut également réaliser des comparaisons par paires (on dit aussi tests post-hoc ou Test de Tukey) pour compléter l'analyse précédente :


::: {.cell}

```{.r .cell-code}
library(multcomp)
post_hoc<-glht(modLin,linfct = mcp("Groups"="Tukey"))
summary(post_hoc)
```

::: {.cell-output .cell-output-stdout}
```

	 Simultaneous Tests for General Linear Hypotheses

Multiple Comparisons of Means: Tukey Contrasts


Fit: lm(formula = I ~ Groups, data = df1)

Linear Hypotheses:
              Estimate Std. Error t value Pr(>|t|)    
LL - CC == 0  0.005868   0.206381   0.028 0.999991    
FF - CC == 0 -0.036923   0.206381  -0.179 0.997896    
LF - CC == 0  1.149596   0.206381   5.570  < 1e-04 ***
FF - LL == 0 -0.042791   0.206381  -0.207 0.996741    
LF - LL == 0  1.143728   0.206381   5.542 0.000103 ***
LF - FF == 0  1.186519   0.206381   5.749  < 1e-04 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
(Adjusted p values reported -- single-step method)
```
:::
:::


Attention dans le cas de la variable TG on n'a pas fait de test post-hoc : c'était inutile étant donné que le test global de Fisher était non significatif. 

# Modélisation à effets mixtes

Les situations décrites dans l'introduction vont être analysées en utilisant un modèle d'ANOVA à effets mixtes. 


## Etude de l'effet temporel dans l'étude sur les rats

Ici on va prendre la dimension temporelle des données. C'est à dire l'on modélise le fait que pour chaque rat il y a eu deux mesures de chaque propriété biochimique.

***Remarques***

1.  Avec deux mesures par individu, la modélisation tenant compte de la mesure répétée est limitée à un effet aléatoire sur l'intercept du modèle.

2.  Un modèle dans lequel on considère des effets fixes et des effets aléatoires s'appelle un modèle à effet mixte.

### Variable réponse BW

Le modèle

$$
BW_{ik}=\mu+\rho_k+\alpha_i+\varepsilon_{ik}
$$

où $BW_{ik}$ représente le poids corporel du rat $k$ à la semaine $i$.

Ici on suppose que les rats sont prélevés aléatoirement dans une population de rats :

1. L'effet rat est aléatoire c'est à dire que $\rho_k\sim \mathcal N(0,\sigma_\rho)$.

2. L'effet semaine est fixe.

3. Les variables aléatoires $\rho_k$ et $\varepsilon_{ik}$ sont indépendantes.


Représentation graphique :


::: {.cell}

```{.r .cell-code}
ggplot(rats,aes(x=Time,y=BW))+
  geom_boxplot()+
  theme_minimal()+
  labs(title = "BW en fonction du temps")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-11-1.png){width=672}
:::
:::


Regardons les analyses descriptives de BW en fonction de Time :


::: {.cell}

```{.r .cell-code}
tab<-rats %>% group_by(Time) %>% summarise(BW=mean(BW))
kable(tab)
```

::: {.cell-output-display}
`````{=html}
<table>
 <thead>
  <tr>
   <th style="text-align:left;"> Time </th>
   <th style="text-align:right;"> BW </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Week 1 </td>
   <td style="text-align:right;"> 392.1125 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Week 11 </td>
   <td style="text-align:right;"> 528.3708 </td>
  </tr>
</tbody>
</table>

`````
:::

```{.r .cell-code}
mean(tab$BW)
```

::: {.cell-output .cell-output-stdout}
```
[1] 460.2417
```
:::
:::


Dans R pour définir un modèle à effets mixtes on va utiliser le package ***lmerTest***. Pour indiquer l'effet aléatoire rats on utilise la synthaxe (1|Rats) :  


::: {.cell}

```{.r .cell-code}
library(lmerTest)
rats$Rats<-as.factor(rats$Rats)
mod<-lmer(BW~Time+(1|Rats),data=rats)
summary(mod)
```

::: {.cell-output .cell-output-stdout}
```
Linear mixed model fit by REML. t-tests use Satterthwaite's method [
lmerModLmerTest]
Formula: BW ~ Time + (1 | Rats)
   Data: rats

REML criterion at convergence: 449.1

Scaled residuals: 
     Min       1Q   Median       3Q      Max 
-1.97913 -0.36945  0.00274  0.33073  2.48793 

Random effects:
 Groups   Name        Variance Std.Dev.
 Rats     (Intercept) 1235.3   35.15   
 Residual              269.6   16.42   
Number of obs: 48, groups:  Rats, 24

Fixed effects:
            Estimate Std. Error      df t value Pr(>|t|)    
(Intercept)  460.242      7.556  23.000   60.91   <2e-16 ***
Time1        -68.129      2.370  23.000  -28.75   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Correlation of Fixed Effects:
      (Intr)
Time1 0.000 
```
:::
:::


Remarques : On constate que

1. L'estimation de $\mu$ correspond au poids moyen des rats. 

2. L'estimation de $\sigma_\rho$ est proche de l'écart type des rats.

En effet si on aggrège les données sur les rats (moyenne des deux semaines) on a :


::: {.cell}

```{.r .cell-code}
R<-rats %>% group_by(Rats) %>% summarise(M=mean(BW))
sd(R$M)
```

::: {.cell-output .cell-output-stdout}
```
[1] 37.01469
```
:::
:::



3. L'estimation de l'effet temporel correspond à la différence entre la moyenne des rats et la moyenne de la semaine 1.

La fonction ***anova*** permet de tester si l'effet fixe (ici semaine) est significatif $H_0:\alpha_1=...=\alpha_I=0$:


::: {.cell}

```{.r .cell-code}
anova(mod)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
     Sum Sq Mean Sq NumDF DenDF F value    Pr(>F)    
Time 222796  222796     1    23  826.51 < 2.2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::
:::


La fonction ***ranova*** permet de tester si l'effet aléatoire est significatif $H_0:\sigma_\rho=0$:


::: {.cell}

```{.r .cell-code}
ranova(mod)
```

::: {.cell-output .cell-output-stdout}
```
ANOVA-like table for random-effects: Single term deletions

Model:
BW ~ Time + (1 | Rats)
           npar  logLik    AIC    LRT Df Pr(>Chisq)    
<none>        4 -224.54 457.07                         
(1 | Rats)    3 -237.42 480.84 25.768  1   3.85e-07 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::
:::



## ANOVA à deux facteurs fixes et un facteur aléatoire

On peut ajouter l'effet régime à l'effet temporel :

$$
BW_{ijk}=\mu+\rho_k+\alpha_i+\beta_j+(\alpha\beta)_{ij}+\varepsilon_{ijk}
$$
Dans le modèle on a considéré une éventuelle intercation entre les deux facteurs.

Représentation graphique :


::: {.cell}

```{.r .cell-code}
ggplot(rats,aes(x=Time,y=BW,fill=Groups))+
  geom_boxplot()+
  theme_minimal()+
  labs(title = "BW en fonction du temps et du régime")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-17-1.png){width=672}
:::
:::


Estimation du modèle sur R :


::: {.cell}

```{.r .cell-code}
mod<-lmer(BW~Groups*Time+(1|Rats),data=rats)
summary(mod)
```

::: {.cell-output .cell-output-stdout}
```
Linear mixed model fit by REML. t-tests use Satterthwaite's method [
lmerModLmerTest]
Formula: BW ~ Groups * Time + (1 | Rats)
   Data: rats

REML criterion at convergence: 410.7

Scaled residuals: 
    Min      1Q  Median      3Q     Max 
-1.6167 -0.4554 -0.0118  0.4622  2.0726 

Random effects:
 Groups   Name        Variance Std.Dev.
 Rats     (Intercept) 1433     37.85   
 Residual              255     15.97   
Number of obs: 48, groups:  Rats, 24

Fixed effects:
              Estimate Std. Error      df t value Pr(>|t|)    
(Intercept)    460.242      8.063  20.000  57.084   <2e-16 ***
Groups1          3.225     13.965  20.000   0.231   0.8197    
Groups2         -2.083     13.965  20.000  -0.149   0.8829    
Groups3          3.683     13.965  20.000   0.264   0.7947    
Time1          -68.129      2.305  20.000 -29.558   <2e-16 ***
Groups1:Time1    5.379      3.992  20.000   1.347   0.1929    
Groups2:Time1   -7.212      3.992  20.000  -1.807   0.0859 .  
Groups3:Time1    3.037      3.992  20.000   0.761   0.4556    
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Correlation of Fixed Effects:
            (Intr) Grops1 Grops2 Grops3 Time1  Gr1:T1 Gr2:T1
Groups1      0.000                                          
Groups2      0.000 -0.333                                   
Groups3      0.000 -0.333 -0.333                            
Time1        0.000  0.000  0.000  0.000                     
Groups1:Tm1  0.000  0.000  0.000  0.000  0.000              
Groups2:Tm1  0.000  0.000  0.000  0.000  0.000 -0.333       
Groups3:Tm1  0.000  0.000  0.000  0.000  0.000 -0.333 -0.333
```
:::
:::


Remarques :

1. Comme précédemment l'estimation de $\mu$ correspond à la moyenne des poids corporels.

2. Dans ce modèle il y a beaucoup de coefficients correspondants aux effets principaux (Groupe et Time) et aux effets d'interaction. 


Pour tester la significativité des effets on va utiliser la fonction anova.



::: {.cell}

```{.r .cell-code}
anova(mod)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
            Sum Sq Mean Sq NumDF DenDF  F value Pr(>F)    
Groups          51      17     3    20   0.0661 0.9772    
Time        222796  222796     1    20 873.6541 <2e-16 ***
Groups:Time   1100     367     3    20   1.4373 0.2616    
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::
:::



- On commence toujours par regarder l'effet d'intercation. Il est ici non significatif ce qui signifie que l'effet du régime sur BW n'est pas différent entre la semaine 1 et la semaine 11 ($F(3,20)=1.43, \ p=.2616$).

- L'effet du régime n'est pas significatif ($F(3,20)=0.0661, \ p=.9772$).

- L'effet de la semaine est significatif ($F(1,20)=873.65, \ p<.001$).

On peut alors envisager un modèle plus parcimonieux (retirer l'effet d'interaction), on parle de modèle additif :


::: {.cell}

```{.r .cell-code}
mod<-lmer(BW~Groups+Time+(1|Rats),data=rats)
summary(mod)
```

::: {.cell-output .cell-output-stdout}
```
Linear mixed model fit by REML. t-tests use Satterthwaite's method [
lmerModLmerTest]
Formula: BW ~ Groups + Time + (1 | Rats)
   Data: rats

REML criterion at convergence: 428.3

Scaled residuals: 
     Min       1Q   Median       3Q      Max 
-1.99916 -0.39801  0.02781  0.31629  2.46790 

Random effects:
 Groups   Name        Variance Std.Dev.
 Rats     (Intercept) 1425.3   37.75   
 Residual              269.6   16.42   
Number of obs: 48, groups:  Rats, 24

Fixed effects:
            Estimate Std. Error      df t value Pr(>|t|)    
(Intercept)  460.242      8.063  20.000  57.084   <2e-16 ***
Groups1        3.225     13.965  20.000   0.231    0.820    
Groups2       -2.083     13.965  20.000  -0.149    0.883    
Groups3        3.683     13.965  20.000   0.264    0.795    
Time1        -68.129      2.370  23.000 -28.749   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Correlation of Fixed Effects:
        (Intr) Grops1 Grops2 Grops3
Groups1  0.000                     
Groups2  0.000 -0.333              
Groups3  0.000 -0.333 -0.333       
Time1    0.000  0.000  0.000  0.000
```
:::
:::


## Effet sur insulinemia


::: {.cell}

```{.r .cell-code}
mod<-lmer(Insulinemia~Groups+Time+(1|Rats),data=rats)
anova(mod)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
       Sum Sq Mean Sq NumDF DenDF F value    Pr(>F)    
Groups 8.8422 2.94741     3    20 15.8114 1.665e-05 ***
Time   0.0034 0.00339     1    23  0.0182    0.8939    
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::
:::

On fait alors des tests post-hoc :


::: {.cell}

```{.r .cell-code}
post_hoc<-glht(mod,linfct = mcp("Groups"="Tukey"))
summary(post_hoc)
```

::: {.cell-output .cell-output-stdout}
```

	 Simultaneous Tests for General Linear Hypotheses

Multiple Comparisons of Means: Tukey Contrasts


Fit: lmer(formula = Insulinemia ~ Groups + Time + (1 | Rats), data = rats)

Linear Hypotheses:
              Estimate Std. Error z value Pr(>|z|)    
LL - CC == 0  0.005868   0.206381   0.028    1.000    
FF - CC == 0 -0.036923   0.206381  -0.179    0.998    
LF - CC == 0  1.149596   0.206381   5.570   <1e-06 ***
FF - LL == 0 -0.042791   0.206381  -0.207    0.997    
LF - LL == 0  1.143728   0.206381   5.542   <1e-06 ***
LF - FF == 0  1.186519   0.206381   5.749   <1e-06 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
(Adjusted p values reported -- single-step method)
```
:::
:::

::: {.cell}

```{.r .cell-code}
ggplot(rats,aes(x=Time,y=Insulinemia,fill=Groups))+
  geom_boxplot()+
  theme_minimal()+
  labs(title = "Insulimenia en fonction du temps et du régime")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-23-1.png){width=672}
:::
:::


# ANOVA à effets imbriqués

On reprend l'exemple sur les boucs.


::: {.cell}

:::


***Question :*** Différence de concentration de ProAKAP4 en fonction de la race ?

Réponse en agrégeant les données


::: {.cell}

```{.r .cell-code}
agreg<-df %>% group_by(Race,Bouc) %>% summarise(M=mean(ProAKAP4)) 
ggplot(agreg,aes(x=Race,y=M))+geom_boxplot()+geom_jitter(width=.05,col="purple")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-25-1.png){width=672}
:::

```{.r .cell-code}
t.test(agreg$M~agreg$Race,var.equal=T)
```

::: {.cell-output .cell-output-stdout}
```

	Two Sample t-test

data:  agreg$M by agreg$Race
t = -0.55338, df = 7, p-value = 0.5972
alternative hypothesis: true difference in means between group 11 and group 13 is not equal to 0
95 percent confidence interval:
 -2.264237  1.405439
sample estimates:
mean in group 11 mean in group 13 
        4.262208         4.691607 
```
:::
:::


En utilisant un modèle à effets imbriqués (plusieurs répétitions pour chauqe bouc de chaque race)

$$
ProAKAP4_{ik}=\mu+\rho_{k(i)}+\alpha_i+\varepsilon_{ik}
$$ 

où $\alpha_i$ est l'effet de la race $i$, et $\rho_{k(i)} \sim \mathcal N(0,\sigma^2_{\rho})$ est l'effet du bouc $k$ de la race $i.$


On écrit le modèle dans R :


::: {.cell}

```{.r .cell-code}
mod<-lmer(ProAKAP4~Race+(1|Bouc:Race),data=df)
summary(mod)
ranova(mod)
```
:::


On en déduit qu'il n'y pas de différence de concentration de ProAKAP4 en fonction de la race.



# Anova split-plot

***Question 1 :***

On agrège les données sur les répétitions (dates Ejacbouc) et le modèle devient alors 


::: {.cell}

```{.r .cell-code}
agreg<-df %>% group_by(Ejacbouc,Milieu)%>% summarise(M=mean(ProAKAP4))
ggplot(agreg,aes(x=Milieu,y=M))+geom_boxplot()+geom_jitter(width=.05,col="purple")
```

::: {.cell-output-display}
![](Dispo_expe_files/figure-html/unnamed-chunk-27-1.png){width=672}
:::

```{.r .cell-code}
mod<-lmer(M~Milieu+(1|Ejacbouc),data=agreg)
anova(mod,type=3)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
       Sum Sq Mean Sq NumDF DenDF F value    Pr(>F)    
Milieu 94.408  47.204     2    52  10.498 0.0001481 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::
:::

Le mileu a donc un effet sur la concentration en ProAKAP4, on peut faire une analyse post-hoc :


::: {.cell}

```{.r .cell-code}
PostHoc<-glht(mod,linfct = mcp("Milieu"="Tukey"))
summary(PostHoc)
```

::: {.cell-output .cell-output-stdout}
```

	 Simultaneous Tests for General Linear Hypotheses

Multiple Comparisons of Means: Tukey Contrasts


Fit: lmer(formula = M ~ Milieu + (1 | Ejacbouc), data = agreg)

Linear Hypotheses:
           Estimate Std. Error z value Pr(>|z|)    
L - B == 0  -2.4090     0.5771  -4.174  < 1e-04 ***
O - B == 0  -0.2599     0.5771  -0.450 0.894250    
O - L == 0   2.1491     0.5771   3.724 0.000613 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
(Adjusted p values reported -- single-step method)
```
:::
:::

***Solution 2 : Split-plot*** 

Le modèle s'écrit dans ce cas 


::: {.cell}

```{.r .cell-code}
mod<-lmer(ProAKAP4~Milieu+(1|Ejacbouc)+(1|Ejacbouc:Bouc),data=df)
anova(mod,type=3)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
       Sum Sq Mean Sq NumDF DenDF F value    Pr(>F)    
Milieu 94.408  47.204     2    52  10.498 0.0001481 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::
:::

::: {.cell}

```{.r .cell-code}
PostHoc=glht(mod,linfct = mcp("Milieu"="Tukey"))
summary(PostHoc)
```

::: {.cell-output .cell-output-stdout}
```

	 Simultaneous Tests for General Linear Hypotheses

Multiple Comparisons of Means: Tukey Contrasts


Fit: lmer(formula = ProAKAP4 ~ Milieu + (1 | Ejacbouc) + (1 | Ejacbouc:Bouc), 
    data = df)

Linear Hypotheses:
           Estimate Std. Error z value Pr(>|z|)    
L - B == 0  -2.4090     0.5771  -4.174  < 1e-04 ***
O - B == 0  -0.2599     0.5771  -0.450 0.894254    
O - L == 0   2.1491     0.5771   3.724 0.000572 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
(Adjusted p values reported -- single-step method)
```
:::
:::

::: {.cell}

```{.r .cell-code}
mod<-lmer(ProAKAP4~Race+Milieu+(1|Bouc)+(1|Race:Ejacbouc)+(1|Ejacbouc:Bouc),data=df,REML=F)
anova(mod,type=3)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
       Sum Sq Mean Sq NumDF  DenDF F value    Pr(>F)    
Race    3.855   3.855     1 24.290  0.8902 0.3547169    
Milieu 94.408  47.204     2 54.001 10.9014 0.0001055 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::

```{.r .cell-code}
ranova(mod)
```

::: {.cell-output .cell-output-stdout}
```
ANOVA-like table for random-effects: Single term deletions

Model:
ProAKAP4 ~ Race + Milieu + (1 | Bouc) + (1 | Race:Ejacbouc) + (1 | Ejacbouc:Bouc)
                    npar  logLik    AIC    LRT Df Pr(>Chisq)
<none>                 8 -177.67 371.34                     
(1 | Bouc)             7 -178.37 370.74 1.3937  1     0.2378
(1 | Race:Ejacbouc)    7 -177.67 369.34 0.0000  1     1.0000
(1 | Ejacbouc:Bouc)    7 -177.67 369.34 0.0000  1     1.0000
```
:::
:::


On peut choisir le meilleur modèle en utilisant la fonction ***step*** :


::: {.cell}

```{.r .cell-code}
step(mod)
```

::: {.cell-output .cell-output-stdout}
```
Backward reduced random-effect table:

                    Eliminated npar  logLik    AIC     LRT Df Pr(>Chisq)
<none>                            8 -177.67 371.34                      
(1 | Race:Ejacbouc)          1    7 -177.67 369.34 0.00000  1     1.0000
(1 | Ejacbouc:Bouc)          2    6 -177.73 367.45 0.11066  1     0.7394
(1 | Bouc)                   3    5 -178.79 367.58 2.12913  1     0.1445

Backward reduced fixed-effect table:
       Eliminated Df Sum of Sq    RSS    AIC F value    Pr(>F)    
Race            1  1     3.688 395.65 134.47  0.7244 0.3973315    
Milieu          0  2    94.408 490.06 147.81  9.3060 0.0002374 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Model found:
ProAKAP4 ~ Milieu
```
:::

```{.r .cell-code}
mod<-lmer(ProAKAP4~Race+Milieu+(1|Bouc)+(1|Ejacbouc:Bouc),data=df,REML=F)
anova(mod,type=3)
```

::: {.cell-output .cell-output-stdout}
```
Type III Analysis of Variance Table with Satterthwaite's method
       Sum Sq Mean Sq NumDF  DenDF F value    Pr(>F)    
Race    3.855   3.855     1 24.289  0.8902 0.3547190    
Milieu 94.408  47.204     2 54.000 10.9013 0.0001055 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
:::

```{.r .cell-code}
ranova(mod)
```

::: {.cell-output .cell-output-stdout}
```
ANOVA-like table for random-effects: Single term deletions

Model:
ProAKAP4 ~ Race + Milieu + (1 | Bouc) + (1 | Ejacbouc:Bouc)
                    npar  logLik    AIC     LRT Df Pr(>Chisq)
<none>                 7 -177.67 369.34                      
(1 | Bouc)             6 -178.37 368.74 1.39373  1     0.2378
(1 | Ejacbouc:Bouc)    6 -177.73 367.45 0.11066  1     0.7394
```
:::
:::

