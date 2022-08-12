# Heroku Buildpack for Logstash

This buildpack downloads and installs Logstash into a Heroku app slug. It is a fork of [omc/heroku-buildpack-kibana](https://github.com/omc/heroku-buildpack-kibana).

## Usage

As a standalone buildpack:

    # Create a new project with the --buildpack option
    $ heroku create --buildpack https://Osprey-Solutions-AS/heroku-buildpack-logstash

    # ...Or update an existing project with heroku buildpacks:set
    $ heroku buildpacks:set https://github.com/Osprey-Solutions-AS/heroku-buildpack-logstash

    # Let the buildpack know where to find Logstash
    $ heroku config:set DOWNLOAD_URL="https://download.elastic.co/logstash/logstash/logstash-8.3.3.tar.gz"

    # Let Logstash know where to find Elasticsearch
    $ heroku config:set ELASTICSEARCH_URL="https://{user}:{password}@osprey-prod.es.northeurope.azure.elastic-cloud.com:9243"

    # Create a Procfile to run the Logstash web server
    ```
    Procfile
    ...
    web: logstash agent -f logstash.conf
    ...
    ```

    # Create a logstash.conf
    $ ...

    # Push the above to trigger a deploy
    $ git push heroku master

    # Verify and profit!
    $ heroku open
