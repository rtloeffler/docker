###Need to run this or android cant login

sudo docker-compose exec --user www-data app php occ config:system:set overwriteprotocol --value="https"


source: 
https://github.com/nextcloud/android/issues/4786
