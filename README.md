# EVE Notifications
EVE Notifications is a cluster of microservices designed to gather information
from around the internet about EVE Online and push notifications to subscibers
with the use of [Google Cloud Messaging](https://developers.google.com/cloud-messaging/).
Each microservice is built as a Docker container and deployed to Google's hosted
Kubernetes service [Google Container Engine](https://cloud.google.com/container-engine/).

# Architecture
![EVE Notifications architecture](https://docs.google.com/drawings/d/1-wmdKDOYrkYCHlieJwbCfjiuxHLUmVmPVe2M64oNGNs/pub?w=1452&amp;h=658g "EVE Notifications architecture")

## Concepts
* __Providers:__ These are services that sit within the cluster and do the
actual work of finding new information that users might be interested in. A
simple example is monitoring RSS feeds and realizing when a new post is made.
Once they detect something worth sending a notification for they contact a
settings service and then publish a message to the [Google PubSub](https://cloud.google.com/pubsub/)
service.
* __Provider Settings:__ Since providers themselves scale in terms of their
workload and that is constant, the setting services for them need to scale
indemendently as their load is based on the number of users for the service. So
the services for exposing the settings are written seperately and expose HTTP
interfaces both internally and externally. Internally this lets the providers
access the information they need to know what users to send a notification to
and extenally this allows clients to get a list of possible settings and to set
those on a per character basis.
* __API Gateway:__ The API Gateway is a simple NGINX service that routes
requests to the apropriate service internally and allows for a single service to
be exposed externally instead of each settings service being exposed.
* __Notification Sender:__ This service monitors the Google PubSub via a pull
subscription and whenever a new notification is found it asks the EN-GCM service
for all of the GCM tokens for a given list of character IDs and then sends a
message via GCM.

## Client Flow
![EVE Notifications client flow](https://docs.google.com/drawings/d/1KuVy3kJGLrkPV0Yusqh0bxVOBvK6vYmu6GIzeIDW-f0/pub?w=1363&amp;h=1164 "EVE Notifications client flow")

# Repos
* __[en-api-gateway](https://github.com/Regner/en-api-gateway):__ NGINX gateway
routing external requests to the apropriate service in the cluster.
* __[en-gcm](https://github.com/Regner/en-gcm):__ Allows the registration of GCM
tokens from clients and also allows services in the cluster to get all tokens
associated with a given list of character IDs.
* __[en-kube-config](https://github.com/Regner/en-kube-config):__ Kubernetes
config files.
* __[en-notifications](https://github.com/Regner/en-notifications):__ Service
that handles polling the notifications pubsub resource and sending notifications
via GCM.
* __[en-rss](https://github.com/Regner/en-rss):__ Polls a list of RSS feeds and
upon new entries sends a notification to all characters subscribed to that feed.
* __[en-rss-settings](https://github.com/Regner/en-rss-settings):__ Allows
clients to configure which RSS feeds they wish to subscribe to and also allows
internal services to lookup all character IDs subscribed to a feed.
* __[en-test](https://github.com/Regner/en-test):__ Allows devlopers to send a
test notification to a character.

## Status Badges
|                                                                | Circle CI Build                                                                                                                | Requirements Status                                                                                                                                                                         |
|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [en-api-gateway](https://github.com/Regner/en-api-gateway)     | [![Circle CI](https://circleci.com/gh/Regner/en-api-gateway.svg?style=svg)](https://circleci.com/gh/Regner/en-api-gateway)     | [![Requirements Status](https://requires.io/github/Regner/en-api-gateway/requirements.svg?branch=master)](https://requires.io/github/Regner/en-api-gateway/requirements/?branch=master)     |
| [en-gcm](https://github.com/Regner/en-gcm)                     | [![Circle CI](https://circleci.com/gh/Regner/en-gcm.svg?style=svg)](https://circleci.com/gh/Regner/en-gcm)                     | [![Requirements Status](https://requires.io/github/Regner/en-gcm/requirements.svg?branch=master)](https://requires.io/github/Regner/en-gcm/requirements/?branch=master)                     |
| [en-notifications](https://github.com/Regner/en-notifications) | [![Circle CI](https://circleci.com/gh/Regner/en-notifications.svg?style=svg)](https://circleci.com/gh/Regner/en-notifications) | [![Requirements Status](https://requires.io/github/Regner/en-notifications/requirements.svg?branch=master)](https://requires.io/github/Regner/en-notifications/requirements/?branch=master) |
| [en-rss](https://github.com/Regner/en-rss)                     | [![Circle CI](https://circleci.com/gh/Regner/en-rss.svg?style=svg)](https://circleci.com/gh/Regner/en-rss)                     | [![Requirements Status](https://requires.io/github/Regner/en-rss/requirements.svg?branch=master)](https://requires.io/github/Regner/en-rss/requirements/?branch=master)                     |
| [en-rss-settings](https://github.com/Regner/en-rss-settings)   | [![Circle CI](https://circleci.com/gh/Regner/en-rss-settings.svg?style=svg)](https://circleci.com/gh/Regner/en-rss-settings)   | [![Requirements Status](https://requires.io/github/Regner/en-rss-settings/requirements.svg?branch=master)](https://requires.io/github/Regner/en-rss-settings/requirements/?branch=master)   |
| [en-test](https://github.com/Regner/en-test)                   | [![Circle CI](https://circleci.com/gh/Regner/en-test.svg?style=svg)](https://circleci.com/gh/Regner/en-test)                   | [![Requirements Status](https://requires.io/github/Regner/en-test/requirements.svg?branch=master)](https://requires.io/github/Regner/en-test/requirements/?branch=master)                   |

* Table generated using [Tables Generator](http://www.tablesgenerator.com/markdown_tables).
