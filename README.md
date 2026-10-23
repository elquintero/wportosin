# Cafetería Portosín (maqueta PWA)

Web responsive y PWA instalable. El contenido (textos, menú del día e imágenes) vive en un `data.json` dentro de un repositorio de GitHub, y la rueda ⚙ de la cabecera abre el panel de administrador. Hay un único administrador: quien tenga el token.

## Puesta en marcha

1. **Repositorio de la web** (público, GitHub Pages): sube `index.html`, `sw.js`, `manifest.webmanifest`, `config.json`, `data.json`, `logo.png`, `logo-white.png`, `icon-192.png` e `icon-512.png`. En *Settings → Pages* elige `main` y `/ (root)`.
2. **Repositorio de datos**: crea `portosin-data` y sube `data.json`. Edita `config.json` con `usuario/portosin-data`.
   - Debe ser **público** para que los clientes puedan leer el menú sin token. El token solo protege la **escritura**: nadie puede modificar la web sin él. Si lo pones privado, los visitantes verán únicamente la copia `data.json` incluida en la web (que no se actualiza al editar).
   - Mejor que sea un repositorio distinto al de la web: cada guardado hace un commit y Pages se reconstruiría cada vez.
3. **Token**: GitHub → Settings → Developer settings → Fine-grained tokens. *Only select repositories* → `portosin-data`, permiso **Contents: Read and write**, con caducidad (p. ej. 90 días).
4. En la web pulsa ⚙ → pega el token → *Guardar y comprobar*. A partir de ahí, ⚙ abre Inicio, Carta, Galería, Contacto y Conexión. Repite en cada dispositivo desde el que quieras administrar.

## Edición diaria del menú

⚙ → Carta: un plato por línea, postres, precios, nota y casillas de publicar/mostrar fecha. Se guarda solo (commit en `data.json`).

## Imágenes

Se reducen a máx. 1280 px (1600 la portada) en JPEG y se guardan dentro de `data.json` como data URL. Las imágenes de ejemplo son las de cafedelborn.com enlazadas por URL; al cambiarlas se sustituyen por las tuyas. Si el JSON crece mucho (varios MB), la carga se vuelve lenta: en ese caso conviene pasar a ficheros de imagen en el repositorio.

## Mover la web a otro sitio

Solo hay que cambiar el `repo` en `config.json`: los datos siguen en GitHub.

## Actualizar la app

Sube los ficheros nuevos y cambia `V='portosin-v1'` en `sw.js` para limpiar cachés antiguas.
