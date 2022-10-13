# Solr Core Config for Geoblacklight
This repo houses static configuration for Blacklight (Geoblacklight) in Solr.

After Solr has been installed, this directory should be placed via symlink into `solr/server/solr`.
It is not advisable to copy it there, but rather symlink it into place. Certain toolchains like the `solr_wrapper` gem's `rake` tasks may delete it otherwise.

Configuration originated with the Geoblacklight project at https://github.com/geoblacklight/geoblacklight-schema

## Data
The `data/` directory is present here, but its contents are not versioned.

## Example
Assuming Solr has been installed to `/usr/local/solr`:

```shell
# Clone this repo into a directory like solr-cores/ and link into place
$ mkdir /usr/local/solr-cores
$ cd /usr/local/solr-cores && git clone git@github.umn.edu:Libraries/geoblacklight-solr-config

# Geoblacklight will be expecting a core named "blacklightcore"
$ ln -s /usr/local/solr-cores/geoblacklight-solr-config /usr/local/solr/server/solr/blacklightcore
```

Restart Solr to load the core. (while logged in or `su` to the user solr should run as)

```shell
$ cd /usr/local/solr && bin/solr restart
```

## Deployment
BTAA Geoportal core deployment instructions reside in internal UMN server build docs.

## Branches and Core Name
`core.properties` must bear the correct name `development` or `production` in the `develop` and `master` branches respectively.

When git-flow creates a release, it may merge the master state of `core.properties` with `name=production` back into the `develop` branch, and solr may fail to start correctly on hosts that have a version of both core branches!  The error is
```
o.a.s.c.SolrCore null:org.apache.solr.common.SolrException: Found multiple cores with the name [production], with instancedirs [/swadm/var/solr/data/production] and [/swadm/var/solr/data/development]
        at org.apache.solr.core.CoreContainer.checkForDuplicateCoreNames(CoreContainer.java:811)
        at org.apache.solr.core.CoreContainer.load(CoreContainer.java:673)
...
...
INFO  (main) [   ] o.e.j.s.Server Started @2674ms
ERROR (qtp898557489-19) [   ] o.a.s.s.SolrDispatchFilter Error processing the request. CoreContainer is either not initialized or shutting down.
WARN  (qtp898557489-19) [   ] o.e.j.s.HttpChannel /solr/production/select
javax.servlet.ServletException: javax.servlet.UnavailableException: Error processing the request. CoreContainer is either not initialized or shutting down.
        at org.eclipse.jetty.server.handler.HandlerCollection.handle(HandlerCollection.java:146) ~[jetty-server-9.4.14.v20181114.jar:9.4.14.v20181114]
        at org.eclipse.jetty.server.handler.HandlerWrapper.handle(HandlerWrapper.java:132) ~[jetty-server-9.4.14.v20181114.jar:9.4.14.v20181114]
        at org.eclipse.jetty.rewrite.handler.RewriteHandler.handle(RewriteHandler.java:335) ~[jetty-rewrite-9.4.14.v20181114.jar:9.4.14.v20181114]
        at org.eclipse.jetty.server.handler.HandlerWrapper.handle(HandlerWrapper.java:132) ~[jetty-server-9.4.14.v20181114.jar:9.4.14.v20181114]
        at org.eclipse.jetty.server.Server.handle(Server.java:502) ~[jetty-server-9.4.14.v20181114.jar:9.4.14.v20181114]
```


### Release Version

B1G Geoportal Version 4.8.0 / GEOMG 0.15.1 / GeoBlacklight 4.0.0
