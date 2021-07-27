# ODS Apps - Supervision

## Deployment guide

#### Create a new dataset from `domaindatasets://` source

- See
  the [documentation here to create the dataset](https://help.opendatasoft.com/platform/fr/publishing_data/04_configuring_a_source/connectors/dataset_of_datasets.html)
- Dataset ID must be : `domaindatasets`
- Source type is the `domain_datasets` extractor
- Tick all settings, but mostly these two are mandatory : `admin_metadata` and `custom_metadata`

[(resource settings available here)](source.json)

#### Set the app processing pipeline

- Processing pipeline [available here](processing_pipeline.json)
- To apply a processing pipeline from a configuration file, please
  see [cmds here](processing_pipeline_copy-paste-cmds.md)
- then publish the dataset

#### Add 4 metadata, 2 custom and 2 admin

- Ask ODS to add these 2 *custom metadata* to your portal (in the default template, ie. it will avoid to prefix the
  field id)
    - "Publication cycle"
        - ID : `cycle`
        - Type : enum
        - Values :
            - ø (Allow empty field)
            - `Collect`
            - `Edit`
            - `Format`
            - `Update`
            - `Finalized`
    - "Periodicity"
        - ID : `periodicity`
        - Type : enum
        - Values :
            - ø (Allow empty field)
            - `Unplanned`
            - `Minute`
            - `Daily`
            - `Weekly`
            - `Monthly`
            - `Quarterly`
            - `Yearly`

- Ask ODS to add these 2 *admin metadata* to your portal (in the `admin` template)
    - "Contact point - name"
        - ID : `contact_point_name` (that will be `admin_contact_point_name` within the `admin` template)
        - Type : Input field / Text
    - "Contact point - email"
        - ID : `contact_point_email` (that will be `admin_contact_point_email` within the `admin` template)
      - Type : Input field / Text

#### Create 3 pages

- `action` and copy it's content [HTML](web/action.html) [CSS](web/action.css)
- `supervised` and copy it's content [HTML](web/supervised.html) [CSS](web/supervised.css)
- `datasets` and copy it's content [HTML](web/datasets.html) [CSS](web/datasets.css)

#### Optionally

You can add the action page to the navigation menu of your portal


# Batch edit of metadata

If you intend to deploy the app on an existing and old open data portal, you probably already have tons of data,
multiple public and private datasets; Therefore filling all metadata values could be a bit long.

ODS CSMs can help you in this task. They developped a POSTMAN Collection, to update all your datasets metadata
automatically by providing the right CSV file. Do not hesitate to get in touch.

[To read more, follow the documentation here](https://github.com/opendatasoft/ods-cookbook/tree/master/management-api)
