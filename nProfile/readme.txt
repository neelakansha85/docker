Docker Commands


# restore the database with /data/database.sql
docker exec $(docker ps -lq) /bin/bash -c "wp db import /data/database.sql --allow-root"

# dump the database to /data/database_bk.sql
docker exec $(docker ps -lq) /bin/bash -c "wp db export /data/database_bk.sql --allow-root"


# install a plugin
docker exec $(docker ps -lq) /bin/bash -c "wp plugin install akismet --allow-root"

# remove a plugins
docker exec $(docker ps -lq) /bin/bash -c "wp plugin uninstall akismet --deactivate --allow-root"