# Campus ISFD 84 · Mi app

App personal de estudio: accesos rápidos al campus real del ISFD N°84 y a Autogestión (ETNA), agenda con repeticiones y calendario, horario semanal y materias. **No pide ni guarda tu usuario o contraseña del campus** y no es la app oficial del instituto.

Funciona sin cuenta (los datos quedan en el teléfono) y, opcionalmente, con una cuenta propia de la app para guardar los datos en la nube y usarlos en varios dispositivos.

## Archivos

`index.html`, `manifest.webmanifest`, `sw.js`, `icon-180.png`, `icon-192.png`, `icon-512.png` → se suben a GitHub Pages.
`firestore.rules` → son las reglas de la base de datos (ya cargadas en Firebase; es solo una copia por si hace falta volver a pegarlas).

## Publicarla en GitHub Pages (desde el celular)

1. Entrá a github.com con tu cuenta y tocá **+ → New repository**.
2. Nombre: `campus84` (o el que quieras). Dejalo **Public** y tocá **Create repository**.
3. En el repositorio nuevo tocá **Add file → Upload files** y subí los 6 archivos de arriba, todos juntos, en la raíz y sin carpetas.
4. Tocá **Commit changes**.
5. Andá a **Settings → Pages**. En *Build and deployment* elegí **Deploy from a branch**, rama **main**, carpeta **/ (root)** y tocá **Save**.
6. Esperá 1–2 minutos. Tu app queda en `https://TU-USUARIO.github.io/campus84/`.

> Si tu celular no te deja elegir varios archivos a la vez, subilos de a uno repitiendo **Add file → Upload files**.

## Instalarla en el iPhone

1. Abrí la dirección en **Safari**.
2. Tocá **Compartir → Agregar a pantalla de inicio**.
3. Se abre como una app, a pantalla completa y también sin conexión.

## Cuentas y datos en la nube

- Cada persona crea su cuenta con su mail y una contraseña propia (no la del campus). Se manda un mail para confirmar la dirección.
- Cada cuenta tiene un único documento en Firestore (`users/<id>`) con sus materias, horarios, eventos y enlaces. Las reglas de `firestore.rules` impiden que alguien lea o escriba el de otra persona.
- No se sincronizan los ajustes de apariencia (son de cada dispositivo).
- Si los datos de la cuenta y los del dispositivo no coinciden, la app pregunta qué conservar o permite juntarlos.
- Desde **Campus → Cuenta** se puede cerrar sesión (conservando o borrando los datos del dispositivo) y **eliminar la cuenta**, que borra el usuario y sus datos de la nube.
- La configuración de Firebase (`apiKey` y `projectId`) está dentro de `index.html`, en la línea `var FB=…`. No son secretos: la seguridad la dan las reglas.

### Recomendado: limitar la clave de Firebase a tu página (opcional)

En console.cloud.google.com → *APIs y servicios → Credenciales* → la clave de navegador de tu proyecto → *Restricciones de la aplicación* → **Sitios web** → agregá `https://TU-USUARIO.github.io/*`. Si además restringís por API, dejá habilitadas: Identity Toolkit API, Token Service API y Cloud Firestore API. Probá el ingreso después de guardar.

## Actualizar

Subí el `index.html` nuevo con **Add file → Upload files** (reemplaza al anterior). La app se actualiza sola la próxima vez que la abras con internet; si no, cerrala del todo y abrila de nuevo.

## Tus datos

Sin cuenta se guardan en el navegador del dispositivo. La app instalada en la pantalla de inicio y la abierta en Safari guardan datos por separado: usá **Campus → Copia de seguridad** o una cuenta para pasarlos de una a otra.
