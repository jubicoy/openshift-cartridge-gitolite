# OpenShift Gitolite Cartridge

This is a Gitolite cartridge for OpenShift.

## Why

Smart HTTP from Git, the fine-grained access control from Gitolite and
authentication from Apache seem to play well together. Why should that *not* be wrapped
into an OpenShift cartridge?

## Authentication

The current version supports only Basic Authentication against
htpasswd file. However, it would be easier to list authentication
backends Apache does not support. The next candidates for wrapping into
the cartridge are most likely LDAP and CAS.

## Installation

This cartridge is an embedded cartridge and requires a primary web
cartridge to function and the intended usage would be to drop this cartridge
into an application with a repository browser, such as Gitweb or Redmine.

Create an application with desired primary cartridge and add this
cartridge as an embedded cartridge by linking the
[manifest.yml](https://github.com/jubicoy/openshift-cartridge-gitolite/raw/master/metadata/manifest.yml)
to the *Install your own cartridge* field.

## Configure

To manage ACLs and repositories clone the gitolite-admin repository using the
provided admin credentials. Adding users requires connecting to the
application with SSH and manually modifying `$OPENSHIFT_DATA_DIR/gitolite-home/.htpasswd`
with `htpasswd`.
