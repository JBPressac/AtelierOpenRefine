# Atelier OpenRefine
OpenRefine est un logiciel libre permettant de traiter des données. Avec OpenRefine, vous pourrez trier vos données, les filtrer, repérer des valeurs manquantes, incomplètes ou aberrantes, supprimer les doublons, harmoniser les valeurs, diviser le contenu d'une colonne en plusieurs, assembler le contenu de plusieurs colonnes en une seule, enrichir les données à partir de bases de données telles que Wikidata.

OpenRefine peut importer des données tabulaires, c'est à dire structurées en lignes et en colonnes telles que des fichiers Microsoft Excel, LibreOffice Calc, OpenOffice Calc, Google Documents, CSV, TSV. Il peut aussi traiter des fichiers XML, JSON.

Dans quels cas OpenRefine pourrait vous être utile ? Vous avez récupéré le fichier Excel de l'inventaire des cylindres phonographiques du Centre de recherche bretonne et celtique et vous avez remarqué qu'il contenait une colonne avec le nom de la commune d'où proviennent les cylindres. Vous aimeriez bien les afficher sur une carte mais vous ne savez pas comment récupérer leurs coordonnées géospatiales.

Vous remarquez également en appliquant un filtre dans Excel quelques erreurs de saisie. Par exemple, Saint-Avé a été saisi une fois « Saint Avé » (sans tiret) et cinq fois « Saint-Avé ». Vous remarquez également que la colonne peut contenir deux noms de communes, séparés par un point-virgule : Saint Avé (56206); Morlaix (29151). OpenRefine peut vous aider à :
1. identifier les erreurs de saisie et les corriger,
2. séparer les noms de communes dans plusieurs colonnes,
3. récupérer les coordonnées spatiales depuis la base de données Wikidata,
4. exporter les noms des communes et les coordonnées spatiales pour les afficher sur une carte du site [uMap][5e5df6f9].

  [5e5df6f9]: https://umap.openstreetmap.fr/fr/ "uMap"
