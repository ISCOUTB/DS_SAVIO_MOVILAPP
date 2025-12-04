Savio App
=================

Savio App es la aplicación móvil oficial de la Universidad Tecnológica de Bolívar (UTB), desarrollada sobre la base de la aplicación móvil original de Moodle. La aplicación tiene una interfaz que usa los colores de la identidad institucional, y permite recibir notificaciones en tiempo real sobre entregas, eventos y novedades académicas.

Además, puede ser instalada coexistiendo con la aplicación original de Moodle, ya que se cambió el nombre de paquete de Android a `com.utb.savioapp` para que el sistema la reconozca como una aplicación diferente.

* [Universidad Tecnologica de Bolivar](https://www.utb.edu.co/)
* [Proyecto original](https://github.com/moodlehq/moodleapp)


Configuración del entorno de compilación:
=================
* Instalar git
  * En Windows, instalar con git bash incluido
* Instalar un navegador basado en Chromium, como puede ser el propio Chromium, Google Chrome, Microsoft Edge, Opera, Brave, etc. Firefox no funcionará. Si ya tienes instalado alguno de estos, ignora este paso.
* Instalar nvm
  * En Linux (Ubuntu/Debian) se instala con alguno de estos comandos:
    * `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash`
    * `wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash`
  * En Windows, debe instalar nvm-windows desde: https://github.com/coreybutler/nvm-windows/releases/download/1.2.2/nvm-setup.exe
* Clonar este repositorio: `git clone https://github.com/ISCOUTB/DS_SAVIO_MOVILAPP`
* Entrar a la carpeta raíz con `cd DS_SAVIO_MOVILAPP` y ejecutar `nvm install`
  * En Windows, ejecutar en su lugar: `nvm install lts`
* Configurar la version a usar de nodeJs: `nvm use lts/jod`
* Instalar todos los paquetes con: `npm install`
  * Por si acaso, ejecutar `npx ionic`, y presionar la tecla y para aceptar su instalacion
* Instalar Android Studio desde su página web y descargar el SDK con las platform tools, las build tools y command line tools. Opcionalmente, instalar el emulador
* Crear una variable llamada ANDROID_HOME, y ponerle de valor la ruta del SDK
* Añadir al PATH las siguientes carpetas que estan dentro del SDK:
  * platform-tools
  * cmdline-tools/latest/bin
  * emulator (si se instaló)
* Descargar el JDK 21
  * En Windows, se instala desde: https://download.oracle.com/java/21/latest/jdk-21_windows-x64_bin.exe
  * En Linux, se debe descargar y añadir manualmente la carpeta bin del JDK al PATH
  * Buscar una version mas reciente de ser necesario. Las pruebas se realizaron con el JDK 21.
* Crear una variable llamada JAVA_HOME, con la ruta del JDK
* Descargar Gradle: https://gradle.org/next-steps/?version=9.1.0&format=bin. Funciona tanto para Linux como para Windows. Buscar una version mas reciente de ser necesario. Las pruebas se realizaron con Gradle 9.1.0.
* Descomprimir el archivo y añadir la carpeta bin al PATH
* Configurar la memoria máxima que puede usar nodeJs: `echo 'export NODE_OPTIONS="--max-old-space-size=capacity"' >> ~/.bashrc` , donde `capacity` debe ser `4096` mínimo, es decir, 4GB de RAM. Se recomienda el valor de `8192`, es decir, 8GB.
* Compilar para Android con `npm run prod:android`

En Windows: se debe usar el git bash, pues en CMD o PowerShell no funcionará el comando de compilación debido a que los scripts de npm usan la sintaxis de bash.

También se debe configurar que los scripts de npm se ejecuten con bash, lo cual se puede hacer con: `npm config set script-shell "C:\\Program Files\\git\\bin\\bash.exe"`. Solo es necesario hacerlo una vez.

Si hay algun error con las versiones de los paquetes, actualizarlos con: `npm update`


Actualizar la rama del fork con los commits del repositorio original
===========================

Para sincronizar manualmente el fork, lo único que hay que hacer es, desde la interfaz de GitHub, hacer clic sobre "Sync Fork" y después en "Update Branch". Al hacerlo, se hará un merge instantáneo de los commits del upstream (repositorio original) en el fork.

<img width="818" height="316" alt="syncfork" src="https://github.com/user-attachments/assets/ad82feb0-d066-45eb-9bfb-dec5479aa681" />

Cabe destacar que en la rama "main" se programó un **action** llamado **Sync upstream weekly** con el cual se sincronizan semanalmente tanto la rama main de este fork como la rama utb. De esta forma, cada domingo a las 00:00 UTC se traerán los commits nuevos del repositorio original (upstream) a estas ramas. Los commits realizados mediante el workflow aparecen realizados por `github-actions[bot]`. Leer la siguiente sección.

## Solucionar conflictos entre commits
Si al intentar sincronizar manualmente aparece un mensaje "This branch has conflicts that must be resolved", o cuando el workflow falla, significa que algunos commits del upstream están haciendo conflicto con los del fork, por lo que es necesario especificar como se debe llevar a cabo el merge. En este caso, la única solución posible es usar la consola de comandos junto con el editor de código.

Los pasos para resolver el conflicto en Visual Studio Code son los siguientes:

* Primero, creamos un branch de prueba, para probar el merge antes de llevarlo al branch: `git checkout -b prueba utb`
* A continuación, se obtienen los cambios hechos en el repositorio original: `git pull https://github.com/moodlehq/moodleapp main --no-rebase`

Ahora, como se ve en la siguiente imagen, aparecerán archivos en conflicto, en color rojo y marcados con un signo de exclamación !. Los archivos en amarillo con una M al lado son aquellos que se modificaron pero no presentan conflictos:

<img width="326" height="133" alt="Screenshot from 2025-10-12 14-46-13" src="https://github.com/user-attachments/assets/c1553be2-8424-45bc-9c5e-6bee1afa70d4" />

* Lo que se debe hacer es abrir cada uno de los ficheros en conflicto, y navegar hasta las secciones problemáticas, como se ve en la siguiente imagen:

<img width="799" height="225" alt="Screenshot from 2025-10-12 15-01-05" src="https://github.com/user-attachments/assets/55d5389d-80d6-4ed9-8bea-0e592bd3b779" />

Como se puede ver, hay varios botones disponibles en la parte superior. Los que nos interesan son: "Accept Current Change" para aceptar lo que ya estaba, o "Accept Incoming Change" para aceptar el cambio que vino del upstream. Se marca la que se desea conservar, y se guarda el archivo en File -> Save.

* Una vez resuelto el archivo, se debe ejecutar `git add archivo`. Se repite este proceso de revision con todos los ficheros problemáticos, y se ejecuta `git add` por cada uno.

Nota: si hay demasiados conflictos en un solo archivo, y únicamente interesa una de las versiones, se puede optar por descargar dicha version desde el repositorio original y reemplazarla. Asi nos evitamos tener que seleccionar muchas veces la opcion "Accept Incoming Change" o "Accept Current Change".

Una vez resuelto todo, hay que continuar el merge con `git merge --continue`.
Despues, se hacen las respectivas pruebas para ver si el branch funciona adecuadamente, y una vez comprobado que sí, se combinan esos cambios en la rama utb:
* `git switch utb`
* `git merge prueba`
* `git push`

Ahora se puede borrar la rama prueba.

License
-------

[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)
