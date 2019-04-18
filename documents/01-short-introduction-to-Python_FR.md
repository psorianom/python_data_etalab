
## Questions:
   - Qu'est-ce que Python?
   - Pourquoi devriez-vous apprendre le python?

## Objectives:
   - Décrire les avantages de l’utilisation de la programmation par rapport à la réalisation manuelle de tâches répétitives.
   - Définir les types de données en Python: **chaînes** (strings), **nombres entiers** (integers) et **flottants** (floats).
   - Effectuer des opérations mathématiques en Python en utilisant des opérateurs de base.
   - Dans le contexte de Python, définissez: **listes** (lists), **tuples** et **dictionnaires** (dictionaries).

## L'interpréteur

Python est un langage interprété qui peut être utilisé de deux manières:

* Mode "interactif": lorsque vous l'utilisez comme "calculatrice avancée" en exécutant
 une commande à la fois. Pour démarrer Python dans ce mode, exécutez chaque commande dans une cellule de code `python` sur votre Jupyter notebook:



~~~
2 + 2
~~~


~~~
4
~~~


~~~
print ("Hello World")
~~~

~~~
Hello World
~~~



* Mode "interpreteur": en lançant la commande `python` suivi par le nom d'un fichier qui contient un script. 

Nous utliserons le mode interactif dans cet atelier. 

## Introduction aux types de données Python intégrés

### Strings, integers et floats

Une des opérations la plus basique que nous puissions faire en Python consiste à affecter des valeurs aux variables:

~~~
text = "Data Carpentry" # Un exemple de string
number = 42 # Un exemple de nombre integer
pi_value = 3.1415 # Un exemple de float
~~~
{ : .language-python}

Ici nous avons assigné des données aux variables `text`,`number` et `pi_value`, en
utilisant l'opérateur d'affectation `=`. Pour vérifier la valeur d'une variable, nous
pouvons écrire le nom de la variable dans l'interpréteur et appuyer sur Màj+Renvoyer:

~~~
text
~~~

~~~
"Charpenterie des données "
~~~



Tout dans Python a un type. Pour obtenir le type de quelque chose, nous pouvons passer cette chose
à la fonction `type`:

~~~
type (text)
~~~

~~~
<classe 'str'>
~~~


~~~
type (number)
~~~

~~~
<classe 'int'>
~~~


~~~
type (6.02)
~~~

~~~
<class 'float'>
~~~



La variable `text` est de type 'str', abréviation de **string** ou chaîne. Les chaînes stockent des séquences de caractères, qui peuvent être des lettres, des chiffres, des signes de ponctuation
ou des formes de texte plus exotiques (même des emoji!).

Nous pouvons également voir la valeur de quelque chose en utilisant une autre fonction intégrée, `print`:

~~~
print(text)
~~~

~~~
Data Carpentry
~~~

~~~
print(11)
~~~

~~~
print(11)
~~~



**Astuce**: `print` et `type`  sont des fonctions intégrées dans Python. Plus loin dans cette
leçon, nous verrons des méthodes et des fonctions définies par l'utilisateur.


### Opérateurs

Nous pouvons effectuer des calculs mathématiques en Python en utilisant les opérateurs de base
`+, -, /, *,%`:

~~~
2 + 2 # Sum
~~~


~~~
4
~~~


~~~
6 * 7 # Multiplication
~~~

~~~
42
~~~

~~~
2 ** 16 # Puissance
~~~

~~~
65536
~~~

~~~
13 % 5 # Modulo
~~~

~~~
3
~~~



Nous pouvons également utiliser opérateurs de comparaison :
`<,>, == ,! =, <=,>= ` et opérateurs logiques telles
que `and, or, not`. Le type de données renvoyées par ces opérateurs
s'appelle _**boolean**_ et renvoie vrai ou faux (true ou false), comme indiqué ci-dessous.

~~~
3 > 4
~~~

~~~
False
~~~


~~~
True and True
~~~

~~~
Vrai
~~~


~~~
True or False
~~~

~~~
True
~~~


~~~
True and False
~~~

~~~
False
~~~


## Séquences: Listes et Tuples

### Listes

**list** (ou les listes) sont une structure de données commune permettant de stocker une séquence ordonnée d'
éléments. Chaque élément est accessible via un index. Notez qu'en Python, les index commencent par 0 au lieu de 1:

~~~
nombres = [1, 2, 3]
nombres[0]
~~~

~~~
1
~~~


Vous pouvez utiliser une boucle `for` pour accéder aux éléments d'une liste ou à d'autres
structures de données Python, l'un après l'autre:

~~~
for num in numbers:
    print(num)

~~~


~~~
1
2
3
~~~


**L'indentation** est très importante en Python. Note que la deuxième ligne dans l'exemple ci-dessus est indenté. C’est ainsi que Python crée un bloc de code. 

Pour ajouter des éléments à la fin d'une liste, nous pouvons utiliser la méthode `append`. Les méthodes
sont un moyen d'interagir avec un objet (une liste, par exemple). Nous pouvons invoquer une
méthode en utilisant le point `.` suivi du nom de la méthode et d'une liste d'arguments
entre parenthèses. Voyons un exemple en utilisant `append`:

~~~
nombres.append (4)
print(nombres)
~~~


~~~
[1, 2, 3, 4]
~~~


Pour savoir quelles méthodes sont disponibles pour un
objet, nous pouvons utiliser la commande `help` intégrée:

~~~
help(nombres)

Help on list object:

class list(object)
 |  list() -> new empty list
 |  list(iterable) -> new list initialized from iterable's items
 ...
~~~
iterable

### Tuples

Un **tuple** est similaire à une liste dans le sens qoù il s'agit d'une séquence ordonnée d'éléments.
Cependant, les n-uplets ne peuvent plus être changés une fois créés (ils sont "immuables"). Les tuples
sont créés en plaçant les valeurs séparées par des virgules entre parenthèses `()`.

~~~
# Les tuples utilisent des parenthèses
une_tuple = (1, 2, 3)
autre_tuple = ('blue', 'green', 'red') '

# Remarque: les listes utilisent des crochets
une_list = [1, 2, 3]
~~~


> ## Tuples _vs._ Lists
> 1. Que se passe-t-il lorsque tu exécutes `une_list[1] = 5` ?
> 2. Que se passe-t-il lorsque tu exécutes `une_tuple[2] = 5`?
> 3. Que dit `type(une_tuple)` à propos de `une_tuple`?
>



## Dictionnaires

Un dictionnaire **dictionary** est un conteneur qui stocke des paires d'objets - clés et valeurs.

~~~
translation = {'one':1, 'two':2}
translation['one']
~~~

~~~
1
~~~
 

Les dictionnaires fonctionnent comme les listes, sauf que l'index est créé en utilisant des *clès* ou **keys**.
Tu peux considérer une clé comme un nom ou un identifiant unique pour un ensemble de valeurs
du dictionnaire. Les clés ne peuvent avoir que des types particuliers, elles doivent être "**hashable**". Les strings et les types numériques sont acceptables, mais les listes ne le sont pas.

~~~
dico = {1: 'un', 2: 'deux'}
dico[1]
~~~

~~~
'un'
~~~


~~~
mauvais = {[1, 2, 3]: 3}
~~~

~~~
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
~~~


En Python, un "**Traceback**" est un bloc d'erreur multiligne imprimé pour l'utilisateur.

Pour ajouter un élément au dictionnaire, nous affectons une valeur à une nouvelle clé:

~~~
dico = {1: 'un', 2: 'deux'}
dico[3] = 'trois'
dico
~~~

~~~
{1: 'un', 2: 'deux', 3: 'trois'}
~~~


Utiliser des boucles `for` avec des dictionnaires est un peu plus compliqué. Nous pouvons le faire
de deux manières:
~~~
for key, value in dico.items():
    print(key, '->', value)
~~~


~~~
1 -> un
2 -> deux
3 -> trois
~~~


ou

~~~
for key in dico.keys():
    print(key, '->', dico[key])
~~~

~~~
1 -> un
2 -> deux
3 -> trois
~~~



## Modification de dictionnaires 

> 1. Commence par imprimer la valeur du `dico` à l'écran.
> 2. Réaffecte la deuxième valeur pour qu'il ne lise plus "deux" mais "pomme".
> 3. Imprimez à nouveau la valeur de `dico`  et regarde si la valeur a changé.
>



## Fonctions
La définition d’une section de code en tant que fonction dans Python est effectuée à l’aide du mot clé `def`.
Par exemple, une fonction prenant deux arguments etleur somme
peut être définie comme suit:

~~~
def add_function(a, b):
    result = a + b
    return result

z = add_function(20, 22)
print(z)
~~~

~~~
42
~~~
