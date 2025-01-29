# Data_engineering_project
Construire Datalake des informations de format JSON (API [Click here](https://earthquake.usgs.gov/fdsnws/event/1/#parameters) sur Azure Data factory

Mettre les données sur data lake pour construire pipeline (est une suite enchaînement de traitement sur données)de data avec microsoft data factory.
Architecture de data factory est basé sur Medallion Architecture, un modèle utilisé principalement dans Databricks et les data lakes pour organiser les données en plusieurs niveaux de qualité et de transformation.
![architecture pipeline](https://github.com/user-attachments/assets/f53e3be4-e3b8-491b-b65b-5d58d9c5d151)


**L'architecture Medallion repose sur trois couches principales**
Bien que le Medallion Architecture soit principalement utilisé avec Databricks, il peut être implémenté dans Azure Data Factory (ADF) en structurant les flux de données de la même manière :
### 1er étape : Bronze => données brutes sous format JSON	1er transform :extract+transofrm les données brutes, non transformées, directement extraites des sources+Stocke l’historique complet des données sans nettoyage dans une autre zone (Silver Layer)pour permettre la traçabilité et la reprise en cas d’erreurs.![setting 1er notebook](https://github.com/user-attachments/assets/57e53cca-97cc-409a-8f29-90ab6959c5a7)
### 2ème étpae :silver=> 2ème niveau de transformation :Données nettoyées, filtrées et normalisées+suppression des valeurs aberrantes ou doublons+Ajout de transformations basiques pour rendre les données exploitables
![setting 2e notebook](https://github.com/user-attachments/assets/3d761f9f-14f0-4a3b-b3f5-308e78f0d4d6)

### 3ème étpae :Gold 	3ème transform:load des données enrichies et prêtes pour l’analyse et la consommation métier et pour l'grégation, jointures et calculs avancés(le reporting, les tableaux de bord et les modèles analytiques).
![setting 3e notebook](https://github.com/user-attachments/assets/71d442ea-fafe-4e7c-a28f-fb2bde7936d5)
Chaque transformation est associé au fichier notebook. Chaque niveau a des informations spécifiques qui va être transformé à la couche suivante pour création d'un workflow.

Pour intégrer cette partie avec Power bi, on doit choisir Model sémantique (variable contenir les données de notebook gold pour le reporting) pour configure moi-même les visuelles ![semantic model](https://github.com/user-attachments/assets/03008caf-01c5-42e3-beb9-f215b34ebea6)

##Résulta finale pour le reporting


![visualisation](https://github.com/user-attachments/assets/e7eaabad-7ccf-4c76-b4ee-0f77432bb03e)



