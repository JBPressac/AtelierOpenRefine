# Atelier OpenRefine, Nanterre, 5 avril 2019
[OpenRefine](http://openrefine.org) est un logiciel libre permettant de traiter des données. Avec OpenRefine, vous pourrez trier vos données, les filtrer, repérer des valeurs manquantes, incomplètes ou aberrantes, supprimer les doublons, harmoniser les valeurs, diviser le contenu d'une colonne en plusieurs, assembler le contenu de plusieurs colonnes en une seule, enrichir les données à partir de bases de données telles que [Wikidata][70123744].

  [70123744]: https://outiquanti.hypotheses.org/875 "Découverte de Wikidata"

OpenRefine peut importer des données tabulaires, c'est à dire structurées en lignes et en colonnes telles que des fichiers Microsoft Excel, LibreOffice Calc, OpenOffice Calc, Google Documents, [CSV][61446736], TSV. Il peut aussi traiter des fichiers XML et JSON et se connecter à une base de données relationnelle (type MySQL ou PostgreSQL).

  [61446736]: https://fr.wikipedia.org/wiki/Comma-separated_values "Comma-separated values"

Dans quels cas OpenRefine pourrait vous être utile ? Vous avez récupéré [le fichier Excel de l'inventaire des cylindres phonographiques](https://f.hypotheses.org/wp-content/blogs.dir/2183/files/2018/12/Inventaire-des-cylindres-phonographiques-du-CRBC.xlsx) du Centre de recherche bretonne et celtique et vous avez remarqué qu'il contenait une colonne avec le nom de la commune d'où proviennent les cylindres. Vous aimeriez bien les afficher sur une carte mais vous ne savez pas comment récupérer leurs coordonnées géospatiales. Vous remarquez également quelques erreurs de saisie en appliquant un filtre dans Excel. Par exemple, Saint-Avé a été saisi une fois « Saint Avé » (sans tiret) et cinq fois « Saint-Avé » (avec un tiret). Vous remarquez également que la colonne peut contenir deux noms de communes, séparés par un point-virgule : Saint Avé (56206); Morlaix (29151).

OpenRefine peut vous aider à :
1. identifier les erreurs de saisie et les corriger,
2. séparer les noms de communes,
3. récupérer les coordonnées spatiales depuis la base de données Wikidata,
4. exporter les noms des communes et les coordonnées spatiales pour les afficher sur une carte du site [uMap][5e5df6f9].

  [5e5df6f9]: https://umap.openstreetmap.fr/fr/ "uMap"

Sous OpenRefine vous ne pourrez pas appliquer des formules mathématiques (calcul de sommes, de moyennes, test du Khi2, exponentielles, etc.) ou dessiner des graphiques comme vous pouvez le faire avec Excel ou LibreOffice Calc. Vous pourrez supprimer des colonnes avec OpenRefine mais pas des lignes.

## Installation de OpenRefine
OpenRefine fonctionne sous Microsoft Windows, Mac OS et Linux. Vous trouverez toutes les instructions d'installation sur [la documentation officielle](https://github.com/OpenRefine/OpenRefine/wiki/Installation-Instructions) (en anglais) ou sur [le cours de Mathieu Saby](https://msaby.gitlab.io/atelier-openrefine-MASA/installation-lancement-desinstallation.html) (en français). Sous Windows, vous aurez probablement besoin d'installer le logiciel [Java](https://www.java.com/fr/download/) (Java est installé par défaut sous Mac et Linux).

## Atelier n°1 : Nettoyage d'une liste de communes bretonnes et récupération des coordonnées géographiques sur Wikidata

Pour le détail des opérations, voir [Créer une carte avec Wikidata, OpenRefine et uMap](https://bylg.hypotheses.org/543).

Autre exemple. Vous souhaitez exploiter les réponses à un questionnaire en ligne mais certaines réponses étaient libres, notamment la commune de résidence et les diplômes obtenus. Comment uniformiser les réponses pour les analyser avec le logiciel R ?
