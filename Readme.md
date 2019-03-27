# Install [Dokku](https://github.com/dokku/dokku)

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
