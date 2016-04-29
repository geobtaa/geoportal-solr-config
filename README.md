# Solr Core Config for Geoblacklight
This repo houses static configuration for Blacklight (Geoblacklight) in Solr.

After Solr has been installed, this directory should be placed via symlink into `solr/server/solr`. 
It is not advised to copy it there, but rather symlink it into place; when using Rake to load a new solr via `rake solr:clean` (provided by `solr_wrapper`) it would be deleted.

Configuration originated with the Geoblacklight project at https://github.com/geoblacklight/geoblacklight-schema

## Data
The `data/` directory is present here, but its contents are not versioned.

## Example
Assuming Solr has been installed to `/swadm/usr/local/solr`:

```shell
# Clone this repo into a directory like solr-cores/ and link into place
$ mkdir /swadm/usr/local/solr-cores
$ cd /swadm/usr/local/solr-cores && git clone git@github.umn.edu:Libraries/geoblacklight-solr-config

# Geoblacklight will be expecting a core named "blacklightcore"
$ ln -s /swadm/usr/local/solr-cores/geoblacklight-solr-config /swadm/usr/local/solr/server/solr/blacklightcore
```

Restart Solr to load the core.  From within Geoblacklight as swadm:

```shell
$ rake solr:restart
```
