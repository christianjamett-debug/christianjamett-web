# Christian Jamett · web

Sitio estático de una sola página (`index.html`, HTML + CSS + JS sin build) para el fotógrafo **Christian Jamett**. Reemplazará a christianjamett.com, que hoy es un WordPress. El usuario escribe en español; responder en español.

## Dirección de diseño
- Es una **casi copia de https://www.albertopolophotography.com/** (misma fuente, mismo minimalismo), con las fotos y las categorías de Christian.
- Rutas con hash: `#/serie`, `#/venta/id`, `#/blog/slug`.
- Idiomas ES / IT / FR / EN con el helper `t({es,it,fr,en})`.
- Datos dentro del HTML:
  - `paginas`: series de fotos.
  - `productos`: tienda "For sale", con `tipo` y precio en `clp` y `usd`.
  - `entradas`: blog.
  - `pieDe`: pie de cada foto con lugar y año, investigado en Instagram y Getty.
- **Inicio**: solo la foto de portada (`paginas['']`), también en escritorio; sin carrusel.
- **Carrusel** (series): suave, con el pie fijo (no se mueve con las fotos). Funciones `avanzar()`, `actualizarPie()` y `actualizarProgreso()`.
- **Tienda**:
  - Grilla continua sin huecos. Los grupos no se parten entre filas (`noPartirGrupos()`).
  - Productos ordenados por tamaño, todos con USD aproximado.
  - Abu cuesta 20.000 CLP y Diaspora 25.000 CLP. El cuadro Afrodescendiente y Apocalipsis de las postales van como "Consultar".
- **Móvil**:
  - Menú minimalista con el nombre en desenfoque (blur) detrás.
  - En el inicio, una sola foto estática horizontal, centrada abajo, sin scroll.
  - "Cintas" tipo scotch (`cintas()`).
- **Blog**: rediseñado, más dinámico (`vistaBlog()`, `vistaEntrada()`).

## Recursos
- `img/` tiene unas 208 fotos (97 MB), bajadas del WordPress con la misma ruta (`img/2022/06/1.jpg`). Constante `const U = 'img/'`.

## Cómo verla en local
```
python -m http.server 5180 --bind 127.0.0.1
```
Para verla en el celular por la red local, usar `--bind 0.0.0.0` (puerto 5181).

## Publicación
- Repo git **privado**: https://github.com/sleyeerz-byte/christianjamett-web (rama `main`). El push usa Git Credential Manager; no hay `gh`.
- **Pendiente:** publicar en Cloudflare Pages, en la cuenta Sleyeerz@gmail.com, la misma de la pizzería. La app de GitHub de Cloudflare solo tiene acceso al repo `carusoweb`; hay que darle acceso a este repo.
- **Dominio christianjamett.com**:
  - No está en NIC Chile. Lo registra PDR, con DNS en sitiodns.net (el hosting del WordPress) y vence el 2027-06-04.
  - El correo info@ depende de sus MX. **Al mover el DNS a Cloudflare, copiar los MX** para no cortar el correo.
  - Falta el acceso al panel del hosting.
- christianjamett.cl está en NIC Chile, también con DNS en sitiodns.
- Nunca iniciar sesión con contraseñas por el usuario: que entre él y después se revisa.
