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

Pour que la leçon sorte le mieux possible, assurons-nous que nous tous sommes dans le même répertoire. Cela devrait nous aider à éviter les inconvénients liés aux noms et chemins de répertoires et de fichiers. Pour commencer, accéde au répertoire `workshop`.


### Nos données

Pour cette leçon, nous allons utiliser les données de "Portal Teaching", qui est un-
sousensemble des données étudiées par Ernst et al.
[Surveillance à long terme et manipulation expérimentale d'un écosystème du désert de Chihuahuan près de Portal, Arizona, États-Unis] (http://www.esapubs.org/archive/ecol/E090/118/default.htm).

Nous utiliserons les données de [Base de données d’enseignement du projet de portail] (https://figshare.com/articles/Portal_Project_Teaching_Database/1314459).
Cette section utilise la `surveys.csv` qui peut être téléchargépartir:
[https://ndownloader.figshare.com/files/2292172](https://ndownloader.figshare.com/files/2292172)

Soitétude de les espèces et le poids des animaux capturés sur les sites de notre zone d'
étude. L'ensemble de données est stocké dans un fichier `.csv`: chaque ligne
contient des informations sur un seul animal et les colonnes représentent:

| Colonne | Description |
| ----------------- | ------------------------------- -------- |
| record_id | identifiant unique de l'observation |
| mois | mois d'observation |
| jour | Jour d'observation |
| année | année d'observation |
| plot_id | ID d'un site particulier |
| espèce_id | code à deux lettres |
| sexe | sexe de l'animal ("M", "F") |
| longueur pied arrière | taille de la jambe en mm |
| poids | poids de l'animal en grammes |


Les premières lignes de notre dossier sont les suivantes:

~~~
record_id, mois, jour, année, plot_id, species_id,sexe, hindfoot_length,poids,
1,7,16,1977,2  NL, F, 32,
2 , 7.16.1977.3, NL, M, 33,,
3.716.1977.2, DM, F, 37,
4.7, 16.1977.7, DM, M, 36,
5.7 16,1977,3, DM, M, 35,
6,7,16,1977,1, PF, M, 14,
7,7,16,1977,2, PE, F,
8,7,16, 1977,1, DM, M, 37,
9,7,16,1977,1, DM, F, 34,
~~~
{: .output}

---

## À propos des bibliothèques
Une bibliothèque en Python contient un ensemble. d'outils (appelés
fonctions) qui effectuent des tâches dans nos données. Importer une bibliothèque revient
à sortir un morceau de laboratoire de notre casier et à l’assembler sur notre
table de travail pour l’utiliser dans notre projet. Une fois la bibliothèque
installée, elle peut être utilisée et appelée pour effectuer de nombreuses tâches.

## Pandas en Python
Une des meilleures options pour travailler avec des données tabulaires en Python consiste à utiliser
[Python Data Analysis Library] (http://pandas.pydata.org/) (aka Pandas). La
bibliothèque Pandas fournit des structures de données, génèregraphiques de haute
desqualité avec [matplotlib] (http://matplotlib.org/) et s’intègre parfaitement
avec les autres bibliothèques utilisant ** ** tableaux ** de [NumPy] (http: //www.numpy.org/)
(qui est une autre bibliothèque Python).

Python ne charge pas toutes les bibliothèques disponibles par défaut. Vous devez utiliser
l'instruction `dansimportation notre codeutiliser les fonctions debibliothèque.
Pour importer une bibliothèque, la syntaxe `import libraryname` est utilisée. Si vous
voulez également mettre un pseudo pour raccourcir les commandes, vous pouvez
ajouter `asadnameAUsar`. Un exemple consiste à importer la bibliothèque pandas en
utilisant son pseudonyme commun `pd` comme ci-dessous.


~~~
importer des pandas en tant que pd
~~~
{: .language-python}

Chaque fois que nous appelons une fonction qui se trouve dans la bibliothèque, la syntaxeest utilisée
`LibraryName.FunctionName '. Ajouter le nom de la bibliothèque
avec un `.` avant le nom de la fonction indique à Python où trouver la fonction.
Dans l'exemple précédent, nous avons importé les pandas sous le nom de `pd`. Cela signifie quepas
nous n'auronsà écrire `pandas` chaque fois que nous appellerons une fonction Pandas et que nous leuniquement
feronsavec son pseudo.

# Lecture des données auCSV à l'aide de pandas

Nous commencerons par rechercher et lire les données du recensement au
formatformat CSV. CSV signifie «valeurs
séparées par des virgules», séparées par des virgules, et constitue un moyen courant de sauvegarder des données. D'autres
symboles peuvent être utilisés, vous pouvez trouver des valeurs séparées par des
tabulations, des points-virgules ou des blancs. Il est facile de remplacer
un séparateur par un autre pour utiliser votre application. La première ligne du
fichier contient généralement les en-têtes indiquant qu'il y en a dans
chaque colonne. Les fichiers CSV (et autres séparateurs) facilitent le partage des données et peuvent
être importés et exportés à partir de différents programmes, y compris Microsoft Excel.
Pour plus de détails sur les fichiers CSV, voir la leçon [Organisation des données dans des tableurs] (http://www.datacarpentry.org/spreadsheet-ecology-lesson/05-exporting-data/).
Nous pouvons utiliser la fonction `Pandasread_csv`pour ouvrir le fichier directement dans
un[dataframe](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe).

## Alors, qu'est-ce qu'un DataFrame?

Un ** DataFrame ** est une structure de données à deux dimensions dans laquelle vous pouvez
enregistrer des données de types différents (tels que des caractères, des entiers, des valeurs à virgule flottante, des
facteurs, etc.) dans des colonnes. Il est similaire à une feuille de calcul, une table SQL ou
le `data.frame` de R. Un ** DataFrame ** a toujours un index (avec un début à 0). L'index
fait référence à la position d'un élément dans la structure de données.

~~~
# Note pd.read_csv utilisé parce queimportation comme pandas géantspd
pd.read_csv( "data / surveys.csv")
{~~~:
.langue-python}

La commande cidessus conduit à l'autre ** sortie**:

~~~
poids record_id année mois jour plot_id hindfoot_length sexe
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

[35549 lignes x 9 colonnes]
~~~
{:}.output

nous pouvons voir que35,549 lignes ont été lues. Chacune des lignes a
9 colonnes. La première colonne est l'index DataFrame. L'index est utilisé
pour identifier la position des données, mais ce n'est pas une colonne du DataFrame.
Il semble que la fonction `read_csv`de Pandas lise correctement le fichier.
Cependant, nous n’avons enregistré aucune donnée en mémoire, nous ne pouvons donc pas les utiliser
. Nous devons affecter ** DataFrame ** à une variable. Rappelezvous
qu'unevariable est un nom pour une valeuras` ou `x`data`.Nous pouvons créer un
nouvel objet avec le nom de la variable et lui attribuer une valeur en utilisant `=`.

Appeldonnées de recensement importées `surveys_df`:

~~~
surveys_df = pd.read_csv ( "données / surveys.csv")
{~~~:
.langue-python}

Notez que lorsattributionune données importées dataframe ** * * Pour une variable,
Python ne produit aucune sortie d'écran. Nous pouvons voir le contenu de `survey_df` en
tapant le nom dans la ligne de commande de Python.t.

~~~
Surveys_df
~~~
{: .language-python}

qui affiche le contenu comme auparavant.

Remarque: si la sortie est plus large que l'écran du terminal lors de l'impression, le résultat sera
différent au fur et à mesure que le jeu de données volumineux passe. Vous pouvez simplement voir la
dernière colonne des données:

~~~
NaN 17
18NaN
NaN19
20 NaN
21NaN
NaN22
23 NaN
24NaN
25 NaN
NaN 26
27NaN
28 NaN
NaN29
... ...
3551936,0
3552048,0



35521 45,0 35522 44,0 35523 27,0 35524 26,0


NaN
35528 25,0
35529 NaN
35530 NaN



35531 43,0 35532 48,0 35533 56,0 35534 53,0








NaN
35544 NaN
35545 NaN
35546 14.0
35547 51.0
35548 NaN

[35549 lignes x 9 colonnes]
~~~
{: .output}

N'ayez crainte, toutes les données sont là, si vous naviguez au-dessus de votre terminal.
ne sélectionnons que quelquesunes des lignes, ce qui rendra plus facile à tenir surde
une bornesortie,on peut voir que Panda formater les données afin que
affiché à l'écran:

~~~
surveys_df.head () # La méthode tête () affiche les premières lignes d'un fichier. Il
                 est discuté ci-dessous.
~~~
{:}.langue-python
~~~
  plot_id mois jour année record_id species_id sexe hindfoot_length \
5 6 7 16 1977 1 M 14,0 PF
Juillet 6 16 Juillet, 1977 2 PE F NaN
8 Juillet 16 Juillet 1977 1 DM 37,0 M
8 9 16 Juillet 1977 1 DM F
34,0 9 10 7 16 1977 6F 20,0PF

  poids
5 NaN
6NaN
NaN7
8NaN
9 NaN
~~~
{:}.output

##Explorationdonnées de recensementespèces

nouveaunous utilisons la `type` voir que quelque chose is`surveys_df`:est:

~~~
Type (surveys_df)

{~~~:.langue-python}
~~~
<class 'pandas.core.frame.DataFrame'>
~~ ~
{: .output}

Comme prévu, il s'agit d'un ** DataFrame ** (ou, en utilisant le nom complet pour
lequel Python utilise en interne, un  `pandas.core.frame.DataFrame`).

Quel genre de choses `survey_df` contient? La tramedonnées ** ** ont un attribut
appelé `dtypes` qui répondcette question:

~~~
surveys_df.dtypes
~~~
{:}.langue-python
~~~
RECORD_ID int64
int64 mois
jour int64
int64 année
plot_id int64
objetspecies_id
sexuelobject
hindfoot_length float64
weight float64
dtype: object
~~~
{: .output}

Toutes les valeurs d'une colonne ont le même type. Par exemple, les mois ont
le type `int64`, qui est un type de nombre entier.cellules de la colonne mois
ne peuvent pas avoir des fractions, mais colonnes weight` et
``hindfoot_length` peuvent, car ils sont tupo `float64`.Le type `object` n'a pas
un nom très utile, mais dans ce cas, il représente un mot (comme 'M' et 'F' dans
le cas du sexe).

Dans une autre leçon, nous discuterons de la signification de différents types.

### Façons utiles de voir les objets ** DataFrame ** en Python

Il existe différentes façons de résumer et d'accéder aux données stockées dans un DataFrame, en
utilisant les attributs et les méthodes fournis par l'objet DataFrame.

Pour accéder à un attribut, utilisez le nom de l'objet ** DataFrame ** suivi
du nom de l'attribut `df_object.attribute`. Utiliser le ** DataFrame ** `Surveils_df`
et l'attribut` colonnes`, un index de tous les noms des colonnes
du ** DataFrame ** sont accessibles avec` survey_df.columns`.

Les méthodes sont appelées de la même manière en utilisant la syntaxe `df_object.method ()`.
Par exemple, `Surveils_df.head ()` obtient les premières lignes de la méthode ** DataFrame **
`Surveys_df` en utilisant ** la méthode` la tête () `**. Avec une méthode, nous pouvons fournir
des informations supplémentaires aux parents pour contrer leur comportement.

Regardons les données en utilisant ceci.

> ## - Reto

DataFrames >> Utilisationnotre dataframe ** ** `survey_df`, exécutez les attributs et méthodes suivants
> et observez-les.

>> 1 `survey_df.columns`
> 2 `survey_df.shape` Prenez note du résultatde` shape` - Quel format a le résultat
>    de l'attribut qui renvoie la forme d'un DataFrame?

>>    Astuce:[Plusacercad et tuples,ici](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences).
> 3 `Surveys_df.head ()` Exécute également `survey_df.head (15)` qu'est-ce que cela fait?
> 4 `survey_df.tail ()`
{: .challenge}


## Calcul des statistiques des données dans un ** DataFrame ** de Pandas

Nous avons lu les données en Python. Calculons maintenant quelques statistiques pour
comprendre un peu des données avec lesquelles nous travaillons. Nous voudrons peut-être
savoir combien d'animaux ont été collectés sur chaque site ou combien d'espèces
ont été capturées. Nous pouvons calculer ces statistiques rapidement en utilisant des groupes.
Mais nous devons d’abord savoir comment nous voulons nous disputer.

Empezemos d'explorerdonnées:

~~~
# Regardons les colonnes
de surveys_df.columns
~~~
{:} .langue-python

qui  retourne ****:

~~~
Index ([ 'record_id', 'mois' , 'jour', 'année', 'plot_id', 'species_id', 'sexe',
      'hindfoot_length', 'poids'],
     'objet' DTYPE =)
~~~
{:} .output

Obtenir une liste de tous espèces. La fonction `pd.unique`indique nous
les différentes valeurs présentes dans lacolonne` espèce_id`.

~~~
pd.unique (survey_df ['espèces_id'])
~~~
{: .language-python}

ce que ** retourne **:

~~~
array (['NL', 'DM', 'PF', «PE», «DS», «PP», «SH», «OT», «DO», «OX», «SS»,
      «OL», «RM», nan, «SA», «PM», "AH", "DX", "AB", "CB", "CM", "CQ",
      "RF", "PC", "PG", "PH", "PU", "CV", "UR" ',' UP ',' ZL ',' UL ',' CS ',
      ' SC ',' BA ',' SF ',' RO ',' AS ',' SO ',' PI ',' ST ',' 'CU', 'HIS', 'RX',
      'PB', 'PL', 'PX', 'CT', 'US'], DTYPE = objet)
~~~
{:}

.langue-python> ## reto -

Statistiques >> 1. Créez une liste des identifiants de site ("plot_id") figurant dans les données du recensement.
>    Appelons cette liste `site_names`. Combien de sites sont les données?,
Combien>   espèces il y a dans les données?

>> 2. Quelle est la différence entre `len (site_names)` et`survey_df ['plot_id']. Nunique ()`?
{: .challenge}

# Groupes dans les pandas

Parfois, nous souhaitons calculer des statistiques de données regroupées par
sous-ensembles ou attributs de nos données. Par exemple, si nous voulons calculer le
poids moyen de nos individus par site.

Nous pouvons calculer des statistiques de base de toutes les données d’une colonne
à l’aide de la commande suivante:

~~~
Surveys_df ['weight']. Describe ()texte
~~~
{: .language-python}
renvoie lesuivant ** exit **

~ ~~
compter32283,000000
42,672428signifie
std 36,631259
4,000000min
2537,000000%20,000000
50%
48,000000 75%
max 280,000000
Nom: poids, DTYPE: float64
~~~
{:} .langue-python

peut également extraire une métrique particulière ::

~~~
surveys_df [ 'poids']. min ()
surveys_df [ 'poids'].max ()
de surveys_df [ 'poids']. moyenne ()
de surveys_df [ 'poids']. std ()
Nombrede surveys_df [ 'poids'] ()
~~~
{: .language-python}

Mais si nous voulons extraire des informations à l'aide d'une ou plusieurs variables, par exemple le sexe,
nous pouvons utiliser la méthode `.groupby` de Pandas **. Une fois que nous avons créé
un groupe ** DataFrame ** , nous pouvons calculer des statistiques en fonction du groupe de notre choix.

~~~
# Pooled parsexe
grouped_data = surveys_df.groupby ( 'sexe')
~~~
{: .langue-python}

La fonction** `describe` ** Panda renvoiestatistiques descriptivesy compris:
moyenne, meadiana, max, min, std et compte pour une colonne particulière des
données. La fonctionne `describe` renvoie que les valeurs de ces statistiques pour les
colonnes numériques.

~~~
# Statistiques pour toussexe colonnes numériques
grouped_data.describe()
# Renvoie la moyenne de chaque colonne numérique sexe
grouped_data.mean ()
{~~~:}


`.langue-pythongrouped_data.mean () ' ** SORTIE: **

~~~
       plot_id \record_id année mois jour
sexe
18036.412046 6.583047 16.007138F 1990.644997 11.440854
16.184286 6.392668 17754.835601 1990.480401 M 11.098282

    hindfoot_length poids
sexe
28.836780F42.170555
29.709578 42.995379M

~~~
{:}.langue-python

commande ` groupby` est très puissant et ne permet pas la génération rapide de
statistiques descriptives.

> ## Reto -  des données

Description>> 1. Combien de personnes sontfemmes f` et combien sont ``m`?hommes
> 2. Que se passe-t-il lorsque vous groupez sur deux colonnes à l'aide de l'instruction suivante
>    et que vous prenez ensuite les valeurs moyennes:
>   - `grouped_data2 = survey_df.groupby (['plot_id', 'sex']) '
>   - `grouped_data2.mean ()`
> 3. Calculez les statistiques de poids descriptives pour chaque site. Conseil:
>    Vous pouvez utiliser la syntaxe suivante pour créer uniquement des statistiques pour une
>   colonne de vos données
>   `By_site [ 'poids']. Describe

()` >>
>> ##que vous avezbon défi # 3T?
>> ** Une sortie pedaxo pour le défi 3 ressemble: **
>>
>> ~~~
>>  site
>>  1comte 1903,000000
>>        51,822911 signifie
>>        std 38,176670
>>        min 4,000000
>>        25%30,000000>
>        50%44,000000
>>        75% 53,000000
>>        max 231,000000
>>          ...
>> ~~~
>> {:
.Output}> {:}
{.Solution:.challenge}

Créationstatistiques ## comptages rapidement avec Pandas

Maintenant, comptons le nombre d'échantillons de chaque espèce. Nous pouvons le faire
de différentes manières, mais nous utiliserons `groupby`method` combiné à ** the count ()`**.

~~~
# Comptez le nombre d'échantillons par espèces
species_counts = surveys_df.groupby ( 'species_id') count () [ 'record_id']
impression (species_counts)
~~~.
{:}.langue-python,

O  peut aussi compter lignes ayant les espèces "DO":

~~~
surveys_df.groupby( 'species_id') [ ''] rECORD_ID count () [ 'DO']
~~~
{:

.langue-python}.> ## Challenge - Making une

liste >> Quelle autre façonlà pour créer une liste d'espèces et associée `count` 
de>  échantillons de données? Astuce: vous pouvez faire exécuter les fonctions
>  `count`, ` min`, etc. dans un groupe ** DataFrame ** de la même manière que
> cela  se fait dans un DataFrame
{: .challenge}

## Fonctions mathématiques de base

Si nous le voulons, nous pouvons effectuer des opérations dans une colonne de
données. Par exemple, multiplions toutes les valeurs de poids par 2. Une utilisation
plus utile pourrait être de normaliser les données avec la moyenne, la surface ou une autre valeur
calculée de nos données.

~~~
# Multipliant toutesvaleurs de poids pour 2
surveys_df [ « poids »] * 2
~~~
{: .langue-python}

données # de Graphing rapidement et facilementPandas

nospeuvent également graphiqueaide Pandas de statistiques descriptives.

~~~
# Assurez-vous que les images apparaissent insérées dans iPython Notebook
% matplotlib inline
# Créez un graphique à barres
espèces_counts.plot (kind = 'bar');
~~~
{:

.langue-python}!deespèces[sitespoids](../fig/countPerSpecies.png)
Chiffres espèces par site

peut aussi voir combien d'animaux ont été capturés parsite:

~~~
TOTAL_COUNT = surveys_df. groupby ('plot_id') ['record_id']. nunique ()
# Nous avons également tracé ce
total_count.plot (kind = 'bar');
~~~
{:}

.langue-python> ## Challenge -

Graphique >> 1. Créez un graphique du poids moyen des espèces par site.
> 2. Créez un graphique du total des hommes par rapport au total des femmes pour
>    l'ensemble de données.
{:}

.Challenge> ## fin  Défi

>>graphique Crée ungraphique à barres empiléesle poids sur l'axe Y, et la
variable> empilementsexe. Le graphique doit indiquer le poids total par sexe
> pour chaque site. Voici quelques conseils qui peuvent vous aiderrésoudre le défi sont les
 

suivants>: >> * [Pour plus d'informations sur le graphique des pandas, visitez le lien suivant.] (http://pandas.pydata.org/pandas-docs/stable/visualization.html#basic-plotting-plot)
> * Vous pouvez utiliser le code suivant pour créer un graphique de barres empilées mais
>    mais les données à empiler doivent être dans des colonnes différentes. Voici un
petit>    exemple des données où « a », « b » et « c » sontgroupes, et « un » et « deux »
sont>    sousgroupes.

>> 
~~~> d = { 'un': pd.Series (, index = [ 'a', 'b', 'c'] [1, 2, 3.]), 'Deux': pd .Series ([1., 2., 3., 4.], index = ['a', 'b', 'c', 'd'])}
> pd.DataFrame (d)
> ~~~
> {:}

.langue-python >> montre les  suivantes

données>> 
~~~>       un
deux>   1
1>   B 2
2>   c Mars
3>   d NaN
4> 
~~~> {:}

.output >> nous pouvons  cettegraphique

>> avec 
~~~> # Graficar empiléstelle sorte quedonnées de l'une «des colonnes et 'deux' sont
empilés> = my_df pd.DataFrame
(d)> my_df.plot (type = 'bar' empilés = True , title = "le titre de mon
graphique")> 
~~~> {:}

.langue-python >> [empilésàgraphiquebarres]

(../ fig / stackedBar1.png) >> * Nous pouvons utiliser la méthode `.unstack ()` pour transformer les données groupées en
>    colonnes pour chaque graphique. Essayez de lancer `.unstack ()` dans un DataFrame
>    précédent et voyez ce qu’il faut.

>> commencertransformer les données misescommun (par site etsexe) dans un
arrangement dépilé> crée alors un graphique empilé.

>>
>> ## Solutions pour le dernier défi
>>
>> données Premières agrupemos par site etsexe, puis calculer le total pour
>>. chaque site
>>
>> ~~~
>> by_site_sex = surveys_df.groupby ([ 'plot_id', 'sexe'])
>> site_sex_count = by_site_sex [ 'poids'] somme ()
>> {~~~.
>> .Langue -python}
>>
>> Ceci calcule la somme des poids pour chaque sexe par site sous forme de tableau
>>
>> ~~~
>> sexe de site
>> plot_id sexe
>> 1 F 38253
>>          M 59979
>> 2 F 50144
>>          M 57250
>> 3 F 27251
>>          M 28253
>> 4 F 3979649377
>>          M
>> <le reste a été omis pour abréger>
>> ~~~
>> {: .output}
>>
>> >> maintenantutilisera .unstack`()` dans les données misescommun pour comprendre comment le poids
>> total pour chaque sexe contribue à chaque site.
>>
>> ~~~
>> by_site_sex = surveys_df.groupby ([ 'plot_id', 'sexe'])
>> site_sex_count = by_site_sex [ 'poids']. Somme ()
>> site_sex_count.unstack ()
>> ~~ ~
>> {: .language-python}
>>
>> La méthode `unstack` ci-dessus affiche le résultat suivant:
>>
>> ~~~
>> sex FM
>> plot_id
>> 1 38253 59979
>> 2 50144 57250
>> 3 27251 28253
>> 4 39796 49377
>> <les autres sites sont omis pour le briefing>
>> ~~~
>> {: .output}
>>
>> Nous créons maintenant un graphique à barres empilées avec les données où le poids pour chaque
>> sexe, il est empilé par site.
>>
>> Au lieu d'afficher commetable, nous pouvons tracer les données empilant des données
>> de chaque sexe comme suit:
>>
>> ~~~
>> by_site_sex = surveys_df.groupby ([ « plot_id », « sexe » ])
>> site_sex_count = by_site_sex [ 'poids']. sum ()
>> = spc site_sex_count.unstack ()
>> s_plot = spc.plot (type = 'bar' = True empilée, title = « poids total parsite etsexe ")
>> s_plot.set_ylabel (" poids ")
>> s_plot.set_xlabel (" Terrain « )
>> {~~~:
>> 
>>
>> .langue-python}[Figurebarres empilées](!../figstackedBar.png/)
> {: .solution}
{: .challenge}

{% include links.md%}




