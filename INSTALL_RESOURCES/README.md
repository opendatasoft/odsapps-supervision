# ODS Apps - Supervision 

## Deployment guide

#### Create a new dataset from `domaindataset://` source

- you must ask ODS to activate domaindataset extractor first
- Dataset ID must be : `domaindatasets`

#### Set the app processing pipeline 

- Processing pipeline [available here](processing_pipeline.json)
- To apply a processing pipeline from a configuration file, please see [cmds here](processing_pipeline_copy-paste-cmds.md)
- then publish the dataset

#### Add 4 custom metadata

 - Ask ODS to add these 4 custom metadata to your portal 
   - "Cycle de publication"
     - ID : `cycle`
     - Type : enum
     - Values :
       - ø (Allow empty field)
       - `Collecter`
       - `Editer`
       - `Mettre en forme`
       - `Mettre à jour`
       - `Finalisé`
   - "Périodicité"
     - ID : `periodicity`
     - Type : enum
     - Values :
       - ø (Allow empty field)
       - `Irrégulier`
       - `Minute`
       - `Quotidien`
       - `Hebdomadaire`
       - `Mensuel`
       - `Trimestriel`
       - `Annuel`
   - "Point de contact - nom"
     - ID : `pointofcontactname`
     - Type : Input field / Text
   - "Point de contact - email"
     - ID : `pointofcontactemail`
     - Type : Input field / Text

#### Create 3 pages

- `action` and copy it's content [HTML](web/action.html) [CSS](web/action.css)
- `periodique` and copy it's content [HTML](web/periodique.html) [CSS](web/periodique.css)
- `jeuxdedonnees` and copy it's content [HTML](web/jeuxdedonnees.html) [CSS](web/jeuxdedonnees.css)

#### Add action page to the navigation menu of your portal


# Logigramme by Datactivist !

To install/get the Logigramme version of the App

- Take actiondatactivist.html/css content instead of action.html/css
- Change metadata values list in jeuxdedonnees.html l.13

Supervision : `'order': [0, 'Tous','Collecter', 'Éditer', 'Mettre en forme', 'Mettre à jour', 'Finalisé','Non suivi']`
Logigramme : `'order': [0, 'Tous','Identifier', 'Valider', 'Extraire', 'Éditer', 'Standardiser','Publier','Mettre à jour','Non suivi']`