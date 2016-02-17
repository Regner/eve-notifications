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
