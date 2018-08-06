Elasticsearch, Kibana and Logstash (ELK)
==================================

Instructions on how to integrate your django application with the elk stack

All these changes are made in your projects `settings.py` file.

Dependencies
------------
* `pip install elastic-apm`

* `pip install python-logstash`


Project Configuration
---------------------
 
* Add `elasticapm.contrib.django` to INSTALLED_APPS
* Add `elasticapm.contrib.django.middleware.TracingMiddleware` to MIDDLEWARE
* Add `elasticapm.contrib.django.middleware.Catch404Middleware` to MIDDLEWARE

Environment Variables
---------------------

* Add `LOGSTASH_URL = os.environ.get('LOGSTASH_URL', '')`
* Add `APM_SERVER = os.environ.get('APM_SERVER', '')`
* Add `ELASTIC_TOKEN = os.environ.get('ELASTIC_TOKEN', '')`


ELK Settings
-------------

`ELASTIC_APM = {
    'SERVICE_NAME': '<PROJECT NAME>',
    'SECRET_TOKEN': ELASTIC_TOKEN,
    'SERVER_URL': APM_SERVER
}
`

Logging
-------
* Add a new handlers for logstash

`'logstash': {
            'level': 'DEBUG',
            'class': 'logstash.TCPLogstashHandler',
            'host': LOGSTASH_URL,
            'port': 5959,
            'version': 1,
            'message_type': 'logstash',
            'fqdn': False,
            'tags': ['<PROJECT NAME>']
        },
`
* Add handler for elk

`'elasticapm': {
            'level': 'INFO',
            'class': 'elasticapm.contrib.django.handlers.LoggingHandler',
        },
`
Add the handlers as part of the loggers.


Production
-------------------
In production remember to add these environment variables

* dokku config:set <app name> LOGSTASH_URL=<url to logstash instance>

If you want to make sure that the settings are correct you can run 

`python manage.py elasticapm test`

this will try and send an example error message to elk. It will let you know whether it was successful or not.
