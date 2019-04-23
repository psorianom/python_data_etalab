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
nous pouvons sélectionner toutes les données d'une colonne nommée `Departements` à partir du DataFrame `isf_df` par son nom. Il y a deux façons de procéder:

```python
# CONSEIL: utilisez la méthode `.head()` décrite précédemment pour raccourcir la sortie.
# Méthode 1: sélectionnez un "sous-ensemble" de données en utilisant le nom de colonne
isf_df['Departements']

# Méthode 2: utilisez le nom de la colonne comme "attribut"; donne la même sortie
isf_df.Departements
```

Nous pouvons également créer un nouvel objet contenant uniquement les données de la
colonne `Departements` comme suit:

```python
# Crée un objet, Surveysspecies, qui uniquement contient la colonne `Species_id`.
departement_isf = isf_df['Departements']
```

Nous pouvons aussi passer une liste de noms de colonnes, en tant qu'index pour sélectionner les colonnes dans cet
ordre. Ceci est utile lorsque nous devons réorganiser nos données.

**REMARQUE:** Si un nom de colonne n'est pas contenu dans le DataFrame, une exception (erreur) sera déclenchée.

```python
# Sélectionnez les colonnes des espèces et des parcelles dans DataFrame
isf_df[['Commune', 'nom_redevables']]

# Que se passe-t-il lorsque vous retournez l'ordre?
isf_df[['nom_redevables', 'Commune']]

# Que se passe-t-il si vous demandez une colonne qui n'existe pas?
isf_df ['Communes']
```

Python nous dit de quel type d'erreur il se trouve dans le traçage, en bas, il indique
`KeyError: 'Communes'` ce qui signifie que `Communes` n'est pas un nom de colonne valide (ni une clé valide dans
le dictionnaire de types de données Python associé).

## Extraction de sous-ensembles basés sur une plage: Découpage

> ## Rappel
> Python utilise l'indexation basée sur 0.

Rappelons-nous que Python utilise l'indexation 'basée sur 0. Cela signifie que le premier élément d'un objet est situé à la position
0. Cela diffère d'autres outils comme R et Matlab qui indexent les éléments dans les objets à partir de 1.

```
# Crée une liste de nombres:
a = [1, 2, 3, 4, 5]
```
{: .language-python}

! [Diagramme d'indexation](../fig/slicing-indexing.png)
! [Diagramme de découpage](../fig/slicing-slicing.png)


## Challenge - Extraction

>1. Quelle est la sortie du code ci-dessous ?

```python
a[0]
```
>2. Et de celui-ci ?
```python
a[5]
```
>3. Pourquoi il existe une erreur dans le code précédent ?
>4. Et ça?

```python
a[len(a)]
```

##Génération des sous-ensembles de lignes en Python

Trancher les données en useutilisant l'opérateur `[]` sélectionne un ensemble de des lignes et/ou des colonnes d'un
DataFrame. Pour découper un ensemble de lignes, vous utilisez la syntaxe suivante:
`data[start: stop]`. Lors du découpage en pandas, la limite de départ est incluse dans la
sortie. La limite d'arrêt est un pas *AU-DELA* de la ligne que vous souhaitez sélectionner. Donc, si vous
souhaitez sélectionner les lignes 0, 1 et 2, votre code ressemblera à ceci:

```python
# Sélectionnez les lignes 0, 1, 2 (la ligne 3 n'est pas sélectionnée)
isf_df[0: 3]
```

La borne d'arrêt en Python est différent de ce à quoi vous pourriez être habitué dans des langages comme Matlab et R.

```python
# Sélectionnez les 5 premières lignes (lignes 0, 1, 2, 3, 4)
isf_df[:5]

# Sélectionnez le dernier élément de la liste
# (la tranche commence au dernier élément et se termine à la fin de la liste)
isf_df[-1:]
```

Nous pouvons également réaffecter des valeurs dans des sous-ensembles de notre DataFrame.

Mais avant cela, examinons la différence entre le concept de copie d'objets et le concept de référencement d'objets en Python.

## Copier des objets vs référencer des objets en Python

Commençons par un exemple:

```python
# Utilisation de la méthode 'copy()'
true_copy_isf_df = isf_df.copy()

# Utilisation de l'opérateur '='
ref_isf_df = isf_df
```

Vous pourriez penser que le code `ref_isf_df = isf_df` crée une nouvelle
copie distincte de l'objet `isf_df` DataFrame. Cependant, l’utilisation de l'opérateur `=`
dans l’instruction `y = x` ne crée pas **une copie** de notre
DataFrame. À la place, `y = x` crée une nouvelle variable `y` qui fait référence au
même **objet** que celui auquel `x` fait référence. D'ailleurs, il n'y a que
un objet (le DataFrame) qui  `x` et `y` réfèrent.

En revanche, la méthode `copy()` d'un DataFrame crée une copie du
DataFrame.

Examinons ce qui se passe lorsque nous réaffectons les valeurs d'un sous-ensemble du
DataFrame qui fait référence à un autre objet DataFrame:

```python
# Assigne la valeur `0` aux trois premières lignes de données du DataFrame
ref_isf_df[0: 3] = 0
```

Essayons le code suivant:

```python
# ref_isf_df a été créé à l'aide de l'opérateur '='
ref_isf_df.head()

# isf_df est l'original du cadre de données
isf_df.head()
```

Quelle est la différence entre ces deux dataframes?

Lorsque nous avons affecté la valeur `0` aux 3 premières colonnes à l'aide du
DataFrame `ref_isf_df`, le DataFrame `isf_df` est également modifié.
Rappelez-vous que nous avons créé l'objet de référence `ref_isf_df` ci-dessus lorsque nous avons
fait `ref_isf_df = isf_df`. Rappelez-vous que `isf_df` et `ref_isf_df` se
réfèrent au même objet exact DataFrame. Si l'un modifie l'objet,
la référence voit les mêmes modifications dans l'objet de référence.

** Pour revoir et récapituler **:

- **Copy** utilise la méthode `copy()` du dataframe

```python
  true_copy_isf_df = isf_df.copy ()
```
- Une **référence** est créé en utilisant l'opérateur `=`

```python
  ref_isf_df = isf_df
```

D'accord, c'est assez de cela. Créons une nouvelle dataframe à partir du données du fichier CSV d'origine.

```python
isf_df = pd.read_csv("data/isfcom2017.csv")
```

## Découper des sous-ensembles de lignes et de colonnes en Python

Nous pouvons sélectionner des plages spécifiques de nos données dans la ligne et les directions de colonne en
utilisant l’indexation par étiquette ou par un nombre entier.

- `loc` est principalement une indexation *label*. Les entiers peuvent être utilisés mais ils sont interprétés comme un * label *.
- `iloc` est principalement un *index* basé sur l'indexation

Pour sélectionner un sous-ensemble de lignes **et** colonnes de notre DataFrame, nous pouvons utiliser la
méthode `iloc`. Par exemple, nous pouvons sélectionner les premières trois colonnes et les premières trois lignes, comme:

```python
# iloc [découpage en rangées, découpage en colonnes]
isf_df.iloc [0: 3, 0:3]
```

qui donne la **sortie** 

```
  Region  Departements  Code_commune_INSEE_
0   AUVERGNE-RHONE-ALPES  AIN   1053
1   AUVERGNE-RHONE-ALPES  AIN   1283
2   AUVERGNE-RHONE-ALPES  ALLIER  3185
```

Notez que nous avons demandé une tranche de 0:3. Cela a donné 3 lignes de données. Lorsque vous
demandez 0:3, vous indiquez à Python de commencer à l'index 0 et de sélectionner les lignes
0, 1, 2 **jusqu'à 3 (3 non compris)**.

Explorons d’autres manières d’indexer et de sélectionner des sous-ensembles de données:

```python
# Sélectionnez toutes les colonnes pour les lignes d’indices 0 et 10
isf_df.loc[[0, 10], :]

# À quoi sert-il?
  isf_df.loc[0, ['Region', 'Commune', 'impot_moyen_euros']]

# Que se passe-t-il lorsque vous tapez le code ci-dessous?
isf_df.loc[[0, 10, 388], :]
```

**NOTE**: Les labels doivent être trouvées dans le DataFrame ou vous obtiendrez un `KeyError`.

L'indexation par les étiquettes `loc` diffère de l'indexation par les entiers `iloc`.
Avec `loc`, les bornes de départ et d’arrivée sont **inclusives**. Lorsque vous utilisez
`loc`, vous pouvez utilizer des entiers, mais les entiers font référence à l'étiquette del index et non pas à la position. Par exemple, utiliser `loc` et sélectionner 1:4
donnera un résultat différent de celui qui utilise `iloc` pour sélectionner les lignes 1: 4.

Nous pouvons également sélectionner une valeur de données spécifique en utilisant une ligne et une colonne du DataFrame avec `iloc`:

```python
# Syntaxe pour l'indexation iloc permettant de rechercher un élément de données spécifique
dat.iloc [ligne, colonne]
```

Dans notre exemple avec `iloc`,

```python
isf_df.iloc[2, 3]
```

donne le ** résultat **

```
'Montlucon'
```

N'oubliez pas que l'indexation Python commence à 0. Ainsi, l'emplacement de l'index [2, 3]
sélectionne l'élément  dans la ligne 2  et la colonne 3 dans le DataFrame.



## Défi
>1. Qu'estce qui se passe lorsque vous exécutez:
>- `isf_df [0:1]` 
>- `isf_df[4]`
>- `isf_df[:-1]`
>
>2. Qu'estce qui se passe lorsque vous lancez:
>-`isf_df.iloc[0:4, 1:4]`
>-`isf_df.loc[0: 4, 1:4]`
>
>- Comment sont les deux commandes différentes?


## Découpage de données à l'aide de critères

Nous pouvons également sélectionner un sous-ensemble de nos données à l'aide de critères. Par exemple, nous pouvons
sélectionner toutes les lignes dont la valeur de région est La Réunion:

```python
isf_df[isf_df.Region == "LA REUNION"]
```

ce qui produit le résultat suivant:

```
  Region  Departements  Code_commune_INSEE_   Commune   nom_redevables  patrimoine_moyen_euros  impot_moyen_euros
380   LA REUNION  LA REUNION  97408   LA POSSESSION   80  2063527   7400
381   LA REUNION  LA REUNION  97409   SAINT ANDRE   59  2679497   10246
382   LA REUNION  LA REUNION  97411   SAINT DENIS   517   2530939   11143
383   LA REUNION  LA REUNION  97415   SAINT PAUL  318   2509763   9170
384   LA REUNION  LA REUNION  97416   SAINT PIERRE  166   2678032   10864
385   LA REUNION  LA REUNION  97414   SAINT-LOUIS   51  2464169   9331
386   LA REUNION  LA REUNION  97418   SAINTE MARIE  74  2117078   8348
387   LA REUNION  LA REUNION  97422   TAMPON  149   2261774   9067

```

Ou nous pouvons sélectionner toutes les lignes ne contenant pas La Réunion:

```python
isf_df[isf_df.Region != "LA REUNION"]
```

Nous pouvons aussi définir des ensembles de critères:

```python
isf_df[(isf_df.nom_redevables>=200) & (isf_df.nom_redevables<=500)]
```

### Syntaxe Python Cheat Sheet

Nous pouvons utiliser la syntaxe ci-dessous lorsque on rêquete les données par critère dans un DataFrame.
Expérimentez avec la sélection de divers sous-ensembles des données "enquêtes".

* Égal: `==`
* Pas égal: `! =`
* Supérieur à, inférieur à: `>` ou `<`
* Supérieur ou égal à `> =`
* Inférieur ou égal à `<=`


>## Challenge -
1. Sélectionnez un sousensemble de lignes dans le dataframe `isf_df` dataframe qui contiennent des données 
>  de la région PROVENCE-ALPES-COTE D'AZUR et qui contiennent un nom_redevables supérieure à 177.

>>
2. Vous pouvez utiliser la commande `isin` en Python pour interroger des données basées sur
>  liste de valeurs comme suit:
>>
```python

> isf_df[isf_df['Region'] isin ([listGoesHere])]

```

>Utilisez la fonction `isin` pour trouver toutes les lignes qui contiennent des redevables dans les departements de MORBIHAN, CHER, EURE-ET-LOIR et INDRE. 
> Combien d'enregistrements contiennent ces valeurs?

>> 3. Le symbole `~` dans Python peut être utilisé pour renvoyer l'OPPOSITE de la
> sélection que vous spécifiez dans Python. Cela équivaut à **is not in**.
> Rédigez une requête qui sélectionne toutes les lignes dont le departement n'est PAS égal à "BRETAGNE" ou "PAYS DE LA LOIRE" dans
les données de l'ISF.
