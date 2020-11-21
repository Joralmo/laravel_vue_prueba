* [x] generar key publica y privada => ssh-keygen -t rsa (NO CONFIGURAR CONTRASEÑA)
* [x] Enviar la clave publica al host
* [x] Guardar key publica en hostinger (en mi caso)
* [x] En caso de ser un servidor diferente al que te vas a conectar, se hace por medio de los siguientes comandos:
  * ssh -p PUERTO -i ./key USUARIO@DIRECCION_HOST mkdir -p .ssh
  * cat key.pub | ssh -i ./key -p PUERTO -oStrictHostKeyChecking=no USUARIO@DIRECCION_HOST 'cat >>   .ssh/authorized_keys'
  * ssh -p PUERTO -i ./key USUARIO@DIRECCION_HOST "chmod 700 .ssh; chmod 640 .ssh/authorized_keys"
* [x] configurar .htaccess en el host:
  ```
    RewriteEngine on
    RewriteCond %{REQUEST_URI} !^public
    RewriteRule ^(.*)$ public/$1 [L]
  ```
* [x] configurar secrests en github:
  * ENV
  * REMOTE_HOST
  * REMOTE_PORT
  * REMOTE_USER
  * SERVER_SSH_KEY
  * TARGET
* [x] configurar .github/workflows/push.yml


# Update
### En el archivo .github/workflows/push.yml se agrega un paso extra gracias a la contribución de [@kiviev](https://github.com/kiviev) para correr las migraciones una vez desplegado, para este paso es necesario actualizar el secret ENV y agregar los accesos correctos a la base de datos de hostinger.
