# investy_landing

Sitio público de Investy: `https://investyapp.com`. Una sola página estática, sin
build y sin dependencias — `index.html` con el CSS adentro.

## Por qué existe este repo y no una carpeta

- **No va en el meta-repo:** publicar con Cloudflare Pages exige darle acceso de
  lectura al repositorio, y el meta contiene los informes legales, los números de
  costos y credenciales de sandbox. No hay motivo para exponer eso por una página
  estática.
- **No va en `investy_frontend`:** ese repo es la app Flutter; un sitio estático
  adentro le ensucia el propósito y el build.

## Qué puede y qué no puede decir esta página

El texto sigue `docs/brand/encuadre-legal.md` del meta-repo, actualizado con la
investigación legal de B158. En resumen, **no** se usa: *asesor* / *asesoría*,
*recomendaciones personalizadas*, *encaja con tu perfil*, *retorno esperado*,
ni ninguna mención de bróker, custodia o cuentas segregadas. Owl se describe como
que *propone activos para practicar en el simulador y explica cada uno*.

La **leyenda del art. 2.40.1.1.2 del Decreto 2555** va en la página y no se saca.

Antes de cambiar una frase, leer esa tabla. Es la misma razón por la que hubo que
reemitir el PDF de campaña (B98, B158).

## Publicación

Cloudflare Pages, conectado a este repositorio; el dominio ya usa los nameservers
de Cloudflare (`aron.ns.cloudflare.com`, `nicolas.ns.cloudflare.com`). Al
publicarlo hay que **quitar la Redirect Rule que manda `investyapp.com` al
formulario de Tally** (B166) y apuntar el dominio al proyecto de Pages.

Cada push a `main` republica. No hay comando de build: *framework preset* = None,
directorio de salida = la raíz.

## Verificar antes de publicar

```bash
python3 -m http.server 8000   # y abrir http://localhost:8000
```
