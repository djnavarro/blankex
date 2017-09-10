# Blank Experiment

A minimal template for running experiments through the browser using jsPsych and Google App Engine. Intended to work in conjunction with MTurk and adhere to UNSW ethics guidelines. Notes:

- In the app.yaml file, edit the project ID
- If there are additional folders add those in app.yaml 
- Each jsPsych trial type needs to be added
- The welcome.js file has various standard fields to fill out
- importData.R is a simple R script that downloads the data from GAE and organises it into a tidy CSV file