---
titre: Indexation, découpage en tranches et sous-ensambling de DataFrames dans l'en Python
enseignement: 30
exercices: 30
questions:
    - "Comment puis-je accéder à des données spécifiques dans mon ensemble de données?"
    - "Comment Python et Pandas peuvent-ils m'aider à analyser mes données?"
objectifs:
    - "Décrire ce qu'est l'indexation basée sur 0."
    - "Manipuler et extraire des données en utilisant des en-têtes de colonnes et des emplacements d'index."
    - "Utiliser le découpage en tranches pour sélectionner des ensembles de données à partir d'un DataFrame."
    - "Utiliser des index et des index pour sélectionner des plages de données dans une trame de données."
    - "Réaffecter des valeurs dans des sous-ensembles d'un DataFrame."
    - "Créer une copie d'un DataFrame."
    - "Interroger / sélectionner un sous-ensemble de données en utilisant un ensemble de critères utilisant les opérateurs suivants:
       `=`,`!=`,`>`,`<`,`> =`,`<=`."
    - "Localiser des sous-ensembles de données à l'aide de masques."
    - "Décrire les objets BOOLEAN en Python et manipuler des données à l'aide de BOOLEAN."
Points clés:
    - "En Python, il est possible d'accéder à des parties des données à l'aide d'indices, de tranches, de titres de colonnes et de
       sous-ensembles basés sur des conditions."
    - "Python utilise l'indexation basée sur 0, dans laquelle le premier élément d'une liste, d'un tuple ou de toute autredonnées
       structure dea un index de 0."
    - "Pandas permettent des étapes d'exploration de données communes telles que l'indexation, le découpage en tranches et le sous-conditionnel de
       ensembledonnées."
---

Dans le premier épisode de cette leçon, nous lisons un fichier CSV dans un DataFrame d'un pandas. Nous avons appris comment:

- affecter un DataFrame à un objet nommé (une variable),
- effectuer des calculs mathématiques de base sur les données,
- calculer des statistiques récapitulatives et
- créer des graphiques en fonction des données que nous avons chargées dans des pandas.

Dans cette leçon, nous explorerons différentes manières d'accéder à différentes parties des données en utilisant:

- l'indexation,
- le découpage en tranches et
- la sous-définition.

## Chargement de nos données

Nous allons continuer à utiliser le jeu de données d'enquêtes avec lequel nous avons travaillé lors du dernier
épisode. Rouvrons-nous et lisons à nouveau les données:

```python
# Assurez-vous que pandas est importé

isf_df = pd.read_csv("data/isfcom2017.csv")
```


## Indexation et découpage en Python

Nous souhaitons souvent travailler avec des sous-ensembles d'un objet **DataFrame**. Il y a
différentes façons d'y parvenir, notamment: en utilisant des étiquettes (en-têtes de colonnes),
des plages numériques ou des emplacements d'index x, y spécifiques.


## Sélection de données à l'aide d'étiquettes (en-têtes de colonnes)

Nous utilisons des crochets `[]` pour sélectionner un sous-ensemble d'un objet Python. Par exemple,
nous pouvons sélectionner toutes les données d'une colonne nommée `Species_id` à partir du DataFrame `isf_df` par son nom. Il y a deux façons de procéder:

```
# CONSEIL: utilisez la méthode .head () décrite précédemment pour raccourcir la sortie.
# Méthode 1: sélectionnez un "sous-ensemble" de données en utilisant le nom de colonne
Surveys_df ['espèce_id'].

# Méthode 2: utilisez le nom de la colonne comme "attribut"; donne la même sortie
isf_df.species_id
```
{: .language-python}

Nous pouvons également créer un nouvel objet contenant uniquement les données de la
colonne `Species_id` comme suit:

```
# Crée un objet, Surveysspecies, qui uniquement contient la colonne `Species_id`.
Surveys_species = Surveys_df ['Specie_ID']
```
{: .language-python}

Nous pouvons aussi passer une liste de noms de colonnes, en tant qu'index pour sélectionner les colonnes dans cet
ordre. Ceci est utile lorsque nous devons réorganiser nos données.

** REMARQUE: ** Si un nom de colonne n'est pas contenu dans le DataFrame, une exceptiondéclenchée
(erreur) sera.

```
# Sélectionnez les colonnes des espèces et des parcelles dans DataFrame
isf_df [['especes_personne', 'id_trigue']]

# Que se passe-t-il lorsque vous retournez l'ordre?
sondages_df [['' plot_id ',' espèce_id ']]]

# Que se passe-t-il si vous demandez une colonne qui n'existe pas?
Surveys_df ['espèces']
```
{: .language-python}

Python nous dit de quel type d'erreur il se trouve dans le traçage, en bas, il indique
`KeyError: 'espèce'` ce qui signifie que' espèce 'n'est pas un nom de colonne valide (ni une clé valide dans
le dictionnaire de types de données Python associé).

## Extraction de sous-ensembles basés sur une plage: Découpage

> ## Rappel
> Python utilise l'indexation basée sur 0.
{: .callout}

Rappelons-nous que Python utilise l'basée sur 0
indexation. Cela signifie que le premier élément d'un objet est situé à la position
0. Cela diffère d'autres outils comme R et Matlab qui indexent les éléments
dans les objets à partir de 1.

```
# Crée une liste de nombres:
a = [1, 2 , 3, 4, 5]
```
{: .language-python}

! [Diagramme d'indexation] (../ fig / slicing-indexing.png)
! [Diagramme de découpage] (../ fig / slicing-slicing.png


)>## Challenge - Extraction
données>>
1. Quellevaleur du code cidessous retour?
>>

```>a
[0]>```>
{:
.langue-python}>>
2.diriezvous
ceci:>>
```>
a
[5]>```>
{: .language-
python}>>
3. Dans l'exemple cidessus, appelant `a [5]` retourne une erreur. Pourquoi donc?
>>
4. Qu'en est-il?
>>

```>a [len
(a)]>```>
{: .langue-python}
{: .challenge}


##sousensembles de lignes de tranchage python

Trancheuseutilisant l'opérateur `[]` sélectionne un ensemble de des lignes et / ou des colonnes d'un
DataFrame. Pour découper un ensemble de lignes, vous utilisez la syntaxe suivante:
`data [start: stop]`. Lors du découpage en pandas, la limite de départ est incluse dans la
sortie. La limite d'arrêt est une étape AU-DELA de la ligne que vous souhaitez sélectionner. Donc, si vous
souhaitez sélectionner les lignes 0, 1 et 2, votre code ressemblera à ceci:

```
# Sélectionnez les lignes 0, 1, 2 (la ligne 3 n'est pas sélectionnée)
isf_df [0: 3]
```
{: .language -python}

L'arrêt lié en Python est différent de ce à quoi vous pourriez être habitué dans des
langages comme Matlab et R.

```
# Sélectionnez les 5 premières lignes (lignes 0, 1, 2, 3, 4)
isf_df [: 5]

# Sélectionnez le dernier élément de la liste
# (la tranche commence au dernier élément et se termine à la fin de la liste)
isf_df [-1:]
```
{: .language-python}

Nous pouvons également réaffecter des valeurs dans des sous-ensembles de notre DataFrame.

Mais avant cela, examinons la différence entre le concept de
copie d'objets et le concept de référencement d'objets en Python.

## Copier des objets vs référencer des objets en Python

Commençons par un exemple:

```
# Utilisation de la méthode 'copy ()'
true_copy_surveys_df = Surveys_df.copy ()

# Utilisation de l'opérateur '='
ref_surveys_df = isf_df
```
{:. language-python}

Vous pourriez penser que le code `ref_surveys_df = Surveys_df` crée une nouvelle
copie distincte de l'objet` Surveils_df` DataFrame. Cependant, l’utilisation de l’`=`
opérateurdans l’instruction simple `y = x` ne crée pas ** une copie de notre
DataFrame. À la place, `y = x` crée une nouvelle variable` y` qui fait référence au
même objet ** que celui auquel x fait référence. En d'autres, il n'y a que
termes** un ** objet (le DataFrame), et `x` et` y` s'y réfèrent.

En revanche, la méthode `copy ()` d'un DataFrame crée une copie conforme du
DataFrame.

Examinons ce qui se passe lorsque nous réaffectons les valeurs d'un sous-ensemble du
DataFrame qui fait référence à un autre objet DataFrame:

```
# Assigne la valeur `0` aux trois premières lignes de données du DataFrame
ref_surveys_df [0: 3] = 0
```
{: .language-python}

Essayons le code suivant:

```
# ref_surveys_df a été créé à l'aide de l'opérateur '='
ref_surveys_df.head ()

# isf_df est l'original du cadre de données
isf_df.head ()
```
{: .language-python}

Quelle est la différence entre ces deux images?

Lorsque nous avons affecté la valeur `0` aux 3 premières colonnes à l'aide du
DataFrame` ref_surveys_df`, le `Data_Frame` Surveys_df` est également modifié.
Rappelez-vous que nous avons créé l'objet de référence `ref_isf_df` ci-dessus lorsque nous avons
fait` ref_isf_df = isf_df`. Rappelez-vous que `isf_df` et` ref_surveys_df` se
réfèrent au même objet exact DataFrame. Si l'un modifie l'objet,
l'autre voit les mêmes modifications dans l'objet de référence.

** Pour revoir et récapituler **:

- ** ** Copie ** utilise la méthode `copy ()` de la base de données

  ```
  true_copy_surveys_df = isf_df.copy ()
  ```
  {: .language-python}
- A ** Référence * * est créé en utilisant l'opérateur `=`

  ```
  ref_surveys_df = Surveys_df
  ```
  {: .language-python}

D'accord, c'est assez de cela. Créons une nouvelle image devierge à partir
donnéesdu fichier CSV de données d'origine.

```
Surveys_df = pd.read_csv ("data / isfcom2017.csv")
```
{: .language-python}

## Découper des sous-ensembles de lignes et de colonnes en Python

Nous pouvons sélectionner des plages spécifiques de nos données dans la ligne et les directions de colonne en
utilisant l’indexation par étiquette ou par nombre entier.

- `loc` est principalement une indexation * label *. * Les entiers * peuvent être utilisés mais
  ils sont interprétés comme un * label *.
- `iloc` est principalement un * index * basé sur l'indexation

Pour sélectionner un sous-ensemble de lignes ** et ** colonnes de notre DataFrame, nous pouvons utiliser la
méthode` iloc`. Par exemple, nous pouvons sélectionner le mois, le jour et l’année (colonnes 2, 3
et 4 si nous commençons à compter à 1), comme:

```
suit# iloc [découpage en rangées, découpage en colonnes]
isf_df.iloc [0: 3, 1 : 4]
```
{: .language-python}

qui donne la sortie ** **

```
   mois jour année
0 7 16 1977
1 7 16 1977
2 7 16 1977
```
{: .output}

Notez que nous demandé une tranche de 0: 3. Cela a donné 3 lignes de données. Lorsque vous
demandez 0: 3, vous indiquez à Python de commencer à l'index 0 et de sélectionner les lignes
0, 1, 2 ** jusqu'à 3 ** non compris.

Explorons d’autres manières d’indexer et de sélectionner des sous-ensembles de données:

```
# Sélectionnez toutes les colonnes pour les lignes des valeurs d’index 0 et 10
isf_df.loc [[0, 10],:]

# À quoi sert-il?
sondages_df.loc [0, ['espèce_id', 'plot_id', 'poids']]

# Que se passe-t-il lorsque vous tapez le code ci-dessous?
sondages_df.loc [[0, 10, 35549],:]
```
{: .language-python}

** NOTE **: Les étiquettes doivent être trouvées dans le DataFrame ou vous obtiendrez un `KeyError`.

L'indexation par les étiquettes `loc` diffère de l'indexation par les entiers` iloc`.
Avec `loc`, les bornes de départ et d’arrivée sont ** inclusives **. Lorsque vous utilisezutiliser des
`loc`, vous pouvezentiers *, mais les entiers font référence à l'
étiquette d'index et non à la position. Par exemple, utiliser `loc` et sélectionner 1: 4
donnera un résultat différent de celui qui utilise` iloc` pour sélectionner les lignes 1: 4.

Nous pouvons également sélectionner une valeur de données spécifique en utilisant unligne et de
emplacement decolonne dans l'indexation DataFrame et `iloc`:

```
# Syntaxe pour l'indexation iloc permettant de rechercher un élément de données spécifique
dat.iloc [ligne, colonne]
```
{: .language-python}

Dans cet exemple `iloc`,

```
Surveys_df.iloc [2, 6]
```
{: .language-python}

donne le ** résultat **

```
'F'
```
{ : .output}

N'oubliez pas que l'indexation Python commence à 0. Ainsi, l'emplacement de l'index [2, 6]
sélectionne l'élément ayant 3 lignes en moins et 7 colonnes en plus dans le DataFrame.



> ## Challenge -
Gamme>>
1. Qu'estce qui se passe lorsque vous
exécutez:>>
- `surveys_df [0:
1]`>- `surveys_df
[4]`>- `surveys_df [: -
1]`>>
2. Qu'estce qui se passe lorsque vous
appelez:>>
- `surveys_df.iloc [0: 4, 1:
4]`>- `surveys_df.loc [0: 4, 1:
4]`>>
- Comment sont les deux commandes différentes?
{: .challenge}


## Sous-définition de données à l'aide de critères

Nous pouvons également sélectionner un sous-ensemble de nos données à l'aide de critères. Par exemple, nous pouvons
sélectionner toutes les lignes dont la valeur d'année est 2002:

```
Surveys_df [isf_df.year == 2002]
```
{: .language-python},

ce qui produit le résultat suivant:

```
record_id mois jour année plot_id espèce_id sexe arrière-poids
pied_longueur33320 33321 1 12 2002 1 DM M 38 44
33321 33322 1 12 2002 1 DO M 37 58
33322 33323 1 12 2002 1 PB M 28 45
33323 33324 1 12 2002 1 AB NaN NaN NaN
33324 33325 1 12 2002 1 DO M 35 29
...
35544 35545 12 31 2002 15 AH NaN NaN NaN
35545 35546 12 31 2002 15 AH NaN NaN NaN
35546 35547 12 31 2002 10 RM F 15 14
35547 35548 12 31 2002 7 DO M 36 51
35548 35549 12 31 2002 5 NaN NaN NaN NaN

[2229 lignes x 9 colonnes]
```
{: .language-python}

Ou nous pouvons sélectionner toutes les lignes ne contenant pas l'année 2002:

```
isf_df [isf_df.year! = 2002]
```
{: .language-python}

Nous pouvons aussi définir des ensembles de critères:

```
isf_df [(isf_df.year> = 1980) & (isf_df.year <= 1985)]
```
{: .language -python}

### Syntaxe Python Cheat Sheet

Nous pouvons utiliser la syntaxe ci-dessous lorsque queryin g données par critère d'un DataFrame.
Expérimentez avec la sélection de divers sous-ensembles des données "enquêtes".

* Égal: `==`
* Pas égal: `! =`
* Supérieur à, inférieur à: `>` ou `<`
* Supérieur ou égal à `> =`
* Inférieur ou égal à `<=`


> ## Challenge -
Requêtes>>
1. Sélectionnez un sousensemble de lignes dans le `surveys_df` dataframe qui contiennentdonnées
de>l'année 1999 et qui contiennentvaleurspoids inférieur ou égal à 8.
Comment>de lignes avezvousfin? Qu'est-ce que votre voisin a eu?
>>
2. Vous pouvez utiliser la commande `isin` en Python pour interroger une tramedonnées basée sur
une>liste de valeurs comme
suit:>>
```>
surveys_df [. Surveys_df [ 'species_id'] isin ([listGoesHere])]
>
```>{:
.langue-python}>>
Utilisez la fonction `isin` pour trouver toutesparcelles qui contiennentespèces
particulières>dans la tramedonnées« enquêtes ». Combien d'enregistrements contiennent ces valeurs?
>>
3. Expérimentez avec d'autres requêtes. Créez une requête qui trouve toutes les lignes avec une
valeur> d'épaisseur> ou égale à 0
.
>> 4. Le symbole `~` dans Python peut être utilisé pour renvoyer l'OPPOSITE de la
> sélection que vous spécifiez dans Python. Cela équivaut à ** n'est pas en **.
> Rédigez une requête qui sélectionne toutes les lignes dont le sexe n'est PAS égal à "M" ou "F" dans
les données "sondages".
{: .challenge}


# Utilisation de masques pour identifier une condition spécifique

Un ** masque ** peut être utile pour localiser l'emplacement d'un sous-ensemble particulier de valeurs
, par exemple les valeurs NaN ou "Pas un nombre". Pour comprendre les masques,
nous devons également comprendre les objets `BOOLEAN` en Python.

Les valeurs booléennes incluent `True` ou` False`. Par exemple,

```
# Définissez x sur 5
x = 5

# Que renvoie le code ci-dessous?
x> 5

# Comment ça?
x == 5
```
{: .language-python}

Lorsque nous demandons à Python si `x` est supérieur à 5, il renvoie` False`.
C'est la façon dont Python dit "Non". En effet, la valeur de «x» est 5
et 5 n’est pas supérieure à 5.

Pour créer un masque booléen:

- Définissez les critères True / False (par exemple, `values> 5 = True`)
- Python évaluera ensuite chaque valeur dans l'objet pour déterminer si la
  valeur répond aux critères (True) ou non (False).
- Python crée un objet de sortie ayant la même forme que l'origine
  objet d', mais avec une valeur `True` ou` False` pour chaque emplacement d'index.

Essayons ceci. Identifions tous les emplacements des données de l'enquête ayant
des valeurs de données nulles (manquantes ou NaN). Nous pouvons utiliser la méthode `isnull` pour faire cela.
La méthode `isnull` comparera chaque cellule avec une valeur nulle. Si un élément
a une valeur null, une valeur `True` lui sera affectée dans l'objet de sortie.

```
pd.isnull (isf_df)
```
{: .language-python}

Un extrait du résultat estci-dessous:

```
      présentérecord_id mois jour année plot_id espèce_id sexe arrière-pied-longueur poids
0 Faux Faux Faux Faux Faux Faux Faux Faux Faux Faux Vrai
1 faux faux faux faux faux faux faux faux Vrai
2 faux faux faux faux faux faux faux faux Vrai
faux 3 faux faux faux faux faux faux faux Vrai
faux 4 faux faux faux faux faux faux faux Vrai

[35549 lignes x 9 colonnes]
```
{ : .language-python}

Pour sélectionner les lignes contenant des valeurs NULL, nous pouvons utiliser
le masque en tant qu’index pour sous-nos données comme suit:

```
définir# Pour sélectionner uniquement les lignes avec des valeurs NaN, nous pouvons utiliser le paramètre () »méthode
surveys_df[pd.isnull (surveys_df) .Tout (axe = 1)]
```
{: .langue-python}

Notez que la colonne` weight` de notre dataframe contient beaucoup`null` ou`NaN`
valeurs. Nous étudierons les moyens dece problème dans la leçon 03.

résoudreNous pouvons également exécuter `isnull` sur une colonne particulière. Que fait le code ci-dessous?

```
# Qu'est-ce que cela fait?
empty_weights = sondages_df [pd.isnull (sondages_df ['poids'])]] ['poids']
print (empty_weights)
```
{: .language-python}

Prenons une minute pour regarder la déclaration ci-dessus. Nous utilisons l'booléen
objet`pd.isnull (isf_df ['weight'])` `comme index de` isf_df`. Nous
demandons à Python de sélectionner les lignes qui ont une valeur `NaN` de poids.


> ## Challenge - Mettre tous
ensemble>>
1. Créez une nouvelle tramedonnées qui ne contient queobservations avecvaleurs sexuelles
qui>sont ** pas **sexe féminin ou masculin. Affectez chaque valeur de sexe dans le nouveau DataFrame à une
nouvelle valeur de 'x'. Déterminez le nombre de valeurs NULL dans le sous-ensemble.
>>
2. Créez une nouvelle tramedonnées qui ne contient queobservations qui sont des hommes de
sexe>ou femme et oùvaleurs de poids sont supérieures à 0. Créer une barre
empilées>parcelle de poids moyen par parcelle avechommes vs valeurs femelles empilées pour
chaque>plot .
{: .challenge}

{% include links.md%}



