Setup locally:
==============

copy buildout.cfg.example to buildout.cfg, edit it and run:

# python bootstrap.py -d
# ./bin/buildout

Setup on Dev environment:
=========================

create a buildout.cfg with the following content:

[buildout]
extends =
    dev.cfg

[jena]
dbhost=<host>
dbname=<dbname>
dbuser=<dbuser>
password=<dbpass>

run:

# python26 bootstrap.py -d --setup-source=sources/distribute_setup.py --download-base=sources
# ./bin/buildout -o -N


Setup on Test environment:
=========================

run:

# python26 bootstrap.py -d --setup-source=sources/distribute_setup.py --download-base=sources -c test.cfg
# ./bin/buildout -o -N -c test.cfg


Setup on Prod environment:
=========================

run:

# python26 bootstrap.py -d --setup-source=sources/distribute_setup.py --download-base=sources -c prod.cfg
# ./bin/buildout -o -N -c prod.cfg


Additional work that might be necessary:
========================================

* create folder /app/researchhub-data/moai
* put moai service into autostart (./bin/paster serve --daemon etc/moai.ini )
* put moai update script under cron control or similar
* beware of load balanced setup for moai (localized data?)
