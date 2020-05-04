##Need to run this or android cant login

sudo docker-compose exec --user www-data app php occ config:system:set overwriteprotocol --value="https"


source: 
https://github.com/nextcloud/android/issues/4786





****** new install
install docker
 - follow digital ocean ubunt 18 tut

fix perms issue 
https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue

install  docker compose
https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04


run composer install on github fork
https://github.com/rtloeffler/docker/tree/master/.examples/docker-compose/with-nginx-proxy-self-signed-ssl/mariadb/fpm
add the external volumes in the docker-compose file
      - /media/rtloeffler:/media/rtloeffler:rw
      - /media/capearson83:/media/capearson83:rw


run this
sudo docker-compose exec --user www-data app php occ config:system:set overwriteprotocol --value="https"

install jellyfin
https://jellyfin.org/docs/general/administration/installing.html#ubuntu
setup jellyfin
http://127.0.0.1:8096/web/index.html?start=wizard#!/wizardstart.html
add to composer install with domain? 


mount drives
sudo mkdir /media/nas
sudo mkdir /media/rtloeffler
sudo mkdir /media/capearson83
sudo chown rtloeffler:rtloeffler /media/nas/
sudo chmod 777 /media/nas
sudo usermod -a -G rtloeffler jellyfin
(super hacky and not good but it works for now)


sudo chown www-data:www-data /media/rtloeffler
sudo chown www-data:www-data /media/capearson83
sudo nano /etc/fstab
<>
//192.168.50.234/Public /media/nas cifs username=admin,password=,uid=rtloeffler,gid=rtloeffler 0 0
//192.168.50.234/rtloeffler /media/rtloeffler cifs username=admin,password=,uid=www-data,gid=www-data 0 0
//192.168.50.234/capearson83 /media/capearson83 cifs username=admin,password=,uid=www-data,gid=www-data 0 0

<>
sudo mount -a
