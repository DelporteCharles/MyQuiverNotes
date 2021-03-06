---
title: Optimisation BDT tH
date: '2018-05-16'
tags: []
---
# Purpose
)
{% highlight sh %}
Optimiser le BDT tH
{% endhighlight %}

# Samples
)
{% highlight sh %}
Signal single-top t/u-phi
Background Sherpa yy + jets
{% endhighlight %}

# Procedure
)
{% highlight sh %}
- identique a l'optimisation du BDT tt : on part de toutes les variables, et on enleve la moins performante a chaque iteration
- le meilleur BDT est celui qui a le moins de variables et qui, des qu'on lui retire une variable de plus, perds en significance
- procedure en 3 temps + 1
  - optimisation pour avoir les meilleurs variables pT/eta/m
  - optimisation pour avoir les meilleurs variables de deltaR/deltaPhi
  - optimisation pour avoir les meilleurs variables comme HT ou Somme Vectorielle des pT (pseudo-MET)
  - re-optimisation parmi les variables selectionnees ci-dessus
{% endhighlight %}

# BDT des variables cinematiques pT/eta
)
![IMAGE](/images/q/C065C0F99A8CD81DF7054C428A5FDCD4.jpg)
{% highlight sh %}
variablesOptimizationLocal rootFiles_tH/h021/  BDTTree_FCNCtphiQHgamgambWqq_v11_tH:BDTTree_FCNCuphiQHgamgambWqq_v11_tH BDTTree_FCNCttShergg_v8_tH pTyy:mW:pTj1:pTb:etayy:etab:etaj0:pTratiobjj0j1:etaj1:pTratioj0j1:pTj0
{% endhighlight %}

{% highlight sh %}
Classement :

1. pTyy
2. mW
4. pTj0
5. pTratioj0j1
6. etaj0
7. etab
8. pTb
9. etayy
10. etaj1
11. pTj1
12. pTratiobjj0j1

Suggestion à garder pour l'optimisation finale :

1. pTyy
2. mW
4. pTj0
5. pTratioj0j1
{% endhighlight %}

# BDT des variables de deltaR
)
{% highlight sh %}
variablesOptimizationLocal rootFiles_tH/h021/  BDTTree_FCNCtphiQHgamgambWqq_v11_tH:BDTTree_FCNCuphiQHgamgambWqq_v11_tH BDTTree_FCNCttShergg_v8_tH mindRbj:dRbW:dPhibW:mindPhibj:dEtabW:costhetastary
{% endhighlight %}

![IMAGE](/images/q/A107E54B7FFA7043D2BAD6D91136D107.jpg)
{% highlight sh %}
Classement :

1. dRbW
2. mindRbj
3. mindPhibj
4. dEtabW
5. costhetastary
6. dPhibW

Suggestion à garder pour l'optimisation finale :

1. dRbW
2. mindRbj
3. mindPhibj
{% endhighlight %}

# BDT des variables HT / pseudo-MET
)
{% highlight sh %}
variablesOptimizationLocal rootFiles_tH/h021/  BDTTree_FCNCtphiQHgamgambWqq_v11_tH:BDTTree_FCNCuphiQHgamgambWqq_v11_tH BDTTree_FCNCttShergg_v8_tH HTcjy0y1bjj0j1:HT4jets:MefftopSM:MefftopEx:HTjets:SumPtVect:SumPtVectAllJets
{% endhighlight %}

![IMAGE](/images/q/CD1AC7FC77846AA42CD54E0038C05321.jpg)
{% highlight sh %}
Classement :

1. MefftopEx (= pTy0 + pTy1)
2. MefftopSM
3. HTjets
4. SumPtVectAllJets
5. HT4jets
6. SumPtVect
7. HTcjy0y1bjj0j1

Suggestion à garder pour l'optimisation finale :

1. MefftopEx
2. MefftopSM
3. HTjets
4. SumPtVectAllJets
{% endhighlight %}

# Optimisation finale
)
{% highlight sh %}
variablesOptimizationLocal rootFiles_tH/h021/  BDTTree_FCNCtphiQHgamgambWqq_v11_tH:BDTTree_FCNCuphiQHgamgambWqq_v11_tH BDTTree_FCNCttShergg_v8_tH pTyy:mW:pTj0:pTratioj0j1:dRbW:mindRbj:mindPhibj:MefftopEx:MefftopSM:HTjets:SumPtVectAllJets
{% endhighlight %}

![IMAGE](/images/q/125C6622BEF04F2A22C90EE00DC49A73.jpg)
{% highlight sh %}
Classement :

1. pTyy
2. mW
3. MefftopSM
4. HTjets
5. mindRbj
6. MefftopEx
7. dRbW
8. pTratioj0j1
9. pTj0
10. SumPtVectAllJets
11. mindPhibj

Suggestion de variables à garder :

1. pTyy
2. mW
3. MefftopSM
4. HTjets
5. mindRbj
6. MefftopEx
7. dRbW

Ou :

MefftopSM = pTb + pTj0 + pTj1
HTjets = Somme scalaire du pT de tous les jets de l'evenement
MefftopEx = pTy0 + pTy1 (le nom vient de la selection ttbar où on a le c)


Fichier xml :

/sps/atlas/d/delporte/FCNC/FCNCAnaPlotStat/AnaPlot/MVA/training_tH_tuphi_3pj_7vars_opt_v0/weights/TMVAClassification_BDTCategories_tH_final_optimisation_v0.weights.xml

Pour lire le BDT, utiliser la methode AddVariable avec les variables dans le meme ordre que le classement de l'optimisation :

1. pTyy
2. mW
3. MefftopSM
4. HTjets
5. mindRbj
6. MefftopEx
7. dRbW

(et ensuite myy et EventNumberMod2 comme variables spectatrices)
{% endhighlight %}


)
