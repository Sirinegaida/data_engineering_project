# data_engineering_project
Construire Datalake des informations de format JSON (API) sur Azure Data factory

Mettre les données sur data lake pour construire pipeline (est une suite enchaînement de traitement sur données)de data avec microsoft data factory.
Architecture de data factory est basé sur Medallion Architecture, un modèle utilisé principalement dans Databricks et les data lakes pour organiser les données en plusieurs niveaux de qualité et de transformation.

**L'architecture Medallion repose sur trois couches principales**
Bien que le Medallion Architecture soit principalement utilisé avec Databricks, il peut être implémenté dans Azure Data Factory (ADF) en structurant les flux de données de la même manière :
### 1er étape : Bronze => données brutes sous format JSON	1er transform :extract+transofrm les données brutes, non transformées, directement extraites des sources+Stocke l’historique complet des données sans nettoyage dans une autre zone (Silver Layer)pour permettre la traçabilité et la reprise en cas d’erreurs.
### 2ème étpae :silver=> 2ème niveau de transformation :Données nettoyées, filtrées et normalisées+suppression des valeurs aberrantes ou doublons+Ajout de transformations basiques pour rendre les données exploitables
### 3ème étpae :Gold 	3ème transform:load des données enrichies et prêtes pour l’analyse et la consommation métier et pour l'grégation, jointures et calculs avancés(le reporting, les tableaux de bord et les modèles analytiques).
Chaque transformation est associé au fichier notebook. Chaque niveau a des informations spécifiques qui va être transformé à la couche suivante pour création d'un workflow.
Model sémantique : variable contenir les données de notebook gold=>pour le reporting


