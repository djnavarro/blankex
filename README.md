# Blank Experiment

A minimal template for running experiments through the browser using jsPsych and Google App Engine. Intended to work in conjunction with MTurk and adhere to UNSW ethics guidelines. Notes:

- If there are additional folders add those in app.yaml 
- Each jsPsych trial type needs to be added
- The welcome.js file has various standard fields to fill out
- Currently it writes data to console; uncomment the lines in endExperiment() to  submit data to GAE instead
- `backend.py` is minimal: it handles writes to datastore only
- Deploy command

`gcloud app deploy --project==PROJECTNAME`

- Downloading data from GAE. see `download` folder.

TODO: I should expand this template to make use of a few more plugins and clean up the documentation