# Campus ISFD 84 · Mi app

App personal de estudio: accesos rápidos al campus real del ISFD N°84 y a Autogestión (ETNA), agenda con repeticiones y calendario, horario semanal y materias. **No pide ni guarda tu usuario o contraseña del campus** y no es la app oficial del instituto.

Funciona sin cuenta (los datos quedan en el teléfono) y, opcionalmente, con una cuenta propia de la app para guardar los datos en la nube y usarlos en varios dispositivos.

## Archivos

`index.html`, `manifest.webmanifest`, `sw.js` y los seis íconos (`icon-180.png`, `icon-192.png`, `icon-512.png` y sus versiones `-dark`) → se suben a GitHub Pages.
`firestore.rules` → son las reglas de la base de datos (ya cargadas en Firebase; es solo una copia por si hace falta volver a pegarlas).

## Publicarla en GitHub Pages (desde el celular)

1. Entrá a github.com con tu cuenta y tocá **+ → New repository**.
2. Nombre: `campus84` (o el que quieras). Dejalo **Public** y tocá **Create repository**.
3. En el repositorio nuevo tocá **Add file → Upload files** y subí todos los archivos de arriba (menos `firestore.rules` y `README.md`, que son opcionales), juntos, en la raíz y sin carpetas.
4. Tocá **Commit changes**.
5. Andá a **Settings → Pages**. En *Build and deployment* elegí **Deploy from a branch**, rama **main**, carpeta **/ (root)** y tocá **Save**.
6. Esperá 1–2 minutos. Tu app queda en `https://TU-USUARIO.github.io/campus84/`.

> Si tu celular no te deja elegir varios archivos a la vez, subilos de a uno repitiendo **Add file → Upload files**.

## Instalarla en el iPhone

1. Abrí la dirección en **Safari**.
2. Tocá **Compartir → Agregar a pantalla de inicio**.
3. Se abre como una app, a pantalla completa y también sin conexión.

**Logo e ícono según el modo:** dentro de la app el logo cambia solo entre versión clara y oscura (sigue al teléfono o a lo que elijas en Campus → Apariencia). El ícono de la pantalla de inicio queda fijo al momento de agregarlo: si el iPhone está en modo oscuro, se usa el ícono oscuro; si está en claro, el claro. Para cambiarlo, borrá el ícono de inicio y volvé a agregarlo con el modo que quieras. Los estilos «Tinted» y «Clear» de iOS los aplica el propio iPhone sobre el ícono.

## Cuentas y datos en la nube

- Cada persona crea su cuenta con su mail y una contraseña propia (no la del campus). Se manda un mail para confirmar la dirección.
- Cada cuenta tiene un único documento en Firestore (`users/<id>`) con sus materias, horarios, eventos y enlaces. Las reglas de `firestore.rules` impiden que alguien lea o escriba el de otra persona.
- No se sincronizan los ajustes de apariencia (son de cada dispositivo).
- Si los datos de la cuenta y los del dispositivo no coinciden, la app pregunta qué conservar o permite juntarlos.
- Desde **Campus → Cuenta** se puede cerrar sesión (conservando o borrando los datos del dispositivo) y **eliminar la cuenta**, que borra el usuario y sus datos de la nube.
- La configuración de Firebase (`apiKey` y `projectId`) está dentro de `index.html`, en la línea `var FB=…`. No son secretos: la seguridad la dan las reglas.

### Recomendado: limitar la clave de Firebase a tu página (opcional)

En console.cloud.google.com → *APIs y servicios → Credenciales* → la clave de navegador de tu proyecto → *Restricciones de la aplicación* → **Sitios web** → agregá `https://TU-USUARIO.github.io/*`. Si además restringís por API, dejá habilitadas: Identity Toolkit API, Token Service API y Cloud Firestore API. Probá el ingreso después de guardar.

## Avisos en el Calendario del iPhone

En **Campus → Avisos en el Calendario** elegís qué mandar (eventos de la agenda, clases del horario), cuándo querés que te avise y hasta qué fecha se repiten las clases. Al tocar **Enviar al Calendario** se abre la hoja de compartir del iPhone con un archivo `.ics`; abrilo con Calendario (o guardalo en Archivos y tocalo) y agregá los eventos. Desde ahí el iPhone avisa solo, aunque la app esté cerrada y sin internet.

- Conviene agregarlos en un calendario aparte (por ejemplo «Campus»): si más adelante cambiás cosas y volvés a mandar, borrás ese calendario y no quedan repetidos.
- Cada evento también tiene su botón **Agregar al Calendario del iPhone** (al abrirlo desde la Agenda).
- Si la hoja de compartir no aparece, usá **Descargar el archivo (.ics)**.
- No hay ningún servidor de por medio: el archivo se arma en tu teléfono.

## Importar fechas (mesas de examen, parciales, entregas)

En **Agenda → Importar** (o en Campus) pegás el listado que tengas (de ETNA, de un mail, de un chat) o elegís un archivo `.ics`, `.csv` o `.txt`. La app detecta fechas y horas (`10/12/2026`, `10 de diciembre`, `2026-12-10`, `18:30`, `18 hs`…), adivina la materia por el nombre y te muestra una vista previa para destildar lo que no quieras. Las fechas que ya están en tu agenda aparecen marcadas y no se agregan de nuevo. Si tenés una captura de pantalla, mantené apretado el texto en la imagen, copialo y pegalo.

## Actualizar

Subí el `index.html` nuevo con **Add file → Upload files** (reemplaza al anterior). La app se actualiza sola la próxima vez que la abras con internet; si no, cerrala del todo y abrila de nuevo.

## Tus datos

Sin cuenta se guardan en el navegador del dispositivo. La app instalada en la pantalla de inicio y la abierta en Safari guardan datos por separado: usá **Campus → Copia de seguridad** o una cuenta para pasarlos de una a otra.
