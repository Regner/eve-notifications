# eve-notifications

# Repos
* [en-api-gateway](https://github.com/Regner/en-api-gateway): NGINX gateway routing external requests to
the apropriate service in the cluster.
* [en-gcm](https://github.com/Regner/en-gcm): Allows the registration of GCM tokens from clients and also
allows services in the cluster to get all tokens associated with a given list of character IDs.
* [en-kube-config](https://github.com/Regner/en-kube-config): Kubernetes config files.
* [en-notifications](https://github.com/Regner/en-notifications): Service that handles polling the
notifications pubsub resource and sending notifications via GCM.
* [en-rss](https://github.com/Regner/en-rss): Polls a list of RSS feeds and upon new entries sends a
notification to all characters subscribed to that feed.
* [en-rss-settings](https://github.com/Regner/en-rss-settings): Allows clients to configure which RSS feeds
they wish to subscribe to and also allows internal services to lookup all character IDs subscribed to a feed.
* [en-test](https://github.com/Regner/en-test): Allows devlopers to send a test notification to a character.

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
