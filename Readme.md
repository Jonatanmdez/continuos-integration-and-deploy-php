# Instalar [Dokku](https://github.com/dokku/dokku)

Ejecutar como sudo:

```
wget https://raw.githubusercontent.com/dokku/dokku/v0.14.6/bootstrap.sh
sudo DOKKU_TAG=v0.14.6 bash bootstrap.sh
```

Luego es simplemente esperar,dokku nos prepara el entorno de docker y 
todo lo que necesitamos para desplegarlos servicios que vamos a utilizar 

Una vez finalizado, simplemente tendremos que entrar al dominio / IP 
donde hemos instalado para configurarlo. En mi caso mi forma favorita
es con subdominios, de la forma *.domain.ext pero tambien sirve con domain.ext/*

# Extender Dokku

Una vez instalado Dokku nos falta empezar a meterle servicios. Aqui tenemos un listado de [plugins para dokku](https://github.com/dokku/dokku/blob/master/docs/community/plugins.md)

## Limitar recursos por instancia de docker

Para mi el primer plugins a instalar es [Dokku Limit](https://github.com/sarendsen/dokku-limit) es un plugin para limitar los recursos que te puede consumir cada Docker antes de considerarlo defectuoso y tirarlo y volver a levantar. 

```
sudo dokku plugin:install https://github.com/sarendsen/dokku-limit.git limit
```

Con eso ya lo tenemos instalado. Por defecto da a cada instancia un máximo de 1 GB (se puede ampliar/reducir por aplicacion-servicio), seran simplemente los valores por defecto para las nuevas maquinas

## Sentry 

Sentry es un programa de monitorización de errores. De manera, que quede registro de todos los errores en tiempo de ejecución con un traza de log. Previamente necesitariamos tener instalados como servicio:
* postgres
* redis
* memcache
* letsencrypt

```
sudo dokku plugin:install https://github.com/dokku/dokku-postgres.git postgres
sudo dokku plugin:install https://github.com/dokku/dokku-redis.git redis
sudo dokku plugin:install https://github.com/dokku/dokku-memcached.git memcached
sudo dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git
```
Y crear la carpeta services y darle permisos a dokku, que es donde se guardan los servicios por defecto:
```
mkdir /var/lib/dokku/services
chown -R dokku:dokku /var/lib/dokku/services

Para instalarlo, simplemente seguir el manual de [dokku-sentry](https://github.com/Jonatanmdez/dokku-sentry)

