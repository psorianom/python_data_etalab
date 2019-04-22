---
title: En commençant avec les données
teaching: 30
exercises: 30
questions:
   - "Comment importer des données en Python?"
   - "Qu'est-ce que Pandas?"
   - "Pourquoi devrais-je utiliser Pandas pour travailler avec des données?"
objectifs:
   - "Explorer le répertoire de l'ateliers et télécharger un jeu de données."
   - "Expliquer ce qu'est une librairie et à quoi elle sert."
   - "Décrivez qu'est-ce que c'est Pandas, la bibliothèque d'analyse de données Python."
   - "Charger en memoire Pandas.
   - "Utiliser `read_csv` pour lire des données tabulaires en Python."
   - "Décrivez qu'est-ce que c'est un **DataFrame** en Python."
   - "Accéder aux données stockées dans un **DataFrame** et les résumer."
   - "Définir l'indexation et sa relation avec les structures de données."
   - "Effectuer des opérations mathématiques de base et calculer des statistiques descriptives sur les données contenues dans un Pandas **Dataframe**."
   - "Créer des graphiques simples."
keypoints:
   - "FIXME"
---

# Utilisation des DataFrames Pandas en Python

Nous pouvons automatiser le processus de manipulation des données avec Python. Il vaut la peine de passer du
temps à écrire le code pour effectuer ces tâches puisqu’une fois écrit,
nous pouvons l’utiliser encore et encore dans différents ensembles de données utilisant un format
similaire. Cela rend nos méthodes facilement reproductibles. Il est également facile de
partager notre code avec nos collègues et ceux-ci peuvent reproduire la même
analyse.

### Commencer au même endroit

Pour que la leçon sorte le mieux possible, assurons-nous que nous tous sommes dans le même répertoire. Cela devrait nous aider à éviter les inconvénients liés aux noms et chemins de répertoires et de fichiers. 


### Nos données

Pour cette leçon, nous allons utiliser des données du Ministère de l'économie et des finances, notament sur l'[Impôt de solidarité sur la fortune](https://www.data.gouv.fr/en/datasets/impot-de-solidarite-sur-la-fortune/).  

Pour chaque commune de plus de 20 000 habitants ayant plus de 50 redevables à l'Impôt de solidarité sur la fortune (ISF), vous pouvez connaître le nombre de redevables, le patrimoine moyen et la cotisation moyenne.

Vous allez trouver ce dataset sur le repertoire `data/` avec le nom `isfcom2017.csv`



Les premières lignes de notre dossier sont les suivantes:

```
Region  Departements  Code_commune_INSEE_ Commune nom_redevables  patrimoine_moyen_euros  impot_moyen_euros
AUVERGNE-RHONE-ALPES  AIN 1053  BOURG-EN-BRESSE 157 2261155 8297
AUVERGNE-RHONE-ALPES  AIN 1283  OYONNAX 88  3236170 12078
AUVERGNE-RHONE-ALPES  ALLIER  3185  MONTLUCON 111 2591793 9721
AUVERGNE-RHONE-ALPES  ALLIER  3190  MOULINS 59  2524509 10026
AUVERGNE-RHONE-ALPES  ALLIER  3310  VICHY 177 2369664 7316
AUVERGNE-RHONE-ALPES  CANTAL  15014 AURILLAC  118 2606677 9251
AUVERGNE-RHONE-ALPES  DROME 26198 MONTELIMAR  170 2694564 10374

```


---

## À propos des bibliothèques
Une bibliothèque en Python contient un ensemble. d'outils (appelés
fonctions) qui effectuent des tâches dans nos données. Importer une bibliothèque revient
à sortir un morceau de laboratoire de notre casier et à l’assembler sur notre
table de travail pour l’utiliser dans notre projet. Une fois la bibliothèque
installée, elle peut être utilisée et appelée pour effectuer de nombreuses tâches.

## Pandas en Python
Une des meilleures options pour travailler avec des données tabulaires en Python consiste à utiliser
[Python Data Analysis Library](http://pandas.pydata.org/) (aka Pandas). La
bibliothèque Pandas fournit des structures de données, génèregraphiques de haute
desqualité avec [matplotlib](http://matplotlib.org/) et s’intègre parfaitement
avec les autres bibliothèques utilisant les **tableaux** de [NumPy](http://www.numpy.org/)
(qui est une autre bibliothèque Python).

Python ne charge pas toutes les bibliothèques disponibles par défaut. Vous devez utiliser
l'instruction `dansimportation notre codeutiliser les fonctions debibliothèque.
Pour importer une bibliothèque, la syntaxe `import libraryname` est utilisée. Si vous
voulez également mettre un pseudo pour raccourcir les commandes, vous pouvez
ajouter `asadnameAUsar`. Un exemple consiste à importer la bibliothèque pandas en
utilisant son pseudonyme commun `pds` comme ci-dessous.


```python
import pandas as pds
```


Chaque fois que nous appelons une fonction qui se trouve dans la bibliothèque, la syntaxeest utilisée
`LibraryName.FunctionName '. Ajouter le nom de la bibliothèque
avec un `.` avant le nom de la fonction indique à Python où trouver la fonction.
Dans l'exemple précédent, nous avons importé les pandas sous le nom de `pds`. Cela signifie quepas
nous n'aurons à écrire `pandas` chaque fois que nous appellerons une fonction Pandas et que nous leuniquement
feronsavec son pseudo.

# Lecture des données au CSV à l'aide de pandas

Nous commencerons par rechercher et lire les données du recensement au
formatformat CSV. CSV signifie «valeurs séparées par des virgules», séparées par des virgules, et constitue un moyen courant de sauvegarder des données. D'autres
symboles peuvent être utilisés, vous pouvez trouver des valeurs séparées par des
tabulations, des points-virgules ou des blancs. Il est facile de remplacer
un séparateur par un autre pour utiliser votre application. La première ligne du
fichier contient généralement les en-têtes indiquant qu'il y en a dans
chaque colonne. Les fichiers CSV (et autres séparateurs) facilitent le partage des données et peuvent
être importés et exportés à partir de différents programmes, y compris Microsoft Excel.
Pour plus de détails sur les fichiers CSV, voir la leçon [Organisation des données dans des tableurs] (http://www.datacarpentry.org/spreadsheet-ecology-lesson/05-exporting-data/).
Nous pouvons utiliser la fonction `pandas.read_csv`pour ouvrir le fichier directement dans
un[dataframe](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe).

## Alors, qu'est-ce qu'un DataFrame?

Un ** DataFrame ** est une structure de données à deux dimensions dans laquelle vous pouvez
enregistrer des données de types différents (tels que des caractères, des entiers, des valeurs à virgule flottante, des
facteurs, etc.) dans des colonnes. Il est similaire à une feuille de calcul, une table SQL ou
le `data.frame` de R. Un ** DataFrame ** a toujours un index (avec un début à 0). L'index
fait référence à la position d'un élément dans la structure de données.

```python
# Note pds.read_csv utilisé parce queimportation comme pandas géantspd
pds.read_csv( "data/isfcom2017.csv")
```

La commande cidessus conduit à l'autre **sortie**:

```
  Region  Departements  Code_commune_INSEE_   Commune   nom_redevables  patrimoine_moyen_euros  impot_moyen_euros
0   AUVERGNE-RHONE-ALPES  AIN   1053  BOURG-EN-BRESSE   157   2261155   8297
1   AUVERGNE-RHONE-ALPES  AIN   1283  OYONNAX   88  3236170   12078
2   AUVERGNE-RHONE-ALPES  ALLIER  3185  MONTLUCON   111   2591793   9721
3   AUVERGNE-RHONE-ALPES  ALLIER  3190  MOULINS   59  2524509   10026
4   AUVERGNE-RHONE-ALPES  ALLIER  3310  VICHY   177   2369664   7316
5   AUVERGNE-RHONE-ALPES  CANTAL  15014   AURILLAC  118   2606677   9251poids record_id année mois jour plot_id hindfoot_length sexe
0 116 Juillet 1977 M 32 NaN 2 NL
1 Février 16 Juillet 1977 33 M NaN3 NL
2 3 16 Juillet 1977 2 37 DM F
NaN37 Avril, 16 DM 1977 7 M 36 NaN
4 5 7 16 35 1977 3 M NaNDM
...
35545 35544 31 Décembre 2002 15 AH NaN NaN NaN
35546 35545 31 Décembre 2002 15 AH NaN NaN NaN
35547 35546 31 Décembre 2002 10 15 14F RM
35 54735548 31 décembre 2002 7 51M dO 36
35 548 3554931 décembre 2002 5 NaN NaN NaN NaN

388 rows × 7 columns
```


Nous pouvons voir que 388 lignes ont été lues. Chacune des lignes a
7 colonnes. La première colonne est l'index DataFrame. L'index est utilisé
pour identifier la position des données, mais ce n'est pas une colonne du DataFrame.
Il semble que la fonction `read_csv`de Pandas lise correctement le fichier.
Cependant, nous n’avons enregistré aucune donnée en mémoire, nous ne pouvons donc pas les utiliser. 
Nous devons affecter le **DataFrame** à une variable. Rappelez vous
qu'unevariable est un nom pour une valeur. Nous pouvons créer un
nouvel objet avec le nom de la variable et lui attribuer une valeur en utilisant `=`.

Appeldonnées de recensement importées `isf_df`:

```python
isf_df = pds.read_csv ( "data/isfcom2017.csv")
```

Nous pouvons voir le contenu de `isf_df` en tapant le nom dans la ligne de commande.

```python
isf_df
```


Ce qui affiche le contenu comme auparavant.

Remarque: si la sortie est plus large que l'écran du terminal lors de l'impression, le résultat sera
différent au fur et à mesure que le jeu de données volumineux passe. Vous pouvez simplement voir la
dernière colonne des données. N'ayez crainte, toutes les données sont là, si vous naviguez au-dessus de votre terminal.
Ci-dessour, nous sélectionnons que quelquesunes des lignes, ce qui rendra plus facile à tenir sur
une cellule de sortie, on peut voir que Pandas format les données afin qu'ils rentrent dans l'écran:

```python
isf_df.head () # La méthode head() affiche les premières lignes d'un fichier. Il
               # est discuté ci-dessous.
```

```
  Region  Departements  Code_commune_INSEE_   Commune   nom_redevables  patrimoine_moyen_euros  impot_moyen_euros
0   AUVERGNE-RHONE-ALPES  AIN   1053  BOURG-EN-BRESSE   157   2261155   8297
1   AUVERGNE-RHONE-ALPES  AIN   1283  OYONNAX   88  3236170   12078
2   AUVERGNE-RHONE-ALPES  ALLIER  3185  MONTLUCON   111   2591793   9721
3   AUVERGNE-RHONE-ALPES  ALLIER  3190  MOULINS   59  2524509   10026
4   AUVERGNE-RHONE-ALPES  ALLIER  3310  VICHY   177   2369664   7316
```

## Exploration de données 

Nous utilisons la `type` voir ce qu'est `isf_df`:

```python
print(type(isf_df))
```
```python
<class 'pandas.core.frame.DataFrame'>
```

Comme prévu, il s'agit d'un **DataFrame** (ou, en utilisant le nom complet pour
lequel Python utilise en interne, un  `pandas.core.frame.DataFrame`).

Quel genre de colonnes `isf_df` contient ? Les dataframes ont un attribut
appelé `dtypes` qui répond à cette question:

```python
isf_df.dtypes
```

```
Region                    object
Departements              object
Code_commune_INSEE_       object
Commune                   object
nom_redevables             int64
patrimoine_moyen_euros     int64
impot_moyen_euros          int64
dtype: object
```


Toutes les valeurs d'une colonne ont le même type. Par exemple, les `nom_redevables` ont
le type `int64`, qui est un type de nombre entier. Le type `object` n'a pas
un nom très utile, mais dans ce cas, il représente un string (comme "Oyonnax" dans le nom de la commune).

Dans une autre leçon, nous discuterons de la signification de différents types.

### Façons utiles de voir les objets **DataFrame** en Python

Il existe différentes façons de résumer et d'accéder aux données stockées dans un DataFrame, en
utilisant les attributs et les méthodes fournis par l'objet DataFrame.

Pour accéder à un attribut, utilisez le nom de l'objet **DataFrame** suivi
du nom de l'attribut `df_object.attribute`. Utiliser le **DataFrame** `isf_df`
et l'attribut `columns`, pour retrouver un index de tous les noms des colonnes
du **DataFrame** (avec` isf_df.columns`).

Les méthodes sont appelées de la même manière en utilisant la syntaxe `df_object.method ()`.
Par exemple, `Surveils_df.head ()` obtient les premières lignes de la méthode **DataFrame**
`isf_df` en utilisant la méthode `head()`. Avec une méthode, nous pouvons fournir
des informations supplémentaires aux parents pour contrer leur comportement.


Regardons les données en utilisant ceci.

##  Dèfi

En utilisant notre dataframe `isf_df`, exécutez les attributs et méthodes suivants
et observez-les.

> 1. `isf_df.columns`
> 2. `isf_df.shape` Prenez note du résultatde `shape` - Quel format a le résultat
>    de l'attribut qui renvoie la forme d'un DataFrame?
> 3. `isf_df.head()` Exécute également `isf_df.head(15)` qu'est-ce que cela fait?
> 4. `isf_df.tail()`



## Calcul des statistiques des données dans un **DataFrame** de Pandas

Nous avons lu les données en Python. Calculons maintenant quelques statistiques pour
comprendre un peu les données avec lesquelles nous travaillons. Nous voudrons peut-être
savoir combien des redevables existent dans chaque commune ou combien d'espèces
ont été capturées. 

Commençons a explorer les données:

```python
# Regardons les colonnes
de isf_df.columns
```

qui retourne :

```python
Index(['Region', 'Departements', 'Code_commune_INSEE_', 'Commune',
       'nom_redevables', 'patrimoine_moyen_euros', 'impot_moyen_euros'],
      dtype='object')
```

Obtenir une liste de toutes les régions. La fonction `pds.unique` nous indique 
les valeurs distinctes présentes dans la colonne `Region`.

```python
pds.unique(isf_df['Region'])
```

ce qui **retourne**:

```
array(['AUVERGNE-RHONE-ALPES', 'BOURGOGNE-FRANCHE-COMTE', 'BRETAGNE',
       'CENTRE-VAL DE LOIRE', 'CORSE', 'GRAND-EST', 'GUADELOUPE', 'GUYANE',
       'LES-HAUTS-DE-FRANCE', 'ILE-DE-FRANCE', 'MARTINIQUE', 'NORMANDIE',
       'NOUVELLE-AQUITAINE', 'OCCITANIE', 'PAYS DE LA LOIRE',
       "PROVENCE-ALPES-COTE D'AZUR", 'LA REUNION'], dtype=object)
```

## Dèfi
### Statistiques
> 1. Créez une liste des codes commune INSEE ("Code_commune_INSEE_") figurant dans les données.
>    Appelons cette liste `insee_codes`. Combien de codes ont les données?,

> 2. Quelle est la différence entre `len(insee_codes)` et`isf_df['Code_commune_INSEE_'].nunique()`?


# Groupes dans les **Dataframes**

Parfois, nous souhaitons calculer des statistiques de données regroupées par
sous-ensembles ou attributs de nos données. Par exemple, si nous voulons calculer le
patrimoine moyen de nos redevables par departement.

Nous pouvons calculer des statistiques de base de toutes les données d’une colonne
à l’aide de la commande suivante:

```python
isf_df['patrimoine_moyen_euros'].describe()
```

renvoie le résultat suivant:

```
count       388.00
mean    2556011.69
std      434621.56
min     1936554.00
25%     2325731.25
50%     2477402.00
75%     2677602.25
max     6026825.00
Name: patrimoine_moyen_euros, dtype: float64
```

peut également extraire une métrique particulière ::

```python
isf_df['patrimoine_moyen_euros']. min ()
isf_df['patrimoine_moyen_euros'].max ()
isf_df['patrimoine_moyen_euros'].mean()
isf_df['patrimoine_moyen_euros'].std()
isf_df['patrimoine_moyen_euros'].count()
```


Mais si nous voulons extraire des informations à l'aide d'une ou plusieurs variables, par exemple le sexe, nous pouvons utiliser la méthode `.groupby` de *Pandas*. Une fois que nous avons créé un groupe **DataFrame** , nous pouvons calculer des statistiques en fonction du groupe de notre choix.

```python
# Groupe par région
grouped_data = isf_df.groupby('Region')
```


La **fonction** `describe` de Pandas renvoie des statistiques descriptives y compris:
moyenne, meadiana, max, min, std et comptage pour une colonne particulière des
données. La fonctionne `describe` renvoie que les valeurs de ces statistiques pour les
colonnes numériques.

```python
# Statistiques pour toutes les colonnes numériques
grouped_data.describe()
# Renvoie la moyenne de chaque colonne numérique 
grouped_data.mean ()

```

```
  nom_redevables  patrimoine_moyen_euros  impot_moyen_euros
Region      
AUVERGNE-RHONE-ALPES  362.11  2532303.83  9437.80
BOURGOGNE-FRANCHE-COMTE   190.91  2588278.55  10198.09
BRETAGNE  355.56  2489823.22  8810.44
CENTRE-VAL DE LOIRE   253.80  2446725.60  9840.60
CORSE   197.50  2631619.00  11437.00
GRAND-EST   302.35  2718509.35  10713.05
GUADELOUPE  101.00  2603757.00  10851.00
GUYANE  58.00   2729433.50  14088.50
ILE-DE-FRANCE   788.74  2576787.71  10013.73
```

La commande `groupby` est très puissant et permet la génération rapide de
statistiques descriptives.

## Défi

> 1. Combien des redevables existent par departement ?
> 2. Que se passe-t-il lorsque vous groupez sur deux colonnes à l'aide de l'instruction suivante
>    et que vous prenez ensuite les valeurs moyennes:
>    `grouped_data2 = isf_df.groupby(['Region', 'Departements'])` 
>    `grouped_data2.mean()`
> 3. Calculez les statistiques de l'impot moyen pour chaque département. Conseil:
>    Vous pouvez utiliser la syntaxe suivante pour créer uniquement des statistiques pour une
>   colonne de vos données   `par_departement['impot_moyen_euros'].describe()`


## Compter rapidement avec Pandas

Maintenant, comptons le nombre de registres de chaque région. Nous pouvons le faire
de différentes manières, mais nous utiliserons `groupby` combiné à `count()`.

```python
# Comptez le nombre d'échantillons par région
counts_by_region = isf_df.groupby('Region')["Departements"].count()
print(counts_by_region)
```

## Fonctions mathématiques de base

Nous pouvons effectuer des opérations dans une colonne de
données. Par exemple, multiplions toutes les valeurs du patrimoine moyen par 2. Une utilisation
plus utile pourrait être de normaliser les données avec la moyenne, l'écart type ou une autre valeur calculée de nos données.

```python
# Multipliant toutes les valeurs du patrimioine moyen pour 2
isf_df["patrimoine_moyen_euros"] * 2
```


## Graphiques avec Pandas

Nous peuvons également faire des graphiques à l'aide de Pandas à propos des statistiques descriptives.

```python
# Assurez-vous que les images apparaissent insérées dans iPython Notebook
% matplotlib inline
# Créez un graphique à barres
# Registres par région
counts_by_region.plot(kind = 'bar')
```

On peut aussi voir combien des redevables ont été enregistrés par departement:

```python
par_departement = isf_df.groupby('Departements')['nom_redevables'].nunique()
# Nous avons également tracé ce
par_departement.plot(kind = 'bar')
```


# Défi

> 1. Créer un graphique du poids patrimoine moyen par departement.
> 2. Créer un graphique du patrimoine moyen par commune que pour la région Ile-de-France

```python
isf_df[isf_df["Region"] == "ILE-DE-FRANCE"][["Commune", "patrimoine_moyen_euros"]].set_index("Commune").plot(figsize=(30,10),kind="bar")
```

