# Atelier OpenRefine, Nanterre, 5 avril 2019

[OpenRefine](http://openrefine.org) est un logiciel libre permettant de traiter des données : inventaires d'archives, bibliographies, réponses à des questionnaires, données prosopographiques, etc.

Avec OpenRefine, vous pourrez trier vos données, les filtrer, repérer des valeurs manquantes, incomplètes ou aberrantes, supprimer les doublons, harmoniser les valeurs, diviser le contenu d'une colonne en plusieurs colonnes ou plusieurs lignes, assembler le contenu de plusieurs colonnes en une seule, enrichir les données à partir de bases de données telles que [Wikidata][70123744].

  [70123744]: https://outiquanti.hypotheses.org/875 "Découverte de Wikidata"

OpenRefine peut importer des données tabulaires, c'est à dire structurées en lignes et en colonnes telles que des fichiers Microsoft Excel, LibreOffice Calc, OpenOffice Calc, Google Documents, [CSV][61446736], TSV. Il peut aussi importer des fichiers XML, JSON ou des données stockées dans des bases de données relationnelles (de type MySQL ou PostgreSQL).

  [61446736]: https://fr.wikipedia.org/wiki/Comma-separated_values "Comma-separated values"

Dans quels cas OpenRefine pourrait vous être utile ? Vous avez récupéré par exemple [le fichier Excel de l'inventaire](https://f.hypotheses.org/wp-content/blogs.dir/2183/files/2018/12/Inventaire-des-cylindres-phonographiques-du-CRBC.xlsx) des [cylindres phonographiques](https://fr.wikipedia.org/wiki/Cylindre_phonographique) du [Centre de recherche bretonne et celtique](https://bylg.hypotheses.org/464). Dans ce fichier, chaque ligne correspond à un cylindre et vous avez remarqué qu'une colonne, _Dublin Core Spatial Coverage_ contient le nom de la commune d'où proviennent les cylindres. Vous aimeriez bien afficher les communes sur une carte mais vous ne savez pas comment récupérer leurs coordonnées géospatiales. Vous remarquez également quelques erreurs de saisie en appliquant un filtre dans Excel. Par exemple, Saint-Avé a été saisi une fois « Saint Avé » (sans tiret) et cinq fois « Saint-Avé » (avec un tiret). Vous remarquez également que la colonne peut contenir deux noms de communes, séparés par un point-virgule : Saint Avé (56206); Morlaix (29151).

OpenRefine peut vous servir à :
1. identifier les erreurs de saisie et les corriger,
2. séparer les noms de communes saisis dans la même cellule,
3. récupérer les coordonnées spatiales depuis la base de données Wikidata,
4. exporter les noms des communes et les coordonnées spatiales pour les afficher sur une carte du site [uMap][5e5df6f9].

  [5e5df6f9]: https://umap.openstreetmap.fr/fr/ "uMap"

> OpenRefine vs. Excel : Sous OpenRefine vous ne pourrez pas appliquer des formules mathématiques (calcul de sommes, de moyennes, test du Khi2, exponentielles, etc.) ou dessiner des graphiques comme vous pouvez le faire avec Excel ou LibreOffice Calc. Vous pourrez supprimer des colonnes avec OpenRefine mais pas des lignes.

## Installation de OpenRefine
OpenRefine fonctionne sous Microsoft Windows, Mac OS et Linux. Vous trouverez toutes les instructions d'installation sur [la documentation officielle](https://github.com/OpenRefine/OpenRefine/wiki/Installation-Instructions) (en anglais) ou sur [le cours de Mathieu Saby](https://msaby.gitlab.io/atelier-openrefine-MASA/installation-lancement-desinstallation.html) (en français). Sous Windows, vous aurez probablement besoin d'installer le logiciel [Java](https://www.java.com/fr/download/) (Java est installé par défaut sous Mac et Linux).

OpenRefine est en anglais par défaut. Il est conseillé de conserver l'interface dans la langue de Shakespeare car la documentation officielle et la grande majorité des tutoriels que vous trouverez sur internet sont en anglais. Si vous préférez toutefois changer la langue, allez dans le menu `Language Settings` affiché à gauche de [la page d'accueil](http://127.0.0.1:3333/) de OpenRefine.

## Atelier n°1 : Nettoyage d'une liste de communes bretonnes et récupération des coordonnées géographiques sur Wikidata

Pour le détail des opérations, voir [Créer une carte avec Wikidata, OpenRefine et uMap](https://bylg.hypotheses.org/543).

## Avant d'aller plus loin
### Une interface web

L'interface de OpenRefine est accessible depuis une page web (http://127.0.0.1:3333/). C'est pourquoi votre navigateur web par défaut est lancé au démarrage de OpenRefine.

Mais qui dit navigateur web ne dit pas « accès autorisé à tous ». Vous êtes seul à pouvoir accéder à cette interface et les données importées restent sur votre ordinateur.

### Un fonctionnement par projets

OpenRefine fonctionne par projet. Il faut créer un projet pour importer des données.

Pour revenir sur des données précédemment importées, il faut ouvrir le projet associé. Pour accéder de nouveau aux données de l'inventaire des cylindres phonographiques, cliquer dans le menu de gauche `Open Project` (`Ouvrir un projet`) depuis la page d'accueil.

### Une sauvegarde automatique

Tant que le projet n'est pas supprimé, les données importées restent présentes dans OpenRefine.

Il n'y a pas de Ctrl + S ou de Pomme + S dans OpenRefine pour sauvegarder votre projet. Toutes les opérations depuis l'importation des données sont automatiquement sauvegardées dans l'historique du projet.

De même, il n'y a pas de Ctrl + Z ou de Pomme + Z dans OpenRefine. Pour annuler une opération, il suffit d'aller dans l'historique du projet et de cliquer sur l'étape précédente.

### OpenRefine ne modifie pas vos fichiers originaux

OpenRefine ne modifie pas les fichiers originaux Excel, LibreOffice, CSV, etc. Il importe les données et les sauvegarde dans son dossier de travail. Pour afficher le dossier de travail, allez dans la liste des projets (menu `Open Project`)...

![Open Project](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2014_45_28-Window.png)

... puis cliquez sur `Browse workspace directory`.

![Browse workspace directory](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2014_29_48-Window.png)

Le contenu du dossier de travail ne vous permettra pas de récupérer vos données une fois nettoyées, vous utiliserez pour cela les fonctions d'exportation de OpenRefine, affichées en haut et à droite de chaque projet. Mais il est conseillé de sauvegarder le dossier de travail avant une mise à jour de OpenRefine. Si vous changez d'ordinateur, vous pourrez récupérer vos projets en cours en copiant ce dossier.

### Le même menu pour chaque colonne

Les menus dans OpenRefine ne sont pas affichés comme dans des logiciels classiques (Word, Photoshop, Firefox, etc.) mais apparaissent en cliquant sur les flèches à côté du titre de chaque colonne. Les menus de chaque colonne, à l'exception de la première colonne du projet proposent toutes les mêmes fonctions.

### Supprimer les espaces de début et de fin

Bonne pratique avant de traiter les données d'une colonne : Appliquer la fonction de suppression des espaces supplémentaires : `Edit cells > Common transforms > Trim leading and trailling whitespace` (`Editer les cellules > Transformations courantes > Supprimer les espaces de début et de fin`). La présence d'espaces supplémentaires arrive fréquemment, autant régler tout de suite le problème.

### Filtrer les données d'une colonne avec une facette

L'équivalent OpenRefine des filtres de Excel ou LibreOffice Calc sont les facettes. Pour avoir un aperçu rapide des valeurs d'une colonne, ou filtrer les lignes du projet en fonction des valeurs d'une colonne (par ex. afficher tous les cylindres dont la commune contient le mot « Saint »).

Vous pouvez cumuler l'affichage de plusieurs facettes (ex. afficher uniquement les cylindres dont la commune contient le mot « Saint » et de la marque « Maison de la bonne presse »).

Vous pouvez afficher l'inverse d'une sélection. Par exemple, dans l'inventaire des cylindres phonographiques, la commune (la colonne `Dublin Core Spatial Coverage`) n'est pas toujours indiquée. Pour afficher les cylindres sans commune, on applique une facette textuelle (`Text facet`) sur la colonne et on clique sur `(blank)`.

![blank](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2017_44_41-Window.png)

Pour afficher uniquement les cylindres pour lesquels la commune a été renseignée, on clique ensuite sur `invert`.

![invert](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2017_44_54-Window.png)

L'entête de la facette prend alors une couleur jaune pour indiquer qu'elle affiche l'inverse d'une sélection. Pour réinitialiser la facette, cliquez sur `reset`.

![invert](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2017_45_08-Window.jpg)

Attention, les fonctions ne s'appliquent que sur les lignes affichées. Pensez à réinitialiser les facettes pour appliquer une fonction sur toutes les lignes du projet.

### Tris permanents

Lorsque vous appliquez un tri sur une colonne (commande `Sort` du menu de la colonne), les lignes sont affichées dans l'ordre du tri, mais il ne s'agit que d'un affichage, l'ordre des lignes, indiqué par le numéro affiché dans la première colonne, `All` (`Toutes`), reste identique. Par conséquent, si vous exportez les données après un tri non permanent, vous constaterez dans le fichier d'export que les lignes auront conservé leur ordre original. De même, si vous quittez le projet, le tri ne sera pas sauvegardé. Pour rendre un tri permanent, cliquez sur `Reorder rows permanently` du menu `Sort`.

![Reorder rows permanently](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-30%2012_49_11-Avoir60ans%20xlsx%20-%20OpenRefine.png)

## Atelier n°2 : Nettoyage des réponses à un questionnaire

Autre exemple. Vous souhaitez exploiter les réponses à un questionnaire en ligne mais certaines réponses étaient libres, notamment la commune de résidence et les diplômes obtenus. Comment uniformiser les réponses pour les analyser avec le logiciel R ?

[Télécharger le fichier XLS](Files/Avoir60ans.xlsx), un inventaire réalisé dans le cadre de travaux dirigés en sciences sociales de l'Université de Bretagne Occidentale (merci à Nicole Roux pour ce fichier).

1. Créez un nouveau projet OpenRefine et importez le fichier Excel.
2. Appliquez une facette textuelle sur la colonne de la commune de résidence.
3. Supprimez les espaces de début et de fin (`Edit cells > Common transforms > Trim leading and trailing whitespace`) et les espaces consécutifs (`Edit cells > Common transforms > Collapse consecutive whitespace`) des noms de communes.
3. Uniformisez les noms des communes. Les noms des communes doivent commencer par une majuscule et il faut supprimer les départements indiqués entre parenthèses.

Pour uniformiser le nom des communes, trois solutions :

Editer à la main les cellules du tableau (commande `edit` au survol des cellules du tableau ou au survol des valeurs affichées dans la facette).

Si le nombre de cellules à nettoyer est trop élevé pour une édition à la main, on peut s'aider des algorithmes du menu `Edit cells > Cluster and edit` (`Editer les cellules > Grouper et éditer`). Cette fonction est également accessible depuis le lien `Cluster` des facettes.

![Cluster](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-30_21_31_24_Avoir60ansxlsx_OpenRefine.png)

> Pour comprendre les différents algorithmes des clusters, voir [le cours de Matthieu Saby](https://msaby.gitlab.io/atelier-openrefine-MASA/explorer-et-nettoyer-ses-donnees.html#regrouper-des-valeurs-proches).

Le problème, avec les précédentes solutions, c'est qu'elles ne permettent pas d'identifier formellement les communes. Par exemple, Tréméven est-elle [Tréméven](https://www.wikidata.org/wiki/Q688371) dans le Finistère ou [Tréméven](https://www.wikidata.org/wiki/Q214578) dans les Côtes-d'Armor ? Les communes saisies correpondent-elles vraiment à des communes ? Comment repérer ces erreurs ? La solution : Utiliser la réconciliation avec la base de données en ligne [Wikidata](https://www.wikidata.org).

Certaines personnes ont répondu en mettant entre parenthèses le nom ou le numéro du département. On aurait tord de ce priver de cette information. Pour séparer le département dans une nouvelle colonne, on choisi dans le menu de la colonne _Commune de résidence_, `Edit column > Split into several columns`, on saisi comme séparateur une parenthèse ouvrante `(` et on coche la case `Remove this column`. On se retouve avec deux colonnes _Commune de résidence 1_ et _Commune de résidence 2_. En appliquant une facette textuelle sur _Commune de résidence 2_ on constate que certaines personnes ont répondu au questionnaire en confondant la parenthèse fermante avec le caractère °. On a donc par exemple `22°` au lieu de `22)`.

On applique de nouveau la commande `Edit column > Split into several columns` mais sur la colonne _Commune de résidence 2_ et en saisisant cette fois `[)°]` comme séparateur et en cochant la case `regular expression`.

Faire une copie de la commune originale (`Edit column > Edit column based on this column`) puis sur la nouvelle colonne : `Reconcile > Start reconciling`.

Selon Wikipédia, en informatique, une expression régulière (regex en abrégé) est une chaîne de caractères qui décrit un ensemble de chaînes de caractères possibles selon une syntaxe précise. Dans notre cas, l'expression régulière `[)°]` correspond soit au caractère `)`, soit au caractère `°`.

On applique une facette textuelle sur la nouvelle colonne des départements et on remplace les noms en toutes lettres par le numéro du département. Par exemple, `Finistère` sera remplacé par `29`. Certains numéros de département sont considérés par OpenRefine comme des nombres. Pour faciliter l'affichage des valeurs avec une facette textuelle, on convertit toutes les valeurs en texte par `Edit Cells > Common transforms > To text`.

Pour améliorer l'identification des colonnes, on renomme les colonnes en _Commune de résidence_ et _Code département_.

On lance ensuite la réconciliation avec Wikidata avec le menu `Reconcile > Start reconciling...` sur la colonne _Commune de résidence_. Pour améliorer la réconciliation, on coche la case en regard de la colonne _Code département_ et on saisi `P131/P2586` dans `As property`. Attention, OpenRefine suggère s'ajouter le préfixe `SPARQL:` à la propriété, mais il faut pas l'accepter.

Certaines communes n'ont pas été réconciliées automatiquement. Soit parce qu'il existe des synonymes (_Saint-Servais_ dans les Côtes-d'Armor et _Saint-Servais_ dans le Finistère) soit à cause d'erreurs d'orthographe (_Landivisieau_ au lieu de _Landivisiau_). Dans ce dernier cas, on peut corriger l'erreur en éditant la cellule puis en cliquant sur `Apply to all identical cells` pour appliquer la modification sur toutes les cellules similaires. On relance ensuite la réconcilation pour toutes les cellules identiques en cliquant sur `Search for match`.

> Les facettes affichées automatiquement après la réconciliation disparaitront à la fermeture de OpenRefine. Pour les afficher de nouveau, menu _Reconcile > Facet > By judgment_.

Si on applique une facette textuelle sur la colonne _Commune de résidence_, on peut s'appercevoir que les noms originaux des communes ont été conservés, ce qui est pratique pour les comparer avec les communes correspondantes dans Wikidata. Toutefois, si on exporte le projet en l'état, la colonne des communes contiendra ces noms originaux. Pour récupérer le nom officiel de la commune, on crée une nouvelle colonne en choisissant dans le menu de la colonne _Commune de résidence_, `Edit Column > Add column based on this column...` et dans la champ `Expression` on saisi `cell.recon.match.name`.

> Cette formule mystérieuse est une expression en GREL (General Refine Expression Language), un language qui permet d'executer une série d'opérations dans OpenRefine. Pour en savoir plus sur le GREL, voir [le chapitre sur le GREL de la documentation officielle de OpenRefine](https://github.com/OpenRefine/OpenRefine/wiki/General-Refine-Expression-Language) (en anglais) ou [le cours de Mathieu Saby](https://msaby.gitlab.io/atelier-openrefine-MASA/annexe-structure-de-donnees-et-grel.html) (en français)

## Atelier n°3 : Fusionner un inventaire de variétés d'arbres de villes françaises avec un fichier d'informations sur ces villes

Le fichier [donnees_exo2.csv](Files/donnees_exo2.csv) contient un inventaire des espèces d'arbres plantés dans des villes françaises (les données sont fantaisistes). On souhaiterait ajouter dans ce fichier les informations sur les villes qui se trouvent dans le fichier [donnees_villes.csv](Files/donnees_villes.csv) (département, région, nombre d'habitants).

Pour fusionner les deux fichiers avec OpenRefine, il faut installer au préalable le [plugin VIB-BITS](https://www.bits.vib.be/software-overview/openrefine) développé par le BioInformatics Training and Services du Vlaams Intituut voor Biotechnologie.

Téléchargez et dézippez le fichier vib-bits.zip. Vous devez obtenir un dossier _vib-bits_.

Allez dans la liste des projets de OpenRefine :  menu `Open Project`...

![Open Project](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2014_45_28-Window.png)

... puis cliquez sur `Browse workspace directory`.

![Browse workspace directory](https://github.com/JBPressac/AtelierOpenRefine/blob/master/Files/2019-03-28%2014_29_48-Window.png)

Créez dans le répertoire qui s'affiche un sous-répertoire _extensions_ et copiez-y le répertoire _vib-bits_. Quittez OpenRefine et relancez-le.

> Pour quitter OpenRefine, il ne suffit pas de quitter votre navigateur web. Si vous êtes sous Windows, il faut fermer la ligne de commande dans laquelle OpenRefine est en cours d'exécution. Si vous êtes sous Mac, utilisez la commande `Quit` du menu de OpenRefine (Sous Mac, OpenRefine conserve son propre menu, en plus de celui du navigateur dans lequel s'exécute son interface). Sous Linux, il faut quitter le shell dans lequel s'execute OpenRefine avec Ctrl + C.

Si le plugin est correctement installé, un bouton VIB-BITS apparait en haut à droite en ouvrant n'importe quel projet.

Importez dans OpenRefine le fichier [donnees_exo2.csv](Files/donnees_exo2.csv) dans un projet que vous nommerez _Données Exo n°2_. Vous choisirez l'encodage (`Character encoding`) UTF-8 dans les paramètres d'importation.

Séparer les villes dans des lignes distinctes avec `Edit cells > Split multi-valued cells` en choisissant le `;` comme séparateur.

Recopiez le nom de l'espèce et le nombre de spéciments dans les nouvelles lignes en appliquant `Edit cells > Fill down` sur les deux colonnes concernées.

Appliquez une facette textuelle sur la colonne des villes pour en uniformiser les noms.

Importez dans un projet que vous nommerez _Données villes_, le fichier [donnees_villes.csv](Files/donnees_villes.csv). Le fichier est également encodé en UTF-8.

Retournez dans le projet _Données Exo n°2_. Puis depuis la colonne _ville_ choisissez `Edit column > Add column(s) from other projects`, une nouvelle fonction rajoutée par le plugin VIB-BITS. Choisissez le projet _Données villes_ puis la colonne correspondante _ville_ (il s'agit là de la colonne _ville_ de _Données villes_) puis les colonnes à importer : _dpt_, _region_, _habitants_.

## Atelier n°4 : Nettoyage d'un extrait de l'inventaire du Powerhouse Museum

Cet atelier s'inspire de "[Cleaning Data with OpenRefine](https://programminghistorian.org/en/lessons/cleaning-data-with-openrefine)", The Programming Historian 2 (2013), Seth van Hooland, Ruben Verborgh, and Max De Wilde. Vous trouverez dans cet article en ligne le détail des opérations à réaliser (en anglais).

Le fichier à nettoyer, [phm-collection.tsv](https://programminghistorian.org/assets/phm-collection.tsv), est un extrait de l'inventaire des objets conservés au [Powerhouse Museum](https://maas.museum/powerhouse-museum/) de Sydney. Chaque ligne du fichier correspond à un objet décrit notamment par un numéro d'enregistrement (_Record ID_), un titre (_Object Title_), un deuxième numéro d'enregisrement (_Registration number_), un texte de description (_Description_) et des _Categories_ (spéciments botaniques, numismatique, échantillons de minéraux, électroménager, etc.).

OpenRefine va nous servir à supprimer les lignes sans _Record ID_, à supprimer les doublons puis à nettoyer les catégories, séparées par des `|`.

### Importer un fichier TSV (Tab-separated values)

Importez dans OpenRefine le fichier phm-collection.tsv en décochant la case `Quotation marks are used to enclose cells containing column separators` et cochez la case `Parse cell text into numbers, dates, …`. Si vous avez bien paramétré l'import, le tableau des données doit comporter 75 814 lignes ou `rows`.

> Quand vous importez un fichier CSV ou TSV, vous avez la possibilité de spécifier son encodage. L'encodage est la manière de coder informatiquement des caractères alpha-numériques. Quelques encodages : UTF-8, ISO-8859-1, Windows-1252 (désigné sous le terme ANSI dans certains logiciels). OpenRefine ne detecte pas toujours très bien l'encodage des fichiers à importer, ce qui provoque des erreurs d'affichage des caractères accentués. Pour connaitre l'encodage des fichiers, vous pouvez les ouvrir avec Notepad++ (Microsoft Windows).

### Supprimer des lignes

A l'aide d'une facette numérique sur _Record ID_ et du menu `All > Edit rows > Remove all matching rows` de la première colonne, supprimez les lignes sans _Record ID_ (les cellules "vides" contiennent des espaces). A l'issue de la suppression, il doit rester 75 811 lignes.

### Supprimer des lignes en doublons

Il existe des lignes avec le même _Record ID_. La colonne étant de type numérique, il n'est pas possible d'afficher les doublons mais vous pouvez les afficher en créant une copie de la colonne, en convertissant ses valeurs en type chaîne de caractères puis en appliquant une facette textuelle qui indique le nombre d'occurences d'une valeur.

Pour supprimer les doublons, triez le contenu de la colonne et rendez le tri permanent avec `Reorder rows permanently` du menu `Sort`. Appliquez la commande `Edit cells > Blank down` sur la colonne _Record ID_. Si tout va bien, le contenu de la colonne est vidée sur 84 lignes. Le fait de vider le contenu de ces lignes crée des _records_ ou _entrées_. Il faut prendre garde de bien rester en mode d'affichage des lignes. Affichez ensuite les lignes vides avec la facette `Facet > Customized facets > Facet by blank` puis supprimez-les avec `All > Edit rows > Remove all matching rows`.

En apparence, les catégories sont séparées par des `|` mais si ont crée un filtre avec l'expression régulière `[|]{2,100}` on se rend compte qu'il peut y avoir deux `|` consécutifs comme séparateur.

On peut se laisser les doubles barres verticles telles quelles et séparer les catégories sur plusieurs lignes avec `Edit cells > Split multi-valued cells` et choisissez l'expression régulière `[|]+` comme caractère séparateur.

On peut aussi remplacer les doubles barres verticales avant de spérarer les catégories avec la commande `Edit cells > Transform` et la formule GREL `value.replace('||', '|')`.

Apliquez une facette textuelle sur la colonne des catégories et cliquez sur le bouton `Cluster` de la facette. Uniformisez les catégories.

Rassemblez de nouveau les catégories par `Edit cells > Join multi-valued cells` sur la colonne des _Categories_.
