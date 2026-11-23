# KHAOS · HOLOGRAPHIC ENGINE

Versión preparada para GitHub Pages a partir del motor original. `index.html` conserva el holograma, Three.js, el runtime KHAOS 5.5 incrustado, Semilla 1, ATM01, controles y carga de experimentos JSON. `KHAOS_HOLOGRAPHIC_ENGINE.original.html` es la copia sin modificar recibida como fuente.

## Publicación con GitHub Pages

1. Sube el contenido de esta carpeta a la raíz de un repositorio GitHub (o copia estos archivos a la raíz del repositorio que quieras usar).
2. En GitHub, abre **Settings → Pages**.
3. En **Build and deployment**, selecciona **Deploy from a branch**, elige la rama principal y la carpeta **/(root)**; guarda.
4. Espera a que GitHub Pages publique el sitio. La dirección de un repositorio de proyecto suele tener el formato `https://USUARIO.github.io/REPOSITORIO/`.
5. Abre esa dirección en Chrome para Android. Confirma que la barra indica HTTPS.

La sesión de trabajo no tenía un checkout de este proyecto ni una conexión GitHub seleccionada, por lo que no se pudo activar Pages ni determinar el dominio final.

## Cámara

La aplicación no pide permiso al cargar. Pulsa **Autorizar cámara** para solicitar vídeo sin audio directamente desde el documento principal. Prefiere `facingMode: user`, muestra el flujo en `cameraVideo` y, si está disponible, inicializa MediaPipe Hands para los gestos. `window.isSecureContext`, `navigator.mediaDevices` y el estado de permiso se consultan con comprobaciones compatibles; la consulta de `Permissions API` puede no estar implementada en todos los navegadores.

Si el permiso está denegado, sigue las indicaciones en pantalla: menú de Chrome → Configuración → Configuración de sitios → Cámara → dominio publicado → Permitir. Regresa y pulsa **Volver a intentar**. La web no dispone de una API compatible para abrir directamente esa pantalla de configuración.

El iframe oculto `sourceFrame` aloja únicamente el runtime KHAOS 5.5 y no captura vídeo; la llamada a `getUserMedia()` permanece en la página superior. No necesita delegación de permiso de cámara.

## Verificación

- Antes de publicar, se puede abrir el HTML localmente para comprobar el holograma, pero los navegadores normalmente restringen la cámara en `file://`.
- Después de publicar por HTTPS, abre el sitio en Chrome Android, toca **Autorizar cámara** y acepta el diálogo nativo.
- Confirma el estado **CÁMARA FRONTAL · ACTIVA**, la imagen de la cámara y los gestos. Para verificar el funcionamiento sin cámara, usa **Continuar sin cámara** y comprueba el holograma y sus controles.
- Esta entrega no afirma una prueba física en Android; requiere realizarla desde el teléfono.

## Dependencias externas

Three.js y MediaPipe Hands se cargan desde el runtime original y jsDelivr; se necesita conexión de red para descargarlos. No se añadió service worker porque no se requiere para HTTPS ni para el acceso a la cámara y el runtime depende de recursos CDN.
