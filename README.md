Savio App
=================

Savio App es la aplicación móvil oficial de la Universidad Tecnológica de Bolívar (UTB), desarrollada sobre la base de la plataforma Moodle. . La aplicación permite recibir notificaciones en tiempo real sobre entregas, mensajes, eventos y novedades académicas.

* [Universidad Tecnologica de Bolivar](https://www.utb.edu.co/)
* [Proyecto original](https://github.com/moodlehq/moodleapp)

Proceso de instalación:
=================
* instalar git, con git bash incluido
* instalar nvm-windows desde: https://github.com/coreybutler/nvm-windows/releases/download/1.2.2/nvm-setup.exe
* clonar el repositorio: git clone https://github.com/ISCOUTB/DS_SAVIO_MOVILAPP
* instalar node js con el comando: nvm install lts
* instalar todos los paquetes con: npm install
* instalar android studio y descargar el SDK, las platform tools, las build tools y command line tools
* descargar el jdk 21 desde: https://download.oracle.com/java/21/latest/jdk-21_windows-x64_bin.exe
* descargar gradle: https://gradle.org/next-steps/?version=9.1.0&format=bin
* Una vez descargados los tres ultimos, ir a las variables de entorno del sistema, meter todas las carpetas al path y crear una variable ANDROID_HOME.
* debido a que hay comandos que tienen la sintaxis de Linux y no funcionan en Windows, toca usar el git bash. Tambien hay que ejecutar: npm config set script-shell "C:\\Program Files\\git\\bin\\bash.exe" para que funcione bien
* si hay algun error, ejecutar: npm update
License
-------

[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)
