# Copilot Instructions for Savio App

## Arquitectura general
- App móvil basada en Ionic + Angular, sobre la plataforma Moodle.
- Estructura modular: cada funcionalidad principal está en `src/addons/`, `src/core/`, y subcarpetas como `features`, `app`, `assets`, `theme`, etc.
- Plugins Cordova personalizados en `cordova-plugin-moodleapp/` y otros en `plugins/`.
- Integración con servicios Moodle y notificaciones push.
- Flujos de datos: la app consume APIs de Moodle, gestiona sesiones y muestra información académica en tiempo real.

## Flujo de compilación y desarrollo
- Instalar dependencias con `npm install`.
- Compilar para Android con `npm run prod:android` (requiere entorno Android Studio, JDK 21, Gradle, variables ANDROID_HOME y JAVA_HOME configuradas).
- En Windows, ejecutar scripts npm con Bash:
  - Configura: `npm config set script-shell "C:\\Program Files\\git\\bin\\bash.exe"`
- Si hay errores de paquetes, actualiza con `npm update`.
- Los scripts de build están en `gulp/` y `scripts/`.

## Convenciones y patrones
- Uso intensivo de servicios Angular para comunicación entre componentes y acceso a datos.
- Los componentes de login y reconexión gestionan la visibilidad de la URL del sitio mediante la variable `displaySiteUrl`.
- Los plugins Cordova se desarrollan y configuran en `cordova-plugin-moodleapp/` y `plugin.xml`.
- Configuración de la app en `config.xml`, `ionic.config.json`, y archivos de entorno en la raíz.
- Los assets y recursos se ubican en `resources/` y `src/assets/`.

## Integraciones y dependencias
- Integración con Moodle a través de APIs y notificaciones push.
- Dependencias principales: Ionic, Angular, Cordova, plugins personalizados y de terceros.
- Configuración de Android y iOS en `platforms/` y `resources/`.

## Ejemplo de flujo de trabajo
1. Modifica el código en `src/` o plugins Cordova.
2. Ejecuta `npm install` si hay cambios en dependencias.
3. Compila con `npm run prod:android` usando Bash.
4. Verifica el resultado en un emulador o dispositivo Android.

## Archivos clave
- `src/`: código fuente principal.
- `cordova-plugin-moodleapp/`: plugin Cordova personalizado.
- `gulp/`, `scripts/`: scripts de build y utilidades.
- `config.xml`, `ionic.config.json`: configuración de la app.
- `README.md`: guía de instalación y compilación.

---
Actualiza estas instrucciones si cambian los flujos de trabajo, dependencias o arquitectura.
