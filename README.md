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
$ cd /usr/local/solr && bin/solr/start
```
