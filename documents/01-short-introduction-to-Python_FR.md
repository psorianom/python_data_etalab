
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



```python
In[]: 2 + 2
```


```
Out[]: 4
```


```python
In[]: print("Hello World")
```

```
Out[]: Hello World
```



* Mode "interpreteur": en lançant la commande `python` suivi par le nom d'un fichier qui contient un script. 

```bash
user:host:~$ python my_script.py
Hello World
```

Nous utliserons le mode interactif dans cet atelier. 

## Introduction aux types de données Python 

### Strings, integers et floats

Une des opérations la plus basique que nous puissions faire en Python consiste à affecter des valeurs aux variables:

```python
In[]:   text = "Data Carpentry" # Un exemple de string
        number = 42 # Un exemple de nombre integer
        pi_value = 3.1415 # Un exemple de float
```

Ici nous avons assigné des données aux variables `text`,`number` et `pi_value`, en
utilisant l'opérateur d'affectation `=`. Pour vérifier la valeur d'une variable, nous
pouvons écrire le nom de la variable dans l'interpréteur et appuyer sur Màj+Renvoyer:

```python
In[]:  text
```

```
Out[]:  "Charpenterie des données "
```

Tout dans Python a un type. Pour obtenir le type de quelque chose, nous pouvons passer cette chose
à la fonction `type`:

```python
In[]:  print(type(text))
```

```python
Out[]:  <classe 'str'>
```


```python
In[]:  print(type(number))
```

```python
Out[]:  print(<classe 'int'>)
```


```python
In[]:  print(type(6.02))
```

```python
Out[]:  <class 'float'>
```



La variable `text` est de type 'str', abréviation de **string** ou chaîne. Les chaînes stockent des séquences de caractères, qui peuvent être des lettres, des chiffres, des signes de ponctuation
ou des formes de texte plus exotiques (même des emoji!).

Nous pouvons également voir la valeur de quelque chose en utilisant une autre fonction intégrée, `print`:

```python
In[]:  print(text)
```

```
Out[]:  Data Carpentry
```

```python
In[]:  print(11)
```

```
Out[]:  11
```



**Astuce**: `print` et `type`  sont des fonctions intégrées dans Python. Plus loin dans cette
leçon, nous verrons des méthodes et des fonctions définies par l'utilisateur.


### Opérateurs

Nous pouvons effectuer des calculs mathématiques en Python en utilisant les opérateurs de base
`+, -, /, *,%`:

```python
In[]:  2 + 2 # Sum
```


```
Out[]:  4
```


```python
In[]:  6 * 7 # Multiplication
```

```
Out[]:  42
```

```python
In[]:  2 ** 16 # Puissance
```

```
Out[]:  65536
```

```python
In[]:  13 % 5 # Modulo
```

```
Out[]:  3
```



Nous pouvons également utiliser opérateurs de comparaison :
`<,>, == ,! =, <=,>= ` et opérateurs logiques telles
que `and, or, not`. Le type de données renvoyées par ces opérateurs
s'appelle _**boolean**_ et renvoie vrai ou faux (true ou false), comme indiqué ci-dessous.

```python
In[]:  3 > 4
```

```python
Out[]:  False
```

```python
In[]:  True and True
```

```python
Out[]:  True
```


```python
In[]:  True or False
```

```python
Out[]:  True
```


```python
In[]:  True and False
```

```python
Out[]:  False
```


## Défi
### Modification de dictionnaires 

> 1. Affecter `5` à la variable `a`
> 2. Affecter `a x 2` à la variable `deux_a`
> 3. Changer la valeur de `a` à 3. Quelle est la valeur de `deux_a`, `6` ou `10` ?



## Séquences: Listes et Tuples

### Listes

**list** (ou liste) est une structure de données commune permettant de stocker une séquence ordonnée d'éléments.
Chaque élément est accessible via un index. Notez qu'en Python, les index commencent par 0 au lieu de 1:

```python
In[]:   nombres = [1, 2, 3]
        nombres[0]
```

```
Out[]:  1
```


Vous pouvez utiliser une boucle `for` pour accéder aux éléments d'une liste ou à d'autres
structures de données Python, l'un après l'autre:

```python
In[]:  for num in numbers:
          print(num)

```


```
Out[]:  1
        2
        3
```


**L'indentation** est très importante en Python. Note que la deuxième ligne dans l'exemple ci-dessus est indenté. C’est ainsi que Python crée un bloc de code. 

Pour ajouter des éléments à la fin d'une liste, nous pouvons utiliser la méthode `append`. Les méthodes
sont un moyen d'interagir avec un objet (une liste, par exemple). Nous pouvons invoquer une
méthode en utilisant le point `.` suivi du nom de la méthode et d'une liste d'arguments
entre parenthèses. Voyons un exemple en utilisant `append`:


```python
In[]:   nombres.append (4)
        print(nombres)
```


```
Out[]:  [1, 2, 3, 4]
```


Pour savoir quelles méthodes sont disponibles pour un
objet, nous pouvons utiliser la commande `help` intégrée:

```python
In[]:  help(nombres)

Help on list object:

class list(object)
 |  list() -> new empty list
 |  list(iterable) -> new list initialized from iterables items
 ...
```

### Tuples

Un **tuple** est similaire à une liste dans le sens où il s'agit d'une séquence ordonnée d'éléments.
Cependant, les n-uplets ne peuvent plus être changés une fois créés (ils sont "immutables"). Les tuples
sont créés en plaçant les valeurs séparées par des virgules entre parenthèses `()`.

```python
# Les tuples utilisent des parenthèses
In[]:   une_tuple = (1, 2, 3)
        autre_tuple = ('blue', 'green', 'red') 

# Remarque: les listes utilisent des crochets
In[]:   une_list = [1, 2, 3]
```


## Défi

> ## Tuples _vs._ Lists
> 1. Que se passe-t-il lorsque tu exécutes `une_list[1] = 5` ?
> 2. Que se passe-t-il lorsque tu exécutes `une_tuple[2] = 5`?
> 3. Que dit `type(une_tuple)` à propos de `une_tuple`?




## Dictionnaires

Un dictionnaire **dictionary** est un conteneur qui stocke des paires d'objets - clés et valeurs.

```python
In[]:  translation = {'one':1, 'two':2}
       translation['one']
```

```
Out[]:  1
```
 

Les dictionnaires fonctionnent comme les listes, sauf que l'index est créé en utilisant des *clès* ou **keys**.
Tu peux considérer une clé comme un nom ou un identifiant unique pour un ensemble de valeurs
du dictionnaire. Les clés ne peuvent avoir que des types particuliers, elles doivent être "**hashable**". Les strings et les types numériques sont acceptables, mais les listes ne le sont pas.

```python
In[]:  dico = {1: 'un', 2: 'deux'}
In[]:  dico[]
```

```
Out[]:  'un'
```


```python
In[]:  mauvais = {[1, 2, 3]: 3}
```

```python
Out[]:  

  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  TypeError: unhashable type: 'list'
```


En Python, un "**Traceback**" est un bloc d'erreur multiligne imprimé pour l'utilisateur.

Pour ajouter un élément au dictionnaire, nous affectons une valeur à une nouvelle clé:

```python
In[]:   fragnol = {"bouteille":"botella", "velo":"bicicleta", "souhaite":"deseo"}
        fragnol["velo"] = 'bicicleta'
        fragnol
```

```python
Out[]:  {'bouteille': 'botella', 'velo': 'bicicleta', 'souhaite': 'deseo'}
```


Utiliser des boucles `for` avec des dictionnaires est un peu plus compliqué. Nous pouvons le faire
de deux manières:
```python
In[]:  for key, value in fragnol.items():
            print(key, '->', value)
```


```
Out[]:  
      bouteille --> botella
      velo --> bicicleta
      souhaite --> deseo
      ordinateur --> computadora

```


ou

```python
In[]:    for key in fragnol.keys():
             print(key, '->', dico[key])
```

```
Out[]:  
      bouteille --> botella
      velo --> bicicleta
      souhaite --> deseo
      ordinateur --> computadora
```



## Défi
### Modification de dictionnaires 

> 1. Commencer par imprimer la valeur du `fragnol` à l'écran.
> 2. Réaffecter la deuxième valeur pour qu'il ne lise plus "bicicleta" mais "bici".
> 3. Imprimer à nouveau la valeur de `fragnol`  et regarde si la valeur a changé.
>



## Fonctions
La définition d’une section de code en tant que fonction dans Python est effectuée à l’aide du mot clé `def`.
Par exemple, une fonction prenant deux arguments etleur somme
peut être définie comme suit:

```python
In[]:    def add_function(a, b):
              result = a + b
              return result

          z = add_function(20, 22)
          print(z)
```

```
Out[]:  42
```
