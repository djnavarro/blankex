# Get data from app engine

Pages where I worked out the app engine side

- https://cloud.google.com/datastore/docs/reference/libraries
- https://cloud.google.com/datastore/docs/concepts/queries

Dealing with the python JSON side 

- https://stackoverflow.com/questions/11875770/how-to-overcome-datetime-datetime-not-json-serializable/36142844#36142844


## Step 1: Update gcloud tools

The install command is:

```
pip install --upgrade google-cloud-datastore
```

## Step 2: Authorisation

- Go to the Create service account key page in the GCP Console. [here](https://console.cloud.google.com/apis/credentials/serviceaccountkey?_ga=2.49411173.-233779197.1524356117) 
- From the Service account drop-down list, select New service account.
- Enter a name into the Service account name field.
- From the Role drop-down list, select Project > Owner.
- Click Create. A JSON file that contains your key downloads to your computer.

I saved mine to "~/Webpage/unswrobot" 

We'll need to set the environment variable too:

```
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/[FILE_NAME].json"
```

## Step 3: Download

The link above re "queries" has a lot of information about how to structure queries to datastore in python, and the stackoverflow page has a good tip for how to get lists out of python and saved as a JSON object.

I wrote a small python script that queries all entities in the data store, stores as python list, serialises to json and then prints it. At the command line, pipe it to a file like so:

```
python downloadall.py > mydata.json
```

The `mydata.json` file now has all the data in a format we can read into R 



## NOTE

In at least one case, we've had issues with people being unable to update the gcloud tools. The problem turned out to be that pip was outdated and was handling openSSL wrong:

Issue with installation. Error message:

```
Could not fetch URL https://pypi.python.org/simple/pip/: There was a problem confirming the ssl certificate: [SSL: TLSV1_ALERT_PROTOCOL_VERSION] tlsv1 alert protocol version (_ssl.c:661) - skipping
```
The issue was tied to the fact that this machine had python 2.7 and 3.2 installed, but pip was 2.7...

Workaround: https://stackoverflow.com/questions/13336852/setting-python3-2-as-default-instead-of-python2-7-on-mac-osx-lion-10-7-5

The safest way is to set an alias in ~/.bashrc:
alias python=python3
That way you avoid breaking things for scripts relaying on python being python2.

This still did not work. Had to use:

```
python3.6 -m pip install --upgrade google-cloud-datastore
```

