* [ ] generar key publica y privada => ssh-keygen -t rsa (NO CONFIGURAR CONTRASEÑA)
* [ ] Enviar la clave publica al host
* [ ] Guardar key publica en hostinger (en mi caso)
* [ ] En caso de ser un servidor diferente al que te vas a conectar, se hace por medio de los siguientes comandos:
  * ssh -p PUERTO -i ./key USUARIO@DIRECCION_HOST mkdir -p .ssh
  * cat key.pub | ssh -i ./key -p PUERTO -oStrictHostKeyChecking=no USUARIO@DIRECCION_HOST 'cat >>   .ssh/authorized_keys'
  * ssh -p PUERTO -i ./key USUARIO@DIRECCION_HOST "chmod 700 .ssh; chmod 640 .ssh/authorized_keys"
* [ ] configurar .htaccess en el host
* [ ] configurar secrests en github:
  * ENV
  * REMOTE_HOST
  * REMOTE_PORT
  * REMOTE_USER
  * SERVER_SSH_KEY
  * TARGET
* [ ] configurar .github/workflows/push.yml