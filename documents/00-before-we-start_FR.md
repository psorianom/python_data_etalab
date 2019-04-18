## Qu'est-ce que Python?

Python est un langage de programmation du type dit général qui permet le développement rapide d’applications d’analyse de données. Le mot "Python" désigne à la fois le langage de programmation et l'outil qui exécute les **scripts** écrits en langage "Python".

Ses principaux avantages sont les suivants:

* Il est gratuit
* Open source
* Disponible pour toutes les grandes plates-formes (macOS, Linux, Windows)
* Il est mis à jour par la Python Software Foundation
* Permet plusieurs paradigmes de programmation
* Une grande communauté
* Un écosystème riche de packages/librairies tiers

* Pourquoi, alors, avez-vous besoin de Python pour l'analyse des données? *

### Facile à apprendre
Python est plus facile à apprendre que d'autres langages de programmation. Ceci est important car la reduction des obstacles facilitent l'apprentissage aux nouveaux membres de la communauté.

### Reproductibilité 
La reproductibilité est la capacité à obtenir les mêmes résultats en utilisant les mêmes données et analyses.

Une analyse de données écrite dans un ** script ** de Python peut être reproduite sur n’importe quelle plate-forme.
De plus, si vous collectez plus de données ou corrigez des données existantes, vous pouvez relancer l'analyse rapidement et facilement!

De plus en plus de revues scientifiques et d'agences de financement s'attendent à ce que les analyses soient reproductibles. Par conséquent, connaître Python vous donnera un avantage sur ces exigences.

### Interdisciplinaire et extensible
Python fournit un cadre qui permet à quiconque de combiner des approches de différentes disciplines pour mieux répondre à tes besoins en analyse.

### Python possède une grande communauté conviviale.
Des milliers de personnes utilisent Python quotidiennement. Beaucoup d'entre eux sont prêts à vous aider à travers les listes de diffusion et les sites Web, tels que [Stack Overflow](https://stackoverflow.com) et le portail de la [communauté Anaconda](https://www.anaconda.com/communauté /).


<br />

## Connaître Anaconda
La distribution Python [Anaconda](https://www.anaconda.com) comprend de nombreux paquets populaires, tels que la console Ipython, Jupyter Notebook et Spyder IDE.
Jetez un coup d'œil au navigateur Anaconda. Vous pouvez exécuter des programmes à partir du navigateur ou utiliser la ligne de commande.

[Jupyter Notebook](https://jupyter.org) est une application Web open source qui vous permet de créer et de partager des documents en combinant du code, des graphiques et du texte narratif.

[Spyder](https://spyder-ide.github.io) est un **environnement de développement intégré** (IDE) qui vous permet d'écrire des **scripts** de Python et d'interagir avec le logiciel de Python à partir d'une seule interface.

Anaconda est également livré avec un gestionnaire de paquets appelé [conda](https://conda.io/docs/), ce qui facilite l’installation et la mise à jour de paquets supplémentaires.

<br />

## Projet d'analyse de données: bonnes pratiques

Il est judicieux de sauvegarder les données, l’analyse, et le texte associés dans un seul dossier.
Par conséquent, tous les **scripts** et les fichiers texte de ce dossier peuvent utiliser des **chemins** (ou paths) relatifs aux fichiers de données.
Travailler de cette façon facilite beaucoup le déplacement de votre projet et le partage avec d'autres personnes.

### Organisation de votre répertoire de travail 

L'utilisation d'une structure de dossiers cohérente dans tes projets vous aidera à garder les choses organisées et à faciliter la recherche/l'archivage des choses à l'avenir. Cela peut être particulièrement utile lorsque vous avez plusieurs projets. En général, vous pouvez créer des répertoires distincts pour tes **scripts**, tes données, et tes documents.


- **`data/`**: Utilisez ce dossier pour sauvegarder tes données brutes. Par souci de transparence et de provenance, vous devez toujours conserver une copie de tes **données brutes**. Si vous devez nettoyer tes données, faites-le par de manière "programmatique" (*c'est-à-dire*, avec **scripts**) et veillez à séparer les données propres des données brutes. Par exemple, vous pouvez enregistrer des données brutes dans `./data/raw/` et les données nettoyées des données dans `./data/clean/`.

- **`documents/`**: utilisez ce dossier pour enregistrer des schémas, des brouillons et d'autres textes.

- **`scripts/`**: Utilisez ce dossier pour enregistrer tes **scripts** (Python) pour le nettoyage, l'analyse et la génération de graphiques que vous utilisez dans un projet en particulier.

Il se peut que vous deviez créer des répertoires supplémentaires en fonction des besoins de votre projet, mais ceux ci-dessus devraient être l’axe principale du répertoire. Pour cet atelier, nous aurons besoin d’un dossier `data/` pour stocker nos données brutes, puis nous devrons créer le dossier `data_output/` lorsque nous apprendrons comment exporter des données sous forme de fichiers CSV.

## Qu'est-ce que la programmation et le codage (coding)?

La programmation est le processus d'écriture des _"programmes"_ qu'un ordinateur peut exécuter en produisant un résultat (utile).
La programmation est un processus en plusieurs étapes qui implique:

1. L’ identification des aspects d’un problème de la vie réelle pouvant être résolus par l'ordinateur.
2. Identifiez la (meilleure) solution informatique.
3. Implémentez la solution dans un langage de programmation spécifique.
4. Testez, validez et ajustez la solution mise en œuvre.

Alors que _"Programmation"_ fait référence à toutes les étapes nommées, _"l'Encodage"_ ne fait référence qu'à l'étape 3: _"Implémente la solution dans un langage de programmation spécifique"_.

## Comment en savoir plus après l'atelier?

Le matériel que nous couvrirons au cours de cet atelier vous donnera un premier test sur la façon dont Python peut être utilisé pour analyser les données de votre propre domain. Cependant, vous aurez toujours besoin d'en savoir plus sur les opérations plus avancées telles que le nettoyage de votre **jeu de données**, l'utilisation de méthodes statistiques ou la création de superbes graphiques. La meilleure façon de devenir compétent et efficace en Python, ainsi qu'avec tout autre outil, consiste à l'utiliser pour répondre à tes propres questions. En tant que débutant, il peut être décourageant de devoir écrire un **script** dès le début. Etant donné que nombreuses personnes partagent leur code sur le Web, la modification du code existant en fonction de tes besoins peut faciliter le démarrage.

## Recherche de l'aide

* regarde le menu _Help_
* tape `help()`
* tape `?object` ou `help(objet)` pour obtenir des informations sur un objet
* [Documentation Python](https://www.python.org/doc/)

Enfin, une recherche générique sur Google ou sur Internet de "Python tâche_à_réaliser" vous mènera généralement vers la documentation du module approprié ou vers un forum où une autre personne qui a déjà posée la même question.

Je suis coincée... J'ai un message d'erreur que je ne comprends pas.
Commence par googler le message d'erreur. Cependant, cela ne fonctionne pas toujourscar, parfois, les développeurs utilisent les messages d'erreur fournis par Python. Si le message est très générique, tu devrais peut-être inclure dans votre requête le nom de la fonction ou du package que tu utilises.


### Demander de l'aide

La clé pour obtenir l'aide de quelqu'un consiste à ce qu'ils comprennent rapidement votre problème. Vous devez faciliter au maximum l'identification des inconvénients.

Essayez d'utiliser les mots corrects pour décrire le problème. Par exemple, un paquet n'est pas la même chose qu'une bibliothèque (ou librairie). La plupart des gens comprendront ce que vous voulez dire, mais d’autres ressentiront la différence de sens. Le point clé est que cela peut rendre les choses déroutantes pour les personnes qui essaient de vous aider.
Essaie d’être aussi précis que possible lorsque vous décrivez votre problème.

Si possible, essayez de résumer ce qui ne fonctionne pas dans un exemple simple et reproductible. Si vous pouvez reproduire le problème en utilisant une petite quantité de données au lieu de tes 50 000 lignes et 10 000 colonnes, fournissez ce petit **dataset**  avec la description de votre problème. Lorsque c'est approprié, essayez de généraliser ce que vous faites, afin que même les personnes qui ne connaissent pas votre domaine d'étude puissent comprendre votre question. Par exemple, au lieu d'utiliser un sous-ensemble de votre dataset réelle, créez plutôt un petit dataset (3 colonnes, 5 lignes).

### Où demander de l'aide?

* À la personne assise à côté de toi pendant l'atelier. N'hésitez pas à parler à ton voisin pendant l'atelier, compare tes réponses, demande de l'aide. Vous voudrez peut-être aussi organiser des réunions régulièrement après l'atelier pour continuer à apprendre les uns des autres.
* Tes collègues amicaux: si vous connaissez une personne plus expérimentée que vous, elle pourrait être prêt à t'aider.
* [Stackoverflow](http://stackoverflow.com/questions/tagged/python): Si votre question n'a pas déjà été répondue et si elle est bien pensée, il est probable que vous obtiendrez une réponse dans 5 minutes. N'oubliez pas de suivre les instructions pour savoir comment demander correctement.
* [Listes de diffusion Python](https://www.python.org/community/lists/)

## Plus de ressources

[PyPI - L'index des packages Python](https://pypi.python.org/pypi)

[The Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/)

[Dive into Python 3](http://getpython3.com/diveintopython3/)



