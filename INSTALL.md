# Instalación de Dolar Satoshi
En esta sección verás la manera más sencilla de desplegar en firebase un sitio de contenido estático hecho en React JS.

Para alojar tu sitio, debes instalar primeramente [Node.js](https://nodejs.org/) y luego las herramientas de línea de comandos de Firebase mediante npm, a continuación se muestran los comandos necesarios para realizar cada paso, el símbolo $ indica el prompt de linux o mac, el '#' indica comentario, si estás haciendo esto en windows simplemente ignóralo.
```
$ npm install -g firebase-tools
```
## Descarga el sitio
Puedes instalar git o descargar directamente los archivos de github en este [link](https://github.com/vegnoll/dolarsatoshi/archive/master.zip)
```
# con git
git clone https://github.com/vegnoll/dolarsatoshi.git
```
Una vez descargado el directorio se llama dolarsatoshi, entramos y descargamos las dependencias.
```
$ cd dolarsatoshi
$ npm install
```
## Firebase
Firebase es un servicio de google que utilizaremos para alojar gratis nuestro sitio, es absolutamente necesario que crees una nueva cuenta de google que no tenga ninguna relación contigo y que no debes usar NUNCA si utilizas CANTV o movilnet, también se recomienda cambiar tus DNS a 1.1.1.1 y 1.0.0.1 y usar una VPN.

Ahora vamos al sitio [firebase](https://console.firebase.google.com) entramos con nuestra nueva cuenta de google y creamos el proyecto dolar satoshi.

Una vez instaladas las tools y creada la nueva cuenta de firebase volvamos a nuestro terminal.
```
# primero nos logueamos a firebase desde la terminal
$ firebase login
# en el directorio donde se encuentra dolar satoshi
$ firebase init
```
En la pregunta `Which Firebase CLI features do you want to setup for this folder?` seleccionamos hosting, luego en `Select a default Firebase project for this directory` seleccionamos el proyecto que recientemente creamos.

En `What do you want to use as your public directory?` dejamos public y en las siguientes preguntas respondemos N.
## Local testing
Puedes ver el sitio funcionar en tu propia máquina ejecutando un solo comando.
```
$ npm run start
```
Ahora puedes modificarlo a tu antojo, es open source :)
## Deploy
Desplegar el código es bastante sencillo solo debes preparar los archivos necesarios con un comando y luego subirlos a firebase con otro comando, pero antes debes modificar tu archivo firebase.json e indicarle que el código que va a ir a producción será el que genere el comando build de react.
```
{
  "hosting": {
    "public": "build", // en esta línea cambiamos public por build
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ]
  }
}
```
Luego ejecutamos los comandos:
```
$ npm run build
$ firebase deploy
```
Eso es todo, firebase te indica la url del sitio, ya eres un [terrorista](https://twitter.com/MinpublicoVE/status/987662317830713346).
