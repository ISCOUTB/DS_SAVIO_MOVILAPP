Savio App
=================

Savio App es la aplicación móvil oficial de la Universidad Tecnológica de Bolívar (UTB), desarrollada sobre la base de la plataforma Moodle. La aplicación permite recibir notificaciones en tiempo real sobre entregas, mensajes, eventos y novedades académicas.

* [Universidad Tecnologica de Bolivar](https://www.utb.edu.co/)
* [Proyecto original](https://github.com/moodlehq/moodleapp)


Configuración del entorno de compilación:
=================
* Instalar git
  * En Windows, instalar con git bash incluido
* Instalar un navegador basado en Chromium, como puede ser el propio Chromium, Google Chrome, Microsoft Edge, Opera, Brave, etc. Firefox no funcionará. Si ya tienes instalado alguno de estos, ignora este paso.
* Instalar nvm
  * En Linux (Ubuntu/Debian) se instala con alguno de estos comandos:
    * curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
    * wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
  * En Windows, debe instalar nvm-windows desde: https://github.com/coreybutler/nvm-windows/releases/download/1.2.2/nvm-setup.exe
* Clonar este repositorio: git clone https://github.com/ISCOUTB/DS_SAVIO_MOVILAPP
* Entrar a la carpeta raíz con cd DS_SAVIO_MOVILAPP y ejecutar nvm install
  * En Windows, ejecutar en su lugar: nvm install lts
* Configurar la version a usar de nodeJs:
  * nvm ls
  * Copiar el numero de version mas reciente
  * nvm use numeroversion 
* Instalar todos los paquetes con: npm install
  * Por si acaso, ejecutar npx ionic, y presionar la tecla y para aceptar su instalacion
* Instalar Android Studio y descargar el SDK con las platform tools, las build tools y command line tools. Opcionalmente, instalar el emulador
* Crear una variable llamada ANDROID_HOME, y ponerle de valor la ruta del SDK
* Añadir al PATH las siguientes carpetas que estan dentro del SDK:
  * platform-tools
  * cmdline-tools/latest/bin
  * emulator (si se instaló)
* Descargar el JDK 21
  * En Windows, se instala desde: https://download.oracle.com/java/21/latest/jdk-21_windows-x64_bin.exe
  * En Linux, se debe descargar y añadir manualmente la carpeta bin del JDK al PATH
* Crear una variable llamada JAVA_HOME, con la ruta del JDK
* Descargar gradle: https://gradle.org/next-steps/?version=9.1.0&format=bin. Funciona tanto para Linux como para Windows
* Descomprimir el archivo y añadir la carpeta bin al PATH
* Compilar con npm run prod:android


Debido a que hay comandos que tienen la sintaxis de Linux y no funcionan en Windows, toca usar el git bash. Tambien hay que ejecutar: npm config set script-shell "C:\\Program Files\\git\\bin\\bash.exe" para que funcione bien

Si hay algun error con las versiones de los paquetes, actualizarlos con: npm update

License
-------

[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)
