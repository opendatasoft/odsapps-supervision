# ODS Apps - Supervision 

## Deployment guide

#### Create a new dataset from `domaindatasets://` source

- See the [documentation here to create the dataset](https://help.opendatasoft.com/platform/fr/publishing_data/04_configuring_a_source/connectors/dataset_of_datasets.html)
- Dataset ID must be : `domaindatasets`
- Source type is the `domain_datasets` extractor
- Tick all settings, but mostly these two are mandatory : `admin_metadata` and `custom_metadata` 

[(resource settings available here)](source.json)

#### Set the app processing pipeline 

- Processing pipeline [available here](processing_pipeline.json)
- To apply a processing pipeline from a configuration file, please see [cmds here](processing_pipeline_copy-paste-cmds.md)
- then publish the dataset

#### Add 4 metadata, 2 custom and 2 admin

 - Ask ODS to add these 2 *custom metadata* to your portal (in the default template, ie. it will avoid to prefix the field id)
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
       - `Mensuelle`
       - `Trimestrielle`
       - `Annuelle`
       
 - Ask ODS to add these 2 *admin metadata* to your portal (in the `admin` template)
   - "Point de contact - nom"
     - ID : `point_de_contact_nom` (that will be `admin_point_de_contact_nom` within the `admin` template)
     - Type : Input field / Text
   - "Point de contact - email"
     - ID : `point_de_contact_email` (that will be `admin_point_de_contact_email` within the `admin` template)
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


# Batch edit of metadata

If you intend to deploy the app on an existing and old open data portal, you probably already have tons of data, multiple public and private datasets;
Therefore filling all metadata values could be a bit long. 

ODS CSMs can help you in this task. They developped a POSTMAN Collection, to update all your datasets metadata automatically by providing the right CSV file. Do not hesitate to get in touch.

[To read more, follow the documentation here](https://github.com/opendatasoft/ods-cookbook/tree/master/management-api)
